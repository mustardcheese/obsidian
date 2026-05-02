
File systems are an OS abstraction to:
- Manage user data
- Manage resources (**multiplexing** access to disk usage)
    - managing scarce resources
- Storage resource **isolation**
- Storage resource **protection**
- Data management

Storage == Data. We don't necessarily care about secondary storage as much as we care about data.

## OS Services Provided by File Systems
- **Isolation**
- **Protection**
    - Granularity changes at different layers of operation (users, files, blocks)
- **Multiplexing**
    - By definition, access to a shared resource by more than one user
    - _Space_ Multiplexing: Ability to use different parts of the resource simultaneously
    - _Time_ Multiplexing: Ability to _order_ access of a resource over time correctly
- **Naming**
    - Higher level abstraction to allow users to interact with data

**A file system is an abstraction to manage data, in general.**
- Not tied to persistent data (e.g., procfs is read-only, generated on-the-fly)
- FS controls access to the data and can access _any_ data
    - `/dev/...` isn't just files
    - `/proc/`, `/sys/`
    - Many parts of the system are exposed to the user via the FS
- Naming and organizing data
- Share data between multiple processes and users (multiplex)
- **Manage state**
    - Export or make data accessible to user space
    - Narrow-waist interface, letting few things through depending on design
    - Adopted to manage Linux control plane (procfs)

### Naming

Ability to address data state. We could address state via:
- I-node
- name
- identifiers
- hashing

It defines the language in which you interact with the 'universe' (data).

**Byte-Level Interface** instead of block-level interaction given to the user

- Translates dev-native to process-native interface (façade pattern)
- Hides complexity of:
    - Differences between storage devices (heterogeneity)
    - Device availability and failure
- Ability to hide topology (local vs. remote)
- "Look and feel" of memory

### Other Uses of Filesystems (beyond persistent storage)
- Device interfaces (`/dev`) — cameras, RAM, raw disk, serial devices
- System metadata (`/proc`, `/sys`) — process info, CPU, memory, kernel config
- Intuitive ways to interface with I/O
- NUMA zones, PCI devices
- Controlling hugepage allocation
- Process info: open file descriptors (`lsof`)

TLDR: **File system => any data, not just persistent storage**

### Storage Trend
![[Pasted image 20260428011337.png|450]] Tradeoff space between throughput and cost

- Want to maximize throughput for minimum cost (top left)
- Everything currently sits on the Pareto (optimal) frontier
- The gap between HDD and DRAM widens, creating massive opportunity
    - This gap contains the entirety of the NVM (SSD) market

![[Pasted image 20260428011732.png|450]]
ramdisk vs. ssd

- By raw performance, ramdisk is obviously faster but costs more
- Normalized for cost, choice depends on use case, workload properties, and design tradeoffs
- High-performance NVM storage is approaching DRAM speeds

## High-Level API Design Choices

- **Granularity** — files, virtual disks, databases (records in RDBMS)
- **File content** — byte array, records, b-tree, key-value stores
- **Organization** — name hierarchy vs. flat names (object IDs)
- **Synchronization** — none vs. locks, transaction rollbacks, multi-version tracking

### API Implications

File descriptors (fd) refer to something

- Preserved even if the file name is changed or deleted

Files can have multiple links (multiple directories), so file info must be stored _separately_ from any directory.

- A file is independent of its names → called an **inode**
- Inode must keep **link count** (when to free)
- Inode must keep **count of open fds** (when in use)
- **Deallocation deferred** until last link AND last fd are removed

## File System Stack

![[Pasted image 20260428013012.png|300]]

Layers (top to bottom):
- File system call interface
- **VFS** — virtual file system (uniform interface across FS types)
- **FS** — block, inode, directory, path resolution
- Log
- Buffer cache
- Disk driver
- Disk firmware

We separate VFS from FS because we want to decouple _using_ files from _storing_ files. Granularity is set at the file level.

### xv6 FS Layers (more concrete)

File descriptor → Pathname → Directory → Inode → Logging → Buffer cache → Disk

- Each layer builds abstractions on top of the next
- Layers interact in nuanced ways, especially for concurrency

## On-Disk Layout

![[Pasted image 20260428013128.png|350]]

- **Boot sector** — to boot (block 0)
- **Superblock** — metadata for the FS
    - inode location, log location, bitmap location, sizes
- **Inodes** — file metadata (no data!)
- **Block bitmap** — free/occupied state for each data block
- **Data blocks** — actual content / "payload"
- **Log blocks** — for crash consistency (covered later)

![[Pasted image 20260428112152.png|400]] xv6 disk layout

### Disk Granularity

- OSes typically use blocks of multiple sectors
- Common: 4KB blocks == 8 sectors (matches page size for page-fault simplicity)
- xv6 uses **1 block = 1 sector = 512 bytes** for simplicity
- "Meta-data" = everything on disk other than file content (superblock, inodes, bitmap, directory contents)

### Block Allocator

- xv6 maintains a free **bitmap on disk**, one bit per block (`sb->bmapstart`)
    - 0 = free, 1 = in use
- Check if block N is free: `buf[N/8] & (0x1 << (N % 8))`

## Inodes

