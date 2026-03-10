_In terms of operating systems, we want to create the illusion that there is only a **sole owner of a shared resource**._

# Idea behind Isolation

## Types of Isolation

- **Failure Isolation** — failures don't propagate between processes; driving motivation for kernel design
- **Performance Isolation** — controls resource consumption; prevents starvation (best effort vs guaranteed)
- **Correctness Isolation** — other programs running in the system shouldn't affect my program's correctness

A perfectly isolated process is useless — can't communicate, can't even produce output. We want _some_ isolation _sometimes_ — changes with workload and time.

## When do we need isolation?

Must have _**shared resources**_ AND _**non-cooperative**_ entities

Think: what are the entities? What is the shared resource?

## Isolation Trade-offs

![[Pasted image 20260309154015.png|400]]

- Stronger isolation → more safety, less usability
- Performance relationship is nuanced (not strictly one direction)
![[Pasted image 20260309154128.png|450]]

# Isolation Mechanisms

## Hardware Isolation

![[Pasted image 20260309154453.png|500]]

- Only ring 0 (kernel) and ring 3 (user) matter in practice

### Ring 0 protects:

- Writes to %cr3 (page table base → address space), %cs (defends CPL), control registers (eflags, %cr4)
- Every memory read/write checked for privilege (S/U bit in PTEs)
- I/O port access (could corrupt inodes, etc.)

## Address Spaces

- Goal is to isolate the memory in different locations

### Segment Selector

![[Pasted image 20260310011936.png|500]]

- 16-bit value: upper 13 bits = index into GDT/LDT, bit 2 = table indicator (0=GDT, 1=LDT), bits 1:0 = RPL

### CPL (Current Privilege Level)

- Lower 2 bits of %cs register. CPL 0 = kernel, CPL 3 = user
- %cs only changed via far jumps, interrupts, `iret` — prevents user self-escalation
- GDT uses flat memory model (base=0, limit=max) — segmentation is a pass-through; **paging does all memory isolation**
- GDT's only real purpose: define DPL so processor can set CPL
- GDT also hosts TSS descriptor — provides kernel stack pointer during privilege transitions

### IDT (Interrupt Descriptor Table)

- Each gate contains: segment selector (→ GDT, sets handler's CPL), offset (handler address), DPL (who can trigger via `int`), type
- **Software interrupts**: processor checks CPL <= DPL of gate → otherwise general protection fault
- **Hardware interrupts bypass DPL check**
- On ring 3→0: processor atomically switches to kernel stack (via TSS), pushes user context (ss/esp/eflags/cs/eip), loads new %cs from gate (CPL→0), jumps to handler

**Key: GDT provides CPL identity → paging checks CPL against U/S bits in PTEs. Layered mechanisms.**

### Unit of Isolation: The Process

- Prevent process X from wrecking/spying on process Y (memory, CPU, FDs, resource exhaustion)
- Prevent processes from wrecking the OS itself
- Must hold against bugs and malice

### Virtual Memory Isolation

- Every process gets identical virtual address space; MMU translates VA → PA
- Privilege enforced at page granularity (finer than segmentation)
- Kernel mapped into upper half of **every** process's address space — protected by U/S bits in PDE/PTE, not separate page tables
- No page table switch on syscall — just CPL change (performance benefit, but what Meltdown exploited)
![[Pasted image 20260310015546.png|400]]

## Time Slicing (CPU Isolation)

CPU quantum to isolate access to CPU for processes

Idea: abstract CPU so each process perceives its own CPU

Scheduler: provides access to resource X to consumer P at time T (who, what, when)

- Cooperative vs Preemptive (policy/how) — yield vs clock driven
- **Cooperative alone is insufficient** — malicious/buggy process can refuse to yield
- Preemptive (timer interrupt) necessary for true CPU isolation
- Perfect isolation with time quanta is hard (side channels: caches, branch predictors)

## System Call Interface (user vs kernel)

Safe, controlled transfer from user to kernel — not arbitrary

- `int` or `sysenter` sets CPL to 0; CPL set back to 3 before return

### Trap handler:

1. Predetermined entry point (user can't jump to arbitrary kernel code)
2. Saves user context, loads kernel context
3. **Sanitizes arguments** — must validate user-supplied pointers are in user-accessible memory (kernel runs at CPL 0 and _can_ write anywhere — it must choose not to)
4. Accepts or denies request

## Permission / Privilege (between users)

- File permissions and user/group model isolate users from each other

## Isolation is NOT Solved

**Meltdown**: speculative execution reads kernel memory before U/S check completes; data leaks via cache side channel. Exploits the fact that kernel is mapped in every process's page table.

**Spectre**: manipulates branch prediction to leak data across process boundaries.

**KPTI fix**: unmaps kernel from user page tables. Requires page table switch + TLB flush on every syscall. Direct safety-vs-performance tradeoff.