

> **Usage:** Use `Ctrl+F` with the tags below to jump to sections.  
> Tags follow the format `[TAG:TOPIC]` for sections and `[Q:keyword]` for individual questions.

---

## Table of Contents

1. `[TAG:ISOLATION]` — Isolation & Protection
2. `[TAG:KERNEL]` — Kernel Organization
3. `[TAG:VMM-BASICS]` — Virtual Memory Basics (Segmentation, Paging)
4. `[TAG:VMM-MULTILEVEL]` — Multi-Level Paging, TLB, 64-bit
5. `[TAG:COW]` — Copy-on-Write & VM Tricks
6. `[TAG:SWAPPING]` — Swapping, Clock Algorithm, Eviction
7. `[TAG:CONCURRENCY]` — Concurrency, Locks, Data Races, Memory Models
8. `[TAG:WAITING]` — Ordering, Waiting, Producer-Consumer, Condition Variables
9. `[TAG:SCHEDULERS]` — Scheduling Policies & Design
10. `[TAG:THREADS]` — User & Kernel Threading
11. `[TAG:CROSS-CUTTING]` — Cross-Cutting Concepts & Quick Reference

---

# [TAG:ISOLATION]

## Isolation & Protection

### Large System Design

**[Q:isolation-definition]**  
**Q: What is isolation in the context of operating systems, and what are we trying to isolate from what?**

- Isolation means creating the illusion that each entity is the sole consumer of a shared resource.
- Examples: preventing processes from accessing other processes' address spaces, separating user-level processes from kernel-level code, isolating access to physical memory regions, preventing processes from wrecking the kernel.

**[Q:isolation-necessity]**  
**Q: Is isolation necessary, and what happens if we don't have it?**

- Yes. Failures are a mathematical certainty, and isolation prevents a failure in one process from propagating to others (failure isolation).
- Without isolation, user-level processes and kernel-level code might interact in catastrophic ways.

**[Q:isolation-types]**  
**Q: What are the three types of isolation?**

- **Failure Isolation** — failures don't propagate between processes; the driving motivation for kernel design.
- **Performance Isolation** — controls resource consumption; prevents starvation.
- **Correctness Isolation** — other programs shouldn't affect my program's correctness.

**[Q:perfect-isolation]**  
**Q: Would a 100% perfectly isolated operating system be useful?**

- No. Full isolation means no communication is possible — multiprocessor apps can't communicate, you can't use kernel services to display output or handle keyboard interrupts. A perfectly isolated process is useless.

**[Q:isolation-when-needed]**  
**Q: When do we need isolation? What are the necessary conditions?**

- Two conditions must both be present: **shared resources** AND **non-cooperative entities**.
- Threads are a counterexample — they are cooperative entities designed to share an address space, so isolation between them is not always desired.

**[Q:isolation-tradeoffs]**  
**Q: As we impose weaker or stronger isolation, what happens to safety, usability, and performance?**

- Stronger isolation → more safety, less usability.
- Isolation is an overhead tax → performance generally decreases.
- Performance relationship is nuanced (not strictly one direction).
- The ideal (top-right of Pareto frontier) is max safety + max usability simultaneously.

**[Q:pareto-frontier]**  
**Q: If two points are on the Pareto frontier, which is better?**

- It depends. Both are Pareto optimal and not directly comparable.

**[Q:isolation-mechanisms]**  
**Q: What concrete mechanisms do we have to enact isolation in an OS?**

- **Hardware isolation** — processor protection rings (ring 0 kernel, ring 3 user).
- **Address spaces** — segmentation and paging.
- **Time slicing** — CPU isolation via scheduler.
- **System call interface** — separates user from kernel.
- **Permissions/privilege** — file permissions, user/group model.

**[Q:ring0-protections]**  
**Q: What does Ring 0 protect?**

- Writes to %cr3 (page table base), %cs (defends CPL), control registers (eflags, %cr4).
- Every memory read/write checked for privilege (S/U bit in PTEs).
- I/O port access.

**[Q:cpl-mechanism]**  
**Q: How does CPL work and how is it protected?**

- CPL = lower 2 bits of %cs register. CPL 0 = kernel, CPL 3 = user.
- %cs only changed via far jumps, interrupts, `iret` — prevents user self-escalation.
- GDT uses flat memory model; paging does all real memory isolation.

**[Q:idt-mechanism]**  
**Q: How does the IDT enforce isolation?**