An on-disk struct (think: **file/directory metadata**) containing:

- **type** (free, file, directory, device)
- **nlink** (how many directories reference this inode)
- **size** (in bytes)
- **addrs[12+1]** (12 direct block addrs + 1 indirect block addr)

> Inodes do **not** contain actual data — only pointers to it.

![[Pasted image 20260428112544.png|250]]

- 12 direct addresses: `12 × 512 B = 6 KB`
- 1 indirect pointer → indirect block holding 128 more addresses: `128 × 512 B = 64 KB`
- **Max file size in xv6**: `(12 + 128) × 512 = 71,680 bytes (≈70KB)`
- Tradeoff: fast direct addressing vs. capacity via indirection

Data in inodes is arranged contiguously by logical offset.

_Where is byte 8000 in this file?_

- `floor(8000 / 512) = 15` → block index 15
- `15 - 12 = 3` → 3rd entry in the indirect block

### Inode On-Disk Structure

- Each inode has an **i-number** (inum)
- Inode is **64 bytes** long
- Byte address on disk: `2 × 512 + 64 × inum`
    - `2 × 512` skips boot sector (block 0) + superblock (block 1)

### Inode API (xv6)

Kernel keeps an inode in-memory until reference count == 0.

|Function|Purpose|
|---|---|
|`ialloc()`|allocate inode|
|`ilock()` / `iunlock()`|sync access to an inode|
|`iget()`|return inode struct, increment ref count|
|`iput()`|decrement ref count, free if ref == 0|
|`iupdate()`|copy modified inode to disk|
|`itrunc()`|discard inode contents|

**Standard usage pattern:**

```c
ip = iget(dev, inum);
ilock(ip);
... examine and modify ip->xxx ...
iunlock(ip);
iput(ip);
```

> **Why does `iget` not hold `ilock`?** Reference counting (presence in cache) is separate from exclusive access. You can have multiple references to an inode (e.g., open fds) without all of them needing to mutate it simultaneously.

### Inode Data Block API

- `readi()` — read data block from inode
- `writei()` — write data block to inode

### Directory Inodes (Dirents)

Directories are _like_ files (but the user can't write to them directly). Their content is an **array of dirents**.

A **dirent** contains:

- `inum` (inode number)
- 14-byte file name
- Dirent is **free if `inum == 0`**

In xv6, directories hold 13 dirents represented as an array on disk.

## Directory Walks

Resolving `/bar/baz/foo.txt` walks through dirent arrays one inode at a time:

![[Pasted image 20260428141457.png]]

Each step: read current directory's data, find matching name, follow inum to next inode, repeat.

### Concurrency Strategies for Walks

**Coarse-grained locking** (naive)

- Lock the _entire_ inode cache to ensure exclusive access to ALL inodes
- Poor performance — effectively no concurrency

**Hand-over-hand locking** (xv6's approach)

- At each step in the walk, lock the inode you're _about to access_, then release the previous inode's lock
- Like climbing a **ladder** rung-by-rung
- Fine-grained → actually supports concurrent path accesses → much better performance

## Buffer Cache

A **doubly-linked list of `buf` structures** holding cached copies of disk block contents.

**Two jobs:**

1. **Synchronize access** to disk blocks
    - One block on disk ↔ one block in memory
    - Only one kernel thread uses a given block at a time
2. **Cache popular blocks** in fixed buffers (avoid disk hits)

### Flags

- `B_BUSY` — buffer locked
- `B_VALID` — buffer has been read from disk (contents are valid)
- `B_DIRTY` — buffer was modified, needs to be written back

### Interface

- `binit()` — called by main at boot
- `bread()` — read buffer from disk block (calls `bget` internally)
- `bwrite()` — write buffer to disk
- `brelse()` — release buffer when done; moves it to head of LRU list

### `bget` Logic (inside `bread`)

- If block already cached and not `B_BUSY` → return it
- If cached but `B_BUSY` → wait (sleep)
- If not present → reuse an existing buffer (LRU eviction)

### Replacement Policy: LRU

- Buffers maintained in a doubly-linked list
- On release (`brelse`): move buffer to **front** of list
- On eviction: start at the **tail** (least recently used)

### Buffer Cache Considerations

- **Reading big files**: disk → buffer cache → user space (extra copy)
    - Could pass user buffer directly to disk driver to avoid copy (zero-copy I/O)
- **How much RAM for buffers?** Tradeoff between hit rate and memory pressure on the rest of the system

## xv6 Code Walk Highlights

**Concurrent `ialloc` calls** — will they get the same inode?

- `ialloc` uses `bread` / `bwrite` / `brelse`
- `bread` locks the block (waits if `B_BUSY`) and reads from disk
- `brelse` unlocks the block
- Synchronization at the buffer-cache layer prevents duplicate allocation

### Deleting a file (`rm a`)

```
write 59  writei  (sys_unlink; directory content)
write 34  iupdate (sys_unlink; link count of file)
write 58  bfree   (itrunc, iput)
write 34  iupdate (itrunc)
write 34  iupdate (iput)
```

A single `rm` triggers multiple metadata writes — motivates the need for the **logging layer** (next lecture) for crash consistency.