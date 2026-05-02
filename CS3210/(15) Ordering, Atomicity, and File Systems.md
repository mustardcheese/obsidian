## Crash Consistency

When a machine crashes mid-operation, what state is the FS in on reboot? We need two properties:

- **Ordering** — updates persist in the order we issued them
- **Atomicity** — an update fully happens or fully doesn't (no partial state)

Motivating example:

```
mkdir("/x");
open("/x/y", O_CREAT...);
```

- mkdir synced _after_ open → file inside a non-existent directory
- y's inode written but data block isn't → corruption, reads garbage
- x's dirent written before y's inode → dangling reference

### Timeline #1: write → crash → recover → read

![[Pasted image 20260428180446.png]]

A single `write()` is not one operation — it touches multiple pieces:

- Allocate new data block(s)
- Write the data
- Update the inode (size, direct pointers)

**Best case**: all three persist, read returns new data. **Worst case (partial persistent state)**:

- New block written, inode never updated → silent data loss
- Inode updated, data block contents are garbage → reads return uninitialized junk
- Connection severed but never re-established → file points to nowhere

![[Pasted image 20260428181923.png]]

### Timeline #2: two writes to two fds

![[Pasted image 20260428182319.png|400]]

Without ordering, the disk can persist writes in any interleaving. Partial writes can land in either fd; sequentiality between writes is not guaranteed.

## Disk Interface

Primitives the disk gives us:

- **read/write block** — may reorder, may buffer, _not atomic_
- **flush** — blocks until all pending I/O is synced; this is our _only_ ordering primitive

On crash: partially-written blocks are possible, and disk-head misbehavior on power-loss can corrupt blocks we weren't even writing.

## Ordering: shrinking the chaos with flush

`flush` establishes a **happens-before** relation between everything before it and everything after it.

For `n + k` writes with no flush: **(n+k)!** possible orderings. With a flush between groups of `n` and `k`: only **n! · k!** orderings.

**Proof that n! · k! ≤ (n+k)!**: The binomial coefficient C(n+k, k) = (n+k)! / (n!·k!) is a positive integer (it's in Pascal's triangle), so (n+k)! = n!·k! · (positive integer), giving (n+k)! ≥ n!·k!. Strict when n, k ≥ 1. ∎

**Takeaway**: imposing partial order via flushes provably shrinks the space of disk orderings, reducing the number of bad outcomes the FS has to defend against. Happens-before is the _only_ primitive that reduces this cardinality.

## Atomicity

We can't update in place — the disk interface won't give us atomic multi-block writes. The general approach: **make a copy, atomically commit it**. Two techniques:

1. Shadowing
2. Logging (journaling)

### Shadowing

**Idea**: reduce a multi-block update to a single atomic bit flip.

Keep two versions of the data plus a **shadow bit** that selects which is live. To update:

1. Copy current → shadow
2. Modify the shadow
3. **Flush**, then flip the shadow bit

**Crash analysis** — at every point, the data is consistent:

- Crash during copy/update: shadow bit still points to old, intact data
- Crash before bit flip: same — old data is the live one
- Crash after bit flip: new data is fully on disk (we flushed before flipping)

**Multiple chained updates**: need a flush _after_ the bit flip too, before starting the next copy. Otherwise the next update's copy could overwrite "current" before the bit flip persists, breaking the invariant.

**Sequencing per update**: shadow writes → flush → bit flip → flush (the trailing flush only needed for chaining).

**Why the bit flip is atomic**: the shadow bit lives in its own block, and a single-block write is the disk's atomic unit.

**Costs**:

- ≥ 2× space (plus the shadow-bit block, which must be on a _separate_ block so the flip is its own atomic write)
- 2 disk writes per update minimum, plus flushes
- Brutally expensive as a primary FS technique

### Logging (Journaling)

Keep a **log** (journal) of intended changes. Each entry: `(type, location, data)`. Each entry gets a **commit** record after the FS is sure the entry is on disk. Putting each entry and each commit in its own block makes commits atomic at the disk level.

**Read rules**:

- Block has a _committed_ log entry → log supersedes the data block
- Entry exists but not committed → ignore it, read the data block
- No log entry → read the data block

