*shoutout claude*
## Copy-on-Write Fork

### The Problem with Naive Fork

It is way too slow and ineffective to create an entire copy of memory (reinstantiate every physical frame) for a new process. If a parent has hundreds of pages, duplicating all of them on `fork()` wastes time and memory — especially since many children immediately call `exec()` and discard everything.

<!-- INSERT: Slide 12 diagram showing parent/child with duplicated physical frames (the "inefficient" version) -->

### The CoW Solution

We defer copying pages until the point of write. Forking becomes fast because we just create a new process and point its page table entries to the **same physical frames** as the parent.

- Instead of duplicating physical pages, the child's PTEs map to the parent's existing frames
- Since the pages are the same, the page tables point to the same pages. And since the page tables are the same, the page directory entries point to the same page tables.
- You can think of the page directory → page table → page structure as a **DAG**: if there is more than one path to reach a page (vertex), then the resource is shared and should not be modified directly

<!-- INSERT: Slide 13 diagram showing parent/child sharing the same physical frames (the "efficient" version) -->

### What Happens on Write (The CoW Fault Flow)

When a process wants to write to a shared page:

1. The CPU traps — a **page fault** occurs because the page is marked read-only in the PTE
2. The OS fault handler checks if this is a **CoW page** (not a real protection violation)
3. The OS **allocates a new physical page** and copies the contents of the shared page into it
4. The OS **updates the writing process's PTE** to point to the new page with write permission enabled
5. The OS **decrements the reference count** on the old shared page
6. If the old page's refcount drops to 1, the sole remaining owner gets write permission **restored** — no future fault needed for that page

We have to create new pages (and update PTEs, page tables, page directories as needed) for the sake of **isolation**. If we allowed the child process to directly edit shared pages, it would modify the parent's data — breaking isolation.

### Critical Detail: Both Parent AND Child Lose Write Permission

On fork, writable pages must be marked **read-only in BOTH processes**, not just the child. If only the child were marked read-only, the parent could write to a shared page and silently corrupt the child's memory.

### Reference Counting (Per Physical Page)

To know when to copy and when to free, we need a **reference count** for each physical page:

- **Incremented** when a new PTE maps to this page (e.g., on fork)
- **Decremented** when a mapping is removed (e.g., CoW copy, process exit)
- **Refcount = 0** → free the page back to the allocator
- **Refcount = 1** → sole owner can have write permission restored (no copy needed on write)

### Corner Cases

- **Grandchildren**: A page can be shared across many processes via chains of forks. Reference counting handles this naturally — each fork increments, each exit/copy decrements.
- **Out-of-memory during CoW fault**: If the allocator cannot provide a new page when a CoW fault occurs, the OS must **kill the process** — there is no way to silently handle this.
- **Resource cleanup on exit**: Every page mapping must be walked, refcounts decremented, and pages freed only when refcount reaches 0.

### Back-Propagation of Changes

When a CoW fault triggers a copy, the changes propagate back through the page table structure: new page allocated → PTE updated → possibly a new page table needed (if it was shared) → possibly page directory entry updated.

---

## Permissions: Logical vs. Physical

We can separate permissions into two types:

- **Logical**: Is it _legal_ to access this memory? (What the process is _entitled_ to do)
- **Physical**: Should the CPU _trap_ for accessing this page? (What the hardware PTE bits say)

These can intentionally **disagree**. This disagreement is how CoW (and many other VM tricks) work:

|Scenario|Logical Permission|Physical PTE Bits|What Happens|
|---|---|---|---|
|Normal writable page|Read + Write|R=1, W=1|Access succeeds|
|CoW shared page|Read + Write|R=1, **W=0**|Write causes fault → OS copies page|
|Truly read-only page|Read only|R=1, W=0|Write causes fault → OS kills process|
|Unmapped page|None|P=0|Any access causes fault → segfault|

The OS distinguishes a CoW fault from a true protection violation by checking **metadata** (e.g., the AVL bits 9–11 in the PTE, which the hardware ignores and the OS can use freely).

---

## CoW Example Walkthrough

<!-- INSERT: Slide 21 diagram — initial state with shared PD1, PT1, PT2, pages P1/P2/P3 -->

### Initial State (before fork)

- Process 1 has PD1 → PT1 (maps P1, P2) and PT2 (maps P3)
- All pages are R=1, W=1

### Step 1: Fork (create Process 2 sharing pages)