- Each gate contains: segment selector (→ GDT, sets handler's CPL), offset (handler address), DPL (who can trigger via `int`), type.
- Software interrupts: processor checks CPL ≤ DPL of gate → otherwise general protection fault.
- Hardware interrupts bypass DPL check.
- On ring 3→0: processor atomically switches to kernel stack (via TSS), pushes user context, loads new %cs from gate (CPL→0), jumps to handler.

**[Q:syscall-sanitization]**  
**Q: How does the system call interface enforce isolation?**

- Predetermined entry point (user can't jump to arbitrary kernel code).
- Saves user context, loads kernel context.
- **Sanitizes arguments** — must validate user-supplied pointers are in user-accessible memory (kernel runs at CPL 0 and _can_ write anywhere — it must choose not to).

**[Q:meltdown-spectre]**  
**Q: How do Meltdown and Spectre break isolation?**

- **Meltdown**: speculative execution reads kernel memory before U/S check completes; data leaks via cache side channel. Exploits kernel being mapped in every process's page table.
- **Spectre**: manipulates branch prediction to leak data across process boundaries.
- **KPTI fix**: unmaps kernel from user page tables. Requires page table switch + TLB flush on every syscall. Direct safety-vs-performance tradeoff.

**[Q:fd-kernel-attack]**  
**Q: What happens when reading a file descriptor into a memory pointer starting with '8' (kernel address space)?**

- The memory pointer belongs to the kernel (MSB = 1). The operation fails because the read syscall's trap handler sanitizes and validates arguments, denying the request.

---

# [TAG:KERNEL]

## Kernel Organization

### Large System Design

**[Q:kernel-vs-os-job]**  
**Q: Does the entirety of the OS belong in the kernel? What are the guiding principles?**

- Not all OS tasks belong inside the kernel. Minimize logic placed in the kernel.
- The kernel fundamentally provides: (1) isolation/protection at process granularity, and (2) a rendezvous mechanism for IPC.
- Moving services out of the kernel provides better maintainability and failure isolation.

**[Q:monolithic-vs-micro]**  
**Q: What are the differences between monolithic and microkernels?**

- **Monolithic**: everything in one kernel. Fast (fewer boundary crossings), but low fault tolerance, difficult to maintain, not modular. A crash can bring down the entire OS. (Linux, Windows, xv6)
- **Microkernel**: minimal kernel, nearly everything in user space. Safe (failure isolation), modular, but slow (boundary crossing overhead). (macOS)

**[Q:mono-fail-vs-micro-fail]**  
**Q: What happens if a monolithic kernel fails vs. a microkernel service fails?**

- Monolithic: all user space processes fail.
- Microkernel: kernel remains healthy, unrelated user space processes are unaffected.

**[Q:kernel-pareto]**  
**Q: Where do microkernels and monolithic kernels sit on the safety vs. performance tradeoff?**

- Microkernel: top-left of Pareto frontier (max safety, less performance).
- Monolithic: bottom-right (max performance, less safety).

**[Q:factor-out-subsystems]**  
**Q: Can major subsystems (file systems, drivers, memory management) be factored out of the kernel?**

- Yes. Drivers can run in user space (e.g., FUSE, SSHFS for file systems). Memory management servers can run in user space. However, IPC must fundamentally be brokered by the kernel.

**[Q:failure-dag]**  
**Q: How can we model failure domains in an OS?**

- Model dependencies as a DAG. To find what fails when a service fails: represent as adjacency matrix, transpose, perform reachability analysis (transitive closure of failures).

**[Q:echo-hello-cat]**  
**Q: How many processes are involved in `echo hello | cat`?**

- Three: the shell, echo (forkexec'd), cat (forkexec'd, connected by pipe). All in user space, all use syscalls.

**[Q:libc-in-kernel]**  
**Q: Can the C standard library (libc) be called from inside the kernel?**

- No. libc lives in user space as system middleware. Not callable from inside xv6.

**[Q:add-syscall]**  
**Q: How do you add a new system call in xv6/Linux?**

- Add the C code, declare it in `syscalls.h`, define a macro associating a syscall number with the function. User triggers interrupt → trap handler → syscall table lookup.

**[Q:syscall-backward-compat]**  
**Q: Why do `dup2`, `dup3`, `pipe2` exist instead of updating the originals?**

- Strict backward compatibility. Once a syscall signature is exposed, you cannot modify it. Must create entirely new syscalls with new names.

---

# [TAG:VMM-BASICS]

## Virtual Memory Basics

### Large System Design

**[Q:why-virtual-memory]**  
**Q: Why do we care about virtual memory?**

- **Isolation**: each process gets independent address space.
- **Resource Multiplexing**: make 1 physical address look like many virtual address spaces.
- **Masks limitations**: allocate more virtual memory than RAM; perform swaps.
- **Protection**: flags and permission bits (read, write, kernel) enforce memory accesses.
- Hides complexity of fragmented physical memory from the developer.

**[Q:segmentation-vs-paging]**  
**Q: Can we get away with segmentation? What are the advantages/disadvantages vs. paging?**

- Segmentation: simple, no v2p translation overhead, but operates with large contiguous ranges → poor utilization (fragmentation).
- Paging: smaller fixed blocks (finer granularity), avoids fragmentation, allows larger virtual address spaces, vastly superior isolation and protection.
- In modern OSes, segmentation is identity mapping (base=0, limit=max), so logical = linear = virtual. Paging does all the real work.

**[Q:cr3-register]**  
**Q: What is the CR3 register responsible for?**

- Holds the **physical address** of the page directory. Must be physical because CR3 is the root of translation — you can't translate without it (chicken-and-egg problem).

**[Q:cr3-why-physical]**  
**Q: Why can't CR3 hold a virtual address?**

- Chicken-and-egg: would need another mechanism to translate it. During boot, the kernel only knows physical addresses.

**[Q:page-table-before-paging]**  
**Q: How do we make the page table before paging is set up?**

- Create a basic temporary page directory directly in physical memory using identity mapping (PA = VA). When paging is enabled, the instruction pointer continues executing seamlessly.

**[Q:two-rom-mappings]**  
**Q: Why are there two ROM mappings at boot?**

- **High mapping** (0xFFFE0000–0xFFFFFFFF): 128KB ROM at top of 4GB, used for reset vector.
- **Low mapping** (0xF0000–0xFFFFF): 64KB alias in 1MB real-mode space, needed after ljmp when CPU can only address 1MB.
- Neither is redundant. High for reset vector, low for continued BIOS execution.

### Paging Mechanics

**[Q:two-level-page-walk]**  
**Q: How does two-level paging translation work step by step?**

1. Load Page Directory physical address into CR3.
2. Use 10 MSB of Linear Address ("Dir") to index into PD → get PDE.
3. Use PDE's PPN to locate the Page Table in physical memory.
4. Use next 10 bits ("Table") to index into PT → get PTE.
5. Use PTE's PPN + last 12 bits ("Offset") → Physical Address.

A 2-level walk requires exactly **2 memory accesses** (one PDE read, one PTE read). CR3 is a register read, offset is arithmetic.

**[Q:pd-size]**  
**Q: What is the significance of the page directory being exactly 4KB?**

- A physical frame is 4KB. The PD (1024 entries × 4 bytes = 4096 bytes) fits perfectly in one page — no wasted space.

**[Q:pte-flags]**  
**Q: What do PTE/PDE flags mean?**

|Bit|Name|Meaning|
|---|---|---|
|0|P|Present (1 = in physical memory; 0 → page fault)|
|1|W|Writable (1 = read/write, 0 = read-only)|
|2|U|User (1 = user-mode accessible, 0 = kernel-only)|
|5|A|Accessed (set by hardware on read/write)|
|6|D|Dirty (set by hardware on write)|
|7|PS|Page Size (PDE only: 0 = 4KB, 1 = 4MB superpage)|
|9-11|AVL|Available for OS use (e.g., CoW tracking)|

- If P=0, hardware raises page fault — OS can store swap location in remaining bits.
- A and D set automatically by hardware; OS clears them for page replacement decisions.

**[Q:single-vs-multi-level]**  
**Q: What are the tradeoffs between single-level and multi-level paging?**

| | Single Level [20|12] | Multi Level [10|10|12] | |---|---|---| | Latency | 1 memory access (faster) | 2 memory accesses (slower) | | Memory Overhead | Full table always: 4MB/process | Sparse — minimum 4KB (just PD) | | Fragmentation | Needs contiguous 4MB | Each table is 1 page (4KB) | | Best For | Processes using most of address space | Most real workloads |

Multi-level trades latency for memory savings. TLB makes this acceptable.

**[Q:large-pages]**  
**Q: What are large/super pages and their tradeoffs?**

- 32-bit: 4KB or 4MB. 64-bit: 4KB, 2MB, 1GB.
- PS=1 in PDE → skip second level, PDE points directly to 4MB frame.
- Tradeoffs: better TLB coverage and fewer entries, but more internal fragmentation.

---

# [TAG:VMM-MULTILEVEL]

## Multi-Level Paging, TLB, 64-bit

**[Q:four-level-paging]**  
**Q: How does four-level paging (x86-64) work?**

```
| PML4 (9) | Dir Ptr (9) | Directory (9) | Table (9) | Offset (12) |
```

- Each level: 512 entries × 8 bytes = 4KB per table.
- Full walk: **4 memory accesses**.
- Supports: 4KB, 2MB (skip last level), 1GB (skip last two levels).
- Only 48 bits used for translation → 256TB addressable (sufficient for current needs).

**[Q:tlb-mechanism]**  
**Q: How does the TLB work?**

```
Virtual Address → TLB
    ├── TLB HIT  → Physical Address immediately (~1 cycle)
    └── TLB MISS → Full page table walk (2-4 memory accesses)
                    → Result cached in TLB
                    └── Page Not Present? → Page Fault → OS handler
```

- **iTLB**: instruction translations only. **dTLB**: data translations only.
- Separating them is efficient because instructions are read-only and won't need updates during CoW.
- **TLB Flush**: changing CR3 (context switch) invalidates the entire TLB — major reason context switches are expensive.
- Larger pages → better TLB hit rate → less thrashing.

**[Q:tlb-makes-multilevel-practical]**  
**Q: Why is the TLB critical?**

- Without it, every memory access would need 2+ extra accesses just for translation. The TLB is what makes multi-level paging practical.

**[Q:one-level-scalability]**  
**Q: What scalability problem does one-level paging with 4KB frames have?**

- Page directory becomes 4MB per process. With 1024 processes → 4GB just for page directories. Ruins system scalability.

**[Q:latency-vs-memory-overhead]**  
**Q: How do two-level and one-level map onto the latency vs. memory overhead tradeoff?**

- Two-level: high latency overhead, minimizes memory overhead.
- One-level: minimizes latency overhead, maximizes memory overhead.

**[Q:walkpgdir]**  
**Q: What does `walkpgdir` output in xv6?**

- A pointer to the Page Table Entry (PTE).

**[Q:va-to-pa-memory-ops]**  
**Q: How many memory operations for a VA→PA translation in two-level?**

- 2 operations for translation, 3 total for overall access (including the final data read).

---

# [TAG:COW]

## Copy-on-Write & VM Tricks

### Large System Design

**[Q:why-cow]**  
**Q: Why is naive fork slow, and how does CoW fix it?**

- Naive fork duplicates all physical frames — wastes time and memory, especially since many children immediately call `exec()`.
- CoW defers copying: child's PTEs point to parent's existing frames. Only copy on write.

**[Q:cow-fault-flow]**  
**Q: What happens on a CoW write (the fault flow)?**

1. CPU traps — page fault (page marked read-only in PTE).
2. OS checks if this is a CoW page (not a real protection violation) via AVL bits.
3. OS allocates a new physical page and copies the shared page contents.
4. OS updates the writing process's PTE to point to new page with write permission.
5. OS decrements refcount on old shared page.
6. If refcount drops to 1, sole remaining owner gets write permission restored.

**[Q:cow-both-lose-write]**  
**Q: Why must BOTH parent AND child lose write permission on fork?**

- If only the child were marked read-only, the parent could write to a shared page and silently corrupt the child's memory.

**[Q:cow-refcounting]**  
**Q: How does reference counting work for CoW?**

- Incremented when a new PTE maps to the page (e.g., fork).
- Decremented when a mapping is removed (CoW copy, process exit).
- Refcount = 0 → free the page.
- Refcount = 1 → sole owner, restore write permission (no copy needed).

**[Q:cow-backpropagation]**  
**Q: What is back-propagation of changes in CoW?**

- New page allocated → PTE updated → possibly new page table needed (if shared) → possibly PDE updated. Must not mutate shared page table/directory directly — breaks isolation.

**[Q:logical-vs-physical-perms]**  
**Q: What is the difference between logical and physical permissions?**

|Scenario|Logical|Physical PTE|What Happens|
|---|---|---|---|
|Normal writable|R+W|R=1, W=1|Access succeeds|
|CoW shared|R+W|R=1, **W=0**|Write → fault → OS copies|
|Truly read-only|R only|R=1, W=0|Write → fault → OS kills|
|Unmapped|None|P=0|Any access → segfault|

OS distinguishes CoW fault from protection violation via AVL bits (9-11).

**[Q:cow-fork-complexity]**  
**Q: What is the complexity of eager fork vs. lazy (CoW) fork?**

- Eager: O(n) — proportional to number of pages in parent.
- Lazy (CoW): O(1) — defers work until writes occur.

**[Q:cow-tlb-invalidates]**  
**Q: How many TLB flushes/invalidates does a CoW write cause?**

- **1 full flush** — only the currently running process's TLB. The other process gets a fresh TLB on its next context switch (CR3 reload).
- 2 entries are _stale_ (writer's PA changed, other process's permissions changed), but only 1 flush happens now.

**[Q:cow-oom]**  
**Q: What happens if the allocator runs out of memory during a CoW fault?**

- The OS must **kill the process**. There is no way to silently handle this.

### Other VM Tricks

**[Q:demand-paging]**  
**Q: What is demand paging / lazy allocation?**

- Record address range as valid but don't allocate physical pages yet. On first access → page fault → allocate then.
- This is oversubscription. Tradeoff: each first access incurs a fault, but total memory usage is much more efficient.

**[Q:zero-page]**  
**Q: How does the single zero-page optimization work?**

- Map all newly allocated pages to a single read-only physical zero page.
- Read → sees zeros (correct). Write → CoW-style fault → allocate real page.
- Security requirement: pages must be zeroed to prevent data leakage from previously freed pages.

**[Q:shared-memory]**  
**Q: Can multiple virtual pages map to the same physical page?**

- Yes. Shared memory for IPC (writes ARE visible to all sharers). Shared libraries loaded once, mapped read-only into many processes.

**[Q:mmap]**  
**Q: What are memory-mapped files?**

- Map file contents into virtual address space via `mmap()`. Read → page fault → OS reads file block from disk. Write → OS marks dirty, writes back. Requires paging (level of indirection).

**[Q:swap-oversubscription]**  
**Q: How does swapping/paging to disk work?**

- When RAM is full, OS evicts pages to swap partition. PTE marked P=0, swap location stored in remaining PTE bits. On access → page fault → OS reads from disk.
- OS can promise more virtual memory than physical RAM (oversubscription).

---

# [TAG:SWAPPING]

## Swapping, Clock Algorithm, Eviction

### Large System Design

**[Q:swapping-mechanisms]**  
**Q: What enabling mechanisms and policy decisions are required for swapping?**

- **Policy**: how to put mechanisms together (e.g., approximate LRU via Clock algorithm).
- **Mechanisms**: present bit shadowing access bit, trapping on access, etc.

**[Q:beladys-algorithm]**  
**Q: What is Belady's Optimal Algorithm?**

- Evict the page accessed **furthest in the future**. Provably optimal. **Impossible in practice** — requires future knowledge. Useful only as theoretical benchmark.

**[Q:why-lru]**  
**Q: Why do we evict least recently used pages?**

- Queuing theory: time since last access is highly predictive of time to next access (temporal locality).

**[Q:lru-impractical]**  
**Q: Why is exact LRU impractical for pages?**

- Requires recording a timestamp on **every single memory access** (every load AND store).
- Even O(1) update is unacceptable because it must happen on each access.
- Worst case: trapping on every access just to record timestamps.
- Unnecessary overhead even with infinite memory.
- (LRU works fine for smaller structures like CPU caches where hardware tracks order.)

**[Q:clock-algorithm]**  
**Q: How does the Clock (Second Chance) algorithm work?**

- Pages in a **circular buffer**, each with an **access bit (a)**.
- **Clock hand** sweeps forward on eviction:
    - a == 1 → clear to 0 ("second chance"), advance.
    - a == 0 → **evict this page**.
- We only trap when transitioning 0→1 (first access after clear), NOT on every read/write.

**[Q:clock-trap-mechanism]**  
**Q: How does the trap mechanism work in the Clock algorithm?**

- When clock hand clears a page (a=0), OS also clears PTE_P (present bit).
- Next access → hardware sees PTE_P=0 → page fault.
- Handler sets a=1, restores PTE_P=1, resumes execution.
- All subsequent accesses hit normally with no trap until the clock hand clears it again.

**[Q:clock-access-transitions]**  
**Q: What are the access bit transitions?**

|Transition|Cause|Meaning|
|---|---|---|
|0 → 1|Process reads/writes → page fault trap|ONLY time we need to trap|
|1 → 0|Clock hand passes during eviction sweep|Second chance used up|
|1 → 1|Page accessed again between sweeps|Actively in use|
|0 → 0|Not accessed, hand hasn't passed|Prime eviction candidate|

**[Q:clock-worst-case]**  
**Q: What is the worst-case complexity of the Clock algorithm?**

- If ALL pages have a==1: first sweep clears all N pages, second sweep evicts first a==0 found.
- **Worst case: 2N inspections** to find one victim.
- In practice this is rare — usually some pages have a==0.

**[Q:xv6-page-fault]**  
**Q: Where does xv6 handle page faults?**

- Vector 14 in the IDT. Handler in `trap.c`. PTE flags like PTE_P, PTE_A defined in page table entry structure. x86 hardware sets PTE_A automatically.

---

# [TAG:CONCURRENCY]

## Concurrency, Locks, Data Races, Memory Models

### Large System Design

**[Q:why-interrupts]**  
**Q: Why do we need interrupts?**

- Handle unpredictable events (keyboard, network, timers, faults). Without them → polling, which wastes cycles on rare events or misses frequent ones.
- Interrupts give a form of concurrency — used to implement concurrency in the system.

**[Q:interrupt-types]**  
**Q: What are the interrupt types?**

|Type|Maskable?|Trigger|Notes|
|---|---|---|---|
|NMI|No|Hardware (power fail, memory)|Vector 2, fatal in xv6|
|INTR|Yes (IF flag)|Hardware (devices via PIC)|`sti`/`cli`|
|INT|N/A (software)|`int N` instruction|xv6 syscalls: `int 0x40`|

**[Q:gate-types]**  
**Q: What are interrupt vs. trap gates?**

|Gate|istrap|IF behavior|Used for|
|---|---|---|---|
|Interrupt gate|0|Clears IF → disables further interrupts|Hardware interrupts|
|Trap gate|1|Leaves IF alone|Syscalls|

Syscalls use trap gates so hardware interrupts still fire during long kernel operations.

**[Q:int-N-sequence]**  
**Q: What happens on `int N`?**

1. Fetch descriptor for vector N from IDT.
2. Permission check: CPL ≤ DPL (software `int` only).
3. If crossing rings: save old SS/ESP, load new from TSS.
4. Push: SS, ESP (if ring crossing), EFLAGS, CS, EIP.
5. Clear IF (interrupt gates only).
6. Set CS:EIP from IDT entry → handler executes.
7. Return: `iret` pops everything back.

**[Q:kernel-handler-deadlock]**  
**Q: How can a kernel and interrupt handler deadlock?**

- Kernel holds lock → interrupt fires → handler tries same lock → spins forever → deadlock on single CPU.
- **Solution:** `Acquire() = interrupt_disable() + Lock()`, `Release() = Unlock() + interrupt_enable()`. Disable before lock, enable after unlock.
- Mutual exclusion with interrupt handler needs interrupt disable, not locks alone.

**[Q:data-race-definition]**  
**Q: What is a data race?**

- Two concurrent accesses to the same memory location, at least one being a write, that are **unordered** (no synchronization between them).

**[Q:too-much-milk]**  
**Q: What is the "too much milk" problem?**

- Two threads check shared variable (fridge), both see empty, both buy milk → safety violation.
- **Safety**: at most one buys milk. **Liveness**: someone buys when needed.
- Mutual exclusion with only loads/stores is extremely hard → need hardware support.
- Sticky notes don't fix it — leaving a note isn't atomic (multiple assembly steps).

**[Q:building-locks]**  
**Q: How do we build locks?**

- Peterson's Algorithm: works with only atomic load/store but impractical (2 processes only, requires sequential consistency).
- **Practical**: use `atomic_exchange` (atomic load + store):

```c
r = 1;
while (r != 0)
    r = exchange(&lock, 1);  // atomically: read old, write 1
// r == 0 means lock was free, we claimed it
```

- lock=0: exchange returns 0, sets lock=1 → acquired.
- lock=1: exchange returns 1, sets lock=1 → spin.
- Release: `lock = 0`.

**[Q:spinlock-states]**  
**Q: What states exist in the spinlock FSA?**

- (lock=0, r=1) → (1, 0): acquire success.
- (1, 1) → (1, 1): spinning.
- (0, 0): **impossible/unreachable**.
- Cannot spin in state (0, 1) — that edge does not exist.

**[Q:memory-model-tso]**  
**Q: What is TSO and why can (0,0) happen?**

```
Initial: x = y = 0
T1: x=1; EAX=y    T2: y=1; EBX=x
```

|EAX|EBX|Under SC?|Under TSO?|
|---|---|---|---|
|0|1|Yes|Yes|
|1|0|Yes|Yes|
|1|1|Yes|Yes|
|**0**|**0**|**No**|**Yes**|

- TSO (Total Store Order, x86): stores totally ordered, but loads can pass preceding stores to different addresses → (0,0) possible.
- We assume SC but aren't promised it by CPU, language, or compiler.

**[Q:drf0]**  
**Q: What is DRF0 semantics?**

- **No data race ⟹ Sequential consistency.** If your code is data-race-free, it behaves as if sequentially consistent. Races → undefined behavior.
- Use proper synchronization (locks, semaphores, CVs, barriers).

**[Q:deadlock]**  
**Q: What is deadlock and how to prevent it?**

- Threads hold locks and wait for each other in a cycle → nobody progresses.
- Dining Philosophers: all grab left fork → circular wait → deadlock.
- **Solution:** impose total ordering on lock acquisition (always acquire lower-numbered first → breaks cycle).

**[Q:volatile-misconception]**  
**Q: Is `volatile` useful for concurrency?**

- **No.** No atomicity, no fencing. Only prevents compiler from optimizing away reads. Only useful for memory-mapped device drivers.

**[Q:reads-only-safe]**  
**Q: If an interrupt handler and kernel code both access a shared variable, but both are reads, is that okay?**

- Yes. No mutation of state possible, so no data race.

---

# [TAG:WAITING]

## Ordering, Waiting, Producer-Consumer, Condition Variables

### Ordering

**[Q:locks-add-ordering]**  
**Q: What kind of ordering do locks enforce?**

- **Partial ordering** (not total). Reduces the space of possible interleavings.
- Acquire → all subsequent reads/writes happen after (fence: nothing leaks above).
- Release → all preceding reads/writes happen before (fence: nothing leaks below).
- By transitivity of happens-before, one critical section provably executes entirely before another.

**[Q:weak-ordering]**  
**Q: What is weak ordering (relaxed consistency)?**

- Hardware/compiler can reorder reads and writes if correct from executing thread's perspective.
- Does NOT concern itself with correctness across threads.
- Without explicit synchronization, almost no ordering guarantees exist.

### Producer-Consumer

**[Q:producer-consumer-evolution]**  
**Q: Walk through the evolution of correct producer-consumer:**

**Attempt 1 (lock only, no check):** Safety BAD — pops from empty queue.

**Attempt 2 (add `if` check):** Safety fine, but Efficiency BAD — must keep retrying (busy-wait).

**Attempt 3 (CV with `if`, no signal):** Liveness BAD — consumer sleeps forever (deadlock).

**Attempt 4 (CV with `if` + signal):** Safety BAD — with multiple consumers, C2 can snipe item after C1 is signaled but before C1 re-acquires lock. Also spurious wakeups.

**Attempt 5 (CV with `while` + signal) ✅:**

```
Produce(v):                Consume():
  lock(lk);                  lock(lk);
  q.push(v);                 while(q.empty())
  cv.signal();                 cv.wait(lk);
  unlock(lk);                v = q.pop();
                              unlock(lk);
                              return v;
```

Safety ✅, Liveness ✅, Efficiency ✅.

**[Q:cv-while-rule]**  
**Q: Why must `wait()` ALWAYS be inside a `while` loop?**

1. **Spurious wakeups** — OS may wake you for no reason.
2. **Stolen wakeups** — another consumer grabs the item before you re-acquire the lock.

**[Q:cv-interface]**  
**Q: What is the condition variable interface?**

|Operation|Behavior|
|---|---|
|`wait(lock *lk)`|Atomically releases lock AND sleeps. Re-acquires lock on wakeup.|
|`signal()`|Wakes one waiter|
|`broadcast()`|Wakes all waiters|

**[Q:signal-placement]**  
**Q: Where can `signal()` be placed in the producer?**

|Placement|Notes|
|---|---|
|Inside lock, after push|Standard and safe|
|After unlock|Correct, slightly more efficient|
|Before lock/push|**WRONG** — breaks happens-before (push must happen before signal)|

All valid placements work because push happens-before signal, signal happens-before wait returns → push happens-before pop (transitivity).

### Context Switch & Sleeping

**[Q:what-saved-on-sleep]**  
**Q: What state is saved when a process sleeps?**

|State|How Saved|
|---|---|
|User address space|In process's page table — nothing to do|
|User context (regs)|Saved on trap/syscall (trapframe on kstack)|
|Kernel address space|Shared — nothing to do|
|Kernel context (regs)|Saved explicitly by `swtch()`|

**[Q:swtch-callee-saved]**  
**Q: Why does `swtch` only save callee-saved registers?**

- `swtch` is voluntary (cooperative). The C compiler already saved caller-saved regs per calling convention. Only saves: %ebp, %ebx, %esi, %edi + %esp.
- Contrast: trap handler is involuntary → must save ALL registers.

**[Q:context-switch-path]**  
**Q: What is the full context switch path in xv6?**

```
User A → [trap] → Kernel (A's kstack) → swtch → Scheduler (sched kstack)
  → swtch → Kernel (B's kstack) → [trap return] → User B
```

Never switches user-to-user directly. `sched` and `scheduler` are coroutines (ping-pong).

**[Q:three-ways-give-up-cpu]**  
**Q: What are the three ways to give up the CPU?**

|Function|Meaning|New State|
|---|---|---|
|`yield()`|Timer interrupt / cooperative|RUNNABLE|
|`sleep()`|Waiting for event|SLEEPING|
|`exit()`|Process done|ZOMBIE|

---

# [TAG:SCHEDULERS]

## Scheduling Policies & Design

### Large System Design

**[Q:scheduler-goal]**  
**Q: What is the goal of a scheduler?**

- **Maximize the amount of work we care about.** Depends on success metrics: fair access, starvation freedom, throughput, or latency SLO attainment.

**[Q:scheduling-not-solved]**  
**Q: Is scheduling a solved problem?**

- No. Resources and application properties are continually shifting, calling for modernized approaches.

**[Q:scheduling-goals-conflict]**  
**Q: What scheduling goals conflict?**

- Throughput vs. latency (batching helps throughput, hurts latency).
- Response time vs. scalability.
- Fairness vs. scalability.
- Resource utilization vs. power consumption.
- **No perfect/universal policy.** Can't have all three of simplicity, performance, cost — pick two.

**[Q:elevator-scheduling]**  
**Q: What is the implicit assumption behind elevator scheduling?**

- There is an **actuation delay** (physical seek cost). Batch nearby requests as the head moves in one direction.

**[Q:long-vs-short-jobs]**  
**Q: How does policy change for long-running vs. short-running jobs?**

- Long jobs: FCFS causes head-of-line blocking. Need preemptive scheduler (round-robin).
- Short jobs: preemptive scheduling adds unnecessary context switch overhead. Let them finish.

**[Q:round-robin-pros-cons]**  
**Q: What are the pros and cons of Round-Robin?**

- Pros: simple, starvation-free (no priority), gives equal access.
- Cons: priority-unaware, duration-unaware, deadline-unaware, poor for latency-sensitive apps.

**[Q:linux-cfs]**  
**Q: How does the Linux CFS scheduler work?**

- Observation: processes that constantly use full CPU are likely lower priority than those that mostly sleep.
- Reduces priority from CPU-hogging processes (dynamic priority adjustment).
- **CFS** = Completely Fair Scheduler, implements Weighted Fair Queuing (WFQ).
- Process weights determine CPU share proportionally. Sleeping processes fall behind on virtual runtime → get boosted on wakeup.

**[Q:linux-scheduling-policies]**  
**Q: What are the Linux scheduling policies?**

|Policy|Use|
|---|---|
|`SCHED_OTHER`|Default time-sharing (CFS)|
|`SCHED_IDLE`|Very low priority background|
|`SCHED_BATCH`|CPU-intensive batch jobs|
|`SCHED_FIFO`|Real-time FIFO (runs until yield/preempted by higher RT)|
|`SCHED_RR`|Real-time round-robin (FIFO + time quanta among same-priority)|

RT policies always preempt normal policies.

**[Q:scheduling-costs]**  
**Q: What are the costs and benefits of scheduling?**

- Costs: context switching (register save/restore + **cache pollution**), algorithm complexity, loss of predictability.
- Benefits: better utilization, priority allocation, QoS guarantees.

**[Q:quantum-comparison]**  
**Q: For two 1-second tasks on a single core, which quantum is best: 10ms, 100ms, or 1000ms?**

- 1000ms. With 10ms quantum, 100 context switches. With 1000ms, only 1 switch. Minimize overhead.

**[Q:real-time-scheduling]**  
**Q: Can virtual memory work in a hard real-time OS?**

- No. Virtual memory operations (traps, pulling frames from disk) inject unpredictability. Hard RTOS needs ultra-predictable response times. VM is highly impractical.

**[Q:tail-latency]**  
**Q: What is tail latency?**

- Latency at a high percentile (e.g., 99th %ile) on the CDF. SLO = Service Level Objective (e.g., "99% of requests ≤ 36ms").

---

# [TAG:THREADS]

## User & Kernel Threading

### Large System Design

**[Q:why-threading]**  
**Q: Why do we want threading?**

- Performance: parallelism with shared memory.
- Organization: modular code, easier to process async events.
- Abstraction of concurrency: illusion of simultaneity even on single core.
- Lightweight switching (shared address space, no page table swap).

**[Q:concurrency-vs-parallelism]**  
**Q: What is concurrency vs. parallelism?**

||Concurrency|Parallelism|
|---|---|---|
|What|Abstraction — illusion of simultaneous progress|Actual simultaneous execution|
|Requires multi-core?|No|Yes|

Concurrency mechanisms _can be used to achieve_ parallelism, but concurrency ≠ parallelism.

**[Q:multithreading-vs-multiprocessing]**  
**Q: What are the advantages/disadvantages of multithreading vs. multiprocessing?**

- Multithreading: shares compute AND memory (lightweight switching, resource sharing). Disadvantage: complex synchronization, data races.
- Multiprocessing: shares compute but NOT memory (isolation guarantee). Communication requires IPC (overhead).

**[Q:thread-private-shared]**  
**Q: What is private vs. shared per thread?**

- **Private:** thread ID, program counter, registers, stack.
- **Shared:** address space (code, heap, globals), open files, signal handlers.

**[Q:threading-models]**  
**Q: What are the three threading models?**

**One-to-One (1:1) — Kernel Threading:**

- Each user thread → one kernel thread. True parallelism. Overhead: kernel thread creation for every user thread.
- Most modern OSes (Linux NPTL, Windows, macOS).

**Many-to-One (M:1) — User Space Threading:**

- Many user threads → one kernel thread. Simple, efficient. Fatal flaw: one blocking syscall → entire process blocks. No true parallelism. Kernel unaware of user threads.

**Many-to-Many (M:N) — Hybrid:**

- M user threads → N kernel threads. Fewer context switches, user threads can run in parallel. Very complex. Most OSes abandoned M:N for 1:1.

**[Q:semantic-gap]**  
**Q: What is the semantic gap problem with user-space threading?**

- Kernel sees one process but user space has many threads. Kernel may preempt at worst time (e.g., while user thread holds a lock). Kernel makes decisions without knowledge of user-space thread state.

**[Q:user-space-threading-feasible]**  
**Q: Can threading be implemented in user space?**

- Yes. Context switching between stacks needs no privileged instructions. Cooperative scheduler sufficient.
- Still needs kernel for: I/O (blocking syscalls), sleep/wakeup (timers), true preemption (timer interrupts).

**[Q:kernel-vs-user-threading-tradeoffs]**  
**Q: Kernel-space vs. user-space threading tradeoffs?**

|Kernel-Space|User-Space|
|---|---|
|True parallelism|Semantically-aware scheduling|
|Preemption possible|Lower context switch overhead|
|More info to kernel|Better cache locality|
|Thread-aware scheduling|Lighter thread creation|

**[Q:futex]**  
**Q: What is a futex?**

- Fast Userspace muTEX. User-space handles locking logic (atomics, CAS). Only traps to kernel when thread needs to **sleep** (contention). Division of labor: kernel manages I/O sleeping, scheduling; user-space manages locks, CVs, semaphores.

**[Q:event-based-parallelism]**  
**Q: Do event-based systems achieve parallelism?**

- No. Single process, single thread, single core. Achieves concurrency but not parallelism.

---

# [TAG:CROSS-CUTTING]

## Cross-Cutting Quick Reference

**[Q:boot-sequence]**  
**Q: What is the x86 boot sequence?**

BIOS/UEFI → Bootloader/Bootblock → Kernel

1. CPU reset vector → 0xFFFFFFF0 (hardwired, top 16 bytes).
2. ljmp to BIOS code in low ROM mirror (16-bit real mode, 1MB addressable).
3. BIOS reads first 512 bytes from boot device, verifies 0x55AA signature, loads at 0x7C00.
4. Bootblock: sets up registers, switches to 32-bit protected mode, enables virtual memory.
5. Kernel takes over.

**[Q:registers-reference]**  
**Q: x86 register naming?**

|Suffix|Meaning|
|---|---|
|a|accumulator|
|b|base|
|c|count|
|d|data|
|si|source index|
|di|destination index|
|bp|base pointer|
|sp|stack pointer|
|ip|instruction pointer|
|E prefix|32-bit|
|R prefix|64-bit|

**[Q:process-characterization]**  
**Q: How are processes characterized for scheduling?**

|Type|Behavior|Scheduling Need|
|---|---|---|
|CPU-bound|Hogs CPU|Tolerate longer quanta, gets deprioritized|
|I/O-bound|Sleeps often|Fast response when ready, gets boosted|
|Interactive|e.g., vim|Low latency critical|
|Batch|e.g., cronjob|Throughput matters|
|Real-time|e.g., audio, AR/VR|Both throughput AND latency|

**[Q:linux-memory-tools]**  
**Q: What Linux tools inspect memory?**

- `cat /proc/iomem` — physical memory layout
- `cat /proc/self/maps` — virtual memory layout of current process
- `pmap` — process memory map
- `free` — physical usage
- `strace` — trace system calls (mmap, brk, etc.)

**[Q:powers-of-two-reference]**  
**Quick reference:**

|Bits|Value|Size|
|---|---|---|
|10|1,024|1 KB|
|12|4,096|4 KB (page)|
|20|1,048,576|1 MB|
|22|4,194,304|4 MB (superpage)|
|30|1,073,741,824|1 GB|
|32|4,294,967,296|4 GB|
|48|—|256 TB (x86-64 used)|

**[Q:how-many-context-switches-on-sleep]**  
**Q: How many context switches happen when a process sleeps?**

Save user context → switch to kernel stack → switch to scheduler kernel context → load target kernel context → restore user context.