## Why Interrupts?

Handle **unpredictable events** (keyboard, network, timers, faults). Without them → **polling** (repeatedly checking), which wastes cycles on rare events or misses frequent ones.

|Use Case|Examples|
|---|---|
|Exceptions|Page faults, math errors, power failure|
|Hardware|Timers, buffers, I/O devices|
|Debugging|Software breakpoints|
|Communication|Inter-processor interrupts (IPI)|
|Control|Watchdog timers, non-maskable interrupts|

## Interrupt Types

<!-- INSERT PICTURE: Interrupt taxonomy tree — Hardware (INTR / NMI) and Software (INT) -->

|Type|Maskable?|Trigger|Notes|
|---|---|---|---|
|**NMI**|No — never ignored|Hardware (power fail, memory corruption)|x86 vector 2, fatal in xv6|
|**INTR**|Yes — controlled by IF flag in EFLAGS|Hardware (devices via PIC)|`sti` enables, `cli` disables|
|**INT**|N/A — software-initiated|`int N` instruction|xv6 syscalls: `int 0x40`|

**PIC (8259A):** Routes device interrupts to CPU's single INTR pin. Two cascaded = 16 interrupt lines. CPU only has 2 pins: INTR + NMI.

## Interrupt Vectors & IDT

Every interrupt type → assigned a **vector** (0–255) → determines which handler runs.

**IDT (Interrupt Descriptor Table):** 256 entries × 8 bytes. Each entry = protected entry-point into kernel. **IDTR register** holds pointer to IDT. Loaded with `lidt`.

<!-- INSERT PICTURE: IDTR register → IDT table with gates at offsets 0, 8, 16... -->

### Gate Types

|Gate|`istrap`|IF behavior|Used for|
|---|---|---|---|
|**Interrupt gate**|0|Clears IF → disables further interrupts|Hardware interrupts|
|**Trap gate**|1|Leaves IF alone → interrupts stay enabled|Syscalls|

**Why it matters:** Syscalls use trap gates so hardware interrupts still fire during long kernel operations.

## What Happens on `int N`

**High level:** Determine vector → permission check → switch stacks → save state → jump to handler

**Detailed sequence:**

- Fetch descriptor for vector N from IDT
- **Permission check:** CPL ≤ DPL (only for software `int`)
- If crossing rings (user → kernel): save old SS/ESP, load new ones from **TSS**
- Push: SS, ESP (if ring crossing), EFLAGS, CS, EIP
- Clear IF (interrupt gates only)
- Set CS:EIP from IDT entry → handler executes

**Return:** `iret` — pops EIP, CS, EFLAGS (and SS, ESP if crossing rings back)

### The Trap Frame

Captures full CPU state at moment of interrupt. Fills bottom-to-top like a stack.

<!-- INSERT PICTURE: Trap frame stack diagram — SS/ESP at bottom (ring crossing only), then EFLAGS, CS, EIP, err, trapno, segment regs, general regs at top -->

|Portion|Filled by|Contents|
|---|---|---|
|Bottom (ring crossing only)|Hardware|`ss`, `esp`|
|Middle|Hardware|`eflags`, `cs`, `eip`, `err`|
|Top|Software (alltraps)|`trapno`, segment regs (`ds`,`es`,`fs`,`gs`), general regs (`pushal`)|

---

# Concurrency

## Why It Matters Here

**Interrupts = pseudo-concurrency.** Even on one CPU, an interrupt handler preempts kernel code at any point → interleaved execution → same problems as multithreading.

## The Kernel vs. Handler Deadlock

<!-- INSERT PICTURE: Kernel code holding lock, interrupt fires, handler tries same lock → deadlock arrow loop -->

Kernel holds lock → interrupt fires → handler tries to acquire **same lock** → spins forever (kernel can never run to release it) → **deadlock on a single CPU**

**Solution:** Disable interrupts while holding locks.

```
Acquire() = interrupt_disable() + Lock()
Release() = Unlock() + interrupt_enable()
```

**Order matters** — disable _before_ lock, enable _after_ unlock.

**Key principle:** Mutual exclusion with an interrupt handler is achieved with **interrupt disable**, not locks alone.

## Data Races

> **Two concurrent accesses to the same memory location, at least one being a write.**