![[Pasted image 20260428215853.png|500]] When a commit is missing, we assume all following entries are invalid — **prefix semantics**. Disregard everything after the first missing commit. Ensures a persistent state, even if it's older.

![[Pasted image 20260428220128.png|500]] Log says committed → use log version ("Hello World").

![[Pasted image 20260428220300.png|500]] Block 6's commit is missing → can't validate → fall back to disk version.

![[Pasted image 20260428220532.png]] Flushes between writes and commits enforce happens-before, imposing partial order. Atomicity (correctness) is guaranteed at the _visibility_ level, even though the underlying disk write isn't atomic.

![[Pasted image 20260428220906.png]] We can represent the log as a DAG where flushes are edges and writes/commits are vertices.

- Why no edge (flush) between $c_1$ and $e_2$? If $e_2$ is visible, then $e_1$ must already exist, so the existence of $e_2$ is tied to the _correctness_ of $e_1$ (verified by $c_1$).

### Properties of the log

- **Implicit ordering**
    - Append-only semantics on write
    - Sequential, ordered reads on recovery
    - Logs → ordering: entry $i$ happens-before entry $i+1$
- **Atomicity**
    - The log itself provides no atomicity
    - Commits provide the atomicity
- **Orthogonality**
    - Small composable components: logs (ordering) + commits (atomicity)

We choose granularity: how many entries per commit, trading data consistency for flush count.

## Checksums

Can we do better — fewer flushes? A plain commit only signals visibility, not correctness; we can't tell an erroneous write from a malformed one.

**Insight**: piggyback correctness on the commit by using a **checksum of the entry as the commit**.

- Multiple entries can share a disk block
- Write all in one operation
- "Commit" = write the checksum; if it doesn't match the entry's contents, it isn't committed
- An entry is only committed if all entries before it are also committed (preserves prefix semantics)

![[Pasted image 20260428230041.png|500]]

Entry and commit can now be written **out of temporal order** — order in _time_ doesn't matter, only that each entry has a specific (sequential) location.

- **NOT spatial reordering**: locations are still fixed.

We've removed the flush between entry and commit and tolerated partial writes. At recovery, recompute the checksum to validate.

- Replaced flush atomicity with checksum atomicity (traded I/O for compute)
- Still prefix semantic

### What if the log gets full?

**Log merge**:

- Iterate committed entries
- Apply each to its target block
- If checksum fails on any entry → break
- Once last committed entry is applied, clear the log

**Are we immune to a crash mid-merge?**

- No — log merge is multiple non-atomic disk I/Os.
- Cases: nothing merged, all merged, partial merge with blocks updated, partial merge with blocks corrupted.

**Recovery is fine because log entries are idempotent**:

- Applying the operation multiple times yields the same result: $op(x) = op \circ op \circ \dots \circ op(x)$
- Gives us easy "at-least-once" semantics — just replay everything.

**Atomic log clear**:

- Don't need a true atomic clear — just invalidate the first entry's checksum (e.g., overwrite with `0x0000`). Prefix semantics handles the rest.
- On startup: merge the log, then clear, then continue.

## Costs / Benefits of Logging

**Benefits**

- (Performance) sequential access → very efficient writes
- (Correctness) general atomicity
- (Correctness) partial ordering — entries commit in order
- (Performance) few flushes required (with checksum commits)

**Costs**

- Doubles writes (log + final location)
- Periodic merge required
- Reads must consult log first

**Real-time AI: journaling or shadowing?**

- Probably shadowing — periodic merges introduce unpredictable latency spikes.
- Trade I/O cost for predictability.

On average, logging is faster than shadowing, but tail latency is worse: occasional merges and post-crash log replay produce a long tail in the recovery-time CDF.

### Modes (mapped to ext4)

Four general choices, mapped to ext4's three modes:

|Choice|Metadata journaled?|Data journaled?|Data ordered before metadata?|ext4 mode|
|---|---|---|---|---|
|Off|No|No|—|(no journal)|
|Metadata-only|Yes|No|No|`writeback`|
|Ordered (default)|Yes|No|Yes|`ordered`|
|Full|Yes|Yes|(atomic with metadata)|`journal`|

