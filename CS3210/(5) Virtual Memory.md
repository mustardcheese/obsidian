## Why do we want virtual memory?

- Isolation
- Resource Multiplexing
    - Make 1 physical address look like many virtual address spaces
- Masks and overcomes resource limitations
    - Allocate more virtual memory than we have ram
    - Swap out processes
- Protection

---

## Segmentation in xv6

### Big Picture: x86

CPU → Selector Offset → Segment Translation → Page Translation → Physical Address

CPU → Translators → Physical

|Segmentation|Paging|
|---|---|
|Avoid v2p translation overhead|Avoid fragmentation|
||Allows larger virtual address space|
||Better physical memory multiplexing|

Paging: Better Isolation + Better Multiplexing

### GDT/LDT

- The GDT lists memory segments which to all processes
- The LDT lists memory segments private to each process (almost not used)

Segmentation Registers refer to the GDT and LDT as appropriate

- GDT has a base, limit, permissions and privilege level

We set up the segments when we bootstrap the GDT

- ESP uses the SS (Stack Segment register)
- EIP uses the CS (Code Segment register)
- Other operations use DS (Data Segment register)

_tldr, xv6 will use memory segmentation for the GDT, with the cs, ss, ds._

---

## Paging

CR3 contains the address that starts the page directory

The 10 MSB of the linear address are used as an index into page directory

The 20 MSB of one entry of the page directory (PDE) points to a page table

The next 10 of the linear address index into the page table

The 12 LSB of the linear address indicate offset in the physical address

_**insert picture from slides**_

CR3 → PD

PDE[31:22] → PT (Page Table)

PT[21:12] →PTE (Page Table Entry)

The Page Directory can store 1024 entries, each of size 32 bits

- The total size is 4096 bytes, the same size as one page
- The page directory can fit within a single page

Each PDE contains two parts:

- A physical page number (PPN)
- Flags that control permissions

The PTE points to a physical frame of memory

- fill in

2-Level System

CRE is the base of the page table, holding physical address

---
KERNBASE >> PDXSHIFT

- KERNBASE is 1 followed by 31 zeroes
- PDXSHIFT is a bitshift of 22 bits, so we can get the 10MSB

Virtual memory maps two locations into one physical location during bootup

The PDE and PTE each have several flags

- The top 20 MSB hold either the page table physical page number, or the physical page number
    
- The bottom 12 LSB are all flags which allows for much more control
    
    Present
    
    Writable
    
    User
    
    Write-Through
    
    Cache Disabled
    
    Accessed
    
    Dirty
    
    Page Size / Page Table Attribute Index
    
    Global page
    
    [3] Available for system use
    

Multilevel Paging is great because it keeps a small page directory and small pages, bad because it does 2 memory lookup hurting performance

- Single level paging sort of works, we can either have massive pages or massive pde
- Still causes memory wastage in some other way, either with a massive unused page or trying to support massive page directories

Latency vs. Memory Overhead

What about the TLB?

2level: High latency, Low memory

1level: Low latency, High memory

In x86-64 four-level paging is used

- 9 | 9 | 9 | 12 split, for 4kb pages
- Change it to larger pages by merging the 9 bits
- 9 | 9 | 21, 2^21 = 2MB
- 9 | 30, 2^30 = 1GB

Cache: TLB (Translation Lookaside Buffer)

- Cache maps va → pa
- Other types of TLB, instruction TLB (iTLB) and data TLB (dTLB)

Suppose we had a TLB with only one entry

- We’d want to hit into fewer large correct addresses over many small addresses
- The more PTEs we have, the less cache friendly it becomes (higher chance of a miss)

---
try to have the entire lab done completed by end of week 2!

xv6 does not have the ability to have multiple virtual pages map to a single page

We have virtual memory via paging

- Standard isolation
- We can lie and be lazy
- Observe, monitor, change, interpose

Paging provides a level of indirection that allows us to

- Interpose on the control path
- Suspend and modify behavior of underlying mechanisms

## Aspects of Virtual Memory

### Copy-on-write Fork

- We copy the pages needed by child process at the point of write
- Forking is relatively quick, we just create a new pid and assign it

It is way to slow and ineffective to create an entire copy of memory again (reinstantiate) for a new process.

