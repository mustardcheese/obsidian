
## Why do we want virtual memory?

- Isolation
    - Each process gets to have it's own independent address space
    - Processes cannot read/write/access another process
- Resource Multiplexing
    - Make 1 physical address look like many virtual address spaces
- Masks and overcomes resource limitations
    - Allocate more virtual memory than we have ram
    - We can perform swaps when we do actually run out
- Protection
    - Lots of flags and permission bits (read,write,kernel) to enforce memory accesses

---

## Segmentation

### Big Picture: x86

![[Pasted image 20260310145055.png]] CPU → Selector Offset → Segment Translation → Page Translation → Physical Address

CPU → Translators → Physical

- The **Logical Address** is the Selector:Offset pair that the CPU produces
- The **Linear Address** (aka Virtual Address) is the output of segment translation and the input to page translation
- In modern OSes (including xv6), segmentation is configured as identity mapping (base=0, limit=max), so logical = linear = virtual in practice

### Segmentation vs. Paging

|Segmentation|Paging|
|---|---|
|Avoid v2p translation overhead|Avoid fragmentation|
||Allows larger virtual address space|
||Better physical memory multiplexing|

Paging: Better Isolation + Better Protection

### GDT/LDT

![[Pasted image 20260310145150.png|400]]

- The GDT lists memory segments which apply to all processes
- The LDT lists memory segments private to each process (almost not used in modern OS)

Segmentation Registers refer to the GDT and LDT as appropriate

- GDT entries are segment descriptors containing: a **base** (physical address where segment starts), a **limit** (where segment ends), **permissions**, and **DPL** (Default Privilege Level)

We set up the segments when we bootstrap the GDT

- ESP uses the SS (Stack Segment register)
- EIP uses the CS (Code Segment register)
    - EIP/CS is typically set via `jmp` instructions or based on definitions in the IDT when interrupts occur
- Other operations use DS (Data Segment register)

---

## Paging

### Two-Level paging (x86-32)