POSIX has very weak partial-protection semantics; at minimum, metadata is protected. The intuition: metadata corruption makes the FS unusable; data corruption is bad but localized.

## Full Journaling

![[Pasted image 20260430105428.png|500]]

What's the issue?

- The diagram isn't to scale. Data entries dwarf metadata entries.

**Write Latency**: 2GB data entry followed by 2KB metadata update → metadata update is **head-of-line blocked** behind the 2GB log write. Without data journaling we'd have saved 2GB of writes entirely.

- Probability of failure grows with time-to-disk.
- Metadata responsiveness suffers (e.g., gcc perf).

**Read Latency**: to read a block, traverse the log to check for commits, then apply deltas, then read. Much more overhead than reading directly from disk.

Plus the log fills faster → more frequent merges → more overhead.

## Ordered Journaling (ext4 default)

Solution to full journaling's problems: **journal metadata only, but order data writes before the metadata commit**.

1. Initiate write to data block first
2. Initiate write to metadata block
3. Flush, then commit
4. Apply metadata update

![[Pasted image 20260430113850.png|400]]

Happens-before is established by a flush between ${d_1, m_1}$ and ${c_1, m_2\text{(next)}}$.

- Partial order: ${d_1, m_1} \to {c_1, m_{2}}$
- $c_i$ visible $\implies m_i$ visible $\implies d_i$ visible
- TLDR: if the commit is visible to the world, the metadata and data have been persisted atomically.

**Ordered Mode breakdown**:

- **Intuition**: think from the perspective of externally visible state.
- **Goal**: at any moment when an inode update is visible, the corresponding data must already be on disk.
- **Mechanism**: enforce happens-before between data and metadata.
    - Practically: ${d_w, m_w} \to \text{flush} \to c_w$
- **Result**: $c_w$ visible $\Rightarrow m_w$ visible $\Rightarrow d_w$ visible. **No stale data possible** — no _visible_ partial state. Either completely old or completely new ⇒ atomicity holds.

![[Pasted image 20260430114921.png|600]]

## POSIX Interface

- **Standard I/O**: read, write, mkdir, create, unlink, chmod, chown
- **File control**: fcntl, flock/funlock
- **Persistency**: **`fsync` — sync a file to disk (makes changes persistent)**

The problem with `fsync`: it conflates ordering and persistence, and its dependency tracking is recursive.

![[Pasted image 20260430115514.png]] Two writes to file 1, two writes to file 2; we `fsync` file 2.

From an external observer's view, $c_2$ should be visible, so $m_2$ must be consistent. But the partial order established by the FS applies **recursively**:

![[Pasted image 20260430115642.png]]

**The downside**: due to recursive guarantees, syncing one file effectively flushes the entire prior log — placing total order on data. Flush operations are _expensive_.

### Atomic File Modification under POSIX

To modify `bar/foo` atomically:

1. Create a log file
2. Store updates in the log
3. Update the actual file
4. Delete the log

```
Create(log)
Write(log, "offset", size, data, chksum)
--> fsync(log)
--> fsync("./")

Write(file, data)
--> fsync(file)

Unlink(log)
--> fsync("./")
```

Why each fsync?

1. `fsync(log)` — persist log contents
2. `fsync("./")` — persist directory inode so the log file is visible
3. `fsync(file)` — persist the actual update
4. `fsync("./")` — persist the unlink (otherwise the log isn't really gone)

**4 fsyncs!** — but do we need persistence each time, or just ordering?

We're syncing for **ordering**. POSIX conflates ordering with persistence in `fsync`.

### Optimistic Crash Consistency (SOSP 2013)

> "The issue is, we conflate ordering and persistency."

Split `fsync` into two primitives:

- **`osync`** — ordering primitive (cheap)
- **`dsync`** — durability primitive (expensive)

Most of the syncs above only need ordering, not immediate persistence:

![[Pasted image 20260430120803.png|400]]

```
Create(log)
Write(log, "offset", size, data, chksum)
osync(log)
osync("./")

Write(file, data)
osync(file)

Unlink(log)
fsync("./")
```

- `osync` ensures the log is in place, the directory is updated, and the file write is ordered after the log.
- Final `fsync` actually pushes everything to disk durably.

We get the same crash-safety with far fewer expensive flushes.
