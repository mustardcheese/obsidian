## Ordering

What does locking enforce?

- Enables exclusivity of access over critical sections

**Data Race:** Two unordered accesses to the same location in memory, where at least one is a write

What does "unordered" mean?

- Locks DO add some kind of order
- We can't exactly specify which thing happens when BUT some kind of order between threads is achieved with locks

**Locks enable dynamic ordering**

- We can determine some partial order after a lock hits
- Reduces the space of possibilities

### Weak Ordering (Relaxed Consistency)

- Hardware/compiler can reorder reads and writes so long as it is still correct **from the executing thread's perspective**
- Weak ordering does NOT concern itself with correctness **across** threads
- Stores from one thread can appear **out of order** to another thread
- A thread might see another thread's writes to different variables at different times
- Without explicit synchronization, **almost no ordering guarantees exist**

Lock acquire/release — mechanism for **partial** order:

- **Acquire** → all subsequent reads/writes in the current thread happen **after** (fence: nothing leaks above)
- **Release** → all preceding reads/writes in the current thread happen **before** (fence: nothing leaks below)

### Ordering Semantics

<!-- INSERT: race condition linked list slides (struct list insert, t1/t2 interleaving diagrams, with and without locks) -->

**Without locks:** both threads read old `list`, both set `next` to old head, both write `list` → one node **lost**.

**With locks:** read-then-write is atomic per thread. Second thread sees the updated `list`.

Three levels of ordering:

- **Unordered:** R₁, R₂, W₁, W₂ — many possible interleavings
- **Partially ordered (w/ locks):** only `R₁ W₁ R₂ W₂` or `R₂ W₂ R₁ W₁` — critical sections are atomic blocks
- **Fully ordered:** exactly one globally visible sequence

**Why partial order is provably correct:** acquire creates a happens-before edge between the acquire and the code inside the critical section. There's also a happens-before between one thread's release and another thread's acquire of the same lock. By **transitivity** of happens-before, one critical section provably executes entirely before the other.

---

## Waiting — Producer Consumer

Keep track of:

- **Safety** — thread safe? no corruption?
- **Liveness** — deadlock-free? progress made?
- **Efficiency** — no wasted CPU?

Correctness first → efficiency second. Overlock if necessary.

**Producer:** adds elements to a queue **Consumer:** removes elements if available; if empty, **wait** for the next element

Mutex alone can't express waiting. We need:

- A computationally efficient waiting primitive
- An ordering primitive (P → C)

**Attempt 1: Lock only, no check**

```
Produce(int v){        Consume(){
  lock(lk);              lock(lk);
  q.push(v);             v = q.pop();   // CRASH if empty
  unlock(lk);            unlock(lk);
}                        return v;
                       }
```

- Safety: **BAD** — pops from empty queue
- Liveness: fine
- Efficiency: bad

**Attempt 2: Add `if` check**

```
Consume(){
  lock(lk);
  if(!q.empty()){
    v = q.pop();
  }
  unlock(lk);
  return v;
}
```

- Safety: fine — checks first
- Liveness: fine
- Efficiency: **BAD** — must keep retrying (busy-wait pattern outside)

### Condition Variables (CV)

**Interface (must know):**

|Operation|Behavior|
|---|---|
|`wait(lock *lk)`|**Atomically** releases lock AND sleeps. Re-acquires lock on wakeup. May have spurious wakeups.|
|`signal()`|Wakes **one** waiter|
|`broadcast()`|Wakes **all** waiters|

**Attempt 3: CV with `if` — no signal**

```
Produce(int v){        Consume(){
  lock(lk);              lock(lk);
  q.push(v);             if(q.empty()){
  unlock(lk);              cv.wait(lk);
}                        }
                         v = q.pop();
                         unlock(lk);
                         return v;
                       }
```

- Safety: fine
- Liveness: **BAD** — no signal, consumer sleeps forever (deadlock)
- Efficiency: fine

**Attempt 4: CV with `if` + signal**

