# VMM
## Segmentation in xv6

When xv6 boots, it sets up four segments — all with **base=0** and **limit=0xFFFFFFFF** (the full 4GB space), effectively making segmentation a pass-through:

```c
c->gdt[SEG_KCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_KERN);
c->gdt[SEG_KDATA] = SEG(STA_W,       0, 0xffffffff, DPL_KERN);
c->gdt[SEG_UCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_USER);
c->gdt[SEG_UDATA] = SEG(STA_W,       0, 0xffffffff, DPL_USER);
```

- The only difference between kernel and user segments is the **DPL** (privilege level)
- Segmentation does NOT provide isolation in xv6 — that job belongs entirely to paging

---

## Bootstrapping Virtual Memory in xv6

### The chicken-and-egg problem

You need page tables to use virtual addresses, but you need to allocate memory to build page tables. xv6 solves this with a **statically-allocated** page directory using 4MB superpages.

### `entrypgdir` — the boot page table

```c
pde_t entrypgdir[NPDENTRIES] = {
    // Map VA's [0, 4MB) to PA's [0, 4MB)        ← identity map
    [0] = (0) | PTE_P | PTE_W | PTE_PS,
    // Map VA's [KERNBASE, KERNBASE+4MB) to PA's [0, 4MB)  ← high map
    [KERNBASE>>PDXSHIFT] = (0) | PTE_P | PTE_W | PTE_PS,
};
```

**Why two entries mapping to the same physical 4MB?**

- The **identity map** (entry 0) is needed because right after paging is turned on, EIP still holds a low physical address. Without this, the next instruction fetch would fault.
- The **high map** (KERNBASE entry) is where the kernel actually wants to run (virtual addresses starting at 0x80000000). Once the kernel jumps to high addresses, the identity map is no longer needed.

### Boot sequence in entry.S

```asm
# Turn on page size extension for 4MB pages
movl    %cr4, %eax
orl     $(CR4_PSE), %eax
movl    %eax, %cr4
# Set page directory (CR3 takes PHYSICAL address)
movl    $(V2P_WO(entrypgdir)), %eax
movl    %eax, %cr3
# Turn on paging
movl    %cr0, %eax
orl     $(CR0_PG|CR0_WP), %eax
movl    %eax, %cr0
```

### Two-phase memory initialization

1. **kinit1()** — called while still using entrypgdir; frees pages from end-of-kernel to 4MB boundary onto the free list
2. **kvmalloc()** — builds the full kernel page table mapping all physical memory, switches CR3
3. **kinit2()** — frees the rest of physical memory (4MB to PHYSTOP)

---

## xv6 Virtual Address Space Layout

```
         +-=> +------------------+  <= 0xFFFFFFFF
         |    |   free memory    |
         |    +------------------+
kernel   |    | kernel text/data |  (mapped from PA 0x100000)
space    |    +------------------+  <= 0x80100000
(CPL=0)  |    |      BIOS        |  (mapped from PA 0x0)
         +-=> +------------------+  <= 0x80000000 (KERNBASE)
         |    |      heap        |
user     |    +------------------+
space    |    |      stack       |
(CPL=3)  |    +------------------+
         |    |  user text/data  |
         +-=> +------------------+  <= 0x00000000
```

- The kernel is mapped into **every** process's address space (above KERNBASE)
- Syscalls don't need to change CR3 — only a privilege level change is needed
- The kernel can directly access user memory since both are in the same page table

---

## `walkpgdir` — Software Page Table Walk

This function does in software what the MMU hardware does: given a virtual address, find (or create) the corresponding PTE.

c

```c
static pte_t *
walkpgdir(pde_t *pgdir, const void *va, int alloc)
{
    pde_t *pde;
    pte_t *pgtab;

    pde = &pgdir[PDX(va)];              // Index into PD using top 10 bits
    if(*pde & PTE_P){
        pgtab = (pte_t*)P2V(PTE_ADDR(*pde));  // PDE present: extract PT phys addr, convert to vaddr
    } else {
        if(!alloc || (pgtab = (pte_t*)kalloc()) == 0)
            return 0;                    // Not present & not allocating: return null
        memset(pgtab, 0, PGSIZE);        // Zero out new page table
        *pde = V2P(pgtab) | PTE_P | PTE_W | PTE_U;  // Install PDE (store phys addr + flags)
    }
    return &pgtab[PTX(va)];             // Index into PT using middle 10 bits, return PTE address
}
```