- Both processes share PD1, PT1, PT2, and pages P1, P2, P3
- **All writable pages become read-only**: R=1, W=0 for BOTH processes

### Step 2: Process 2 writes to P1

- CPU traps: write to read-only page → page fault
- Fault handler recognizes this as a CoW fault (checks AVL/CoW bits)
- Allocates new page P4 (copy of P1)
- Process 2's PTE now points to P4 with R=1, W=1
- Process 1's PTE still points to P1 — if refcount on P1 is now 1, restore W=1

<!-- INSERT: Slide 23 diagram — after CoW, showing P1 still with Process 1, P4 (P1') with Process 2, new PD2/PT3 -->

### After the write:

- Process 1: PT1 → P1 (R=1, W=1 restored), P2 (R=1, W=0 still shared)
- Process 2: PT3 → P4 (R=1, W=1), PT2 → P3 (R=1, W=0 still shared)

---

## TLB Implications for CoW

**On a CoW write fault:**

- The **writing process** needs its TLB entry invalidated (PA changed to new page, W bit now set)
- The **other process sharing the page** may need its TLB entry invalidated (if its W bit is being restored because refcount dropped to 1)

**Exam-style question:** "How many TLB flushes does a CoW write cause?" Answer: **1 full flush** — only the currently running process's TLB needs flushing. The other process gets a fresh TLB on its next context switch (CR3 reload flushes everything).

**Exam-style question:** "How many TLB page invalidates on write to P1?" Answer: **2 entries are stale** — one for the writer (new PA + new permissions) and one for the other process (permissions changed from R/O back to R/W). But in xv6, only 1 flush happens now; the other is handled implicitly on the next context switch.

---

## Other VM Tricks

### Demand Paging / Lazy Allocation

If a process requests additional memory (e.g., via `sbrk()`), we can do so lazily:

- Record that the address range is valid (increase the process's size field) but **don't allocate physical pages yet**
- When the process actually touches the page → page fault → allocate and map the page then
- **Benefit**: Processes that allocate large heaps but touch little memory waste no physical RAM
- **This is oversubscription** — assigning more virtual memory than physical memory exists
- **Tradeoff**: Each first access to a new page incurs a page fault (slower), but total memory usage is much more efficient

### On-Demand Zero-Filled Pages / Single Zero Page

Pages from the kernel are zeroed by default — this is a **security requirement**. Without zeroing, a newly allocated page could contain sensitive data from a previously freed page (passwords, keys, etc.).

But do we need to zero them on allocation?

- **Optimization**: Map ALL newly allocated zero-pages to a **single read-only physical zero page** (`memset(0)`)
- When the process reads → sees zeros (correct behavior)
- When the process writes → CoW-style fault → allocate a real page, zero it, map it writable
- **Massive savings**: If a process allocates 100 pages but only writes to 5, only 5 physical pages are ever allocated

<!-- INSERT: Slide 38 diagram — multiple virtual pages mapping to single zero-filled physical page with read-only note -->

### Virtual Shared Memory

Does every virtual page need to map to a **unique** physical page? No.

- Multiple processes can intentionally share a physical page for **inter-process communication**
- Unlike CoW, writes **ARE visible** to all sharers (this is the point)
- Shared libraries: loaded once in physical memory, mapped read-only into many process address spaces — saves enormous amounts of memory

### Memory-Mapped Files

Virtual mappings don't have to be backed by RAM — they can be backed by **files on disk**:

- Map a file's contents into the virtual address space using `mmap()`
- Read a page → page fault → OS reads the file block from disk into a physical page
- Write a page → OS marks it dirty and writes it back to the file (on sync or unmap)
- Provides a natural, efficient interface for file I/O without explicit `read()`/`write()` calls

### Paging to Disk (Swap) / Memory Oversubscription

Our physical memory is **not limited to RAM**:

- **Swapping**: When RAM is full, the OS evicts pages to a swap partition on disk. The PTE is marked as not-present (P=0, and the OS can store the swap location in the remaining PTE bits). On access → page fault → OS reads the page back from disk.
- **Oversubscription**: The OS can promise more total virtual memory than physical RAM exists, relying on the fact that not all pages are active simultaneously.

### Linux Memory Map Tools

- `cat /proc/iomem` — physical memory layout
- `cat /proc/self/maps` or `cat /proc/PID/maps` — virtual memory layout of a process
- `pmap` — reports the memory map of processes
- `free` — reports physical usage of memory
- `strace` — trace system calls (useful for seeing mmap, brk, etc.)

---