Hard to reproduce — only manifest in _some_ interleavings. **Better to over-lock than under-lock** (correctness > performance).

## The "Too Much Milk" Problem

<!-- INSERT PICTURE: Bob/Alice fridge-store diagram and problematic interleaving timeline -->

Two threads, shared variable (fridge). Both check → both see empty → both buy milk → **safety violation**.

|Property|Meaning|
|---|---|
|**Safety**|At most one person buys milk (nothing bad happens)|
|**Liveness**|Someone buys milk when needed (something good happens)|

**Core lessons:**

- Mutual exclusion with only loads/stores is **extremely hard** → need hardware support
- Code must work for **ALL** interleavings, not just most
- Concurrency bugs only appear in **some** interleavings
- Be mindful of shared data access **between** check and update

## Building Locks

**Peterson's Algorithm:** Works with only atomic load/store, but **completely impractical** — only 2 processes, requires sequential consistency.

**What we actually need:** Atomic read-and-write in one operation.

### C11 Atomics

|Operation|What it does|
|---|---|
|`atomic_load()`|Atomic read|
|`atomic_store()`|Atomic write|
|`atomic_fetch_add()`|Atomic read-modify-write|
|`atomic_exchange()`|**Atomic load + store** (key for spinlocks)|
|`atomic_compare_exchange()`|Conditional load + store (CAS)|

### Spinlock via atomic_exchange

```c
r = 1;
while (r != 0) {
    r = exchange(&lock, 1);  // atomically: read old, write 1
}
// r == 0 means lock was free and we just claimed it
```

<!-- INSERT PICTURE: State machine — (lock=0,r=1)→(1,0) "acquired"; (1,1)→(1,1) "spin" -->

- `lock=0`: exchange returns 0 (was free), sets lock=1 → **acquired**
- `lock=1`: exchange returns 1 (was held), sets lock=1 → **spin**
- Release: `lock = 0`

## Memory Models

### The Interleaving Puzzle

```
Initial: x = y = 0
T1: movl $1,(x)    T2: movl $1,(y)
    movl (y),%eax      movl (x),%ebx
```

<!-- INSERT PICTURE: Four interleaving timelines for outcomes B(0,1), C(1,0), D(1,1), A???(0,0) -->

|%eax|%ebx|Possible under SC?|Possible under TSO?|
|---|---|---|---|
|0|1|Yes (T1 first)|Yes|
|1|0|Yes (T2 first)|Yes|
|1|1|Yes (stores interleaved)|Yes|
|**0**|**0**|**No** — can't reorder within a thread|**Yes** — TSO allows load before store to _different_ address|

### TSO — Total Store Order (x86)

- Stores are **totally ordered** across CPUs
- **Respects:** W→W, R→W ordering
- **Does NOT respect:** W→R ordering → loads can pass preceding stores to different addresses
- This is why (0,0) is possible on real hardware

### Sequential Consistency vs. Reality

We **assume** SC (every statement executes in order). We are **not promised** SC by CPU, language, or compiler.

### C11 DRF0 Semantics

> **No data race ⟹ Sequential consistency**

If your code is data-race-free, it behaves as if sequentially consistent. If you have races → **undefined behavior**.

**Takeaway:** Use proper synchronization primitives (locks, semaphores, condition variables, barriers). C11 atomics only in rare expert cases.

## Deadlock

Threads hold locks and wait for each other **in a cycle** → nobody progresses.

**Dining Philosophers:** N philosophers, N forks. Each needs 2 forks. All grab left fork → circular wait → deadlock.

<!-- INSERT PICTURE: Philosophers A, B, C in cycle with numbered forks 1, 2, 3 -->

**Solution: Impose total ordering on lock acquisition.** Always acquire lower-numbered lock first → breaks the cycle.

## `volatile` — A Misconception

|What people think|Reality|
|---|---|
|Makes variables thread-safe|**No** — no atomicity, no fencing|
|Substitute for atomics|**No** — only prevents compiler from optimizing away reads|
|Useful for concurrency|**No** — only useful for memory-mapped device drivers|

## Spinlock Shortfalls

Complex call chains (A calls B calls C, all acquiring same lock) → deadlock.

**Solutions:** enforce locking rules (programmer tracks held locks), recursive locks (complex), consistent lock ordering.
