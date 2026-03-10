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
