## Why Threading?

- Performance: parallelism with shared memory resources
- But also benefits **beyond performance** (even on single-core, pre-2004):
    - **Organization** — modular code, easier to process asynchronous events (e.g., UI thread + background worker)
    - **Abstraction of concurrency** — illusion of simultaneity even without true parallelism
- Switching between threads is lightweight (shared address space, no page table swap)
- **Challenge:** synchronization (race conditions, deadlocks)

---

## Concurrency vs. Parallelism

||Concurrency|Parallelism|
|---|---|---|
|What|An **abstraction** — illusion of simultaneous progress|**Actual** simultaneous execution|
|Requires multi-core?|No (single core, single thread suffices)|Yes|
|Mechanisms|Threads, multi-processing, event-based|Threads or processes on multiple CPUs|

- Concurrency mechanisms **can be used to achieve** parallelism, but concurrency ≠ parallelism

---

## Mechanisms of Concurrency

### Multi-processing

- Processes share compute resources but **not** memory
- **Key guarantee:** memory space isolation
- Communication requires IPC (overhead)

### Threads

- Deliberately **break** memory isolation
- **Key guarantee:** shared memory resources by design

### Event-based Systems

- Single process, single thread
- **Voluntarily preemptive** (program explicitly yields — e.g., callbacks, Node.js)
- No locks needed, but can't exploit multiple CPUs alone

---

## Thread Defined

> "A **thread** of execution is the smallest sequence of programmed instructions that can be managed independently by a scheduler"

> "A thread, sometimes called a lightweight process, is a basic unit of CPU utilization; it comprises a **thread ID, a program counter, a register set, and a stack**"

**Private per thread:** thread ID, program counter, registers, stack **Shared across threads:** address space (code, heap, globals), open files, signal handlers

---

## Benefits of Threads

- **Responsiveness** — UI stays interactive (abstraction of concurrency)
- **Resource Sharing** — threads share memory by default; processes don't
- **Economy** — creation/destruction much cheaper than processes (no address space duplication)
- **Multiprocessors** — can achieve true parallelism (vs. single-processor illusion)

---

## Threading Design Models

### One-to-One (1:1) — "Kernel Threading"

![[Pasted image 20260303143530.png|500]]

- Each user thread maps to one kernel thread
- Improved concurrency — kernel is aware of every thread
- **Can run in parallel** on multiprocessor
- **Overhead:** must create a kernel thread for every user thread (syscall + kernel stack + kernel data structures)
- Most modern OSes use this (Linux NPTL, Windows, macOS)

### Many-to-One (M:1) — "User Space Threading"

![[Pasted image 20260303143619.png|500]]

- Many user threads map to one kernel thread
- Simple, efficient, application has semantic awareness of its own threads
- **Fatal flaw:** one thread making a blocking syscall → **entire process blocks**
- Only one kernel thread → only one CPU → **no true parallelism**
- Kernel is completely unaware of user threads

### Many-to-Many (M:N) — "Hybrid Threading"

![[Pasted image 20260303150242.png|500]]

- M user threads map to N kernel threads (M ≥ N)
- **Advantages:** user threads can run in parallel, fewer context switches, lightweight user thread creation
- **Disadvantages:** kernel thread stalls still block mapped user threads, still not cooperative CPU use, high complexity
- Most OSes **abandoned M:N** in favor of 1:1

---

## User-Space Threading Library

How it works — **same mechanisms as xv6 kernel threading:**

- `swtch` — context switch (swap registers + stack pointer)
- Scheduler — chooses which thread to run next
- Concurrency primitives — built from user-space atomics and queues

Why it's feasible:

- Threading assumes **cooperation** → cooperative scheduler is sufficient
- No privileged instructions needed — thread context, stacks, registers all in user space
- **Can switch stacks in user space**

What user-space **still needs the kernel for:**

- I/O (blocking syscalls like `read()`)
- Sleep/wakeup (kernel controls timers)
- True preemption (timer interrupts)

---

## Kernel vs. User-Space Threading Tradeoffs

|Kernel-Space|User-Space|
|---|---|
|True parallelism|Semantically-aware scheduling (app knows its workload)|
|Preemption possible|Lower context switch overhead (no mode switch)|
|More info available to kernel|Better cache locality|
|Can control resource utilization|Lighter weight thread creation|
|Thread-aware process scheduling|No kernel involvement for thread ops|

### The Semantic Gap Problem

- With user-space threading, the kernel sees **one process** but user space has many threads inside
- Kernel may preempt the process at the worst time (e.g., while a user thread holds a lock)
- Kernel makes scheduling decisions **without knowledge** of user-space thread state

### Parallelism Example

**User-space threading (M:1)** — single CPU:

- Thread 1: `do_work()` → `sleep(100)` → `do_work()`
- Thread 2: `read(network, buf)` (blocks for a long time)
- Problem: `read()` is a syscall — the **kernel thread** blocks → Thread 1 never gets to run either
- User-space scheduler never even gets a chance to switch

**Kernel threading (1:1)** — Thread 1 on cpu1, Thread 2 on cpu2:

- Thread 1 sleeps → kernel reschedules on cpu1
- Thread 2 blocks on `read()` → kernel handles it on cpu2
- True parallel execution, kernel manages blocking correctly

---

## Scheduler Activations (1991)

One approach to making M:N work — **communication between kernel and user space:**

1. Kernel notifies user-space scheduler of kernel events via **upcalls**
2. User space can notify kernel of its decisions

Implemented in NetBSD → **abandoned**. Attempted in Linux 2.4.x → abandoned. Complexity wasn't worth it.

---

## Modern Threading Libraries

Industry settled on **1:1 kernel threading** (pthreads/NPTL), but with user-space optimizations:

- **`futex`** (Fast Userspace muTEX) — kernel sleep/wakeup mechanism
    - User-space handles locking logic (atomics, CAS)
    - Only traps to kernel when thread needs to **sleep** (contention)
- **Division of labor:**
    - Kernel manages: I/O sleeping, process sleeping, scheduling
    - User-space manages: locks, condition variables, semaphores

<!-- TODO: Consider adding the OS threading model table (Linux 1:1, FreeBSD M:N→1:1, Solaris M:N→1:1, Windows 1:1, etc.) if you want quick-reference for exam -->

---