- CR3 is the register that contains the address that points to the page directory
- **CR3 holds a PHYSICAL address** (not virtual — it must be physical because CR3 is the root of translation; you can't translate without it)
- The 10 MSB of the linear are used to index into pd (2^10 = 1024, 1024 entries in pd)
- The next 10 of the linear are used to index into pt (2^10 = 1024, 1024 entries in pt)
- The offset of linear is the same as the offset used in PA for page accessing

![[Pasted image 20260310145308.png|600]]

### Virtual Address Translation — Step by Step

1. Load Page Directory physical address into **CR3**
2. Use 10 MSB of Linear Address ("Dir") to **index** into PD → get a PDE
3. Use PDE's PPN to **locate the Page Table** in physical memory
4. Use next 10 bits of Linear Address ("Table") to **index** into PT → get a PTE
5. Use PTE's PPN + last 12 bits of Linear Address ("Offset") → **Physical Address**

**A 2-level page walk requires exactly 2 memory accesses** (one to read the PDE, one to read the PTE). CR3 is a register read (not a memory access), and the offset is arithmetic.

### Page Directory

The Page Directory can store 1024 entries, each of size 32 bits

- The total size is 4096 bytes, **the same size as one page**
- The page directory can fit within a single page

Each PDE contains two parts:

- A physical page number (PPN) in the 20 MSB
- PPN points to a page table (i.e., each PDE is essentially a pointer into physical memory where the next-level page table lives)
- Flags that control permissions in the lower 12 bits

### Page Table

The Page Table can store 1024 entries, each of size 32 bits

- Total size is 4096 bytes, **the same size as one page**
- The page table can also fit within a single page
- Each virtual address space has its own set of Page Tables

Each PTE contains two parts:

- A physical page number (PPN) in the 20 MSB
- PPN points to an actual physical frame of memory
- Flags that control permissions in the lower 12 bits

Together, the Page Directory (level 1) and Page Tables (level 2) form a **Two-Level Hierarchy**.

### PTE / PDE Flags

![[Pasted image 20260310150808.png]]

```
Bit 0:  P   — Present (1 = page in physical memory; if 0, hardware faults)
Bit 1:  W   — Writable (1 = read/write, 0 = read-only)
Bit 2:  U   — User (1 = user-mode accessible, 0 = kernel-only)
Bit 3:  WT  — Write-Through (1 = write-through, 0 = write-back caching)
Bit 4:  CD  — Cache Disabled
Bit 5:  A   — Accessed (set by hardware on read/write)
Bit 6:  D   — Dirty (set by hardware on write)
Bit 7:  PS  — Page Size (PDE only: 0 = 4KB pages, 1 = 4MB superpage)
Bit 8:  G   — Global page
Bits 9-11: AVL — Available for OS use
```

- If **P=0**, hardware raises a **page fault** — the OS can store anything it wants in the remaining bits (e.g., swap location)
- **A** and **D** are set automatically by hardware; the OS clears them and uses them for page replacement decisions
- **PS=1** in a PDE means skip the second level — the PDE points directly to a 4MB frame

---

### Large / Super Pages (Single-Level)

For 32-bit with PS=1, translation uses only one level:

```
| Directory (10 bits) | Offset (22 bits) |
```

- Page size = 2^22 = **4MB**
- Only the Page Directory is used; no Page Table needed

Page sizes available:

- **32-bit**: 4KB, 4MB
- **64-bit**: 4KB, 2MB, 1GB

**Tradeoffs of larger pages**: better TLB coverage and fewer page table entries, but more internal fragmentation (wasted space if the page isn't fully used)

---

### Single Level vs. Multi Level

|                     | Single Level [20 \| 12]                                              | Multi Level [10 \| 10 \| 12]                                                       |
| ------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Latency**         | 1 memory access per walk (faster)                                    | 2 memory accesses per walk (slower)                                                |
| **Memory Overhead** | Full table always allocated: 2^20 × 2^2 = 2^22 = **4MB per process** | Sparse — only allocate page tables for regions in use; minimum = 4KB (just the PD) |
| **Fragmentation**   | Needs contiguous 4MB for the table                                   | Each table is exactly 1 page (4KB), easy to allocate                               |
| **Best Use:**       | Processes using most of address space                                | Most real workloads                                                                |


**tldr**: dependent on design choices. Multi-level trades latency for memory savings. The TLB makes this trade off acceptable -> we use multilevel for lots of things.

![[Pasted image 20260310151348.png]]

---

### Four-Level Paging (x86-64)

```
| PML4 (9) | Dir Ptr (9) | Directory (9) | Table (9) | Offset (12) |
  bits 47-39   bits 38-30    bits 29-21      bits 20-12   bits 11-0
```

- Same idea as 2-level, just more levels of indirection
- Each level has 512 entries (2^9) × 8 bytes = 4KB per table (still fits in one frame)
- A full page walk requires **4 memory accesses**
- Supports page sizes: 4KB, 2MB (skip last level), 1GB (skip last two levels)

![[Pasted image 20260310151950.png]]

---

## TLB (Translation Lookaside Buffer)

The **MMU (Memory Management Unit)** handles VA → PA translation in hardware, and the **TLB** is a special hardware cache that stores recent translations.
![[Pasted image 20260310152101.png|500]]

```
Virtual Address → TLB
    ├── TLB HIT  → Physical Address immediately (~1 cycle)
    └── TLB MISS → Full page table walk (2-4 memory accesses)
                    → Result written into TLB
                    └── Page Not Present? → Page Fault → OS handler (may go to disk)
```

- **iTLB** — caches instruction translations only
- **dTLB** — caches data translations only
- **TLB Flush** — changing CR3 (e.g., on context switch) **invalidates the entire TLB**. This is a major reason context switches are expensive — the new process starts with a cold TLB.

The TLB is what makes multi-level paging practical. Without it, every memory access would need 2+ extra accesses just for translation.

---

## ![[powers_of_2.png|650]]