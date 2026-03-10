# 1. x86 Boot Process

## Three-Stage Boot: BIOS → Bootloader → Kernel

The bootloader is a common middleman between hardware (BIOS) and software (kernel), so each kernel doesn't need its own hardware boot logic.

## BIOS Boot Sequence

**Reset Vector:** A hardwired CPU behavior (baked into silicon) that sets the instruction pointer to a fixed address at the top of the address space. On i386, IP → 0xFFFFFFF0 (4GB − 16 bytes). These 16 bytes hold a single long jump instruction into BIOS ROM.

```nasm
0xfffffff0: ljmp $0xf000,$0xe05b
```

**16-Bit Real Mode:** Every x86 processor boots in 16-bit real mode for compatibility. In this mode, the CPU uses a 20-bit address space (1MB). Physical addresses are computed as CS << 4 + IP. For the reset vector jump: CS=0xF000, IP=0xE05B → physical address = 0xFE05B.

**Address Line Trick:** At power-on, the top 12 address bus lines are forced high by hardware so the 16-bit CPU (which can only compute 20-bit addresses) actually reaches 0xFFFFFFF0. This forcing stops permanently after the first ljmp, and the CPU enters true real mode addressing within the 1MB space.

**Two ROM Mappings:** The same ROM chip is mapped at two ranges: a high mapping (top of 4GB) used only for the reset vector fetch, and a low mirror (within the 1MB real-mode space) so BIOS code can continue executing after the ljmp drops into true real mode.

## BIOS → Bootloader Handover

1. BIOS reads first 512 bytes from boot device (sector 0)
2. Verifies boot signature (last two bytes = 0x55AA)
3. Copies 512 bytes into RAM at 0x7C00
4. Jumps to 0x7C00

0x7C00 is a convention chosen to avoid the IVT and BIOS data area.

## Bootloader's Job

The CPU is still in 16-bit real mode with only physical addressing. The bootloader must: initialize x86 registers to a sane state, disable BIOS interrupts, and switch the processor from real mode to 32-bit protected mode (enabling virtual address mapping).

## Registers

General-purpose: AX (accumulator), BX (base), CX (count), DX (data), SI (source index), DI (destination index), BP (base pointer), SP (stack pointer), IP (instruction pointer). E- prefix for 32-bit, R- prefix for 64-bit.

---

# 2. Isolation

_The goal: create the illusion of sole ownership of a shared resource._

## Types of Isolation

**Failure Isolation** — failures don't propagate between processes; the driving motivation for kernel design. **Performance Isolation** — controls resource consumption, prevents starvation. **Correctness Isolation** — other programs shouldn't affect my program's correctness.