```
Produce(int v){        Consume(){
  lock(lk);              lock(lk);
  q.push(v);             if(q.empty()){
  cv.signal();             cv.wait(lk);
  unlock(lk);            }
}                        v = q.pop();
                         unlock(lk);
                         return v;
                       }
```

- Safety: **BAD** — with multiple consumers, C2 can snipe the item after C1 is signaled but before C1 re-acquires lock. C1 wakes, queue empty, `pop()` fails. Also spurious wakeups.
- Liveness: fine
- Efficiency: fine

**Attempt 5: CORRECT — `while` loop ⚠️**

```
Produce(int v){        Consume(){
  lock(lk);              lock(lk);
  q.push(v);             while(q.empty()){
  cv.signal();             cv.wait(lk);
  unlock(lk);            }
}                        v = q.pop();
                         unlock(lk);
                         return v;
                       }
```

- Safety: **FINE** — re-checks condition after every wakeup
- Liveness: **FINE**
- Efficiency: **FINE**

**RULE: `wait()` MUST ALWAYS be inside a `while` loop.** Two reasons:

1. **Spurious wakeups** — OS may wake you for no reason
2. **Stolen wakeups** — another consumer grabs the item before you re-acquire the lock

C++11 `condition_variable` even enforces this pattern.

### Signal Ordering

Where to place `signal()` in the producer? Three valid positions:

|Placement|Code|Notes|
|---|---|---|
|Inside lock, after push|`lock → push → signal → unlock`|Standard and safe|
|After unlock|`lock → push → unlock → signal`|Correct. Slightly more efficient (avoids "hurry up and wait")|
|Before lock|`signal → lock → push → unlock`|Correct but wasteful — may wake consumer before data is ready; `while` loop saves you|

All three work because of happens-before: `push` happens-before `signal`, `signal` happens-before `wait` returns → `push` happens-before `pop`.

<!-- INSERT: signal ordering slide with happens-before arrow diagram -->

---

## Waiting Mechanism

When a process waits, the CPU either:

1. **Switches to another process** (productive)
2. **Sleeps** (idle — only if nothing else to run)

### What's saved when sleeping?

|State|How saved|
|---|---|
|User address space|Already in process's **page table** — nothing to do|
|User context (regs)|Saved on **trap/syscall into kernel** (trapframe on kstack)|
|Kernel address space|Shared — nothing to do|
|Kernel context (regs)|Saved **explicitly** by `swtch()`|

### swtch — only callee-saved registers

`swtch` is **voluntary** (cooperative). The C compiler already saved caller-saved regs per calling convention. `swtch` only saves: `%ebp, %ebx, %esi, %edi` + `%esp`.

**Contrast:** trap handler is **involuntary** (interrupt) → must save **ALL** registers.

---

## Scheduling

### Context Switch Path

xv6 **never** switches user-to-user directly. Full path:

```
User A → [trap] → Kernel (A's kstack) → swtch → Scheduler (sched kstack)
  → swtch → Kernel (B's kstack) → [trap return] → User B
```

Two kinds of `swtch`:

1. Process kernel context → scheduler context
2. Scheduler context → process kernel context

### Three ways to give up CPU

All follow the same protocol: acquire `ptable.lock` → release other locks → update state → call `sched`

|Function|Meaning|New State|
|---|---|---|
|`yield()`|Timer interrupt / cooperative|RUNNABLE|
|`sleep()`|Waiting for event|SLEEPING|
|`exit()`|Process done|ZOMBIE|

**yield chain:** `trap` → `yield()` → `sched()` → `swtch()` → `scheduler()` → picks next RUNNABLE → `swtch()` → new process resumes in its `sched()` return point

`sched` and `scheduler` are **coroutines** — they always switch to each other in a ping-pong. Exception: `forkret` when a process is first scheduled.

### Linux Scheduling Policies

|Policy|Description|
|---|---|
|`SCHED_OTHER`|Default time-sharing (CFS)|
|`SCHED_IDLE`|Very low priority background|
|`SCHED_BATCH`|CPU-intensive batch|
|`SCHED_FIFO`|Real-time, FIFO (no preemption within priority)|
|`SCHED_RR`|Real-time, round-robin|

---