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
    - Control register accesses

![[Pasted image 20260310011936.png|500]]

- Bit 2 indicates which table (global/local descriptor table)
- Bit 0,1 tell the protection range: 3 = user 0 = kernel (ring numbers)

## Address Spaces
- Goal is to isolate the memory in different locations

### Segment Selection
- The segment selector is a 16-bit value where the upper 13 bits are an index into a descriptor table (GDT, LDT), bit 2 = table indicator, bit 1:0 = privilege level
- Descriptor tables no longer are used for memory as now paging is more effective
- **Descriptor tables are only now used to determine privilege level based on protection level (ring number)**

Interrupt handling is dealt with the interrupt descriptor table (IDT)
- IDT entries (gate descriptors) contain a segment descriptor (CS) 
- CPL is the 2 LSB of %cs (segment selector)
- **Interrupt handler checks CPL in current %cs register**

We *need* to sanitize instructions because of the way memory and kernel access is set up.

***For the purpose of isolation the CPL are still used to check the privilege level.***

### Granularity
Splitting 'things' into processes
- Prevent process X from wrecking or spying on process Y
- Prevent the process from wrecking the OS itself
- Isolated w/ bugs or malicious intent

tldr; different processes are seperate from eachother

### Virtual Memory (VMM)
- Give every process it's virtual space
- Handle conflicts using a paging unit
- MMU turns VA -> PA
- **Enforces privilege level at page granularity, finer than segmentation**
![[Pasted image 20260310015546.png|400]]
## Time Slicing (CPU Isolation)
CPU quantum to isolate access to CPU for processes

Idea: Abstract the CPU so each process perceives it’s own CPU
Schedulers
- Provides access to resource X to consumer P at time T (give who, what, when)
- Cooperative vs Preemptive (how)
	- yield vs. clock

**We suspend and unsuspend reality for those things simultaneously, like they don’t know**

## System call interface (user vs kernel)
Safe transfer of control from user to kernel

We switch between rings by with a protected protocol transfer
- set cpl to zero
- reset cpl to 3 before going back to user space

Trap handler to safely handover

## Permission / Privilege (between users)