Key macros:

- `PDX(va)` — extracts page directory index (bits 31-22)
- `PTX(va)` — extracts page table index (bits 21-12)
- `PTE_ADDR(pte)` — masks off flag bits, giving the physical address
- `P2V()` / `V2P()` — convert between physical and virtual addresses (add/subtract KERNBASE)

---

## xv6 VMM Limitations vs. Real OSes

|Feature|xv6|Linux / Real OS|
|---|---|---|
|Many-to-one VA→PA mapping|**No** — at most kernel + 1 user per physical page|**Yes** — many virtual pages can share one physical frame|
|Copy-on-Write fork|**Not supported** (Lab 2 adds this)|Fully supported|
|Shared memory / shared libraries|**Not supported**|Supported via shared mappings|
|Page reference counting|**Not needed** — pages are binary free/used|**Required** — must track how many mappings exist per frame|
|Physical memory|Maps up to 2GB|Uses all available RAM + swap|


## CoW

### xv6 VMM Limitations

- xv6 currently has **no ability** to have multiple virtual pages map to a single physical page
- Physical page tracking is simple and binary: free or used (no reference counting)
- Once the kernel and one user process map a physical page, no more mappings are possible
- This makes CoW, shared memory, and shared libraries difficult/impossible in vanilla xv6

### Page Table Walk in xv6 (`walkpgdir`)

c

```c
static pte_t *
walkpgdir(pde_t *pgdir, const void *va, int alloc)
{
  pde_t *pde;
  pte_t *pgtab;

  pde = &pgdir[PDX(va)];             // Index into PD using top 10 bits
  if(*pde & PTE_P){
    pgtab = (pte_t*)P2V(PTE_ADDR(*pde)); // PDE present: get PT base vaddr
  } else {
    if(!alloc || (pgtab = (pte_t*)kalloc()) == 0)
      return 0;                        // Not present and can't alloc: fail
    memset(pgtab, 0, PGSIZE);         // Zero the new page table
    *pde = V2P(pgtab) | PTE_P | PTE_W | PTE_U; // Install PDE
  }
  return &pgtab[PTX(va)];            // Index into PT using next 10 bits
}
```

### Key xv6 Macros

- `PDX(va)` = `(((uint)(va) >> PDXSHIFT) & 0x3FF)` — page directory index
- `PTX(va)` = `(((uint)(va) >> PTXSHIFT) & 0x3FF)` — page table index
- `PTE_ADDR(pte)` = `((uint)(pte) & ~0xFFF)` — mask flags to get physical frame number
- `P2V(pa)` — physical to virtual address (adds KERNBASE)
- `V2P(va)` — virtual to physical address (subtracts KERNBASE)

### xv6 TLB Management

- xv6 flushes the TLB **only on CR3 updates** (i.e., on context switches)
- No fine-grained `invlpg` — the entire TLB is cleared on every process switch
- This is simple but wasteful compared to real OSes

### Lab 2 Notes

- Lab 2 implements CoW **page allocation only** — NOT CoW page table or page directory allocation
- Each process still gets its own freshly allocated page directory and page tables
- Only the physical data pages are shared and CoW'd

# Scheduling
**
---

## xv6 Scheduler Implementation

### Context Switch Path

xv6 **never** switches directly user→user. Always goes through scheduler:

1. User → Kernel (syscall or timer interrupt)
2. Process kernel context → Scheduler context (`swtch` #1)
3. Scheduler context → New process kernel context (`swtch` #2)
4. Kernel → User (trap return)

<!-- INSERT PICTURE: Diagram from lecture showing user space (shell, cat) above the line, kernel space below with kstack_shell → swtch → kstack_scheduler → swtch → kstack_cat, with save/restore arrows -->

### `swtch`

```c
void swtch(struct context **old, struct context *new);
```

Thread-agnostic — just saves/loads register sets (contexts):

1. Loads args into `%eax`, `%edx` (before losing them when `%esp` changes)
2. Pushes **callee-save** registers: `%ebp`, `%ebx`, `%esi`, `%edi`
3. Saves `%esp` → `*old`
4. Loads `new` → `%esp` (now on the new stack)
5. Pops saved registers, `ret` pops `%eip`

Only callee-save registers because caller-save regs are already on the stack per C calling convention. `%eip` was saved by the `call` instruction.

### `yield` → `sched` → `swtch`

Timer interrupt → trap handler calls `yield()` → `sched()` → `swtch(&proc->context, cpu->scheduler)`

### Protocol for Giving Up CPU

A process must:

1. Acquire `ptable.lock`
2. Release any other locks (avoid deadlock)
3. Update own state (RUNNABLE / SLEEPING / ZOMBIE)
4. Call `sched`

`yield`, `sleep`, and `exit` all follow this protocol.

### Scheduler Loop (Round-Robin)

```c
acquire(&ptable.lock);
for(p = ptable.proc; p < &ptable.proc[NPROC]; p++){
    if(p->state != RUNNABLE) continue;
    proc = p;
    switchuvm(p);          // switch to process page table
    p->state = RUNNING;
    swtch(&cpu->scheduler, p->context);
    switchkvm();           // back to kernel page table
    proc = 0;
}
release(&ptable.lock);
```

Linear scan of process table → runs first RUNNABLE process found.

### `sched` ↔ `scheduler` = Coroutines

`sched` always switches to `scheduler`, `scheduler` always switches back to a process in `sched`. Exception: `forkret` — runs when a process is first scheduled (no prior `sched` to return to).**

# Concurrency

## Interrupt Flow

**Entry:** `vectorN` → `alltraps` → `trap()` → `syscall()` (or other handler) **Exit:** `syscall()` → `trapret()` → `iret`

**Key vectors:** 14 = page fault (lab2), 32 = timer/scheduler (lab3), 0x40 = syscall

## IDT Init (trap.c)

```c
void tvinit(void) {
    for (i = 0; i < 256; i++)
        SETGATE(idt[i], 0, SEG_KCODE<<3, vectors[i], 0);
    // Syscall: trap gate, user-invokable
    SETGATE(idt[T_SYSCALL], 1, SEG_KCODE<<3, vectors[T_SYSCALL], DPL_USER);
}
```

|Entry|istrap|DPL|Why|
|---|---|---|---|
|All others|0 (interrupt gate)|0 (kernel only)|Disable interrupts during handling|
|T_SYSCALL|1 (trap gate)|DPL_USER|User code can invoke; interrupts stay enabled|

## Spinlock

```c
struct spinlock {
    atomic_uint locked;   // 0=free, 1=held
    char *name;           // debugging
    struct cpu *cpu;      // which CPU holds it
    uint pcs[10];         // call stack that acquired it
};
```

**acquire():** `pushcli()` (disable interrupts, nested counter) → panic if already held → `atomic_exchange_explicit(&locked, 1, memory_order_acq_rel)` spin loop → record debug info

**release():** panic if not held → clear debug info → `atomic_store_explicit(&locked, 0, memory_order_release)` → `popcli()` (re-enable interrupts when nesting count hits 0)

**pushcli/popcli:** Nested interrupt disable. Increments/decrements per-CPU counter. Only re-enables interrupts when counter reaches 0 — safe for nested lock acquisition.

## Deadlock in xv6

xv6 holds **at most 2 locks** simultaneously. Examples: `ideintr` holds IDE lock + acquires ptable lock via `wakeup`; file system locks directory + file. Prevention via **consistent lock ordering**.


# Waiting, Ordering, Scheduling

### xv6 `swtch` (assembly)

```asm
swtch:
  movl 4(%esp), %eax     # eax = old context pointer
  movl 8(%esp), %edx     # edx = new context pointer
  pushl %ebp              # save callee-saved regs to old stack
  pushl %ebx
  pushl %esi
  pushl %edi
  movl %esp, (%eax)       # save old stack pointer into *old
  movl %edx, %esp         # switch to new stack
  popl %edi               # restore callee-saved regs from new stack
  popl %esi
  popl %ebx
  popl %ebp
  ret                      # returns using NEW stack's return address
```

Key: `ret` pops return address from the **new** stack — `swtch` returns into a different function than the one that called it.

### xv6 sleep/wakeup channels

- xv6 uses **one global process table** (no per-CV wait lists)
- `sleep(chan, lock)` — sets state to SLEEPING, records `chan`, calls `sched`
- `wakeup1(chan)` — scans entire ptable, any SLEEPING process with matching `chan` → RUNNABLE

```c
// wakeup1 implementation
for(p = ptable.proc; p < &ptable.proc[NPROC]; p++)
  if(p->state == SLEEPING && p->chan == chan)
    p->state = RUNNABLE;
```

### xv6 sleeplock (built on spinlock + sleep)

```c
struct lock { struct spinlock *l; int locked; List waitlist; };

void lock(struct lock *lk) {
    acquire(lk->l);
    while (locked == 1) {
        sleep(&lk->waitlist, l);   // sleep releases spinlock
    }
    locked = 1;
    release(lk->l);
}

void unlock(struct lock *lk) {
    acquire(lk->l);
    lk->locked = 0;
    wake_one(&lk->waitlist);
    release(lk->l);
}
```

Uses spinlock for the brief state-check; sleeps for the long wait.

### xv6 scheduler

```c
void scheduler(void) {
    for(;;) {
        sti();                             // enable interrupts
        acquire(&ptable.lock);
        for(p = ptable.proc; p < &ptable.proc[NPROC]; p++) {
            if(p->state != RUNNABLE) continue;
            c->proc = p;
            switchuvm(p);                  // load process page table
            p->state = RUNNING;
            swtch(&c->scheduler, p->context);  // switch to process
            switchkvm();                   // back to kernel page table
            c->proc = 0;
        }
        release(&ptable.lock);
    }
}
```

- `switchuvm(p)` — loads process page table
- `switchkvm()` — restores kernel-only page table (used between processes)
- Process must release `ptable.lock` after being switched in, re-acquire before switching out

### xv6 yield

```c
void yield(void) {
    acquire(&ptable.lock);
    myproc()->state = RUNNABLE;
    sched();
    release(&ptable.lock);
}
```

<!-- INSERT: context switch diagram slide (shell → kstack → scheduler kstack → cat kstack → cat userspace) -->


# Threading

## xv6 Specifics

### Current State

- Each process has its own **kernel stack**
- **No user threads** exist
- Scheduler has no SMP awareness

### Goal: 1:1 Kernel Threading (Lab 3)

- Threads scheduled by existing scheduler
- Shared memory (shared page directory)
- Synchronization primitives:
    - Waiting: `waitpid`, `thread_wait`
    - Spinlocks: `init`, `acquire`, `release`
    - Mutexes: `park`/`setpark`/`unpark`, `mutex_init`/`acquire`/`release`
    - Condition variables: `cond_wait`, `cond_signal`

### `clone()` System Call

- `int clone(void *stack, int size)`
- Like `fork()`, **except:** reuses parent's address space entirely (no copy, no COW)
- Caller provides the new thread's stack

### `thread_create()` — User API

- `thread_create(void *(*start_routine)(void*), void *arg)`
- Wrapper around `clone()` — allocates stack, sets up arguments, calls clone

### Linux Parallel: clone() Unifies Threads and Processes

- In Linux, both threads and processes are **"tasks"** — schedulable entities
- `fork()` → clone with **separate** memory (new process)
- `clone()` with shared memory → new thread
- There is no hard kernel-level distinction; it's a **spectrum of resource sharing**