- Instead, we could just point to the original frames after the fork
- **This is what we have to do in lab2, create a way to point to already existing frames of memory**

Since the pages are the same, the page table will also be the same since it points to the same pages. And since the page tables are the same then the page directory is also the same.

- We can treat them as a DAG, if there are more than one path to reach a page (vertex), then it means the resource is shared and should not be modified
- The child process, if they want to edit the values of the original pages, they’d have to create a copy of the page, change the PTE, create a new page table, and create a new page directory
    - We have to create all these new things for the sake of _**isolation**_, if we allowed the child process to edit pages, pte, page tables it breaks isolation which is bad!

Back Propagation of changes required to make few changes

### Demand Paging / Lazy Allocation

- If a process requests additional memory, we can do so lazily (deferred until as late as possible)

### On demand Zero-filled pages

- memset pages set them to zero, but we could instead just create a pointer to a physical frame filled with zeroes

### Virtual Allocation

- Virtually give each process its own memory space, with ‘fake’ values

### Virtual Shared Memory

Memory Mapped files

Paging to disk (swap) Memory over subscription

## Permissions

We can seperate permissions into two types:

- Logical: Is it legal to access this memory
- Physical: It is possible to access this memory

---
Copy-on-write Fork

- We don’t need to copy the entire virtual address, just copy when changes are made

In terms of memory:

- Low frames are code
- Middle frames are typically heap
- High frames are stack

When we copy-on-fork the child process is likely to edit the stack — we can’t allow the write to proceed because the child might overwrite the parent stack!

When the child process starts editing frames, we need to throw a trap

- When do we throw the trap? When a shared page is altered
- How do we know if a page is shared? If there are multiple inputs (processes) using the page
- What does the trap handler do? Need to create a new page. This page has a new address, so you’ll need a new page table. A new page table means the page directory needs to be changed, therefore a new page directory.
- How do we actually make the changes? Flags! Present bit (LSB) and Writable bit (differentiates logical from physical permissions)

**Logical Permission:** Can this actually alter this page

**Physica**l **Permission:** Should this actually be able to alter this page, physically?

If we treat the connections like an adjacency matrix, when we transpose the adjacency matrix, it’s like all the arrows that go from process to page are flipped.

- This is a straightforward way to think about how many processes actually use a page
- tldr need DSA to determine if a page is shared
---
Memory Backing

- Physical memory isn’t limited by RAM
- Virtual mappings aren’t backed by RAM

_Swapping_ — Saving memory to disk when we run out of RAM; “swap” memory to disk

_Memory Mapping_ — Mapping file information into virtual address, writing back into file

## Swapping

### Least Recently Used (LRU)

How do we choose which page to evict to disk?

- **Belady’s min** theoretically chooses the page furthest in the future
- We can’t predict the future so instead we use **LRU**
    - Acts as a heuristic to assume certain programs won’t be used in the future

LRU is expensive to track by time

- Accessing and comparing each timestamp is slow
- Interposing on every memory access is the most expensive of all because you’ll have to take a trap just to capture the timestamp
- **Unnecessary overhead even with infinite memory**
- Worst overhead is taking a trap on every access

**LRU is bad**

### Clock (CAC) Algorithm

- We keep track of a monotonically increasing virtual clock
- Keep a circular buffer with an access flag

![image.png](attachment:7622aec6-ea24-41e7-b3b0-26b412f4bd20:image.png)

If the access bit is 1, we continuously increase the clock counter until we reach one where the accessed bit is 0.

![image.png](attachment:8522a1d7-e595-4e0b-a4d7-392df00124a1:image.png)

![image.png](attachment:10316706-fa26-4521-bec6-d818a20b8a05:image.png)

So when do we need to trap on the page read?

![image.png](attachment:ffa0e22a-5a68-48a2-9362-564ce334a093:image.png)

0 → 1 : There’s nothing in the clock algorithm to change 0 → 1. This is the trap on read.

1 → 0: We passed over this in the clock but didn’t access it — mark for removal

1 → 1: We passed over this in the clock and did access it — keep it

By the time read/write is done, we want access to be 1

### Worst-Case complexity

oops i forgot but O(n)