A perfectly isolated process is useless (can't communicate). We want some isolation sometimes. Isolation is needed when there are shared resources AND non-cooperative entities.

**Tradeoff:** Stronger isolation → more safety, less usability.

## Hardware Isolation (Protection Rings)

Only Ring 0 (kernel) and Ring 3 (user) matter in practice.

**Ring 0 protects:** writes to CR3 (page table base), CS (defends CPL), control registers, EFLAGS. Every memory access is checked for privilege via U/S bits in PTEs. I/O port access is restricted.

## CPL (Current Privilege Level)

The lower 2 bits of the CS register. CPL 0 = kernel, CPL 3 = user. CS can only be changed via far jumps, interrupts, or `iret` — preventing user self-escalation.

## Segment Selectors and GDT

A segment selector is a 16-bit value: upper 13 bits index into the GDT/LDT, bit 2 selects table (0=GDT, 1=LDT), bits 1:0 = RPL. The GDT uses a flat memory model (base=0, limit=max), making segmentation a pass-through. Paging does all real memory isolation. The GDT's main purpose is to define DPL so the processor can set CPL, and it hosts the TSS descriptor for kernel stack pointers during privilege transitions.

## IDT (Interrupt Descriptor Table)

Each gate contains: a segment selector (→ GDT, sets handler's CPL), offset (handler address), DPL (who can trigger via `int`), and type. Software interrupts check CPL ≤ DPL (otherwise → general protection fault). Hardware interrupts bypass the DPL check. On ring 3→0 transition: the processor atomically switches to the kernel stack (via TSS), pushes user context (SS/ESP/EFLAGS/CS/EIP), loads new CS from the gate (CPL→0), and jumps to the handler.

**Layered mechanism:** GDT provides CPL identity → paging checks CPL against U/S bits in PTEs.

## The Process as Unit of Isolation

Prevent process X from wrecking/spying on process Y (memory, CPU, FDs, resource exhaustion). Prevent processes from wrecking the OS. Must hold against both bugs and malice.

## Virtual Memory Isolation

Every process gets an identical virtual address space; the MMU translates VA → PA. Privilege is enforced at page granularity. The kernel is mapped into the upper half of every process's address space, protected by U/S bits (not separate page tables). No page table switch on syscall — just a CPL change. This is a performance benefit, but is what Meltdown exploited.

## Time Slicing (CPU Isolation)

Abstract the CPU so each process perceives its own. The scheduler determines who gets the CPU, what resource, and when. Cooperative scheduling alone is insufficient — a malicious/buggy process can refuse to yield. Preemptive scheduling (timer interrupt) is necessary for true CPU isolation.

## System Call Interface

Safe, controlled transfer from user to kernel at predetermined entry points (user can't jump to arbitrary kernel code). `int` or `sysenter` sets CPL to 0; CPL set back to 3 before return. The trap handler saves user context, loads kernel context, sanitizes arguments (must validate user-supplied pointers are in user-accessible memory since kernel at CPL 0 can write anywhere), and accepts or denies the request.

## Isolation is NOT Solved

**Meltdown:** Speculative execution reads kernel memory before the U/S check completes; data leaks via cache side channel. Exploits kernel mapping in every process's page table. **Spectre:** Manipulates branch prediction to leak data across process boundaries. **KPTI fix:** Unmaps kernel from user page tables, requiring a page table switch + TLB flush on every syscall — a direct safety-vs-performance tradeoff.

---

# 3. Kernel Organization

## Monolithic Kernel

Everything (scheduling, file system, I/O) runs in kernel space, accessed via syscalls.

**Pros:** High performance (fewer user-kernel boundary crossings), simpler programming model for user-space. **Cons:** Low fault tolerance (kernel crash → entire OS down), difficult to maintain, not modular. Examples: Linux, xv6, Windows.

## Microkernel

Minimal kernel; nearly everything else runs as user-space programs.

**Pros:** Strong failure isolation (file system crash doesn't kill the kernel), easy to extend. **Cons:** Performance overhead from frequent user/kernel boundary crossings, harder to compartmentalize. Example: macOS (built on a microkernel).

**Key tradeoff:** Monolithic = great for speed, not safety. Micro = great for isolation, not speed.

## What belongs in the kernel?

The kernel provides isolation, protection, and inter-process communication. xv6 has three types of syscalls: process, memory, and file system. The line between user and kernel space is a design decision — not all OS tasks belong inside the kernel.

---

# 4. Virtual Memory

## Why Virtual Memory?

**Isolation** — each process gets its own independent address space. **Resource Multiplexing** — make one physical address space look like many virtual spaces. **Overcoming Limitations** — allocate more virtual memory than physical RAM; use swapping. **Protection** — permission bits (read, write, user/kernel) enforce access control.

## Segmentation (x86)

CPU produces a Logical Address (Selector:Offset) → Segment Translation → Linear/Virtual Address → Page Translation → Physical Address. In modern OSes (including xv6), segmentation is identity-mapped (base=0, limit=max), so logical = linear = virtual.

**GDT entries** are segment descriptors containing: base, limit, permissions, and DPL. ESP uses SS (stack segment), EIP uses CS (code segment), other operations use DS (data segment).

## Paging

### Two-Level Paging (x86-32)

CR3 holds the physical address of the page directory (must be physical because CR3 is the root of translation). The 10 MSB of the virtual address index into the page directory (1024 entries), the next 10 bits index into the page table (1024 entries), and the last 12 bits are the offset within the page.

**Translation step by step:**

1. CR3 → page directory physical address (register read, not memory access)
2. 10 MSB ("Dir") index into PD → get PDE
3. PDE's PPN locates the page table in physical memory
4. Next 10 bits ("Table") index into PT → get PTE
5. PTE's PPN + 12-bit offset → physical address

**A 2-level page walk requires exactly 2 memory accesses** (one for PDE, one for PTE).

### Page Directory and Page Table

Both hold 1024 entries × 32 bits = 4096 bytes = exactly one page. Each entry has a 20-bit PPN in the upper bits and 12 bits of flags. PDE's PPN points to a page table; PTE's PPN points to an actual physical frame.

### PTE/PDE Flags

```
Bit 0: P   — Present (0 → page fault)
Bit 1: W   — Writable (0 = read-only)
Bit 2: U   — User-accessible (0 = kernel-only)
Bit 5: A   — Accessed (set by hardware on read/write)
Bit 6: D   — Dirty (set by hardware on write)
Bit 7: PS  — Page Size (PDE only: 1 = 4MB superpage, skip second level)
Bits 9-11: AVL — Available for OS use (used for CoW metadata, etc.)
```

If P=0, hardware raises a page fault — the OS can store anything in the remaining bits (e.g., swap location). A and D are set by hardware; the OS clears them for page replacement decisions.

### Large/Super Pages

With PS=1 in a PDE, translation uses only one level: 10-bit directory + 22-bit offset = 4MB pages. Available sizes: 4KB/4MB (32-bit), 4KB/2MB/1GB (64-bit). Tradeoff: better TLB coverage but more internal fragmentation.

### Single-Level vs. Multi-Level Page Tables

||Single Level|Multi Level|
|---|---|---|
|Latency|1 memory access (faster)|2 memory accesses (slower)|
|Memory Overhead|Always 4MB per process|Sparse — only allocate for regions in use|
|Fragmentation|Needs contiguous 4MB|Each table = 1 page (4KB), easy to allocate|

Multi-level trades latency for memory savings. The TLB makes this tradeoff acceptable.

### Four-Level Paging (x86-64)

PML4 (9) | Dir Ptr (9) | Directory (9) | Table (9) | Offset (12). Each level has 512 entries × 8 bytes = 4KB. A full walk requires 4 memory accesses. Supports 4KB, 2MB, and 1GB pages.

## TLB (Translation Lookaside Buffer)

The MMU handles VA→PA translation; the TLB is a hardware cache of recent translations.

TLB hit → physical address in ~1 cycle. TLB miss → full page table walk (2–4 memory accesses), result cached in TLB. Page not present → page fault → OS handler.

**iTLB** caches instruction translations, **dTLB** caches data translations. Changing CR3 (e.g., context switch) flushes the entire TLB — a major reason context switches are expensive.

The TLB is what makes multi-level paging practical.

---

# 5. Copy-on-Write (CoW)

## The Problem

Naive `fork()` duplicates all physical pages — extremely slow and wasteful, especially since many children immediately call `exec()` and discard everything.

## The CoW Solution

On fork, the child's page table entries point to the same physical frames as the parent. No pages are copied. The page directory → page table → page structure forms a DAG: if more than one path reaches a page, the resource is shared and must not be modified directly.

**Critical:** Both parent AND child lose write permission on fork. If only the child were marked read-only, the parent could silently corrupt the child's memory.

## CoW Fault Flow

1. CPU traps (page fault — page is marked read-only)
2. OS checks if this is a CoW page (not a real protection violation) using AVL/metadata bits
3. OS allocates a new physical page and copies the shared page's contents
4. OS updates the writing process's PTE to the new page with write enabled
5. OS decrements the reference count on the old page
6. If refcount drops to 1, the sole remaining owner gets write permission restored

## Reference Counting

Each physical page has a reference count. Incremented when a new PTE maps to it (fork), decremented when a mapping is removed (CoW copy, process exit). Refcount = 0 → free the page. Refcount = 1 → sole owner, restore write permission.

**Corner cases:** Grandchildren are handled naturally by refcounting. Out-of-memory during a CoW fault → OS must kill the process. On exit, all page mappings are walked and refcounts decremented.

## Logical vs. Physical Permissions

|Scenario|Logical Permission|Physical PTE|What Happens|
|---|---|---|---|
|Normal writable|Read + Write|R=1, W=1|Access succeeds|
|CoW shared page|Read + Write|R=1, W=0|Write → fault → OS copies|
|Truly read-only|Read only|R=1, W=0|Write → fault → OS kills process|
|Unmapped page|None|P=0|Any access → segfault|

The OS distinguishes CoW faults from real violations using the AVL bits (9–11) that hardware ignores but the OS uses freely.

## TLB and CoW

On a CoW fault: the writing process needs its TLB entry invalidated (PA changed, W bit set). The other process's stale entry is handled implicitly on its next context switch (CR3 reload flushes TLB). So only 1 flush happens now; the other is implicit.

---

# 6. VM Tricks

## Demand Paging / Lazy Allocation

On `sbrk()`, record the address range as valid but don't allocate physical pages. On first access → page fault → allocate and map then. Benefit: processes that allocate large heaps but touch little memory waste no RAM. This is oversubscription. Tradeoff: each first access incurs a page fault.

## Zero-Filled Pages

Pages from the kernel are zeroed by default (security requirement — prevents leaking old data). Optimization: map all zero-pages to a single read-only physical zero page. Reads see zeros. Writes trigger a CoW-style fault → allocate a real page. If 100 pages allocated but only 5 written, only 5 physical pages exist.

## Virtual Shared Memory

Multiple processes can intentionally share a physical page for IPC. Unlike CoW, writes ARE visible to all sharers. Shared libraries: loaded once physically, mapped read-only into many address spaces.

## Memory-Mapped Files

Map a file into the virtual address space via `mmap()`. Read → page fault → OS reads from disk. Write → OS marks dirty, writes back on sync/unmap. Efficient file I/O without explicit `read()`/`write()`.

## Swapping

When RAM is full, the OS evicts pages to a swap partition on disk. The PTE is marked not-present (P=0), and the OS stores the swap location in the remaining PTE bits. On access → page fault → OS reads the page back from disk.

---

# 7. Swapping & Page Replacement

## Belady's Optimal Algorithm

Evict the page accessed furthest in the future. Provably optimal. Impossible in practice (requires future knowledge). Used only as a theoretical benchmark.

## LRU (Least Recently Used)

Evict the page used longest ago (temporal locality). Impractical for pages because it requires recording a timestamp on every memory access. The per-access overhead is unacceptable — you'd pay the cost even if you never need to evict.

## Clock (Second Chance) Algorithm

An efficient LRU approximation using a single access bit per page.

**Structure:** Pages in a circular buffer, each with an access bit (a). A clock hand sweeps forward.

**On eviction:**

- If a == 1: clear to 0 ("second chance"), advance hand
- If a == 0: evict this page

**How trapping works:** When the clock hand clears a page's access bit, the OS also clears PTE_P. Next access → page fault → handler sets a=1, restores PTE_P, resumes. All subsequent accesses hit normally until the hand clears it again.

**Key efficiency:** We only trap on the 0→1 transition (first access after a clear), NOT on every read/write.

**Access bit transitions:**

|Transition|Cause|Meaning|
|---|---|---|
|0 → 1|Process accesses page → page fault|Only time we trap|
|1 → 0|Clock hand sweeps over|Second chance used up|
|1 → 1|Accessed again between sweeps|Actively in use|
|0 → 0|Not accessed, hand hasn't passed|Prime eviction candidate|

**Worst case:** All pages have a=1 → first full sweep clears all to 0, second sweep evicts the first a=0 found. Cost: 2N page inspections.

---

# 8. Concurrency

## Interrupts

Handle unpredictable events. Without them → polling (wastes cycles or misses events).

|Type|Maskable?|Trigger|Notes|
|---|---|---|---|
|NMI|No|Hardware (power fail, memory corruption)|Vector 2, fatal|
|INTR|Yes (IF flag)|Hardware devices via PIC|`cli` disables, `sti` enables|
|INT|N/A (software)|`int N` instruction|xv6 syscalls: `int 0x40`|

## IDT and Gates

256 entries, each a protected entry-point into kernel. IDTR register holds pointer to IDT.

**Interrupt gate** (istrap=0): clears IF → disables further interrupts. Used for hardware interrupts. **Trap gate** (istrap=1): leaves IF alone → interrupts stay enabled. Used for syscalls.

## What Happens on `int N`

Fetch IDT descriptor → permission check (CPL ≤ DPL, software int only) → if crossing rings: save old SS/ESP, load new from TSS → push SS, ESP, EFLAGS, CS, EIP → clear IF (interrupt gates) → jump to handler. Return via `iret`.

### Trap Frame

|Portion|Filled by|Contents|
|---|---|---|
|Bottom (ring crossing)|Hardware|ss, esp|
|Middle|Hardware|eflags, cs, eip, err|
|Top|Software (alltraps)|trapno, segment regs, general regs (pushal)|

## Data Races

Two concurrent accesses to the same memory location, at least one a write. Hard to reproduce — only manifest in some interleavings. Better to over-lock than under-lock.

## Kernel vs. Handler Deadlock

Kernel holds lock → interrupt fires → handler tries same lock → spins forever → deadlock on single CPU. Solution: disable interrupts while holding locks.

```
Acquire() = interrupt_disable() + Lock()
Release() = Unlock() + interrupt_enable()
```

Disable before lock, enable after unlock. Mutual exclusion with an interrupt handler requires interrupt disable, not locks alone.

## Building Locks

We need atomic read-and-write in one operation. Key primitive: `atomic_exchange` — atomically reads old value and writes new value.

### Spinlock via atomic_exchange

```c
r = 1;
while (r != 0) {
    r = exchange(&lock, 1);  // read old, write 1
}
// r == 0 means lock was free, we claimed it
// Release: lock = 0
```

## Memory Models

### TSO (Total Store Order) — x86

Stores are totally ordered across CPUs. Respects W→W and R→W ordering. Does NOT respect W→R — loads can pass preceding stores to different addresses.

Classic puzzle: x=y=0, T1 writes x then reads y, T2 writes y then reads x. Under sequential consistency, both reading 0 is impossible. Under TSO (real x86), both reading 0 IS possible.

### C11 DRF0

No data race ⟹ sequential consistency. If you have races → undefined behavior. Use proper synchronization primitives.

## Deadlock

Threads hold locks and wait for each other in a cycle. Classic example: dining philosophers — all grab left fork → circular wait → deadlock. Solution: impose total ordering on lock acquisition (always acquire lower-numbered first).

## `volatile` is NOT for Concurrency

No atomicity, no fencing. Only prevents the compiler from optimizing away reads. Only useful for memory-mapped device registers.

---

# 9. Ordering, Waiting, Scheduling

## Ordering

Locks enable dynamic, partial ordering. They reduce the space of possible interleavings to only valid ones.

**Without locks:** both threads read old value, both write → one update lost. **With locks:** critical sections execute as atomic blocks — either T1 then T2, or T2 then T1.

**Why partial order is correct:** Acquire creates a happens-before edge. Release-to-acquire of the same lock creates a happens-before between threads. By transitivity, one critical section provably executes entirely before the other.

### Weak Ordering

Hardware/compiler can reorder reads and writes as long as it's correct from the executing thread's perspective. Without synchronization, almost no cross-thread ordering guarantees exist. Lock acquire acts as a fence (nothing leaks above), release acts as a fence (nothing leaks below).

## Producer-Consumer with Condition Variables

**CV Interface:**

|Operation|Behavior|
|---|---|
|`wait(lock *lk)`|Atomically releases lock AND sleeps. Re-acquires on wakeup. May spuriously wake.|
|`signal()`|Wakes one waiter|
|`broadcast()`|Wakes all waiters|

**The correct pattern (memorize this):**

```c
Produce(int v) {           Consume() {
  lock(lk);                  lock(lk);
  q.push(v);                 while (q.empty()) {
  cv.signal();                 cv.wait(lk);
  unlock(lk);                }
}                            v = q.pop();
                             unlock(lk);
                             return v;
                           }
```

**RULE: `wait()` MUST ALWAYS be inside a `while` loop.** Two reasons: spurious wakeups (OS may wake you for no reason) and stolen wakeups (another consumer grabs the item before you re-acquire the lock).

Using `if` instead of `while` is a classic bug — a signaled consumer can wake up to find an empty queue if another consumer sniped the item.

**Signal placement:** All three positions (inside lock after push, after unlock, before lock) are correct because of happens-before guarantees. The `while` loop protects against all orderings.

## Waiting Mechanism

When a process waits, the CPU switches to another process (or sleeps if nothing to run).

**What's saved:**

|State|How|
|---|---|
|User address space|Already in page table — nothing to do|
|User context (regs)|Saved on trap into kernel (trapframe on kstack)|
|Kernel address space|Shared — nothing to do|
|Kernel context (regs)|Saved explicitly by `swtch()`|

**swtch** is voluntary (cooperative). Only saves callee-saved registers (%ebp, %ebx, %esi, %edi, %esp). Contrast: trap handler is involuntary → must save ALL registers.

## Context Switch Path

xv6 never switches user-to-user directly:

```
User A → [trap] → Kernel (A's kstack) → swtch → Scheduler
  → swtch → Kernel (B's kstack) → [trap return] → User B
```

### Three Ways to Give Up CPU

All follow: acquire ptable.lock → release other locks → update state → call sched.

|Function|Meaning|New State|
|---|---|---|
|`yield()`|Timer interrupt / cooperative|RUNNABLE|
|`sleep()`|Waiting for event|SLEEPING|
|`exit()`|Process done|ZOMBIE|

`sched` and `scheduler` are coroutines — they always switch to each other (ping-pong).

---

# 10. Scheduling

## Scheduling Goals

**Throughput** — maximize work completed (batching helps). **Latency** — minimize response time. **Fairness** — equitable resource distribution. **SLO attainment** — e.g., "99% of requests ≤ 36ms." These goals conflict — no universal policy exists.

**Systems conjecture:** Can't have all three of simplicity, performance, and cost.

## Key Dimensions

Throughput vs. latency (batching helps one, hurts the other). Preemptive vs. cooperative. Quantum size: small = responsive but more overhead, large = less overhead but less responsive.

## Process Types

|Type|Behavior|Need|
|---|---|---|
|CPU-bound|Hogs CPU|Tolerates longer quanta|
|I/O-bound|Sleeps often|Fast response when ready|
|Interactive|e.g., vim|Low latency critical|
|Batch|e.g., cronjob|Throughput matters|
|Real-time|e.g., audio, AR/VR|Both throughput AND latency|

## Round-Robin

Fixed time unit per process, cycles through all. Starvation-free but no priority distinction.

## Linux CFS (Completely Fair Scheduler)

Based on Weighted Fair Queuing. Processes that constantly use full CPU get lower priority. Processes that mostly sleep get boosted (fall behind on virtual runtime → compensated when they wake).

Process A (weight 2) + Process B (weight 1) → A gets 2/3 CPU, B gets 1/3.

### Linux Scheduling Policies

|Policy|Use|
|---|---|
|SCHED_OTHER|Default time-sharing (CFS)|
|SCHED_BATCH|CPU-intensive batch|
|SCHED_FIFO|Real-time FIFO (runs until yield or preempted by higher RT)|
|SCHED_RR|Real-time round-robin (FIFO + time quanta at same priority)|

RT policies always preempt normal policies.

## Real-Time Scheduling

**Hard real-time** — guaranteed time bound. Impractical with virtual memory (page faults → unbounded latency). **Soft real-time** — critical tasks get priority. Requires priority scheduling and low dispatch latency.

---

# 11. Threading

## Why Threads?

Performance (parallelism with shared memory), organization (modular code, async events), and abstraction of concurrency. Thread switching is lightweight (shared address space, no page table swap). Challenge: synchronization.

## Concurrency vs. Parallelism

**Concurrency** — abstraction of simultaneous progress (doesn't require multi-core). **Parallelism** — actual simultaneous execution (requires multi-core). Concurrency mechanisms can achieve parallelism, but they're not the same thing.

## Thread Definition

Private per thread: thread ID, program counter, registers, stack. Shared across threads: address space (code, heap, globals), open files, signal handlers.

## Threading Models

### One-to-One (1:1) — Kernel Threading

Each user thread = one kernel thread. True parallelism on multiprocessor. Overhead: must create a kernel thread for every user thread. Used by most modern OSes (Linux NPTL, Windows, macOS).

### Many-to-One (M:1) — User-Space Threading

Many user threads → one kernel thread. Lightweight but fatal flaw: one blocking syscall blocks the entire process. No true parallelism. Kernel is unaware of user threads.

### Many-to-Many (M:N) — Hybrid

M user threads → N kernel threads. Theoretically best of both worlds but too complex. Most OSes abandoned M:N in favor of 1:1.

## User-Space vs. Kernel Threading Tradeoffs

|Kernel-Space|User-Space|
|---|---|
|True parallelism|Semantically-aware scheduling|
|Preemption possible|Lower context switch overhead|
|Thread-aware scheduling|Better cache locality|
|Can control resources|Lighter thread creation|

**Semantic Gap Problem:** With user-space threading, the kernel sees one process but user space has many threads. Kernel may preempt at the worst time (e.g., while a user thread holds a lock).

**M:1 blocking problem:** If one user thread calls `read()` (a blocking syscall), the kernel thread blocks and the user-space scheduler never gets a chance to switch — all threads in the process are stuck.

## Modern Approach

Industry settled on 1:1 kernel threading with user-space optimizations. **futex** (Fast Userspace muTEX): user-space handles locking with atomics/CAS, only traps to kernel when a thread needs to sleep (contention). Division of labor: kernel manages I/O/sleep/scheduling, user-space manages locks/CVs/semaphores.