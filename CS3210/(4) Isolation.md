*In terms of operating systems, we want to create the illusion that there is only a **sole owner of a shared resource**.*

# Idea behind Isolation
## Types of Isolation

- **Failure Isolation**
    - Failures don’t propagate around
    - If a failure happens in a process, make sure it doesn’t spread into other processes
- **Performance Isolation**
    - The way resource consumption is controlled
    - Prevents contention and starvation between processes
- **Correctness Isolation**
    - Correctness of my program shouldn’t be affected by other programs running in the system

A perfectly isolated process is still useless:
- Processes need to communicate with each other
- We want _some_ isolation sometimes, but it depends

## When do we need isolation?

- We want isolation when we have ***shared resources***
- Processes need isolation (memory is shared)

But what about threads!
- Threading are multiple entities that use shared resources, but they can’t be isolated
- We need isolation when they are non-cooperative

Must require ***shared** **resources*** AND have ***non-cooperative*** entities

**Ex:**
Kernel Space <-> User Space
User processes from each other
Memory
Security Functions <-> Non-security Functions
## Isolation Trade-offs

Isolation is a scale with trade-offs
![[Pasted image 20260309154015.png|400]]
- *Generally*, performance will increase with less isolation
- Things like context switches can be expensive
 ![[Pasted image 20260309154128.png|450]]
# Isolation Mechanisms

## Hardware Isolation

- Hardware “rings”/protection level

![[Pasted image 20260309154453.png|500]]
- For all intents and purposes, only care about level 0 and level 3 (1 and 2 are rarely used)

### Ring 0 protection?
- CPU shared resources
    - Writes to %cr3 register
    - Writes to %CS
    - Every memory read/write is checked for privilege level
    - I/O Port access is privileged
        - Could overwrite inodes, cause corruption, etc.
    - Control register acceses

![image.png](attachment:b76c1e66-cda5-4ce5-bf16-a160c130f40f:image.png)

- The 2nd LSB indicates which table (global/local descriptor table)
- Bottom 2 LSB tell the protection range: 3 = user 0 = kernel (ring numbers)

## Address Spaces (Segmentation, Virtual Memory, Paging)

- Isolate the memory

Interrupt handling is dealt with the interrupt descriptor table (IDT) containing the CS + eip to handler

- CS descriptor is the 2 LSB of the segment descriptor of the segment table
- Interrupt handler checks CPL in current %cs register

Unit of isolation are the processes

- Prevent process X from wrecking or spying on process Y
- Prevent the process from wrecking the OS itself
- Isolated w/ bugs or malicious intent

Virtual Memory Isolation

- Give every process a virtual space
- Segmentation: Course grain, Paging: Fine grain

## Time Slicing (CPU Isolation)

- CPU quantum to isolate access to CPU for processes

Idea: Abstract the CPU so each process percieves it’s own CPU

Scheduler: provides access to resource X to consumer P at time T (give who, what, when)

- Cooperative vs Preemptive (policy/how), yield vs. clock

**We suspend and unsuspend reality for those things simultaneously, like they don’t know**

## System call interface (user vs kernel)

- Safe transfer of control from user to kernel

We switch between rings by with a protected protocol transfer

- set cpl to zero
- reset cpl to 3 before going back to user space

Trap handler to safely handover

## Permission / Privilege (between users)