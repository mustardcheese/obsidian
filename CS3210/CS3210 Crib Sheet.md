## Table of Contents

### Part 1 — Conceptual
- [L03 — x86 Architecture](<#L03 — x86 Architecture>)  *(→ [xv6](<#L03 — x86 Architecture — xv6>))*
- [L04 — Isolation](<#L04 — Isolation>)  *(→ [xv6](<#L04 — Isolation — xv6>))*
- [L05 — Kernel Organization & APIs](<#L05 — Kernel Organization & APIs>)  *(→ [xv6](<#L05 — Kernel Organization & APIs — xv6>))*
- [L06 — Virtual Memory I (Basics)](<#L06 — Virtual Memory I (Basics)>)  *(→ [xv6](<#L06 — Virtual Memory I (Basics) — xv6>))*
- [L07 — Virtual Memory II (Lazy / CoW)](<#L07 — Virtual Memory II (Lazy / CoW)>)  *(→ [xv6](<#L07 — Virtual Memory II (Lazy / CoW) — xv6>))*
- [L08 — Virtual Memory III (CoW & Tricks)](<#L08 — Virtual Memory III (CoW & Tricks)>)  *(→ [xv6](<#L08 — Virtual Memory III (CoW & Tricks) — xv6>))*
- [L09 — Concurrency I (Interrupts & Traps)](<#L09 — Concurrency I (Interrupts & Traps)>)  *(→ [xv6](<#L09 — Concurrency I (Interrupts & Traps) — xv6>))*
- [L10 — Concurrency II (Locks & Memory Models)](<#L10 — Concurrency II (Locks & Memory Models)>)  *(→ [xv6](<#L10 — Concurrency II (Locks & Memory Models) — xv6>))*
- [L11 — Schedulers](<#L11 — Schedulers>)  *(→ [xv6](<#L11 — Schedulers — xv6>))*
- [L12 — Ordering, Waiting & Context Switch](<#L12 — Ordering, Waiting & Context Switch>)  *(→ [xv6](<#L12 — Ordering, Waiting & Context Switch — xv6>))*
- [L13 — User & Kernel Threads](<#L13 — User & Kernel Threads>)  *(→ [xv6](<#L13 — User & Kernel Threads — xv6>))*
- [L14 — Security I (Goals, Threats, Memory Safety)](<#L14 — Security I (Goals, Threats, Memory Safety)>)  *(→ [xv6](<#L14 — Security I (Goals, Threats, Memory Safety) — xv6>))*
- [L15 — Security II (Access Control, Sandboxing)](<#L15 — Security II (Access Control, Sandboxing)>)  *(→ [xv6](<#L15 — Security II (Access Control, Sandboxing) — xv6>))*
- [L16 — Networking](<#L16 — Networking>)  *(→ [xv6](<#L16 — Networking — xv6>))*
- [L17 — File Systems I](<#L17 — File Systems I>)  *(→ [xv6](<#L17 — File Systems I — xv6>))*
- [L18 — File Systems II](<#L18 — File Systems II>)  *(→ [xv6](<#L18 — File Systems II — xv6>))*
- [L19 — FS Atomicity I](<#L19 — FS Atomicity I>)  *(→ [xv6](<#L19 — FS Atomicity I — xv6>))*
- [L20 — FS Atomicity II](<#L20 — FS Atomicity II>)  *(→ [xv6](<#L20 — FS Atomicity II — xv6>))*
- [L21 — Distributed Systems](<#L21 — Distributed Systems>)  *(→ [xv6](<#L21 — Distributed Systems — xv6>))*
- [L22 — Efficient AI Stack](<#L22 — Efficient AI Stack>)  *(→ [xv6](<#L22 — Efficient AI Stack — xv6>))*

### Part 2 — xv6 Implementation
- [L03 — x86 Architecture — xv6](<#L03 — x86 Architecture — xv6>)  *(→ [concept](<#L03 — x86 Architecture>))*
- [L04 — Isolation — xv6](<#L04 — Isolation — xv6>)  *(→ [concept](<#L04 — Isolation>))*
- [L05 — Kernel Organization & APIs — xv6](<#L05 — Kernel Organization & APIs — xv6>)  *(→ [concept](<#L05 — Kernel Organization & APIs>))*
- [L06 — Virtual Memory I (Basics) — xv6](<#L06 — Virtual Memory I (Basics) — xv6>)  *(→ [concept](<#L06 — Virtual Memory I (Basics)>))*
- [L07 — Virtual Memory II (Lazy / CoW) — xv6](<#L07 — Virtual Memory II (Lazy / CoW) — xv6>)  *(→ [concept](<#L07 — Virtual Memory II (Lazy / CoW)>))*
- [L08 — Virtual Memory III (CoW & Tricks) — xv6](<#L08 — Virtual Memory III (CoW & Tricks) — xv6>)  *(→ [concept](<#L08 — Virtual Memory III (CoW & Tricks)>))*
- [L09 — Concurrency I (Interrupts & Traps) — xv6](<#L09 — Concurrency I (Interrupts & Traps) — xv6>)  *(→ [concept](<#L09 — Concurrency I (Interrupts & Traps)>))*
- [L10 — Concurrency II (Locks & Memory Models) — xv6](<#L10 — Concurrency II (Locks & Memory Models) — xv6>)  *(→ [concept](<#L10 — Concurrency II (Locks & Memory Models)>))*
- [L11 — Schedulers — xv6](<#L11 — Schedulers — xv6>)  *(→ [concept](<#L11 — Schedulers>))*
- [L12 — Ordering, Waiting & Context Switch — xv6](<#L12 — Ordering, Waiting & Context Switch — xv6>)  *(→ [concept](<#L12 — Ordering, Waiting & Context Switch>))*
- [L13 — User & Kernel Threads — xv6](<#L13 — User & Kernel Threads — xv6>)  *(→ [concept](<#L13 — User & Kernel Threads>))*
- [L14 — Security I (Goals, Threats, Memory Safety) — xv6](<#L14 — Security I (Goals, Threats, Memory Safety) — xv6>)  *(→ [concept](<#L14 — Security I (Goals, Threats, Memory Safety)>))*
- [L15 — Security II (Access Control, Sandboxing) — xv6](<#L15 — Security II (Access Control, Sandboxing) — xv6>)  *(→ [concept](<#L15 — Security II (Access Control, Sandboxing)>))*
- [L16 — Networking — xv6](<#L16 — Networking — xv6>)  *(→ [concept](<#L16 — Networking>))*
- [L17 — File Systems I — xv6](<#L17 — File Systems I — xv6>)  *(→ [concept](<#L17 — File Systems I>))*
- [L18 — File Systems II — xv6](<#L18 — File Systems II — xv6>)  *(→ [concept](<#L18 — File Systems II>))*
- [L19 — FS Atomicity I — xv6](<#L19 — FS Atomicity I — xv6>)  *(→ [concept](<#L19 — FS Atomicity I>))*
- [L20 — FS Atomicity II — xv6](<#L20 — FS Atomicity II — xv6>)  *(→ [concept](<#L20 — FS Atomicity II>))*
- [L21 — Distributed Systems — xv6](<#L21 — Distributed Systems — xv6>)  *(→ [concept](<#L21 — Distributed Systems>))*
- [L22 — Efficient AI Stack — xv6](<#L22 — Efficient AI Stack — xv6>)  *(→ [concept](<#L22 — Efficient AI Stack>))*

---

# Part 1 — Conceptual

## L03 — x86 Architecture

*([→ xv6 implementation for this lecture](<#L03 — x86 Architecture — xv6>))*

> **Tags:** `x86` `lec3` `L03` `architecture` `von neumann` `CPU` `boot` `BIOS` `UEFI` `registers` `memory modes` `IO` `instruction set` `ISA`

---

## Table of Contents
1. [Von Neumann Model](#1-von-neumann-model)
2. [x86 Registers](#2-x86-registers)
3. [x86 Instruction Classes](#3-x86-instruction-classes)
4. [CPU Modes: Real Mode vs Protected Mode](#4-cpu-modes-real-mode-vs-protected-mode)
5. [Boot Process](#5-boot-process)
6. [Memory Layout](#6-memory-layout)
7. [Segmentation](#7-segmentation)
8. [Paging & Virtual Memory](#8-paging--virtual-memory)
9. [I/O Mechanisms: PMIO vs MMIO](#9-io-mechanisms-pmio-vs-mmio)
10. [Interrupts, Traps & System Calls](#10-interrupts-traps--system-calls)
11. [Protection Rings & Privilege Levels](#11-protection-rings--privilege-levels)
12. [xv6 Implementation](#12-xv6-implementation)

---

## 1. Von Neumann Model
> **Tags:** `von neumann` `CPU model` `instruction pointer` `IP` `fetch-decode-execute` `abstract CPU`

- CPU fetches instruction at address pointed to by **IP (Instruction Pointer)**
- After execution, IP advances to next instruction (unless control flow instruction)
- All modern x86 systems are von Neumann machines
- Components: CPU ↔ Main Memory (shared instruction + data bus)

```
[CPU] <--fetch instructions--> [Main Memory]
        <--read/write data-->
```

**Key Idea:** Performance — the fetch-execute cycle speed is the fundamental bottleneck; every architectural feature (caches, TLBs, multi-level paging) exists to keep this cycle fast.

---

## 2. x86 Registers
> **Tags:** `registers` `EAX` `EBX` `ECX` `EDX` `ESI` `EDI` `EBP` `ESP` `EIP` `EFLAGS` `CS` `DS` `SS` `ES` `FS` `GS` `CR0` `CR3` `segment registers` `general purpose registers` `control registers`

### General Purpose (32-bit with E prefix; 64-bit with R prefix)
| Register | Full Name | Common Use |
|---|---|---|
| `EAX` | Accumulator | Return values, arithmetic |
| `EBX` | Base | Base address calculations |
| `ECX` | Counter | Loop counters, `rep` prefix |
| `EDX` | Data | I/O port numbers, multiply overflow |
| `ESI` | Source Index | String source, memory source |
| `EDI` | Destination Index | String dest, memory dest |
| `EBP` | Base Pointer | Stack frame base |
| `ESP` | Stack Pointer | Top of stack |

- **`EIP`** — Instruction Pointer; points to next instruction to execute
- **`EFLAGS`** — Status flags (ZF=zero, CF=carry, SF=sign, IF=interrupt enable, etc.)

### Segment Registers
| Register | Used With | Meaning |
|---|---|---|
| `CS` | `EIP` | Code Segment; **lower 2 bits = CPL** |
| `DS` | general data | Data Segment |
| `SS` | `ESP` | Stack Segment |
| `ES`, `FS`, `GS` | extra data | Extra segments |

### Control Registers (privileged)
| Register | Meaning |
|---|---|
| `CR0` | PE bit (bit 0): enables protected mode; PG bit (bit 31): enables paging |
| `CR3` | **Physical** address of Page Directory base (root of page table) |
| `CR4` | Extended features (PAE, PSE, etc.) |

> **Key:** `CR3` must hold a **physical** address — if it were virtual, you'd need page tables to translate it, creating a bootstrap paradox.

---

## 3. x86 Instruction Classes
> **Tags:** `MOV` `PUSH` `POP` `ADD` `SUB` `JMP` `JZ` `JNZ` `CALL` `RET` `INT` `IRET` `IN` `OUT` `HLT` `CLI` `STI` `LIDT` `LGDT` `REP MOVSB` `instruction set` `ISA`

| Class | Examples | Notes |
|---|---|---|
| Data Movement | `MOV`, `PUSH`, `POP`, `XCHG` | Core of any computation |
| Arithmetic/Logic | `ADD`, `SUB`, `AND`, `OR`, `XOR`, `TEST`, `SHL`, `SHR` | Sets EFLAGS |
| Control Flow | `JMP`, `JZ`, `JNZ`, `JE`, `JNE`, `CALL`, `RET` | CALL pushes EIP, RET pops |
| I/O | `IN`, `OUT` | Port-mapped I/O; requires CPL=0 |
| String | `REP MOVSB`, `REP STOSD` | Bulk memory operations |
| System | `INT N`, `IRET`, `LIDT`, `LGDT`, `HLT`, `CLI`, `STI`, `IRET` | Privileged/trap instructions |

- `CLI` — **clear** interrupt flag (disable maskable interrupts); `STI` — **set** interrupt flag
- `LGDT` / `LIDT` — load GDT/IDT register; `LLDT` — load LDT
- `IRET` — returns from interrupt; pops EIP, CS, EFLAGS (and ESP, SS if ring crossing)

---

## 4. CPU Modes: Real Mode vs Protected Mode
> **Tags:** `real mode` `protected mode` `16-bit` `32-bit` `mode switch` `PE bit` `CR0` `flat memory` `segmented memory` `compatibility` `8086` `80386` `mode transition`

### Comparison Table

| Attribute | Real Mode | Protected Mode |
|---|---|---|
| **Bit Width** | 16-bit registers | 32-bit registers |
| **Address Space** | 20-bit → 1 MB max | 32-bit → 4 GB max |
| **Address Calc** | `PA = CS<<4 + IP` | Segment descriptor + paging |
| **Memory Protection** | None — any code can access any address | Hardware-enforced via GDT/paging |
| **Privilege Levels** | None — all code equally privileged | 4 rings (0–3); only 0 and 3 used in practice |
| **Interrupt Handling** | IVT (Interrupt Vector Table) — simple 4-byte pointers | IDT (Interrupt Descriptor Table) — 8-byte descriptors with privilege checks |
| **Virtual Memory** | No — only physical addresses | Yes — paging enabled via CR0.PG |
| **Why it exists** | Backward compatibility with 8086 | Full OS capabilities |
| **Pareto Position** | Dominated — strictly worse except for compatibility | Pareto optimal for OS use |

**Pros of Real Mode:**
- Simple address calculation
- Backward compatible with legacy code

**Cons of Real Mode:**
- No protection — bugs/malware can corrupt anything
- Only 1 MB addressable
- No multitasking/isolation

**Pros of Protected Mode:**
- Full 4 GB address space
- Hardware memory protection and privilege separation
- Foundation for virtual memory

**Design Alignment:** Real mode → *none (legacy only)*. Protected mode → **Isolation + Protection + Multiplexing**

### Mode Transition (Real → Protected)
1. Disable interrupts: `CLI`
2. Load GDT: `LGDT [gdtdesc]`
3. Set PE bit in CR0: `OR CR0, 1`
4. Far jump to flush pipeline and set CS: `ljmp $SEG_KCODE, $start32`
5. Now in 32-bit protected mode — reload all segment registers
6. Set up stack (`ESP`), then call `bootmain`

---

## 5. Boot Process
> **Tags:** `boot` `BIOS` `UEFI` `bootloader` `bootblock` `reset vector` `0xfffffff0` `0x7c00` `boot signature` `0x55AA` `real mode` `protected mode` `three stage` `handover protocol` `entry.S` `bootasm.S` `bootmain`

### Three-Stage Boot: BIOS/UEFI → Bootloader → Kernel

```
Power ON
  └─ Reset Vector (0xFFFFFFF0, hardwired in silicon)
       └─ BIOS ROM (128KB mapped at 0xFFFE0000–0xFFFFFFFF high, mirror at 0xF0000–0xFFFFF low)
            └─ BIOS initializes hardware
                 └─ Reads 512 bytes from disk sector 0
                      └─ Verifies 0x55AA boot signature
                           └─ Copies to 0x7C00 → jmp 0x7C00 (Bootloader)
                                └─ Bootloader: real→protected, loads kernel ELF
                                     └─ Kernel entry point → main()
```

**Why three stages?** Each stage handles a different level of hardware abstraction — without bootloader, every kernel would need to know how to boot on every hardware variant.

### Stage 1: Reset Vector
- CPU hardwired to fetch from `0xFFFFFFF0` on power-on
- Hardware forces top 12 address bus lines high — then releases after first `ljmp`
- ROM mapped **twice**: high (0xFFFE0000–0xFFFFFFFF) for reset vector; low mirror (0xF0000–0xFFFFF) for continued real-mode BIOS execution
- First instruction: `ljmp $0xf000, $0xe05b` — jumps into BIOS code in low ROM

### Stage 2: Bootloader (512 bytes, lives at 0x7C00)
- CPU is still in 16-bit real mode at this point
- Address bus: `PA = CS<<4 + IP`
- **Tasks:**
  - Disable interrupts (`CLI`) — prevent BIOS interrupts from interfering
  - Set up bootstrap GDT (null + code + data, flat 4 GB)
  - Enable CR0.PE → switch to protected mode
  - Far jump to flush pipeline
  - Load kernel ELF from disk into physical memory at `0x00100000` (1 MB)
  - Jump to kernel entry point

### Stage 3: Kernel Entry
- `entry.S` sets up bootstrap page directory (2 entries):
  - PDE[0]: Identity map (VA=PA, needed so instructions keep executing after CR0.PG set)
  - PDE[512]: KERNBASE (0x80000000) → 0x00000000 (maps kernel high VAs to physical 0)
- Sets CR3 to bootstrap page directory
- Sets CR0.PG → paging enabled
- Jumps to `main()` in high virtual address space

**Performance Note (CDF):** Boot latency is dominated by disk reads (ms range), not CPU transitions (µs or less). CDF of boot time is bimodal: fast (SSD, ~1s) vs slow (HDD, ~10s+). The mode transition itself is negligible in comparison.

---

## 6. Memory Layout
> **Tags:** `memory map` `address space` `physical memory` `low memory` `extended memory` `KERNBASE` `0x80000000` `0x100000` `IVT` `BIOS data area` `VGA` `device memory` `hole` `memory layout`

### Real Mode Memory Map (First 1 MB, 20-bit space)
| Address Range | Size | Contents |
|---|---|---|
| `0x00000000–0x000003FF` | 1 KB | **IVT** (Interrupt Vector Table) |
| `0x00000400–0x000004FF` | 256 B | BIOS Data Area |
| `0x00000500–0x00007BFF` | ~29 KB | Conventional memory (free) |
| **`0x00007C00–0x00007DFF`** | **512 B** | **Bootloader loaded here** |
| `0x00007E00–0x0009FFFF` | ~480 KB | Conventional memory (free) |
| `0x000A0000–0x000BFFFF` | 128 KB | VGA / Video display memory |
| `0x000C0000–0x000EFFFF` | ~192 KB | ROM expansion / BIOS shadow |
| `0x000F0000–0x000FFFFF` | 64 KB | **System BIOS** (low ROM mirror) |

### Protected Mode Physical Memory (32-bit)
| Address | Contents |
|---|---|
| `0x00000000` | Low RAM (base memory) |
| `0x00007C00` | Boot sector |
| `0x000A0000` | Device memory (reserved hole) |
| `0x000F0000` | BIOS ROM mirror |
| **`0x00100000`** | **Kernel loaded here** (~1 MB mark, avoids the hole) |
| `0xFE000000–0xFFFFFFFF` | 32-bit memory-mapped I/O devices |

---

## 7. Segmentation
> **Tags:** `segmentation` `GDT` `LDT` `TSS` `segment descriptor` `segment selector` `CPL` `DPL` `RPL` `base` `limit` `flat memory` `logical address` `linear address` `code segment` `data segment` `stack segment` `seginit` `lgdt` `CS` `flat segmentation`

### Big Picture: Address Translation
```
CPU → [Selector:Offset] → Segment Translation → [Linear Addr] → Page Translation → [Physical Addr]
      (Logical Address)                          (= Virtual Addr in flat model)
```

### GDT (Global Descriptor Table)
- Array of 8-byte **segment descriptors**, one per segment
- Pointed to by **GDTR register** (loaded via `lgdt`)
- Each descriptor contains:
  - **Base**: 32-bit physical start address of segment
  - **Limit**: size of segment (in bytes or 4KB pages)
  - **Permissions**: read, write, execute bits
  - **DPL**: Default Privilege Level (0=kernel, 3=user)
  - **Type**: code, data, system

### Segment Selector (16-bit value in CS, DS, SS…)
```
[Bits 15:3 = Index into GDT/LDT] [Bit 2 = TI: 0=GDT, 1=LDT] [Bits 1:0 = RPL]
```
- **RPL** = Requested Privilege Level (what the caller is asking for)
- **CPL** = Current Privilege Level = **lower 2 bits of CS**; 0=kernel, 3=user

### Key Tables
| Table | Scope | Usage |
|---|---|---|
| **GDT** | Global (all processes) | Defines all segments; OS-managed |
| **LDT** | Per-process | Rarely used in modern OSes |
| **TSS** (Task State Segment) | Per-CPU | Stores kernel ESP/SS for ring 3→0 transitions on interrupt |

### Segmentation vs. Flat Model Comparison

| | Full Segmentation | Flat Segmentation (modern xv6) |
|---|---|---|
| **How it works** | Each segment has distinct base+limit | All segments: base=0, limit=0xFFFFFFFF |
| **Logical vs Linear** | Logical ≠ Linear | Logical = Linear (identity) |
| **Protection** | Segment-level bounds checking | Paging does all protection |
| **Fragmentation** | External fragmentation | None (paging handles it) |
| **Complexity** | High (managing segment registers) | Low (set-and-forget) |
| **Pareto Position** | Dominated by flat+paging in modern OS | Pareto optimal (simpler + more powerful) |

**Design Alignment:** Segmentation → **Protection** (via DPL/CPL checks) + **Isolation** (segment bounds). Flat segmentation → defers protection entirely to **Paging**.

**Granularity:** Segment-based protection is coarse (per-segment) vs page-based (per-4KB page). Finer granularity = more flexible isolation but more metadata overhead.

---

## 8. Paging & Virtual Memory
> **Tags:** `paging` `page table` `PTE` `PDE` `page directory` `CR3` `TLB` `MMU` `virtual address` `physical address` `linear address` `page fault` `two-level` `four-level` `multilevel` `invlpg` `U/S bit` `R/W bit` `present bit` `KERNBASE` `address space` `isolation` `v2p` `p2v` `page walk`

### Why Virtual Memory?
- **Isolation**: Each process has its own independent address space
- **Multiplexing**: One physical memory → many virtual spaces
- **Protection**: Per-page permission bits (read, write, execute, user/kernel)
- **Overcommit**: Allocate more virtual memory than physical RAM (swap to disk)

### x86-32 Two-Level Page Table

```
Linear Address (32 bits):
[ Dir (10) | Table (10) | Offset (12) ]
    ↓            ↓            ↓
  CR3         PDE          PPN
  (PD base)   (PT base)    + Offset = Physical Address
```

**Walk steps:**
1. Load PD physical address from **CR3**
2. Use bits [31:22] (Dir) to index into PD → get **PDE**
3. PDE gives physical address of PT
4. Use bits [21:12] (Table) to index into PT → get **PTE**
5. PTE gives **PPN** (Physical Page Number)
6. Append bits [11:0] (Offset) → Physical Address

- PD: 1024 entries × 4 bytes = 4 KB (fits in one page)
- Each PT: 1024 entries × 4 bytes = 4 KB

### PTE Flags
| Bit | Name | Meaning |
|---|---|---|
| 0 | Present (P) | Page is in physical memory |
| 1 | R/W | 0=read-only, 1=read-write |
| 2 | U/S | 0=supervisor only, 1=user accessible |
| 3 | PWT | Write-through caching |
| 4 | PCD | Cache disable |
| 5 | Accessed | Set by MMU on access |
| 6 | Dirty | Set by MMU on write |
| 7 | PS (in PDE) | 1=4MB superpage, 0=4KB page |

### x86-64 Four-Level Paging
```
[ PML4 (9) | Dir Ptr (9) | Directory (9) | Table (9) | Offset (12) ]
```
- 4 memory accesses per page walk (without TLB)
- Supports 4KB, 2MB, 1GB page sizes

### Multi-Level Paging: Design Choice Analysis

| Approach | Memory for Table | Walk Latency | Best For |
|---|---|---|---|
| Single-level (1024×1024 flat) | 4MB **always allocated** per process | 1 access | Tiny address spaces |
| 2-level | Only allocate PTs for used regions | 2 accesses | 32-bit, sparse spaces |
| 4-level | Very sparse allocation | 4 accesses | 64-bit, huge spaces |

**Pareto Frontier:** Single-level is dominated (wasteful memory, no benefit). 2-level vs 4-level lie on the Pareto frontier: 2-level wins on latency for small spaces, 4-level wins on memory efficiency for large/sparse spaces.

**Granularity Analysis (page size):**
| Page Size | Fragmentation | TLB Coverage | Table Size | Best For |
|---|---|---|---|---|
| 4 KB (fine) | Low (less waste per page) | Low (fewer mappings cached) | More PTEs | General purpose |
| 2 MB (huge page) | Higher (more internal waste) | High (covers 512× more per TLB entry) | Fewer PDEs | Databases, large buffers |
| 1 GB (gigantic) | Very high | Highest | Minimal | NUMA/hypervisors |

**Design Alignment:** Paging → **Isolation** (per-process address spaces) + **Protection** (U/S bits enforce ring separation) + **Multiplexing** (physical memory shared across processes)

### TLB (Translation Lookaside Buffer)
> **Tags:** `TLB` `TLB flush` `invlpg` `iTLB` `dTLB` `context switch cost` `MMU` `page walk` `cache`

- Hardware cache of recent VA→PA translations (~1 cycle hit vs 2–4 memory accesses on miss)
- **iTLB**: caches instruction translations; **dTLB**: caches data translations
- **TLB miss** → full page walk → result written into TLB
- **TLB flush** triggered by writing `CR3` (e.g., context switch) → **entire TLB invalidated**
- `invlpg <vaddr>` — selectively invalidate one TLB entry (cheaper than full flush)

**When to flush vs invlpg:**
- Full flush: on process context switch (CR3 write) — necessary for isolation
- `invlpg`: when modifying a single PTE in a still-running process (e.g., remapping one page)

**Performance CDF:** TLB hit rate is typically very high (>99% for locality-friendly workloads). CDF of translation latency is thus bimodal: ~1 cycle (hit) vs ~100+ cycles (miss + page walk + possible page fault → disk → milliseconds). Most processes sit near the fast end; pathological access patterns (random large arrays) shift toward the slow tail.

---

## 9. I/O Mechanisms: PMIO vs MMIO
> **Tags:** `IO` `PMIO` `port-mapped IO` `MMIO` `memory-mapped IO` `IN` `OUT` `device registers` `PCI` `DMA` `1024 ports` `side effects` `device discovery`

### Comparison Table

| | Port-Mapped I/O (PMIO) | Memory-Mapped I/O (MMIO) |
|---|---|---|
| **Address Space** | Separate 16-bit I/O space (max 65,536 ports) | Shared physical address space |
| **Instructions** | `IN`/`OUT` (x86 specific) | Normal `MOV` / load-store |
| **Privilege** | Requires CPL=0 (or IOPL) | Enforced by page table permissions |
| **Size Limit** | Only 65,536 port addresses | Limited only by physical address space |
| **Cache Behavior** | Non-cacheable by design | Must mark pages as non-cacheable (PCD bit) |
| **Side Effects** | Explicit (separate instructions) | Implicit (reads/writes may trigger device actions) |
| **Discovery** | PCI: port 0xCF8 (CONFIG_ADDRESS), 0xCFC (CONFIG_DATA) | Bus scanning / ACPI tables |
| **Portability** | x86-specific only | Architecture-agnostic |
| **Use Cases** | Legacy devices, PCI config space discovery | Modern NICs, GPUs, framebuffers |

**Pareto Frontier:** PMIO is partially dominated — MMIO is more general, but PMIO still wins for PCI device *discovery* (you need PMIO ports 0xCF8/0xCFC before you know where the device's MMIO regions are). Neither is purely dominated in practice.

**Design Alignment:** PMIO → **Protection** (privileged instruction gate). MMIO → **Performance** (regular load/store, cacheable if desired) + **Sharing** (devices appear in unified address map).

### PCI Discovery via PMIO
- Two-register scheme: write BDF address to CONFIG_ADDRESS (0xCF8), read from CONFIG_DATA (0xCFC)
- 256 buses × 32 devices × 8 functions = up to 65,536 slots to scan
- Vendor ID = 0xFFFF → slot empty, skip
- CONFIG_ADDRESS bit layout: `[31=enable][23:16=bus][15:11=device][10:8=func][7:2=reg][1:0=00]`

---

## 10. Interrupts, Traps & System Calls
> **Tags:** `interrupt` `trap` `exception` `IDT` `IDTR` `interrupt vector` `NMI` `INTR` `PIC` `8259A` `INT` `IRET` `int 0x40` `trap gate` `interrupt gate` `DPL` `CPL` `alltraps` `trapframe` `iret` `syscall` `hardware interrupt` `software interrupt` `exception` `page fault`

### Interrupt Types
| Type | Maskable? | Source | x86 Handling |
|---|---|---|---|
| **NMI** (Non-Maskable) | Never | Hardware (power fail, memory error) | Always handled; vector 2 |
| **INTR** | Yes (IF flag) | Hardware devices via PIC | `STI`/`CLI` controls; 16 lines (two cascaded 8259A) |
| **Software INT** | N/A | `INT N` instruction | Syscalls, debugging |
| **Exceptions** | N/A | CPU faults (page fault, divide-by-zero, GPF) | Synchronous; may push error code |

### IDT (Interrupt Descriptor Table)
- 256 entries × 8 bytes; loaded into **IDTR** via `lidt`
- Each entry (gate descriptor) contains: segment selector (→GDT, sets CPL of handler), offset (handler address), DPL (who can invoke via software `int`), type (trap/interrupt gate)

### Gate Type Comparison

| | Interrupt Gate | Trap Gate |
|---|---|---|
| **`istrap` flag** | 0 | 1 |
| **IF behavior** | Clears IF → further interrupts disabled | Leaves IF alone → interrupts stay enabled |
| **Used for** | Hardware interrupts | System calls / exceptions |
| **Why** | Prevents interrupt re-entrancy on hardware events | Syscalls can be preempted (safe for long operations) |

### What Happens on `INT N` (full sequence)
1. Fetch descriptor for vector N from IDT (via IDTR)
2. **Permission check** (software `int` only): `CPL ≤ DPL` — else General Protection Fault
3. If ring crossing (CPL 3→0): save old SS/ESP in CPU-internal register, load new SS/ESP from **TSS**
4. Push (onto kernel stack): `[ss, esp]` (ring crossing only), `eflags`, `cs`, `eip`, `[error code]`
5. If interrupt gate: clear IF
6. Set `CS:EIP` from IDT descriptor → handler executes

**Return:** `IRET` — pops EIP, CS, EFLAGS (and ESP, SS if returning to lower privilege)

### Trap Frame Layout (stack bottom to top)
```
[ss / esp]   ← pushed by hardware ONLY if ring 3→0 crossing
[eflags]     ← hardware
[cs]         ← hardware
[eip]        ← hardware
[err code]   ← hardware (for exceptions that produce one)
[trapno]     ← pushed by software (alltraps)
[ds,es,fs,gs]← pushed by alltraps
[pushal]     ← all general-purpose registers (eax,ecx,edx,ebx,esp,ebp,esi,edi)
```

**SLO Analysis:** Interrupt latency SLO is *heterogeneous* across interrupt types:
- Hardware (timer, disk): SLO ~microseconds; tail latency limited by handler complexity
- NMI: must complete immediately (no SLO negotiation possible)
- Software (syscall): SLO measured in application-level terms (e.g., ≤1ms per syscall)
These are fundamentally heterogeneous because their urgency, source, and handler semantics differ.

**Design Alignment:** IDT + hardware interrupt mechanism → **Protection** (DPL gates prevent user code from invoking arbitrary kernel handlers) + **Isolation** (ring switch + stack switch ensures handler runs in clean kernel context)

---

## 11. Protection Rings & Privilege Levels
> **Tags:** `privilege` `rings` `CPL` `DPL` `RPL` `ring 0` `ring 3` `kernel mode` `user mode` `protection` `isolation` `CR3 write` `IOPL` `supervisor` `unprivileged` `privileged instructions`

### Ring Model
```
Ring 0 (kernel) — most privileged
Ring 1, 2       — rarely used (hypervisors sometimes use ring 1)
Ring 3 (user)   — least privileged
```

- **CPL** = lower 2 bits of `%cs`; changes only via far jump, interrupt, or `IRET`
- A user process **cannot self-escalate** CPL — `%cs` is read-only except via hardware mechanisms

### What Ring 0 Protects
- Writes to **CR3** (changing page table base → new address space)
- Writes to **CR0** (enabling/disabling paging and protected mode)
- Every memory access: hardware checks **U/S bit** in PTE against CPL
- **I/O port** access (`IN`/`OUT`) unless IOPL set — kernel sets IOPL=0 for user processes
- Modifying **EFLAGS.IF** (interrupt enable/disable)
- Loading `IDTR`, `GDTR`

### Privilege Check Layers (x86 Defense in Depth)
```
1. GDT → sets CPL via CS descriptor's DPL
2. Paging → checks CPL against U/S bit in every PTE
3. IDT → checks CPL ≤ DPL before software INT
```
**Key:** These layers are independent and composed — GDT provides identity (who am I?), paging enforces memory access, IDT enforces trap entry. All three must be correct.

### Segmentation vs. Paging for Isolation

| | Segmentation | Paging |
|---|---|---|
| **Isolation unit** | Segment (variable size) | Page (fixed 4KB) |
| **Fragmentation** | External fragmentation possible | Only internal (≤4KB waste) |
| **Virtual address space** | Limited by segment count | Full 4GB per process |
| **Physical multiplexing** | Poor (segments contiguous in PA) | Excellent (any page anywhere) |
| **Overhead** | Descriptor table lookup | Page walk (mitigated by TLB) |
| **Modern usage** | Flat (identity) — primarily for CPL | Primary isolation + protection mechanism |
| **Pareto position** | Dominated for isolation; essential for CPL/privilege | Pareto optimal |

**Design Alignment:** Paging → **Isolation** (per-process AS) + **Protection** (U/S bits, R/W bits) + **Multiplexing** (any physical page maps anywhere)

---


---

## L04 — Isolation

*([→ xv6 implementation for this lecture](<#L04 — Isolation — xv6>))*


> **Tags:** `isolation` `L04` `lec4` `kernel org` `L05` `lec5` `process isolation` `memory isolation`
> `CPU isolation` `protection rings` `CPL` `privilege levels` `ring 0` `ring 3` `segmentation`
> `virtual memory` `paging` `MMU` `time-slicing` `scheduling` `system calls` `syscall`
> `controlled handover` `trap handler` `monolithic kernel` `microkernel` `exokernel`
> `failure isolation` `performance isolation` `correctness isolation` `meltdown` `spectre`
> `side channels` `pareto frontier` `granularity` `multiplexing` `sharing` `protection`

---

## 1. Definition

> **Tags:** `definition` `what is isolation` `separation` `entities` `shared resources`

**Isolation** = complete separation of two or more entities such that one cannot affect the other.

- Entities interact only through **controlled, well-defined interfaces**
- Goal: prevent one entity from **wrecking**, **spying on**, or **interfering with** another
- Each entity behaves as if it has **exclusive access** to resources, even though resources are shared

---

## 2. When Is Isolation Necessary?

> **Tags:** `necessity conditions` `shared resources` `non-cooperative entities` `bitcoin mining`

Two conditions that together make isolation **desirable**:

| Condition | Example |
|-----------|---------|
| **Shared Resources** | Physical memory is shared → processes need isolation |
| **Non-Cooperative Entities** | Untrusted apps, competing processes (e.g., bitcoin mining), different users |

- **Shared resources alone**: threads access same address space → correctness problem (sync), not isolation
- **Non-cooperative entities alone**: single process → no issue
- **Both together** → isolation required

---

## 3. Isolation Pros

> **Tags:** `isolation pros` `failure isolation` `performance isolation` `correctness isolation` `security`

| Property | Description |
|----------|-------------|
| **Failure isolation** | Failures don't propagate — one process crash doesn't take down others |
| **Performance isolation** | Aberrant resource consumption is controlled; avoids starvation |
| **Correctness isolation** | Correctness of my program is not affected by other programs running |
| **Security / Privacy** | Processes/users cannot spy on or corrupt each other's data |

---

## 4. Isolation Cons — The Paradox

> **Tags:** `isolation cons` `perfect isolation` `useless` `paradox` `tradeoff` `some isolation sometimes`

- **100% perfect isolation** → process is **useless**
  - Cannot communicate
  - Cannot provide output
  - Cannot collaborate
- **0% isolation** → no protection at all

> **Takeaway (verbatim from lecture):** *"We want some isolation sometimes — this can change with workload, this can change with time."*

---

## 5. Isolation Use Cases

> **Tags:** `use cases` `what to isolate` `kernel user space` `processes` `memory` `security functions`

| What to Isolate | Entities | Shared Resource | Mechanism |
|-----------------|----------|-----------------|-----------|
| Kernel from user space | Kernel vs user process | CPU, memory | Protection rings + paging |
| Processes from each other | Process X vs Process Y | Physical memory, CPU | Virtual memory + time-slicing |
| Bitcoin mining competition | Competing processes | CPU time | Scheduling (preemptive) |
| Security-sensitive functions | Trusted vs untrusted code | Execution context | Privilege separation |

**Framework:** For each scenario, ask: *What are the entities? What is the shared resource?*

---

## 6. Isolation Mechanisms Overview

> **Tags:** `mechanisms` `hardware isolation` `address spaces` `segmentation` `paging` `time-slicing` `system calls` `permissions`

1. **Hardware**: Processor rings / protection levels
2. **Address spaces**: Segmentation (legacy), Virtual memory / Paging
3. **Time-slicing**: CPU isolation via scheduling
4. **System call interface**: Controlled user→kernel transfer
5. **Permissions / privilege**: Between users (file permissions, UIDs)

---

## 7. Hardware Isolation: Protection Rings

> **Tags:** `protection rings` `x86` `CPL` `current privilege level` `ring 0` `ring 3` `kernel` `user` `DPL` `RPL` `segment descriptor`

### Privilege Levels in x86

```
Ring 0 — OS Kernel         (most privileged)
Ring 1 — OS Services       (rarely used in modern OS)
Ring 2 — OS Services       (rarely used in modern OS)
Ring 3 — Applications      (least privileged / user)
```

### CPL: Current Privilege Level
- Stored in **lower 2 bits of `%CS`** (Code Segment register)
- `CPL = 0` → kernel (privileged)
- `CPL = 3` → user (unprivileged)
- xv6 uses only `0x009b` → `0000 0000 1001 1011` for CS in QEMU

### What Ring 0 Protects (CPU shared resources)

| Protected Resource | Why It Matters |
|--------------------|----------------|
| **Writes to `%CR3`** | CR3 = page directory base = address space control |
| **Writes to `%CS`** | Defends CPL itself — prevents privilege escalation |
| **Every memory read/write** | Checked against privilege (S/U flag on PTE) |
| **I/O port accesses** | e.g., overwriting inodes, disk corruption |
| **Control register accesses** | eflags, `%CR4`, etc. |

### Segment Selectors and Privilege Checks
- **CPL**: current privilege (in `%CS`)
- **DPL**: Descriptor Privilege Level (in segment descriptor / IDT entry)
- **RPL**: Requested Privilege Level (in segment selector)
- **Access check**: `max(CPL, RPL) ≤ DPL` to proceed
- Interrupt handling: IDT entry has CS + eip to handler; handler checks CPL in `%CS`

---

## 8. Address Space Isolation: Segmentation (Legacy)

> **Tags:** `segmentation` `GDT` `global descriptor table` `LDT` `segment selector` `real mode` `protected mode` `contiguous memory`

- Old-school virtual memory: divides physical memory into "segments" with base, limit, permissions
- **Real mode (16-bit)**: Physical address = `CS<<4 + IP` — minimal protection
- **Protected mode (32-bit)**: Segment registers point into the GDT
  - GDT holds region bounds, protection (R/W), privilege levels
  - After segmentation, addresses are called **Linear Addresses**

### What Segmentation Provides:
- **Isolation**: non-overlapping segments = isolated address spaces
- **Multiplexing**: multiple processes share physical memory

### Why Paging Replaced Segmentation:

| Segmentation | Paging |
|---|---|
| Requires **contiguous** physical memory | Arbitrary page mapping (non-contiguous OK) |
| Per-segment permissions | **Per-page permissions** (finer grained) |
| Still used in x86 but largely bypassed | Default modern mechanism |
| Hard to dynamically resize | Easy to grow/shrink at page granularity |

> Q posed in lecture: *"Might we ever want segmentation over paging?"* (hint: embedded/special cases)

---

## 9. Address Space Isolation: Virtual Memory & Paging

> **Tags:** `virtual memory` `paging` `MMU` `page tables` `PDE` `PTE` `U/S bit` `R/W bit` `present bit` `page fault` `CR3` `address translation` `TLB`

### Core Idea
- Give every process an **identical virtual address space** (illusion of exclusive memory ownership)
- Hardware **MMU** translates virtual → physical address transparently
- **Enforce privilege level at page granularity** (U/S bit per PTE)

### Address Translation (32-bit x86)
```
Virtual Address (32 bits)
 [31:22] Page Directory Index (10 bits)
 [21:12] Page Table Index (10 bits)
 [11:0]  Page Offset (12 bits)

%CR3 → Page Directory → PDE → Page Table → PTE → Physical Page + Offset
```

### PDE / PTE Permission Bits

| Flag | Meaning |
|------|---------|
| **P** (Present) | 0 → page fault on access |
| **R/W** | 0 = read-only, 1 = read+write |
| **U/S** | 0 = supervisor only (kernel), 1 = user accessible |
| **D** (Dirty) | Set by hardware on write |
| **A** (Accessed) | Set by hardware on access |
| **PWT, PCD** | Cache control |

### Access Check During Page Walk:
1. PTE not present (P=0) → **page fault**
2. CPL=3 (user) + U/S=0 (supervisor page) → **page fault**
3. Write attempt + R/W=0 (read-only) → **page fault**

### Context Switching = Memory Isolation
- Switching processes = **write new process's page table base into `%CR3`**
- Since writing `%CR3` requires ring 0, user processes **cannot** change their own address space mapping
- Each process has a **hardware-enforced isolated address space**

### CR3 and TLB
- `%CR2`: holds faulting address on page fault
- `%CR3`: physical address of page directory (reloading flushes TLB for non-global pages)
- `%CR4`: architectural extensions (e.g., page size, virtualization)

---

## 10. CPU Isolation: Time-Slicing

> **Tags:** `time-slicing` `CPU isolation` `scheduler` `cooperative` `preemptive` `yield` `clock interrupt` `quantum` `starvation` `timing side channels` `covert channels`

### Core Idea
- Abstract the CPU so each process perceives its **own dedicated processor**
- Scheduler answers: **who** gets CPU, **what** they can do, **when** they get it

### Cooperative vs Preemptive

| | Cooperative | Preemptive |
|---|---|---|
| **Mechanism** | Process calls `yield()` voluntarily | Timer interrupt forces switch |
| **Isolation guarantee** | Weak — buggy/malicious process can starve others | Strong — kernel retains control |
| **Overhead** | Low | Higher (interrupt handling, context save/restore) |
| **When used** | Trusted environments, simple embedded | General-purpose OS (Linux, xv6) |

### Isolation Concern with Time-Slicing
> *"Perfect isolation with time quanta is hard"* — L04

- **Timing side channels**: Process A measures cache eviction timing → infers what Process B is doing
- **Covert channels**: processes communicate via shared resources (caches, memory access patterns)

---

## 11. System Call Interface: Controlled Handover

> **Tags:** `system calls` `syscall` `INT instruction` `sysenter` `trap handler` `controlled handover` `argument sanitization` `CPL transition` `user to kernel` `protected transfer`

### Switching Between Protection Rings
- Use **`INT`** or **`sysenter`** to set CPL to 0 (kernel)
- Set CPL back to 3 before returning to user space
- Safety is guaranteed by switching to kernel **only at a predetermined entry point** (trap handler)

### Trap Handler Responsibilities (Controlled Handover)
1. **Save user space context** (registers, `%EIP`, `%CS`)
2. **Load a safe kernel context** (kernel stack, kernel page tables)
3. **Sanitize arguments** for the specific kernel request
4. **Load arguments from user space stack** carefully
5. **Accept or deny the request** (kernel decides)

### Why Argument Sanitization Matters
```c
// Dangerous unsanitized syscall:
char *buff = get_virus_code();       // user-controlled pointer
int fd = open("/tmp/virus", ...);
write(fd, buff, size);
read(fd, (char *)(0x80100000), size); // ← points to KERNEL MEMORY!
```
- Without checking: user process can **read/write arbitrary kernel memory**
- Kernel must verify all pointers stay **within user address space** (e.g., `< 0x80000000`)

### System Call Counts by OS

| OS | # System Calls |
|---|---|
| **xv6** | 21 |
| **Linux** | 300+ |
| **FreeBSD** | 500+ |
| **Windows 10/11** | ~465 core / 2000+ total |

> Tip: `strace <program>` traces system calls on Linux.

---

## 12. Kernel Organization and Isolation

> **Tags:** `kernel organization` `monolithic kernel` `microkernel` `exokernel` `fos` `fuchsia` `zircon` `kernel responsibilities` `isolation tradeoffs` `kernel threading models`

### Kernel Responsibilities
Minimal kernel must provide: **Isolation** + **Protection**

### Kernel Architecture Designs

#### Monolithic Kernel (e.g., xv6, Linux)
- All kernel services (fs, scheduler, memory, drivers, net) run in **ring 0**
- System calls go directly into kernel functions
- **Note**: C standard library lives above the kernel — cannot call C stdlib inside xv6

#### Microkernel (e.g., Plan 9, Fuchsia/Zircon, FOS)
- Kernel only manages **isolation** — everything else runs as user-level system processes
- Communication via **message passing** between isolated servers
- Fuchsia uses **capability-based security** — each syscall requires a capability

#### Exokernel
- Kernel provides only **protections** (not even full isolation)
- Applications access hardware directly via their own **libOS**
- Abstractions like isolation provided by untrusted user-level programs

### Kernel Architecture Comparison

> See [L05 — Kernel Organization & APIs §15](<#L05 — Kernel Organization & APIs>) for the full Monolithic / Microkernel / Exokernel comparison table.

### Key Tradeoff (L05 lecture quote):
> *Microkernel: "If the FS crashes, the rest of the kernel will be fine." Disadvantage: Performance.*

### Kernel Threading Models

| Model | Description | Isolation | Concurrency |
|---|---|---|---|
| **Many-to-One** | All user processes → single kernel thread | Low | Sequential syscalls only |
| **One-to-One** | Each user process → own kernel stack/thread | High | Concurrent syscalls |
| **Many-to-Many** | Pool of user threads → pool of kernel threads | Medium | Balanced |

- **xv6 uses One-to-One**: each process has its own kernel context
- One-to-One: stack not shared, no waiting, concurrent accesses to syscall handlers

---

## 13. Comparison Table: Isolation Mechanisms

> **Tags:** `comparison` `tradeoffs` `design choices` `mechanisms` `pros cons`

| Mechanism | Isolation Type | Pros | Cons | Tradeoff |
|-----------|---------------|------|------|----------|
| **Protection Rings (CPL)** | CPU privilege | Hardware-enforced, fast | Only 2 effective levels (0/3) | Coarse privilege, binary |
| **Segmentation** | Memory | Simple, historical compat | Contiguous memory, coarse, legacy | Replaced by paging |
| **Paging (VMM)** | Memory | Fine-grained, flexible | TLB overhead, page walk cost | Overhead vs. granularity |
| **Time-slicing (Preemptive)** | CPU | Strong guarantee, prevents starvation | Overhead, context switch cost | Fairness vs. throughput |
| **Time-slicing (Cooperative)** | CPU | Low overhead | Weak isolation (process can hog) | Simplicity vs. safety |
| **System Calls** | Kernel/User | Controlled interface | Overhead per call | Safety vs. performance |
| **Monolithic Kernel** | Architecture | Fast IPC, shared state | Kernel bug affects everything | Performance vs. isolation |
| **Microkernel** | Architecture | Strong compartmentalization | IPC overhead | Isolation vs. performance |

---

## 14. Pareto Frontier Analysis

> **Tags:** `pareto frontier` `pareto optimal` `design space` `safety` `usability` `performance`

### From L04 (Isolation Tradeoffs Diagram):
```
           Safety
              ^
              |           Dream point
   Reality 1  |  Reality 2  (unachievable)
      ●        |      ●
              |
   Bad design ●
              |
    Weaker ───┼─────────── Stronger
          Isolation ──→ Usability/Performance
```

**Induced tradeoffs (verbatim axis labels from lecture):**

| Direction | Effect on Safety | Effect on Usability | Effect on Performance |
|-----------|-----------------|--------------------|-----------------------|
| **Weaker isolation** | ↓ | ↑ | ↑ |
| **Stronger isolation** | ↑ | ↓ | ↓ |

### L05 Pareto Frontier (Kernel Organization):
```
     Safety
       ^
       |   microkernel ●
       |
       |         ● monolith
       |
       +──────────────→ Performance
```

- **Microkernel**: better isolation/safety, worse performance → **Pareto optimal** on safety axis
- **Monolithic**: worse isolation, better performance → **Pareto optimal** on performance axis
- Neither dominates the other → **both are Pareto optimal** on the safety-performance frontier
- A "bad design" is one dominated on both axes (worse safety AND worse performance than alternatives)

### Pareto Optimal Designs Summary:
- **Strong isolation** (microkernel, paging + CPL, preemptive): Pareto-optimal for safety
- **Weak isolation** (monolithic, cooperative scheduling): Pareto-optimal for performance
- No design achieves maximum safety AND maximum performance simultaneously

---

## 15. Key Ideas Alignment

> **Tags:** `isolation` `multiplexing` `protection` `performance` `sharing` `key ideas alignment`

| Design Choice | Isolation | Multiplexing | Protection | Performance | Sharing |
|---------------|:---------:|:------------:|:----------:|:-----------:|:-------:|
| **Protection rings (CPL)** | ✓ | | ✓ | ✓ (fast check) | |
| **Segmentation** | ✓ | ✓ | ✓ | | |
| **Paging / VMM** | ✓ | ✓ | ✓ | (overhead) | |
| **Preemptive scheduling** | ✓ | ✓ | ✓ | (overhead) | |
| **Cooperative scheduling** | | ✓ | | ✓ | ✓ |
| **System call interface** | ✓ | | ✓ | (overhead) | |
| **Microkernel** | ✓ | | ✓ | | |
| **Monolithic kernel** | | ✓ | | ✓ | ✓ |
| **Exokernel** | | ✓ | ✓ | ✓ | |

---

## 16. Granularity Analysis

> **Tags:** `granularity` `granularity spectrum` `unit of isolation` `page level` `segment level` `process level` `fine grained` `coarse grained`

### The Unit of Isolation: **The Process**
From L04 (verbatim):
- Prevent process X from wrecking or spying on process Y (memory, CPU, FDs, resource exhaustion)
- Prevent a process from wrecking the OS itself (preventing kernel from enforcing isolation)
- In the face of bugs or malice (e.g., a bad process may try to trick hw or kernel) — **Spectre and Meltdown**
- If one process has a bug, it shouldn't impact others that are not its children

### Granularity Spectrum for Memory Isolation

```
Fine ←──────────────────────────────────────────→ Coarse
Page (4 KB)    Segment    Region    Process    System-wide
     +               -
     flexible         simpler
     more overhead    less overhead
     fine control     coarse control
     TLB pressure     contiguous requirement (seg)
```

| Granularity | Unit | Pros | Cons |
|-------------|------|------|------|
| **Page-level** | 4 KB pages | Fine-grained control per page, arbitrary mapping | TLB overhead, page walk cost |
| **Segment-level** | Variable-size region | Simple, hardware-supported (legacy) | Requires contiguous physical memory |
| **Process-level** | Entire address space | Strongest isolation model | High overhead to switch, no sharing |

### Granularity Spectrum for Scheduling
- **Fine**: short quanta (high fairness, high overhead)
- **Coarse**: long quanta (low overhead, less responsive)

---

## 17. Performance Analysis

> **Tags:** `performance` `CDF` `context switch latency` `overhead` `system call overhead` `TLB flush`

### Events with Performance Impact

| Event | Overhead Source | CDF Shape |
|-------|----------------|-----------|
| **Context switch** | Save/restore registers, flush TLB (CR3 write), reschedule | Short tail — most switches fast; long tail from cache cold-start |
| **System call** | Ring transition, argument validation, kernel execution, return | Bimodal — fast simple calls (getpid), slow I/O-bound calls |
| **Page fault** | Page walk failure → kernel handler → demand paging | Heavy tail — most faults fast (present, wrong perm); rare ones involve disk I/O |
| **TLB miss** | CR3 reload, multi-level page walk | Short tail — most hits in TLB; misses add ~10-100 cycles |

### What a Context Switch CDF Looks Like:
- **X-axis**: Switch latency (microseconds)
- **Y-axis**: Fraction of switches ≤ that latency
- **Shape**: Steep rise near median (most switches fast), long right tail (cold cache, preemption of I/O-bound)
- **Key insight**: Stronger isolation (microkernel IPC vs monolith syscall) pushes the CDF right (slower median, longer tail)

---

## 18. Objective Analysis (SLOs)

> **Tags:** `SLOs` `service level objectives` `failure isolation SLO` `performance isolation SLO` `homogenous` `heterogenous`

### Possible SLOs for Isolation

| Isolation Type | SLO | Homogenous/Heterogenous |
|----------------|-----|------------------------|
| **Failure isolation** | Process crash does not affect others within T ms | **Homogenous** — same guarantee across all processes |
| **Performance isolation** | Process receives ≥ X% CPU over any Y-second window | **Heterogenous** — critical vs. background differ |
| **Memory isolation** | No cross-process read/write without explicit sharing | **Homogenous** — universal, no exceptions |
| **Kernel isolation** | User process cannot read/write kernel memory | **Homogenous** — absolute |
| **Security isolation** | User A cannot access User B's files | **Homogenous** — enforced by permission bits |

### Implications:
- **Homogenous SLOs** (memory safety, kernel separation): non-negotiable, binary
- **Heterogenous SLOs** (CPU quotas, memory limits): workload-dependent, best-effort vs. guaranteed
- Real-time processes vs. background: heterogenous performance SLOs → different quanta lengths
- Starvation prevention: performance SLO may require **guaranteed minimums** (not just best effort)

---

## 19. Meltdown & Spectre: Isolation Is Not Solved

> **Tags:** `meltdown` `spectre` `side channels` `speculative execution` `KPTI` `isolation break` `CVE-2017-5754` `CVE-2017-5753` `CVE-2017-5715`

From L04 (verbatim):
- **Meltdown**: *"breaks the most fundamental isolation between user applications and the operating system"*
- **Spectre**: *"breaks the isolation between different applications"*

| | Meltdown | Spectre |
|---|---|---|
| **CVE** | CVE-2017-5754 | CVE-2017-5753, CVE-2017-5715 |
| **Breaks** | User ↔ Kernel isolation | Process ↔ Process isolation |
| **Root cause** | Speculative execution bypasses memory permission checks | Speculative execution leaves observable cache side effects |
| **Fix** | KPTI — separate kernel/user page tables | Microcode updates, CPU redesign |
| **Difficulty** | Patchable in software | Fundamentally hard — requires hardware changes |

### Research Frontier:
**Theseus OS** (OSDI 2020): uses compiler-enforced isolation instead of solely hardware mechanisms
- *"Many tiny components with clearly-defined, runtime-persistent bounds interact without holding states for each other"*
- *"Intralingual approach: compiler enforces invariants about OS semantics"*
- https://www.usenix.org/conference/osdi20/presentation/boos

---


---

## L05 — Kernel Organization & APIs

*([→ xv6 implementation for this lecture](<#L05 — Kernel Organization & APIs — xv6>))*


> **Tags:** `kernel org` `L05` `lec5` `kernel organization` `kernel apis` `kernel design`
> `monolithic` `microkernel` `exokernel` `libOS` `kernel responsibilities` `what goes in kernel`
> `draw the line` `minimal kernel` `kernel interface` `system call table` `syscall categories`
> `process syscalls` `memory syscalls` `fs syscalls` `file descriptors` `fd` `pipe` `IPC`
> `message passing` `FOS` `factored operating system` `fuchsia` `zircon` `capability based`
> `declarative interface` `imperative interface` `service user mapping` `echo hello cat`
> `add system call` `sysfile` `sysproc` `syscall.c` `concurrency handling` `kernel threading`
> `many to one` `one to one` `many to many` `N-1` `1-1` `M-N` `kernel stack` `context`
> `trap vector` `trap handler` `unix history` `glibc` `POSIX` `dup` `poll` `epoll`
> `pareto frontier` `ukernel` `isolation` `protection` `performance` `sharing` `multiplexing`
> `exokernel engler` `notional exokernel` `jobs` `capability`

> **Cross-reference:** High-level isolation mechanisms, ring-0 protection, paging, preemptive scheduling, and basic monolithic/microkernel comparison tables are in **isolation.md**. This sheet covers the *design decision framework*, *kernel API depth*, *IPC mechanics*, *threading model specifics*, and *modern systems*.

---

## 1. The Central Design Question

> **Tags:** `kernel design question` `what goes in kernel` `draw the line` `OS vs kernel` `kernel responsibilities`

- **Kernel ≠ OS**: The OS includes middleware, daemons, C std library. The kernel is the privileged core.
- **Central question**: Do all OS tasks belong inside the kernel? Where do we draw the line?
- **Framework for deciding**: Anything that requires **privilege (ring 0)** to enforce → kernel. Everything else → user space.
- **Minimum kernel must provide**: **Isolation** + **Protection** (from L05 slide verbatim)

```
Kernel must handle:
  ├── Isolation (address spaces, CPU time-slicing)
  └── Protection (enforce privilege, prevent unauthorized access)

Everything else is optional inside the kernel:
  ├── Filesystem management
  ├── Memory allocation policies
  ├── Networking stack
  ├── Device drivers
  └── IPC mechanisms
```

---

## 2. Kernel Organization: The Spectrum

> **Tags:** `kernel separation` `kernel organization spectrum` `monolithic architecture` `microkernel architecture` `service layer`

### Conceptual Model: Who Has Access to Which Services?

**Monolithic** — every user process can access all kernel services:
```
U1 → {all s_i}
U2 → {all s_i}
Un → {all s_i}
                  ┌──────────────────────────┐
[u1] [u2] ... [un]│          kernel          │
                  └──────────────────────────┘
```

**Microkernel** — users access specific services; services run at user level:
```
U1 → {s1, sn}
U2 → {s1, s2, s...}
Un → {s..., sn}
          ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐
[u1] [u2] │  s1  │  │  s2  │  │ ...  │  │  sn  │  ← user-level servers
     [un]  └──────┘  └──────┘  └──────┘  └──────┘
          ┌──────────────────────────────────────┐
          │             micro kernel              │
          └──────────────────────────────────────┘
```

### Interface Types Between Users and Services

| Type | Description | Example |
|------|-------------|---------|
| **Declarative** | Specify *what* you want; server decides *how* | SQL queries, resource policy specs |
| **Imperative** | Specify *how* to do it step by step | Traditional syscalls (read, write, open) |

- Microkernel services can expose either interface type
- Monolithic kernel exposes only imperative (direct syscalls)

---

## 3. Monolithic Kernel Architecture (Layers)

> **Tags:** `monolithic layers` `C std library above kernel` `middleware` `daemons` `cron` `systemd` `x server`

```
┌─────────────────────────────────────────────────────┐  ← apps layer
│                    Applications                      │
└─────────────────────────────────────────────────────┘
┌──────────┬──────────┬────────────┬──────────┬───────┐  ← system layer
│ C Std Lib│ X Server │ Middleware  │ Daemons  │ Init  │
│          │          │            │(Cron,etc)│systemd│
└──────────┴──────────┴────────────┴──────────┴───────┘
┌─────────────────────────────────────────────────────┐  ← kernel layer
│   fs  │  sched  │  Monolithic Kernel  │ proc │ mem  │
└─────────────────────────────────────────────────────┘
```

> **CRITICAL NOTE (from slide):** *"C Std Library lives **above** the kernel — you cannot call C std lib within xv6!"*

- All kernel services (fs, scheduler, memory, drivers, net) run in **ring 0** together
- A bug in any one component can crash the entire kernel

---

## 4. Kernel Interface: xv6 System Call Table

> **Tags:** `xv6 syscalls` `syscall table` `fork` `exec` `wait` `kill` `getpid` `sleep` `sbrk`
> `open` `read` `write` `close` `dup` `pipe` `chdir` `mkdir` `mknod` `fstat` `link` `unlink`
> `process syscalls` `memory syscalls` `file system syscalls`

### xv6 System Calls by Category

| Category | System Call | Description |
|----------|------------|-------------|
| **process** | `fork()` | Create a process |
| **process** | `exit()` | Terminate the current process |
| **process** | `wait()` | Wait for a child process to exit |
| **process** | `kill(pid)` | Terminate process pid |
| **process** | `getpid()` | Return the current process's pid |
| **process** | `sleep(n)` | Sleep for n clock ticks |
| **process** | `exec(filename, *argv)` | Load a file and execute it |
| **memory** | `sbrk(n)` | Grow process's memory by n bytes |
| **fs** | `open(filename, flags)` | Open a file; flags indicate read/write |
| **fs** | `read(fd, buf, n)` | Read n bytes from an open file into buf |
| **fs** | `write(fd, buf, n)` | Write n bytes to an open file |
| **fs** | `close(fd)` | Release open file fd |
| **fs** | `dup(fd)` | Duplicate fd |
| **fs** | `pipe(p)` | Create a pipe and return fd's in p |
| **fs** | `chdir(dirname)` | Change the current directory |
| **fs** | `mkdir(dirname)` | Create a new directory |
| **fs** | `mknod(name, major, minor)` | Create a device file |
| **fs** | `fstat(fd)` | Return info about an open file |
| **fs** | `link(f1, f2)` | Create another name (f2) for file f1 |
| **fs** | `unlink(filename)` | Remove a file |

**Total in xv6: 21 syscalls** (vs ~300 Linux, ~465 Windows core)

---

## 5. Kernel API: The `echo Hello | cat` Example

> **Tags:** `echo hello cat` `pipe example` `kernel api example` `sh` `cat` `echo` `file server`
> `monolithic api` `microkernel api` `send message` `IPC example`

### Monolithic Kernel (e.g., xv6, Linux)

```
┌────┐  ┌────┐  ┌──────┐
│ sh │  │cat │  │ echo │   (user space)
└──┬─┘  └──┬─┘  └───┬──┘
   │exec,   │read/   │write
   │open,   │write   │call
   │close,  │calls   │
   │pipe    │        │
   │calls   │        │
═══╪════════╪════════╪════════════ kernel-user space divide ══
   ↓        ↓        ↓
┌──────────────────────────────────────────────────────┐
│           Monolithic Kernel (e.g., xv6 or Linux)     │
│                         ┌───────────┐                │
│                         │File server│ ← INSIDE kernel│
│                         └───────────┘                │
└──────────────────────────────────────────────────────┘
```

### Microkernel (e.g., Plan 9, Fuchsia)

```
                                    ┌─────────┐ ┌──────────────┐
                                    │ Mem mgr │ │Cache service │  (user space servers)
                                    └────┬────┘ └──────┬───────┘
┌────┐  ┌────┐  ┌──────┐  ┌───────────────────────────┐
│ sh │  │cat │  │ echo │  │       File server         │  ← OUTSIDE kernel
└──┬─┘  └──┬─┘  └───┬──┘  └──────────────────┬────────┘
 Send    Send      Send                       ↑ (IPC reply)
Message Message   Message                     │
═══╪════════╪════════╪════════════════════════╪═══ kernel-user divide ══
   ↓        ↓        ↓                        │
┌──────────────────────────────────────────────────────┐
│           Micro Kernel (e.g., Plan 9, Fuchsia)       │
└──────────────────────────────────────────────────────┘
```

**Key difference**: File server is inside the kernel for monolithic, outside (user-level) for microkernel.

---

## 6. File Descriptors

> **Tags:** `file descriptors` `fd` `integer handle` `per-process fd table` `console` `stdin` `stdout` `stderr` `pipe fd`

- Kernel maintains a **per-process list of file descriptors**
- FDs are **integer handles** for: files, console I/O, pipes between user programs, any I/O object
- Syscalls enable files and **file-like objects** to be created (pipes behave like files)
- The shell uses the syscall interface to: allow users to interact with the kernel AND allow programs to interact with each other

---

## 7. Microkernel Communication: IPC / Message Passing

> **Tags:** `IPC` `inter process communication` `message passing` `microkernel IPC` `send message`
> `FOS` `factored operating system` `message proxy lib` `name cache` `fos microkernel`
> `FS request walkthrough`

### Why IPC Is Necessary in Microkernels
- Services run at user level → cannot share kernel memory
- All communication must cross the kernel boundary via **message passing**
- Kernel only routes messages; services do the work

### FOS (Factored Operating System) — Microkernel Example
**Source:** Wentzlaff et al., *Factored Operating Systems (fos): The case for a scalable OS for Multicores*

FOS layout (distributed across cores):
```
[M] [FS] [M]  [M]  [FS] [M]  [M]  [FS] [M]
[I] [  ] [I]  [ ]  [ ]  [ ]  [I]  [ ]  [I]   ← Idle cores
[M] [  ] [M]  [M]  [FS] [M]  [M]  [FS] [M]
```
- **M** = Physical Memory Allocation Server
- **FS** = File System Server
- **I** = Idle Processor Core
- **Blue squares** = Application instances

### FOS Message Walkthrough (FS Access, 9 steps)

```
Application side:                    File System Server side:
①  App makes func call to
   message proxy lib
②  Message (mesg) is formed
③  Sent to fos-microkernel    →  (kernel routes)  →  ⑥ mesg arrives at FS server
④  Name cache lookup                                  ⑦ FS server processes request
⑤  Delivery confirmed                                 ⑧ Response formed
                               ←  (kernel routes)  ←
⑨  App receives response
```

- Syscall → message proxy lib → kernel → OS server → kernel → response
- IPC overhead is the primary cost vs. direct monolithic function calls

---

## 8. Microkernel Pros and Cons (L05 Verbatim)

> **Tags:** `microkernel advantages` `microkernel disadvantages` `FS crash` `compartmentalized design`
> `microkernel performance penalty`

**Advantages:**
- **Increased Isolation** — if the FS crashes, the rest of the kernel will be fine
- **Compartmentalized Design** — each service is its own fault domain

**Disadvantages:**
- **Performance** — every OS service call requires IPC (message pass + kernel crossing)
- **Hard to compartmentalize** — *"If the FS crashes, does everything still work fine?"* (not always obvious; depends on which processes need FS at that moment)

> Microkernel motto: *"My kernel survived FS error. My networked file server is crushing it now."*

---

## 9. Modern Microkernels: Fuchsia / Zircon

> **Tags:** `fuchsia` `zircon` `zircon microkernel` `google fuchsia` `capability based security`
> `capability` `jobs` `resource limitations` `IoT` `android` `GPL` `oracle lawsuit`

- **Fuchsia** = Google OS (Pink + Purple), bootable on Pixelbook, open source, not a Linux/UNIX descendant
- Based on **Zircon microkernel**
- Syscalls are **access-controlled (capability-based security model)**
  - Unlike Linux: a thread must **possess the capability** to invoke a syscall
  - Capability = unforgeable token that grants access to a specific resource
- **Processes owned by "jobs"** that define resource limitations (memory caps, CPU limits)
- Provides sufficient primitives for C/C++ libraries
- Targeted at **IoT and ubiquitous computing** as a secure OS
- Also frees Google from **GPL** (governing Android) and the Oracle Java lawsuit

| Feature | Linux | Fuchsia/Zircon |
|---------|-------|----------------|
| Syscall access | Any process can call any syscall | Requires capability for each syscall |
| Kernel type | Monolithic | Microkernel |
| Syscall wrapping | glibc wraps syscalls | Direct or via Fidl IPC library |
| Heritage | UNIX | New (not Linux/UNIX) |

---

## 10. Exokernels

> **Tags:** `exokernel` `libOS` `library OS` `protections only` `direct hardware access`
> `engler` `MIT` `exokernel thesis` `notional exokernel` `ExOS` `abstraction`
> `multiplexes not abstracts` `security focused`

- **Core claim**: Kernel need only provide **protections** — not even full isolation
- Kernel determines what processes are allowed to access which resources → **multiplexes but does NOT abstract**
- Abstractions like isolation are provided by **untrusted user-level programs** that access hardware directly via their own **libOS**

### Exokernel Architecture

```
┌──────────────────┐   ┌────────────────────────────┐
│  gcc application │   │  Specialized WWW server     │
│  ┌─────────────┐ │   │  ┌────────────────────────┐ │
│  │    libOS    │ │   │  │     libOS subset        │ │
│  │ [VM][NET][FS│ │   │  │   [FS][NET]             │ │
│  └─────────────┘ │   │  └────────────────────────┘ │
└────────┬─────────┘   └───────────────┬─────────────┘
         └──────────────┬──────────────┘
              ┌─────────▼──────────┐
              │     exokernel      │   ← protections only
              └─────────┬──────────┘
         ┌──────────────┼──────────────┐
      [memory pages]  [disk]       [network]
```

- Each application has its **own libOS** — can implement custom VM, FS, NET policies
- **Pros**: Performance, application control over hardware resources
- **Cons**: Each app must implement its own OS abstractions; trust boundary complex
- Source: Engler, D.R. *The Exokernel Operating System Architecture*. Ph.D. Thesis. MIT. Oct. 1998.

---

## 11. UNIX Syscall History & API Evolution

> **Tags:** `unix history` `syscall history` `glibc` `POSIX` `linux syscall count` `dup dup2 dup3`
> `pipe pipe2` `select poll epoll` `syscall interface evolution` `mainframe` `shared mainframe`

- UNIX syscall interface originally designed to let users **concatenate programs together** via shell on shared mainframes (1970s)
- Later expanded to support graphical, network interaction
- **xv6**: 21 syscalls; syscalls used **directly** by programs
- **Linux**: ~300 syscalls; syscalls **wrapped by glibc** (standard C library) — `read()` in C calls `sys_read` via glibc

### Linux API Is "Littered with Mistakes"

| Issue | Evidence |
|-------|---------|
| `dup` wasn't enough | → `dup2`, then `dup3` added |
| `pipe` wasn't enough | → `pipe2` added |
| `select` had limits | → `poll` added → `epoll` added |
- Linux API is **standardized** → difficult to alter but **can be added to**
- This backwards-compatibility burden is why Linux syscall count keeps growing

---

## 12. How to Add a System Call

> **Tags:** `add syscall` `add system call` `syscall number` `syscall handler` `unistd.h` `syscalls.h`
> `macro associate` `extend kernel api`

### Steps to Add a Syscall (xv6 or Linux — nearly identical)

1. **Write the C implementation** of the syscall handler function
2. **Add it to `syscalls.h`** (xv6) or equivalent header (Linux)
3. **Add a syscall number** to `unistd.h` (Linux) or `syscall.h` (xv6)
4. **Call the macro** to associate the number with the function
5. *(Linux only)* Add to the syscall table in architecture-specific code

```c
// xv6 example addition in syscall.c:
static int (*syscalls[])(void) = {
[SYS_fork]    sys_fork,
[SYS_exit]    sys_exit,
// ... add:
[SYS_mycall]  sys_mycall,   // ← step 4: macro associates number → function
};
```

```c
// xv6 new handler in sysproc.c or sysfile.c:
int sys_mycall(void) {
    // step 1: implementation
    return 0;
}
```

> In xv6: file-related syscalls → `sysfile.c`; process-related → `sysproc.c`; dispatch table → `syscall.c`

---

## 13. Kernel Concurrency Handling

> **Tags:** `kernel concurrency` `concurrent syscalls` `two processes one kernel` `concurrency in kernel`
> `kernel locking` `single tenant` `shared kernel stack`

**Problem**: Two user-space programs call into the same kernel simultaneously. How does the kernel handle this?

```
[user-space prog A]   [user-space prog B]
         ↓                    ↓
    ════════════════════ kernel ════════════════════
    Trap Vector → Trap Handler → System Call Table → sys_read
```

The answer depends on the **threading model** chosen.

---

## 14. Kernel Threading Models (In-Depth)

> **Tags:** `kernel threading models` `many to one` `one to one` `many to many` `N-1` `1-1` `M-N`
> `kernel stack per process` `single kernel context` `pool of kernel threads` `P >= C`
> `concurrent syscall access` `underutilize resources`

### Many-to-One (N-1): All Processes → Single Kernel Stack

```
[user prog A]  [user prog B]
       ↓              ↓
   ┌──────────────────────────────────────┐
   │ ┌─────────────────────┐             │
   │ │Single Kernel Stack / │             │
   │ │Context (must lock!)  │             │  Xv6 kernel
   │ │    Trap Vector       │             │
   │ └──────────────────────┘             │
   │         → Trap Handler → Syscall Table → sys_read
   └──────────────────────────────────────┘
```

- Only **1 process can be in a syscall at any given time**
- **Advantage**: Concurrency is simplified (single tenant) — no locking needed inside kernel
- **Disadvantage**: Underutilizes resources; not practical on multicore or I/O-bound systems

### Many-to-Many (M-N): P User Processes → C Kernel Stacks (P ≥ C)

```
[u1][u2][u3]...[uP]   (P user programs)
         ↓
   ┌──────────────────────────────────────┐
   │ ┌──────┐┌──────┐                    │
   │ │KStack││KStack│ ... (C contexts)    │  Xv6 kernel
   │ │      ││      │ Typically P ≥ C     │
   │ └──────┘└──────┘                    │
   │   Trap Vector (contexts run together)│
   │       → Trap Handler → Syscall Table │
   └──────────────────────────────────────┘
```

- **Advantage**: Save memory (fewer kernel stacks than N-1's overhead in 1-1 case)
- **Disadvantage**: Still need concurrent locking inside the kernel (contexts can run together)
- Used by: old IRIX, HP-UX, Solaris (hybrid: kernel decides between M:M and 1:1)

### One-to-One (1-1): Special case of M:N where P == C

```
[user prog A]  [user prog B]  [user prog C]
       ↓              ↓               ↓
   ┌──────────────────────────────────────┐
   │ ┌──────┐ ┌──────┐ ┌──────┐         │
   │ │KStack│ │KStack│ │KStack│          │  Xv6 kernel
   │ └──────┘ └──────┘ └──────┘          │
   │   Trap Vector (contexts run together)│
   │       → Trap Handler → Syscall Table │
   └──────────────────────────────────────┘
```

- Each user process has its **own kernel stack and context**
- **Advantage**: Stack is NOT shared; don't have to wait; **concurrent access to syscall handlers**
- **Disadvantage**: Memory overhead — N kernel stacks for N processes
- Used by: **Linux, Windows 95+, Solaris, xv6**

### Threading Model Comparison

| Model | Kernel Stacks | Concurrent Syscalls | Memory Use | Locking Needed | Used By |
|-------|--------------|--------------------:|-----------|---------------|---------|
| **Many-to-One (N-1)** | 1 (shared) | No — sequential only | Minimal | No | Simple embedded |
| **Many-to-Many (M-N)** | C (pool, P≥C) | Yes (up to C) | Medium | Yes | Old IRIX, HP-UX |
| **One-to-One (1-1)** | P (one per process) | Yes (full) | High | Yes | Linux, xv6, Windows |

---

## 15. Comparison Table: Kernel Architecture Designs

> **Tags:** `comparison table` `monolithic vs microkernel` `exokernel comparison` `pros cons tradeoffs`

| | Monolithic | Microkernel | Exokernel |
|---|---|---|---|
| **What's in kernel** | All services (fs, net, sched, mem, drivers) | Only isolation primitives | Only protection/multiplexing |
| **Fault containment** | FS bug can crash entire kernel | FS crash isolated from kernel | Up to each libOS |
| **Performance** | Fast — direct function calls | Slow — IPC overhead per service call | Fastest — direct HW access |
| **IPC mechanism** | Direct kernel function call | Message passing via kernel | Direct HW or minimal kernel call |
| **Example** | Linux, xv6 | Plan 9, Fuchsia/Zircon, FOS | MIT Exokernel (research) |
| **Complexity** | Large kernel codebase | Complex IPC design | Complex per-app libOS |
| **Aligns with** | **Performance, Sharing** | **Isolation, Protection** | **Performance, Protection** |

---

## 16. Pareto Frontier Analysis

> **Tags:** `pareto frontier` `pareto optimal` `safety vs performance` `ukernel on pareto` `monolith on pareto`
> `bad design` `dream design` `isolation tradeoffs`

```
        Safety
          ^
          |   ukernel ●   ← Reality 1: high safety, lower performance
          |                  (Pareto-optimal on safety axis)
          |
          |         ● Bad design (dominated: worse safety AND worse performance)
          |
          |                       ● monolith  ← Reality 2: lower safety, higher performance
          |                                      (Pareto-optimal on performance axis)
          |
          |                              ★ dream (unachievable: max both)
          +──────────────────────────────────→ Performance
```

- **Microkernel (ukernel)**: Pareto-optimal for safety — no design achieves better safety without losing performance
- **Monolith**: Pareto-optimal for performance — no design achieves better performance without losing safety
- **Neither dominates the other** → both are Pareto-optimal on the safety-performance frontier
- **Bad design**: Worse safety AND worse performance than both → not on frontier → avoid

---

## 17. Key Ideas Alignment

> **Tags:** `isolation` `multiplexing` `protection` `performance` `sharing` `key ideas` `alignment`

| Design Choice | Isolation | Multiplexing | Protection | Performance | Sharing |
|---------------|:---------:|:------------:|:----------:|:-----------:|:-------:|
| **Monolithic kernel** | Partial | ✓ | ✓ | ✓ (no IPC overhead) | ✓ |
| **Microkernel** | ✓ | ✓ | ✓ | ✗ (IPC cost) | |
| **Exokernel** | | ✓ | ✓ | ✓ (direct HW) | |
| **One-to-One threading** | ✓ | ✓ | | ✓ (concurrent) | |
| **Many-to-One threading** | | ✓ | | ✓ (simple) | ✓ |
| **File descriptors** | | ✓ | ✓ | | ✓ (pipes/shared FDs) |
| **Capability-based (Fuchsia)** | ✓ | | ✓ | | |

---

## 18. Performance Analysis

> **Tags:** `performance` `IPC overhead` `CDF` `syscall latency` `context switch cost`
> `microkernel latency` `message passing latency`

### Syscall Latency CDF by Architecture

| Architecture | Median Latency | Tail | CDF Shape |
|---|---|---|---|
| **Monolithic** | Low (direct call) | Short | Steep rise early; minimal tail |
| **Microkernel** | High (2x kernel crossings + IPC) | Long | Shifted right; longer tail from IPC variability |
| **Exokernel** | Lowest (direct HW, minimal kernel) | Very short | Steepest rise; very minimal tail |

### What a Microkernel Syscall CDF Looks Like:
- **X-axis**: Latency (µs)
- **Y-axis**: Fraction of calls ≤ that latency
- **Shape**: Bimodal — fast IPC (cached routes) at left peak; slow IPC (cache miss, server preempted) at right peak
- **Key insight**: Monolith CDF is entirely to the LEFT of microkernel CDF — monolith always faster for the same operation

### Many-to-One vs One-to-One Syscall Throughput CDF:
- **Many-to-One**: CDF rises fast but plateaus early (serialized → low throughput ceiling)
- **One-to-One**: CDF rises more slowly per request but achieves much higher total throughput (concurrent)

---

## 19. Granularity Analysis

> **Tags:** `granularity` `granularity spectrum` `kernel service granularity` `service decomposition`

### Granularity of Kernel Services

```
Fine ←──────────────────────────────────────────────────→ Coarse
 Every function    Service per       Subsystem      Everything
 is a server       resource type     (fs, net, mem)  in kernel
  (extreme µkernel) (FOS-style)      (typical µkernel) (monolith)

Pros of fine:
  - Maximum fault isolation
  - Hot-reload individual services
  - Security compartments

Cons of fine:
  - Extreme IPC overhead
  - Complex service discovery
  - Hard to maintain service composition
```

### Granularity of Kernel Stacks (Threading)

```
Fine (1-1) ←──────────────────────────→ Coarse (N-1)
One stack per process             One shared stack
  + concurrent syscalls              + simple locking
  + no waiting                       - serialized access
  - memory overhead                  - underutilizes CPU
```

---

## 20. Objective Analysis (SLOs)

> **Tags:** `SLOs` `service level objectives` `syscall latency SLO` `isolation SLO`
> `homogenous` `heterogenous` `microkernel SLO` `monolith SLO`

| SLO | Design Choice | Homogenous/Heterogenous |
|-----|--------------|------------------------|
| Syscall completes within X µs | Monolithic: easier to guarantee | **Homogenous** — same for all processes |
| FS crash does not affect process within T ms | Microkernel: guaranteed; monolith: not | **Homogenous** (micro) / **N/A** (mono) |
| Process receives syscall slot within Y ms | 1-1: guaranteed per process | **Homogenous** (1-1) / **Heterogenous** (M-N: depends on pool) |
| No unauthorized resource access | Fuchsia: per-capability; Linux: DAC | **Homogenous** (Fuchsia) / **Heterogenous** (Linux root vs user) |

**Implications:**
- Microkernel enables more **homogenous fault-isolation SLOs** (each service independently bounded)
- Monolith enables more **homogenous latency SLOs** (no IPC variance)
- Capability model (Fuchsia) enables **homogenous security SLOs** (every syscall checked uniformly)

---


---

## L06 — Virtual Memory I (Basics)

*([→ xv6 implementation for this lecture](<#L06 — Virtual Memory I (Basics) — xv6>))*


> **Tags:** `vm1` `L06` `lec6` `virtual memory` `VM` `paging` `segmentation` `address translation`
> `linear address` `logical address` `virtual address` `physical address` `v2p` `va to pa`
> `MMU` `memory management unit` `TLB` `translation lookaside buffer` `iTLB` `dTLB` `TLB flush`
> `page table` `page directory` `PDE` `PTE` `PPN` `VPN` `VFN` `PFN` `CR3` `CR0` `CR4`
> `two-level paging` `multi-level paging` `four-level paging` `PML4` `PDPT` `PML4E` `PDPTE`
> `IA-32e` `x86-64` `4KB page` `4MB page` `2MB page` `1GB page` `huge page` `superpage`
> `page size` `page frame` `frame` `bootstrapping paging` `entrypgdir` `KERNBASE`
> `PTE_P` `PTE_W` `PTE_U` `PTE_PS` `PTE_A` `PTE_D` `walkpgdir` `mappages` `setupkvm`
> `kvmalloc` `kinit1` `kinit2` `kalloc` `kfree` `freelist` `kmem` `kmap`
> `GDT` `LDT` `segment selector` `segment descriptor` `base limit flags` `DPL`
> `SEG_KCODE` `SEG_KDATA` `SEG_UCODE` `SEG_UDATA` `seginit` `lgdt` `STA_X` `STA_W` `STA_R`
> `CS DS SS ES FS GS` `EIP CS` `ESP SS` `page walk` `pagewalk overhead` `page table size`
> `pareto paging` `latency vs memory overhead` `swapping` `resource multiplexing`
> `protection` `isolation` `lazy allocation` `copy on write` `CoW`

> **Cross-reference:** Segmentation/GDT also appears in **x86.md** and **isolation.md** (ring-0 enforcement). This sheet focuses on the **paging mechanism**, **multi-level translation**, and the **xv6 boot-time VM bootstrap**. Lazy alloc / CoW / page faults are covered in **vm2.md** and **vm3.md**.

---

## 1. Why Virtual Memory? — The Four Goals

> **Tags:** `why virtual memory` `vm motivation` `vm goals` `isolation multiplexing protection`

- **Isolation** — each process sees its own address space; a buggy process can't read/clobber another's memory.
- **Resource multiplexing** — *one* physical address space appears as *many* virtual address spaces.
- **Masks / overcomes resource limitations** — virtual memory can be larger than RAM (swapping to disk).
- **Protection** — per-page R/W/X + user/supervisor flags enforced by the MMU.

### Key-idea alignment
| Goal | Maps to |
|---|---|
| Isolation | **Isolation** (per-process address space) |
| 1 phys → many virt | **Multiplexing** + **Sharing** (overcommit RAM, share pages) |
| Allocate > RAM | **Performance** (latency hiding via swap) + **Multiplexing** |
| R/W/X, user/supervisor | **Protection** |

---

## 2. The Big Picture: x86 Address Translation Pipeline

> **Tags:** `x86 translation pipeline` `logical linear physical` `selector offset` `two-stage translation`

```
         Selector                Linear                  Physical
CPU ──── Offset ──► Segment ──── Address ──► Page ──── Address ──► RAM
         (Logical)  Translation   (Virtual)   Translation   (PA)
```

- **Logical address** = Selector : Offset (output of CPU).
- **Linear address** = output of segmentation = **Virtual address** (this is the address userspace believes it's using).
- **Physical address** = output of paging = actual DRAM index.
- In modern x86 OSes (incl. xv6 *post-boot*), segmentation is effectively a no-op (flat 0..0xFFFFFFFF segments) → all the heavy lifting is paging.

---

## 3. Segmentation vs. Paging

> **Tags:** `segmentation vs paging` `seg vs page` `pareto segmentation` `flat segments`

### Comparison Table

| Aspect | Segmentation | Paging |
|---|---|---|
| Granularity | Variable-size segments | Fixed-size pages (4KB typical) |
| Translation overhead | Low (just base+offset add) | Higher (multi-level table walk) |
| Fragmentation | **External** fragmentation (variable holes) | **Internal** only (last-page slack) |
| Address-space size | Limited by segment ranges | Easily 32-bit / 48-bit / 64-bit |
| Phys mem multiplexing | Coarse, contiguous | Fine, scattered |
| Protection granularity | Per-segment | Per-page |
| Sharing | Awkward | Natural (multiple PTEs → 1 frame) |

### Pareto / design winner
- **Paging dominates segmentation** on the (fragmentation, isolation, protection, sharing) axes.
- Segmentation only wins on **translation latency** — but TLBs largely close that gap.
- Modern x86: paging is the **pareto-optimal** mechanism; segmentation is kept around for legacy / ring-level use only.
- **Slide takeaway**: *"Paging: better isolation AND protection mechanism."*

### Key-idea alignment
- Segmentation → **Performance** (cheap translation), weak on **Isolation/Sharing**.
- Paging → **Isolation**, **Protection**, **Multiplexing**, **Sharing**; pays cost in **Performance** (mitigated by TLB).

---

## 4. Segmentation Mechanics (x86 legacy + xv6 minimal use)

> **Tags:** `GDT` `LDT` `global descriptor table` `local descriptor table` `segment descriptor`
> `segment selector register` `CS DS SS ES FS GS` `STA_X STA_W STA_R` `DPL` `SEG_ASM`

### Tables
- **GDT** (Global Descriptor Table) — list of segments visible to all processes.
- **LDT** (Local Descriptor Table) — per-process segments. Almost unused in modern OSes.

### Each GDT entry (segment descriptor) contains
- **Base** — physical address where segment starts.
- **Limit** — last valid address in segment.
- **Permissions** — R / W / X (e.g. STA_X executable, STA_R readable, STA_W writable).
- **DPL** (Descriptor Privilege Level) — ring 0 (kernel) vs ring 3 (user).

### Segment registers (which selector applies?)
- `EIP` uses **CS** (Code Segment).
- `ESP` uses **SS** (Stack Segment).
- Data ops use **DS** (Data Segment).
- ES / FS / GS — extra/thread-local segments.
- CS is loaded via `jmp` / `iret` / IDT entries on interrupts.

### xv6 GDT setup

Bootloader (`bootasm.S`) — minimal flat GDT:
```asm
SEG_NULLASM
SEG_ASM(STA_X|STA_R, 0x0, 0xffffffff)   # code seg
SEG_ASM(STA_W,       0x0, 0xffffffff)   # data seg
```

Kernel (`seginit` per-CPU):
```c
c->gdt[SEG_KCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_KERN);
c->gdt[SEG_KDATA] = SEG(STA_W,       0, 0xffffffff, DPL_KERN);
c->gdt[SEG_UCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_USER);
c->gdt[SEG_UDATA] = SEG(STA_W,       0, 0xffffffff, DPL_USER);
lgdt(c->gdt, sizeof(c->gdt));
```
- **Base = 0, Limit = 0xFFFFFFFF** → flat, segmentation effectively bypassed; only purpose is to switch DPL between ring 0 and ring 3.

---

## 5. Paging Basics — 32-bit Two-Level

> **Tags:** `paging basics` `two level paging` `page directory` `page table` `Dir Table Offset`
> `10 10 12` `4KB page` `1024 entries` `4 byte PTE`

### Address breakdown (x86 32-bit, 4KB pages)
```
 Linear (Virtual) Address (32 bits)
 ┌───────┬───────┬─────────┐
 │  Dir  │ Table │ Offset  │
 │ 10b   │ 10b   │  12b    │
 └───┬───┴───┬───┴────┬────┘
     │       │        │
     │       │        └──► 12-bit offset into 4KB physical frame
     │       └──► index into Page Table (PT)  → PTE
     └──► index into Page Directory (PD)      → PDE
```

### The structures
- **CR3** — control register holding **physical address** of current Page Directory (the "root" of the page table tree). Loaded via `mov %eax, %cr3`. Switching CR3 changes the address space and **flushes the TLB**.
- **Page Directory (PD)** — 1024 × 4-byte = **4KB** (fits in one frame). Each entry = **PDE**.
- **Page Table (PT)** — 1024 × 4-byte = **4KB**. Each entry = **PTE**.
- Both PDE and PTE hold a **20-bit PPN** (physical page number) + 12 bits of flags.

### Translation steps (page walk, 2 memory accesses)
1. CR3 holds PA of Page Directory.
2. Use top 10 bits ("Dir") to index PD → fetch PDE.
3. PDE.PPN points to the Page Table (in physical memory).
4. Use next 10 bits ("Table") to index PT → fetch PTE.
5. PTE.PPN || (last 12 "Offset" bits) → final physical address.

### PDE / PTE Flag Bits
| Bit | Name | Meaning |
|---|---|---|
| 0 | **P** | Present (in memory) |
| 1 | **W** | Writable |
| 2 | **U** | User-accessible (else kernel-only) |
| 3 | WT | Write-through caching |
| 4 | CD | Cache disabled |
| 5 | **A** | Accessed (set by HW on read/write) |
| 6 | **D** | Dirty (PTE only — set on write) |
| 7 | **PS** | Page Size: 0 = 4KB (use PT), 1 = 4MB superpage (skip PT) |
| 8 | G | Global (not flushed on CR3 reload) |
| 9–11 | AVL | Available for OS use |
| 12–31 | PPN | Physical Page Number |

### Q: Is CR3 a virtual or physical address?
- **Physical.** Required, otherwise translating the page table would itself need translation → infinite regress / chicken-and-egg.
- The "How do we make the page table before paging is set up?" answer: build it as a static array **inside the kernel image** (xv6's `entrypgdir`).

---

## 6. Single-Level vs. Multi-Level Paging — Design Tradeoffs

> **Tags:** `single level paging` `multi level paging` `page table size` `4MB page` `superpage`
> `pareto paging` `memory overhead` `latency overhead` `paging tradeoff`

### Page-size options (x86)
- **32-bit:** 4KB, 4MB.
- **64-bit:** 4KB, 2MB, 1GB.

### Structural variants (32-bit)
| Design | Bit split | Levels | Single-PT size if fully populated | Walk cost |
|---|---|---|---|---|
| 1-level, 4MB pages | 10 \| 22 | 1 | 4KB (1024 PTE × 4B) | 1 mem access |
| 1-level, 4KB pages | 20 \| 12 | 1 | 4MB (2²⁰ × 4B) **per process** | 1 mem access |
| 2-level, 4KB pages | 10 \| 10 \| 12 | 2 | 4KB PD + only-needed PTs | 2 mem accesses |

### Tradeoffs

| Design | Pros | Cons | Use case |
|---|---|---|---|
| Single-level (10/22, 4MB pages) | Tiny PT; 1-lookup walk; fast translation | **Internal fragmentation** (4MB granularity — 8–12MB minimum waste) | Kernel boot, hugepage workloads, DBs |
| Single-level (20/12, 4KB pages) | 1-lookup walk; fine-grained | **Huge per-process PT (4MB)** even for tiny processes | Few large processes |
| Two-level (10/10/12, 4KB) | Sparse PT (allocate PTs on demand); small footprint for tiny processes | 2-lookup walk; 2× translation latency | Default modern OS |

### Pareto Frontier (Latency vs. Memory Overhead)

```
Latency
overhead
  ▲
  │   ● 2-level (low mem, higher latency)
  │     ╲
  │      ╲___
  │          ╲___
  │              ● 1-level 4KB (low latency, high mem)
  │
  │ ● dream                     ✗ Bad design (high both)
  └──────────────────────────────► Memory overhead
```
- **2-level** and **1-level (4KB)** both lie on the pareto frontier (different operating points).
- "Dream" point (low latency + low memory) is **unachievable** without extra mechanism (TLB caches, hugepages, hashed PTs).
- "Bad design" = high both → strictly dominated → never pareto optimal.
- **Takeaway slide:** *"Design choices often shift the bottleneck in the system."* (Going from 2-level → 1-level shifts cost from latency → memory.)

### Granularity analysis (page size)
| Page size | Pros | Cons |
|---|---|---|
| Small (4KB) | Low internal fragmentation; fine protection; precise swapping | Many TLB entries needed; bigger PTs; more page faults |
| Medium (2MB / 4MB) | Few TLB entries (better hit rate); smaller PTs; faster walks | Wasted memory if process is small; coarse protection |
| Huge (1GB) | Minimal TLB pressure for huge mappings (DBs, JVMs) | Massive internal frag; allocation difficult |

- **Sweet spot** for general-purpose: 4KB default + opt-in hugepages (transparent hugepages on Linux).

### Key-idea alignment
- More levels → favors **Multiplexing** (sparse address spaces) and **Isolation** (per-process tables) at cost of **Performance**.
- Larger pages → favors **Performance** (TLB) at cost of **Multiplexing** efficiency.

---

## 7. 64-bit Paging — Four-Level (IA-32e)

> **Tags:** `four level paging` `x86-64 paging` `IA-32e` `PML4` `PDPT` `48 bit virtual`

### Address breakdown (4KB page mode, 48-bit canonical virtual)
```
 ┌──────┬──────────┬──────────┬───────┬──────────┐
 │ PML4 │ Dir Ptr  │ Directory│ Table │  Offset  │
 │  9b  │   9b     │   9b     │  9b   │   12b    │
 └──┬───┴────┬─────┴────┬─────┴───┬───┴────┬─────┘
    │        │          │         │        │
    │        │          │         │        └► 4KB page offset
    │        │          │         └► PT  →   PTE
    │        │          └► PD       →   PDE  (PS=0)
    │        └► PDPT     →   PDPTE
    └► PML4  →   PML4E
   (CR3 → PML4 base)
```
- **9 bits per level** because 4KB / 8B-per-entry = 512 entries = 2⁹.
- Page-table entries are now **8 bytes** (vs 4 in 32-bit).
- Page sizes available: **4KB, 2MB, 1GB**.
  - 2MB: stop walk at PD level (PDE.PS=1).
  - 1GB: stop walk at PDPT level (PDPTE.PS=1).
- **Walk cost:** up to 4 memory accesses without TLB (vs 2 in 32-bit).
- "Same idea, more levels of indirection."

### CDF — page-walk latency

```
 P[walk_time ≤ x]
   1 │              ────────
       │           ╱        ← slow tail: full 4-level walk + cache misses
       │     ╱──╱
   .9 │   ╱
       │  │   ← TLB hits (≈99% of accesses, ~1 cycle)
   0 │_/
       └──────────────────►  walk time
        0    ~few ns       hundreds of ns
```
- Bimodal: TLB hit (~1 cycle) vs TLB miss (≈ N memory loads, can be 100+ cycles even with page-walk caches).
- TLB hit rate is what makes paging viable.

---

## 8. The MMU and TLB

> **Tags:** `MMU` `memory management unit` `TLB` `translation lookaside buffer` `iTLB` `dTLB`
> `TLB flush` `TLB miss` `cr3 flush` `address space switch`

- **MMU** = hardware that performs VA → PA translation on every memory access.
- **TLB** = hardware cache of recent VA → PA translations (and their flags).
- **Optimizations:**
  - **iTLB** caches *instruction*-fetch translations.
  - **dTLB** caches *data*-access translations.
  - PCID / ASID tags entries with address-space ID → avoid full flush on context switch.
- **TLB flush triggers:**
  - `mov ... %cr3` — full flush (most common; happens on process switch).
  - `invlpg <addr>` — flush single entry.
  - PTE update by the kernel (kernel must `invlpg` to ensure CPU sees new mapping).
- **Why TLB flushes hurt:** every access becomes a cache miss + page walk for a while → cold-start penalty after `fork`, `exec`, context switch.

### Key-idea alignment
- TLB embodies **Performance** in a system that otherwise pays huge cost for **Isolation**.

---

## 9. Bootstrapping Paging — The Chicken-and-Egg

> **Tags:** `bootstrap paging` `chicken and egg` `entrypgdir` `kernbase` `4MB superpage`
> `enable paging` `cr0 PG` `cr4 PSE` `V2P` `P2V`

### Problem
1. To translate VAs, hardware needs a PD pointed to by CR3.
2. CR3 holds a **physical** address.
3. Kernel runs at virtual addresses linked above `KERNBASE` — but at boot, paging is OFF, so it's executing at low PAs.
4. Need to enable paging *while the EIP transitions from low PA to high VA without breaking*.

### Solution (xv6 `entry`/`main.c`)
- Hand-craft a static page directory **at compile time**:
```c
__attribute__((__aligned__(PGSIZE)))
pde_t entrypgdir[NPDENTRIES] = {
  // Map VA's [0, 4MB)              → PA's [0, 4MB)   (identity)
  [0]                  = (0) | PTE_P | PTE_W | PTE_PS,
  // Map VA's [KERNBASE, KERNBASE+4MB) → PA's [0, 4MB) (high-half)
  [KERNBASE>>PDXSHIFT] = (0) | PTE_P | PTE_W | PTE_PS,
};
```
- Uses **PTE_PS = 4MB superpages** → only the PD is needed (no PTs).
- Two PDEs both point to PA `[0, 4MB)`:
  - Identity entry **[0]** keeps low-VA EIP working **the instant after** paging is turned on.
  - High-half entry **[KERNBASE>>PDXSHIFT]** lets the kernel jump into its linked addresses.
- Enable paging:
```asm
movl  $(V2P_WO(entrypgdir)), %eax  # CR3 wants physical
movl  %eax, %cr3
movl  %cr0, %eax
orl   $(CR0_PG | CR0_WP), %eax     # turn on paging + write-protect
movl  %eax, %cr0
```
- After enabling: jump to a high-VA symbol → from now on EIP runs in the high-half mapping. Once stable, the identity [0] mapping is removed.

### ENTRYPGDIR diagram
```
Virtual                  Physical
0xFFFFFFFF                0xFFFFFFFF
   │                          │
   │  ┌──[KERNBASE+4MB]──┐   │
   │  │   4MB (kernel)   │───┐
0x80000000────────────────   │
   │                          │  ┌─[0..4MB]─┐
   │                          │  │   4MB    │
   │  ┌──[0..4MB]─────────┐  │  │ (BIOS+   │
   │  │   4MB identity    │──┴──┤  kernel) │
0x00000000                0x00 └──────────┘
```

---


---

## L07 — Virtual Memory II (Lazy / CoW)

*([→ xv6 implementation for this lecture](<#L07 — Virtual Memory II (Lazy / CoW) — xv6>))*


> **Tags:** `vm2` `L07` `lec7` `VMM finale` `tips and tricks` `lazy design` `eager vs lazy`
> `copy on write` `CoW` `cow fork` `copy-on-write fork` `PTP dedup` `page table dedup`
> `page table page deduplication` `dedup` `logical permissions` `physical permissions`
> `R W P bits` `permission bits` `lazy allocation` `demand paging` `on demand allocation`
> `lazy zeroing` `zero page` `single zero page` `zero filled page` `zero-fill-on-demand`
> `ZFOD` `shared memory` `shared library` `libc shared` `vsyscall` `vdso`
> `memory mapped files` `mmap` `mmap demo` `swapping` `swap to disk` `paging to disk`
> `memory oversubscription` `overcommit` `eager fork` `on-demand fork` `OnDemandFork`
> `EuroSys21` `Snowflock` `Kaleidoscope` `VM cloning` `microsecond fork`
> `kalloc != malloc` `walkpgdir` `mappages` `copyuvm` `freelist` `kmem` `kfree`
> `TLB flush on cow` `invlpg cow` `trap 14` `page fault trap` `T_PGFLT`
> `pgfault handler` `xv6 cow lab` `lab2` `n != 2` `orphans` `reparent to init`
> `pipe read write cow` `kernel writes to user` `reference count` `refcount` `pgrefcnt`
> `eager allocation` `complexity O n` `deferred complexity` `amortized cost`

> **Cross-reference:** Foundational paging mechanism, MMU, TLB, multi-level structure, and bootstrapping covered in **vm1.md**. CoW lab implementation details (refcount tables, fork/exit handling) covered in **vm3.md**. Page-fault trap dispatch covered in **isolation.md** and **kernel_org.md**. This sheet focuses on **lazy design as a system-design discipline** and the family of VM tricks that flow from it.

---

## 1. The Lazy Design Principle — The Core Idea

> **Tags:** `lazy design` `lazy vs eager` `defer work` `pay on use` `amortized work`
> `do nothing now do later` `fork now copy later` `optimistic`

- **Eager** (do it now): pay full cost up front, predictable latency, possibly wasted work.
- **Lazy** (do it later, only if needed): defer work until *forced* by a trigger (typically a trap/page fault). If the trigger never fires, the work is *never done*.
- The OS designer's mantra: **"Don't pay for what you don't use."**
- Triggers in VM-land are almost always **page faults (trap 14)** — the MMU itself raises the alarm when the lazy state needs concretizing.
- Three things to think about for *every* lazy scheme:
  1. **Trigger** — what fault/event forces materialization?
  2. **Per-resource bookkeeping** — what extra state is needed (e.g. refcounts)?
  3. **Cleanup / corner cases** — how does the last consumer know it's last?

### Eager vs Lazy — The Universal Tradeoff

| Aspect | Eager | Lazy |
|---|---|---|
| Up-front latency | High (do all the work) | Low (record intent only) |
| Steady-state latency | Predictable | Spiky (faults amortize work) |
| Wasted work | Possibly large (build state nobody uses) | None |
| Bookkeeping complexity | Minimal | Higher (per-page state, refcounts) |
| Cleanup correctness | Trivial | Tricky (orphans, last-ref) |
| Failure mode | OOM at fork() | OOM later, mid-execution |

### Key-idea alignment
- Lazy designs primarily serve **Performance** (avoid wasted work) and **Multiplexing** (overcommit the resource).
- They generally cost extra **Protection** machinery (must trap & validate on every access) and **Sharing** state (refcounts).

### CDF — work-per-operation under lazy vs eager

```
P[cost ≤ x]
  1 │     ████──── lazy: most ops are cheap, rare big spikes (faults)
      │   ╱
      │  ╱
      │ │     ────── eager: every op pays the same big cost
      │ │   ╱
   0 │_│ /
      └────────────────► cost
```
- Eager → narrow CDF (deterministic).
- Lazy → bimodal: cheap path + tail of fault-handling spikes.
- SLO consequence: **lazy hurts p99/p99.9**, helps the mean.

---

## 2. Copy-on-Write Fork — The Canonical Lazy Design

> **Tags:** `cow fork` `copy on write fork` `fork now copy later` `parent child sharing`
> `cow page fault` `write fault` `cow trap` `do_cow` `pgfault cow`

### The question
- `fork()` creates a child with an identical address space. Naive xv6 implementation: walk parent PT, `kalloc` a fresh frame for *every* mapped page, `memmove` it (`copyuvm` in `vm.c`).
- **Naive cost:** O(N_pages) for **every** fork — even though ~95% of forks are immediately followed by `exec` (most pages are *thrown away* before they're written).

### The CoW idea
1. On `fork()`, **don't** copy any user pages. Both parent and child PTs point to the *same* physical frames.
2. Mark all those PTEs **read-only** (clear `PTE_W`).
3. Either process attempting a write triggers a **page fault** (write-protection violation).
4. Fault handler: `kalloc` a fresh frame, `memmove` the original into it, install it in *the faulting process's* PT with `PTE_W` set, drop the refcount on the original, return.

### Slide takeaway diagram
```
Before fork:                 After fork (CoW):
parent ─► [0xcafe, 0xbeef]   parent ─►┐
                                       ├──► [0xcafe, 0xbeef]   (R only)
                             child  ─►┘

After child writes 0x05FE:
parent ─► [0xcafe, 0xbeef]
child  ─► [0xcafe, 0x05FE'] ← new frame, RW
```

### Complexity
- **Up-front (fork):** O(#PTEs) just to flip `PTE_W` and bump refcounts (no page copy).
- **Deferred (per write fault):** O(1) per page actually written.
- **Total amortized:** O(#pages_written), which is `≤` O(#pages_mapped) — strictly better than eager.

### Comparison: Eager Copy vs CoW

| Aspect | Eager `copyuvm` | CoW fork |
|---|---|---|
| `fork()` latency | O(N) memcpys | O(N) PTE flips (faster) |
| Memory at fork | 2× | 1× (shared) |
| Cost per write | 0 (already private) | One trap + memcpy |
| `fork-then-exec` | Wastes all the work | Free (child unmaps before any write) |
| Bookkeeping | None | Per-frame refcount, write-protect bookkeeping |
| Works for read-only pages? | Always copies them anyway | Pages stay shared forever (free memory!) |

### Pareto / design winner
- CoW **dominates** eager for almost all workloads (fork, fork-exec, server pre-fork pools).
- Only loss case: a process that *immediately* writes every page. Then CoW pays the trap+copy *plus* the fork-time PTE walk → strictly worse.
- → CoW is **pareto-optimal** for the typical fork distribution but **not** dominant in *all* workloads.

### Key-idea alignment
- **Sharing** (multiple PTEs → one frame) + **Performance** (skip the copy) + **Multiplexing** (many forked processes fit in same RAM until they diverge).
- Pays cost in **Protection** complexity (must trap + validate every write).

---

## 3. Logical vs. Physical Permissions

> **Tags:** `logical permissions` `physical permissions` `is it legal vs will it trap`
> `read only mapping` `permission bits R W P` `cow trap mechanism`

### The distinction (from the slides — important conceptually)
| Type | Question | Stored in |
|---|---|---|
| **Logical** | "Is it *legal* for the program to access this memory?" | OS-side bookkeeping (the *intent*) |
| **Physical** | "Will the CPU give me a trap on this access?" | The PTE flag bits actually loaded into the MMU |

- These can **diverge by design** — that's the trick.
- For CoW: logically the page is **writable** (the program *should* be able to write it), but physically the PTE is **read-only**, so the write traps and the kernel can do the copy "behind the scenes."
- For zero-fill-on-demand: logically writable, physically not even *present* — first access traps and the page is materialized.

### Why it matters
- The kernel uses the PTE as a *programmable trap source*, not just an enforcement mechanism.
- General pattern: **temporarily lie to the hardware** about permissions to get a trap on the action you care about, then fix up state and resume.

---

## 4. Page-Table-Page (PTP) Deduplication

> **Tags:** `PTP dedup` `page table dedup` `share page tables` `share PTs across processes`
> `cow page directory` `cow page table` `cow PT page` `dedup PT pages`

### The next-level lazy
- After CoW dedupes physical *frames*, the question: do we still need a separate **page table** per process?
- If two processes have identical mappings, their PT pages are byte-identical → dedupe *those* too.
- Same recipe: mark the **PD entry** (or PT entry pointing to a PT) as read-only, fault on the first divergent write, lazily allocate a private PT page, fix up.

### How permissions propagate (the trick)
- Page-walk perms are **most-restrictive-wins** (HW ANDs perms across levels for the access type — but here we're flipping the *write* bit at higher levels).
- If PD says "R only" → all 1024 entries inherit R-only on writes → any write through that PD traps.
- After fault: kernel must un-share both the PT page (kalloc/memcpy a new PT) **and** the offending data page (the original CoW step), then update its own PD entry to point at the new PT.

### Worked slide example (PT1, PT2 shared between Process 1 & 2)

| Stage | PD1 | PT1 (R/W) | PT2 (R/W) | P1 | P2 | P3 |
|---|---|---|---|---|---|---|
| Initial fork (CoW + PTP dedup) | shared | R only | R only | R only | R only | R only |
| Process 2 writes P1 → trap | – | clone PT1' | – | clone P1' | – | – |
| After fix-up | PD1' for proc2 | PT1' RW for P1' | – | – (proc1 still R) | – | – |

### TLB cost on a write to P1 (slide quiz answer = **1**)
- The fault handler updates **one PTE** (the one for P1 in proc 2's PT1').
- → **One** `invlpg` is needed for that specific virtual page.
- Updating the PT pointer in the PD does not require a TLB flush of every entry (the TLB caches *final* translations, not intermediate ones — page-walk caches do, but invalidating one VA suffices).

### Pareto / Granularity of dedup

| Granularity of CoW | Up-front fork cost | Memory saved | Complexity |
|---|---|---|---|
| No dedup (eager) | High (copy everything) | None | Lowest |
| Frame-level CoW only | O(#PTEs) | Per-frame | Medium |
| Frame + PTP dedup | O(#PD entries) | Per-frame + per-PT (~4KB each) | Highest |

- **PTP dedup is the pareto-optimal point** when fork is on the hot path *and* address spaces are large (lots of PT pages).
- Diminishing returns: most apps have few PT pages compared to data pages.

---

## 5. CoW Engineering — What to Track

> **Tags:** `cow engineering` `refcount` `pgrefcnt` `per physical page state`
> `corner cases` `orphans` `out of memory` `cleanup` `fork chain` `n != 2`

### Per-physical-page state
- Need a way to know: "**how many** PTEs across **all** processes still point at this frame?"
- Standard answer: a **reference count array** indexed by PFN (one byte / int per physical page).
- xv6 doesn't have this in the base code — Lab 2 makes you add `pgrefcnt[]` (or similar).

### When to copy (fault handler logic)
```
on write_fault(va):
    pa = walk(va)
    if pgrefcnt[pa] == 1:         # last reference -> just give it back
        set PTE_W; invlpg(va); return
    new = kalloc()
    memcpy(new, pa)
    pgrefcnt[pa]--
    pgrefcnt[new] = 1
    *pte = new | PTE_W | PTE_U | PTE_P
    invlpg(va)
```

### When to free (kfree logic)
- `kfree` becomes "decrement refcount; if refcount hits 0, push onto freelist."
- This is the **biggest invariant change** to xv6 from Lab 2.

### Corner cases (slides + lab list)
- **Children / grandchildren** — chain of forks: `n != 2`. Pages can be shared by 3+ processes.
- **Orphans** — parent dies, child reparented to `init`. Refcounts must NOT depend on parent-child pointers.
- **OOM during CoW fault** — `kalloc` returns 0 in the fault handler. Must kill the process *and* leave the still-shared page intact for the other readers.
- **Concurrent fork+write race** — two processes faulting on the same page simultaneously. Need a lock around the refcount + PTE update.
- **`exec` after CoW fork** — exec replaces the address space; must drop refs cleanly.
- **Kernel writing to user memory** (the **syscall pitfall**) — `read`, `write`, `pipe`, etc. The kernel is *not* a userspace write, so it bypasses the MMU's `PTE_W` check on certain paths. Must manually trigger CoW from inside the syscall handler.

---

## 6. Lazy Allocation / Demand Paging

> **Tags:** `lazy allocation` `demand paging` `on demand allocation` `sbrk lazy` `lazy sbrk`
> `oversubscription` `overcommit` `pgfault on first access` `materialize on touch`

### The idea
- `sbrk(n)` / `mmap` / process startup don't need to *actually* allocate physical frames immediately.
- Just **bump the process's logical size** (e.g. `myproc()->sz += n`); leave the PTEs **invalid (P=0)**.
- First touch of any of those VAs → page fault (P=0) → kernel `kalloc`s, zeroes, installs the PTE, returns.

### Why
- Programs routinely `sbrk` huge amounts (heap headroom) but never touch most of it.
- Allows **overcommit**: total VA across all processes > physical RAM, as long as live working set fits.

### Comparison

| | Eager allocation | Demand paging |
|---|---|---|
| `sbrk(big)` latency | Slow (allocate now) | Instant (just bump sz) |
| Phys mem at sbrk | Full | Zero |
| First touch latency | 1 memory access | Page fault → ~µs |
| Can overcommit? | No (fail at sbrk) | Yes |
| OOM timing | Predictable (fail at sbrk) | Unpredictable (mid-execution) |

### Granularity (page size)
- Smaller page = finer-grained lazy materialization, more faults, more bookkeeping.
- Bigger page = fewer faults but each one materializes more memory.
- → most OSes still use 4KB for the *lazy* path, even with huge pages elsewhere.

### Key-idea alignment
- **Multiplexing** (overcommit) + **Performance** (skip allocation for unused pages).
- Cost: **Protection** complexity in the page-fault handler must distinguish "lazy not-yet-materialized" from "actual access violation."

---

## 7. Lazy Zeroing & The Single Zero Page

> **Tags:** `lazy zeroing` `zero fill on demand` `ZFOD` `single zero page`
> `shared zero frame` `BSS lazy` `kfree poisons` `pages zeroed by default`

### Lazy zeroing
- For **security** (don't leak previous owner's data), every fresh user page must be zeroed.
- Eager: zero in `kalloc`. Lazy: only zero when actually handed to a process.
- xv6's `kfree` already pre-poisons (memset 1) for debugging — you can flip that to memset 0 to amortize zeroing on free instead of alloc.

### The single zero page (ZFOD)
- Take it further: have **one** global all-zero frame in the kernel. Map every newly-allocated VA to *that frame*, **read-only**.
- All processes' "fresh" pages cost zero physical memory until first write.
- On write: classic CoW fault → `kalloc` a fresh page, memset(0), install RW.

### Granularity tradeoff
| Sharing depth | Memory saved | Cost |
|---|---|---|
| Per-process zero pool | Low | Low complexity |
| **One global zero frame** | High | Slightly more work in fault handler |
| No zero frame (zero on alloc) | None | Eager zeroing CPU cost |

### CDF — first-touch latency
```
P[t ≤ x]
  1│           ────────
    │      ╱            ← write fault: kalloc + memset → page → ~µs
    │   ╱
    │  │  ← read of a VFN backed by the zero frame: ~1 ns (TLB hit)
   0│ /
    └──────────────────►
```
- Reads of zero-backed pages are *as fast as any TLB hit* — almost free.
- Writes pay one fault.

---

## 8. Shared Memory & Shared Libraries

> **Tags:** `shared memory` `shared library` `libc shared` `dynamic linking`
> `read only sharing` `HPC shared memory` `mmap shared` `proc maps libc`

- Multiple virtual pages (in different processes) can map the **same physical frame** intentionally.
- Use cases:
  - **Shared libraries** (libc, libm, ld.so) — read-only & executable; one copy of libc in RAM serves *every* process.
  - **HPC distributed simulation** — all-gather into a shared region so worker processes/threads see one merged data structure.
  - **IPC** (System V shm / POSIX `shm_open` / `mmap(MAP_SHARED, fd)`).
- In Linux, observable via `cat /proc/<pid>/maps`:
  ```
  33b0c00000-33b0d8a000 r-xp /lib64/libc-2.12.so   ← code, R+X, shared
  33b0d8a000-33b0f8a000 ---p /lib64/libc-2.12.so   ← guard
  33b0f8a000-33b0f8e000 r--p /lib64/libc-2.12.so   ← rodata
  33b0f8e000-33b0f90000 rw-p /lib64/libc-2.12.so   ← data, CoW per-proc
  ```

### xv6 limitation (recap from vm1)
- xv6's freelist stores metadata *inside* the free pages → **no refcount** → cannot share frames cleanly. Lab 2 fixes this.

### Key-idea alignment
- **Sharing** is the primary key idea, full stop.
- Shared libraries also serve **Performance** (TLB hits across processes — same PA can hit on the same iTLB entry on architectures with PCIDs/global pages).

---

## 9. Memory-Mapped Files

> **Tags:** `mmap` `memory mapped files` `mmap demo` `file backed memory` `MAP_PRIVATE`
> `MAP_SHARED` `page cache` `read write through mmap`

- Map a file's bytes directly into a process's address space. Reads/writes to that VA become reads/writes of the *file*.
- Uses **demand paging** under the hood: PTE is initially invalid; on access the kernel reads the appropriate disk block into a frame and installs the mapping.
- **MAP_SHARED**: writes go back to the file (and to other mappers).
- **MAP_PRIVATE**: CoW — first write privatizes a copy.

### Why it's a big deal
- No `read()`/`write()` syscall overhead for hot-path access.
- The OS page cache becomes the file cache *automatically*.
- Replaces "load the whole file then mutate" with "stream pages on demand."

### Key-idea alignment
- **Multiplexing** (file as backing store) + **Sharing** (page cache shared across processes) + **Performance** (no syscall in steady state).

---

## 10. Memory Backing & Swapping (Oversubscription)

> **Tags:** `swapping` `swap to disk` `paging to disk` `memory backing` `oversubscription`
> `overcommit` `disk as RAM extension` `swap page out` `swap page in`

### Two ways physical state can live "outside RAM"
| Mechanism | Direction | Use case |
|---|---|---|
| **Swapping** | RAM → disk (and back on fault) | Cold pages evicted to recover RAM under pressure |
| **Memory mapping** | Disk → RAM (lazily, on fault) | File contents accessed via VA |

### Swapping mechanics (sketch)
- Pick a victim page (LRU-ish), write its contents to a **swap area** on disk, mark its PTE `P=0` with the swap slot encoded in the spare bits.
- On future access → page fault → kernel reads back from swap, allocates a frame, installs PTE, retries.

### Performance / SLO impact
- A swap-in costs **~1 ms** (HDD) to **~50 µs** (NVMe) — *thousands* of times slower than a RAM access.
- An app that "thrashes" (working set > RAM) sees throughput collapse — this is why the **CDF tail explodes** under memory pressure.

### CDF — memory access under pressure
```
P[t ≤ x]
  1 │           ────────────
      │       ╱       ← swap-in on disk: ms!
      │     ╱
      │    │  ← TLB miss + walk: ~100 ns
   .99│   ╱
      │  ┃   ← TLB hit: ~1 ns
      │ ┃
   0  │┃
      └────────────────────► t (log scale)
```
- Knees: TLB-hit / TLB-miss / page-fault-from-RAM / **page-fault-from-disk** (the killer).

### SLO implication
- Latency-sensitive workloads (Redis, low-latency trading): often **disable swap entirely** (`swappiness=0`) — accept OOM-kill rather than tail-latency disasters.
- Throughput workloads (batch jobs, ML training): tolerate swap; use it to fit larger working sets.
- **Heterogeneous SLO**: same machine, different processes want opposite policies → need cgroup-level memory controls.

### Key-idea alignment
- **Multiplexing** (RAM appears bigger than it is) at extreme cost to **Performance**.

---

## 11. The Whole Lazy-VM Toolbox (Slide Recap)

> **Tags:** `vm tips and tricks` `lazy vm tricks` `vm trick list`

| Trick | Trigger | What's deferred | Memory savings |
|---|---|---|---|
| Copy-on-Write fork | Write fault on shared page | Frame copy | Pages never written |
| PTP dedup | Write fault through dedup'd PT | PT page copy | 4KB per shared PT page |
| Demand paging | First touch (P=0 fault) | Frame allocation | Untouched VAs |
| Lazy zeroing | First write to zero page | Memset+kalloc | Read-only zero VAs |
| Single zero page | First write | One frame for all zero VAs | Huge for fresh BSS/heap |
| Shared library | n/a (eager but shared) | Multiple copies of libc | (N−1) × libc size |
| Memory-mapped file | First access to mapped VA | Disk read | Untouched file regions |
| Swapping | Access to swapped-out page | Loss of RAM | Cold pages on disk |
| Oversubscription | Combination of above | Allocating physical frames eagerly | Up to total VA — RAM ratio |

---

## 12. Research Perspective (slides — open your minds)

> **Tags:** `snowflock` `kaleidoscope` `on demand fork` `OnDemandFork` `eurosys`
> `vm cloning` `microsecond fork` `vm research`

- **Snowflock (EuroSys '09, Test-of-Time '23)** — "fork a VM in under a second to a networked cluster." Uses on-demand paging + CoW + selective page transfer. Demonstrates lazy design at *cluster* granularity.
- **Kaleidoscope (EuroSys '11)** — efficient stateful VM replication via "VM state coloring." Same ideas applied to live migration / elasticity.
- **On-Demand Fork (EuroSys '21)** — drop-in replacement for `fork()` that performs **PTP CoW** (the slide example you saw). For 1 GB process: **65× fork speedup**, 59-226% throughput improvement, 99% reduction in fork-blocking time. Motivation: large-memory apps (databases, ML) had `fork()` latency dominated by PT copy.
- Theme: **the longer you can stay lazy, the bigger the win.** PT-page CoW is just CoW one level up the indirection chain; same idea, bigger payoff.

---

## 13. Common Pitfalls / Exam Gotchas

> **Tags:** `cow gotchas` `lazy gotchas` `vm trick questions`

- **TLB invalidation after permissions change is *required*.** When the CoW handler flips `PTE_W` from 0→1, the CPU's stale TLB entry still says "read-only" → infinite fault loop without `invlpg(va)`.
- **TLB flushes on CoW write = 1**, not 2 — only the faulting VA's entry is stale; the un-modified VAs' entries are still correct.
- **Refcount changes must be atomic.** Two cores faulting on the same shared page *will* race the decrement.
- **`fork-then-exec` is the killer workload.** The eager copy is *all* wasted work in this very common pattern. Real-world reason CoW exists.
- **OOM in fault handler is a real failure mode** under lazy/overcommit — Linux's "OOM killer" exists because allocation can fail at unexpected times.
- **Kernel-side writes bypass MMU permission checks for some operations** → syscalls like `read`/`write`/`pipe` need to *manually* trigger CoW, otherwise they corrupt shared pages.
- **Logical ≠ Physical permissions** — exam favorite. "The page is logically writable but physically read-only because of CoW" is a common correct phrasing.
- **Single zero page is *read-only*.** Easy to forget — if it were RW, every write would silently corrupt every other process's "fresh memory."
- **`n != 2`**: parent–child refcount tracking is wrong. You need a per-frame counter, not a per-process flag. Don't try to track family trees.
- **PTP dedup ≠ same address space.** Processes share the *bytes* of the PT page, not the *meaning* — a fork+divergent-CR3 still gives independent address spaces; only physical memory is saved.

---


---

## L08 — Virtual Memory III (CoW & Tricks)

*([→ xv6 implementation for this lecture](<#L08 — Virtual Memory III (CoW & Tricks) — xv6>))*


> **Tags:** `vm3` `L08` `lec8` `copy on write` `CoW` `cow fork` `lazy allocation` `demand paging`
> `lazy zeroing` `zero page` `single zero page` `zero-fill on demand` `ZFOD`
> `virtual allocation` `oversubscription` `overcommit` `shared memory` `shmem` `mmap`
> `memory mapped files` `swapping` `paging to disk` `swap` `page out` `page in`
> `interpose` `suspend reality` `vm tricks` `vm tips` `lie and be lazy`
> `logical permission` `physical permission` `R W bit` `PTE_W clear` `write fault` `protection fault`
> `page fault handler` `T_PGFLT` `trap 14` `cr2` `error code` `fork optimization`
> `many-to-one mapping` `physical refcount` `page refcount` `pa refcount` `kref`
> `PD copy` `PT copy` `PTP CoW` `page table CoW` `lab2` `Dirty CoW` `CVE-2016-5195`
> `Snowflock` `Kaleidoscope` `On-Demand-Fork` `EuroSys`
> `tlb flush on cow` `invlpg` `cr3 reload` `homonym` `vfork` `posix_spawn`

> **Cross-reference:** Builds on **vm1.md** (paging mechanism) and **vm2.md** (page fault handling, lazy alloc). This sheet focuses on the **"VM as a level of indirection"** tricks unlocked by paging — *Copy-on-Write* in particular — and the xv6 Lab 2 implementation.

---

## 1. Why VM Tricks Exist — The Indirection Dividend

> **Tags:** `why vm tricks` `indirection` `interpose` `observe monitor change` `lazy lying`

- Paging gives the kernel a **level of indirection** between VA and PA on every memory access.
- That indirection is the **mechanism**; the **policy** can be anything the kernel wants:
  - **Observe** — track which pages are touched (Accessed bit).
  - **Monitor** — see what writes happen (Dirty bit).
  - **Change** — remap on the fly without informing the process.
  - **Interpose** — trap on access (clear `PTE_P` or `PTE_W`) to run kernel logic **before** the access completes.
- Tagline from slides: *"We get to lie and be lazy!"* — the kernel can promise a page exists / is private without actually backing it, fixing things only when forced to.
- "Suspend reality and modify the behavior of underlying mechanisms" (DejaVu / Matrix metaphor in lecture).

### Catalogue of tricks (slide list)
- Copy-on-write fork
- Demand paging / lazy allocation
- On-demand zero-filled pages (ZFOD)
- One shared zero page
- Virtual allocation (oversubscription)
- Virtual shared memory
- Memory-mapped files (`mmap`)
- Paging to disk (swap)
- Memory oversubscription

### Key-idea alignment
| Trick | Maps to |
|---|---|
| CoW fork | **Performance** (skip copy) + **Sharing** (until divergence) |
| Lazy alloc / ZFOD | **Performance** + **Multiplexing** (allocate only what's used) |
| Single zero page | **Sharing** + **Multiplexing** |
| Shared memory / mmap | **Sharing** |
| Swap / oversubscription | **Multiplexing** (RAM > installed RAM illusion) |
| Interpose generally | **Protection** (W^X enforcement, debugging) |

---

## 2. Logical vs Physical Permissions — The Lie Mechanism

> **Tags:** `logical vs physical permission` `legal access` `cpu trap` `pte_w lie` `permission lie`
> `read-only trick` `cow trick` `protection bit lie`

- **Logical permission** — *Should this access be legal at the OS-policy level?* (e.g., process *should* be allowed to write this page.)
- **Physical permission** — *What does the PTE say to the hardware?* (e.g., PTE has `PTE_W=0`, so HW will trap.)
- The kernel is allowed to **lie**: set physical perms more restrictive than logical perms so HW raises a fault, then the page-fault handler can do bookkeeping and **fix up the PTE** before retrying.
- Every trick in this lecture is a variation of this lie:
  - CoW: logical = RW, physical = RO → on write fault, copy + grant W.
  - Lazy alloc: logical = mapped, physical = not present → on fault, kalloc + map.
  - ZFOD: logical = "your fresh zero page", physical = read-only mapping to a single shared zero frame.
  - Mmap'd file: logical = file region, physical = not present until accessed → on fault, read from disk.
- Always: **the user code is unaware** — the fault is invisible (just a stall), retrying the faulting instruction after fixup.

---

## 3. Copy-on-Write Fork — Core Idea

> **Tags:** `copy on write fork` `cow fork` `fork optimization` `fork copy avoidance`
> `parent child shared pages` `write fault duplicates` `eager copy vs lazy copy`

### Problem with eager-copy fork
- Standard `fork()` semantics: child has a *private* copy of parent's address space.
- Naive (xv6 baseline) implementation: walk every PTE in parent, `kalloc` a new frame, `memmove` page contents → **proportional to mapped memory**.
- ~99% of forks are immediately followed by `exec`, which throws away the copied pages → **wasted work**.

### CoW insight
- Defer the actual copy until **someone writes**.
- After fork, parent and child PDs **both point to the same physical pages**, marked **read-only**.
- A write triggers a page fault → handler:
  1. Allocates a fresh frame.
  2. Copies the page contents.
  3. Updates the *writer's* PTE to point at the new frame, with `PTE_W=1`.
  4. Decrements refcount on the old frame; if count drops to 1, restore `PTE_W` for the remaining owner; if it drops to 0, free it.
  5. `invlpg` to flush stale TLB entry.
  6. Resume the faulting instruction (transparent to user).

### Eager vs Lazy fork — Comparison Table

| Aspect | Eager (memcpy fork) | CoW fork |
|---|---|---|
| Fork latency | O(mapped pages) — copy everything | O(mapped pages) PT setup, **no data copy** |
| Memory overhead | 2× per fork until divergence | 1× + small refcount table |
| Write latency | Cheap (just a store) | First write to a page = **page fault + copy** (slow tail) |
| TLB churn | Just CR3 reload | CR3 + per-page `invlpg` on each first-write |
| Fork+exec workflow | Copies pages then immediately frees | **Almost zero data copy** |
| Implementation complexity | Trivial | Refcounting + fault handler + concurrency-safe |
| Failure modes | OOM at fork time (loud) | OOM **at write time** (quiet, hard to recover) |

### Pareto positioning (latency-of-fork vs memory-cost)
```
fork()
latency
  ▲
  │ ● Eager copy (slow fork, 2× mem, fast writes)
  │   ╲
  │    ╲
  │     ╲___
  │         ╲● CoW (fast fork, 1× mem, faulty writes)
  │            ╲
  │ ● Dream (fast everywhere)        ✗ Bad: slow + 2×
  └──────────────────────────────►  memory overhead
```
- Both eager and CoW lie on the **pareto frontier** (different operating points).
- CoW *dominates* eager when fork is followed by exec (the common case) — that's why every modern Unix uses CoW.
- The "dream" point requires extra mechanism (e.g., **vfork** which doesn't even copy the PT — but breaks isolation if the child writes).
- **On-Demand-Fork (EuroSys 2021)** pushes further: also do CoW on the **page tables themselves** — 65× faster than xv6-style fork on 1 GB workloads.

### Page-table overhead — N-process arithmetic (worked example)

> **Tags:** `page table overhead` `pagedir overhead` `N processes overhead` `fork overhead math`
> `eager fork cost` `cow fork cost` `pagetable size calculation` `1000 processes`
> `2-level paging overhead` `4kb page` `pagedir 4kb` `pagetable 4kb`

**Setup:** 32-bit, two-level paging, 4 KB pages.
- Each **page directory** = 1024 PDEs × 4 B = **4 KB** (1 page).
- Each **page table** = 1024 PTEs × 4 B = **4 KB** (1 page).
- Suppose a process has working set covering `K` page tables (e.g., `K=4` ⇒ 16 MB of mapped VA).

**Per-process metadata only (no data pages counted):**
- 1 pagedir + `K` pagetables = `(1+K) × 4 KB`.

**Eager fork of N processes** (parent + N−1 children, each with a private full PT tree):
- Total PT metadata = `N × (1+K) × 4 KB`.
- E.g., **N = 1000**, K = 4: `1000 × 5 × 4 KB = 20 MB` of pure pagetable metadata, **before** counting any data pages.
- Plus eager fork copies all data pages: if each proc maps `D` data pages, `N × D × 4 KB` more.

**CoW fork (data CoW, page tables still copied per child — xv6/Linux baseline):**
- PT metadata identical to eager: `N × (1+K) × 4 KB` — **CoW does NOT save pagetable bytes by itself**.
- Data savings: 1× until divergence instead of N×.

**CoW on page tables themselves (PTP CoW / On-Demand-Fork):**
- Children initially share parent's PT pages read-only.
- Total PT metadata at fork: `1 × (1+K) × 4 KB` (regardless of N), plus per-child a single shared pagedir entry until first write to a PT.
- For **N=1000, K=4**: 20 MB → ~20 KB. A **1000× reduction** in metadata.
- This is exactly the win On-Demand-Fork (EuroSys 2021) measures.

**Single-level (one giant page table) overhead for comparison:**
- 32-bit / 4 KB pages → `2³² / 4 KB = 1M` PTEs × 4 B = **4 MB per process**, allocated whether mapped or not.
- N=1000 → **4 GB** pure metadata. Two-level wins by only allocating PT pages for *populated* PD slots.

### Granularity analysis (what unit do we share?)

| Granularity | Pros | Cons |
|---|---|---|
| Whole address space (eager) | Simple | Slow, wasteful |
| Per-page (standard CoW) | Fine-grained sharing; copies only the dirtied pages | Page-fault per first write (TLB cold start) |
| Per-PT (PTP CoW, On-Demand-Fork) | Avoid copying 2 MB of PT for a 1 GB process | More complex refcount; PT-level faults |
| Per-region (vfork, fork without copy) | Zero overhead | Loses isolation; only safe if child immediately execs |

- **Sweet spot** for general use: per-page CoW with optional PT-level CoW for huge processes.

### Key-idea alignment
- CoW = **Performance** + **Sharing** at cost of **Protection mechanism complexity** (refcount races) and **latency tail** on first write.

---

## 4. The CoW Algorithm in Detail

> **Tags:** `cow algorithm` `cow implementation` `cow fault handler` `cow refcount` `pa refcount`

### Fork path (`cowfork`)
1. Allocate new PD.
2. For each PTE in parent's address space:
   - Clear `PTE_W` in **parent's** PTE.
   - Copy the (now-RO) PTE into **child's** PT (allocating a new PT frame at child if necessary).
   - Increment per-frame refcount (`refcount[PA >> PGSHIFT]++`).
3. Flush parent's TLB (CR3 reload or per-page `invlpg`s) — child has none yet.
4. Mark each shared page as "CoW" using a software-available bit (e.g., `PTE_COW` in the AVL bits 9–11).

### Page-fault handler (write to RO CoW page)
1. CPU traps with `T_PGFLT` (vector 14), error code shows **write + protection violation**, faulting VA in `CR2`.
2. Handler walks the PT, finds PTE with `PTE_COW=1, PTE_W=0`.
3. Inspects refcount of the underlying PA:
   - **refcount == 1** → I'm the last owner. Just flip `PTE_W=1`, clear `PTE_COW`, `invlpg`, return. (No copy needed!)
   - **refcount > 1** → kalloc fresh frame, `memmove(new, old, PGSIZE)`, set my PTE to `(new | PTE_W | PTE_U | PTE_P)`, decrement old refcount, `invlpg`, return.
4. If `kalloc` fails → **OOM**: kill the process or signal `SIGSEGV`.

### Why the AVL `PTE_COW` flag?
- The hardware doesn't distinguish "RO because policy" from "RO because pending CoW".
- A genuine RO page (text segment, mmap'd RO file) should *not* be silently made writable on a write fault.
- The kernel uses an AVL bit to remember "this PTE is RO **only because** of CoW" so it knows it's safe to upgrade.

### Refcount placement options

| Approach | Description | Tradeoff |
|---|---|---|
| Sidecar array indexed by PFN | `int refcount[PHYSTOP/PGSIZE]` | O(RAM) memory overhead (~0.1%); fast O(1) access |
| Embedded in `struct page` | Linux's approach | Tied to general page-info infrastructure |
| Inside the free-page itself | xv6's `kalloc` style — **does not work for CoW** | xv6 must add a sidecar |

---

## 5. CoW Walkthrough Example (from slides)

> **Tags:** `cow example` `pd1 pt1 pt2 p1 p2 p3 p4` `cow walkthrough`

### Initial state (after `fork()`)
- Both parent (Process 1) and child (Process 2) point to same `PD1`.
  - *(Slides simplify by sharing PDs initially; in real CoW each process gets its own PD that copies entries.)*
- All shared pages (P1, P2, P3) get `W=0` in both PTs.
- Refcount[P1]=2, refcount[P2]=2, refcount[P3]=2.

### Step 1: Process 2 writes to P1
- HW page fault (write to RO page).

### Step 2: Handler creates a private copy P4 (= P1')
- Allocates new PT (`PT3`) for the affected region of the child (so changing child's PTE doesn't mutate parent's PT).
- New PD (`PD2`) for the child so the PD entry can point to PT3.
- New page P4 gets the copied contents of P1.
- Process 2's PTE for that VA now: `PA=P4, R=1, W=1`.
- Process 1's PTE for P1: still `R=1, W=0` — but now refcount[P1]==1 → can also be flipped to `W=1` lazily on next write fault, or eagerly here.

### Final state
| Process | PD | PT for region | VA → PA | Perms |
|---|---|---|---|---|
| P1 (parent) | PD1 | PT1 | →P1 | R=1, **W=0** (still RO until next write fault, or restored eagerly) |
| P2 (child) | PD2 | PT3 | →**P4** | R=1, W=1 |
| Both | — | PT2 | →P3 | R=1, W=0 (still shared) |

### Slide fine-print
- **"Lab2 does not use CoW page table / page directory allocation — only CoW page allocation."** I.e., Lab 2 makes a fresh PD + PT per process at fork (eager), but shares the data **pages** with refcount + RO trick.
- True PTP-CoW (sharing the PTs themselves) is more advanced (On-Demand-Fork research).

---

## 6. TLB Implications of CoW

> **Tags:** `tlb cow` `tlb invalidate cow` `invlpg cow` `tlb flush count` `cr3 reload cow`

### "How many TLB invalidates on a write to P1?" (slide quiz)
- The fault handler updates **only one PTE** (the writer's PTE for the faulting VA).
- Therefore: **1 `invlpg`** on the writer's CPU for that one VA.
- If the **other** owner's PTE is also flipped W=1 (eager restore), that's a second `invlpg` on **its** CPU (cross-core IPI / TLB shootdown).
- xv6 **only flushes on `cr3` reload** (no fine-grained invalidate scheme), so a CoW handler in xv6 typically does a CR3 reload → flushes *the entire TLB* of the current process (D. 42-style "many" — but in xv6 specifically you reload CR3, so it's "all entries of this address space" not literally one).

### "How many TLB flushes will the write to P1 cause?" (slide quiz)
- In a fine-grained system: **1** (a single `invlpg`).
- In xv6: **1 full TLB flush of the current address space** because xv6 only knows how to flush by `lcr3()`.

### Performance impact
- CoW pays a one-time *TLB miss + page-walk* tax after each CoW resolution.
- Cumulative cost depends on how many distinct CoW pages get written → **bursty fault tail** right after fork.

---

## 7. CoW CDF (Performance Analysis)

> **Tags:** `cow cdf` `fork latency cdf` `write latency cow` `slow tail cow`

### CDF: time to complete `fork()` itself
```
P[fork ≤ x]
  1│              ──────────
   │           ╱
   │         ╱   ← eager fork: linear in mapped MB (slow tail)
   │       ╱
   │     ╱
.99│   ╱
   │  ╱           ● CoW fork: ~constant (sub-ms even for GB)
.5 │ ┃
   │ ┃
  0│┃
   └────────────────────────►  fork latency
       µs       ms        s
```

### CDF: time per write after fork
```
P[write ≤ x]
  1│                ────────
   │              ╱      ← page-fault tail (CoW resolution)
.999│           ╱
   │         ╱
.99│       ╱
   │     ╱
   │  ┃   ← TLB-hit, regular store (~1 cycle)
  0│ ┃
   └────────────────────────► write latency
      ns      µs       ~ms (if OOM-> kill)
```
- **Bimodal**: 99%+ writes are normal stores; tail is dominated by first-write CoW faults.
- A workload that writes its entire AS once after fork → degenerates into eager-copy cost (deferred, paid lazily).

### SLOs
- **Fork latency SLO** (microservice spawn, shell pipe): p99 fork ≤ 100 µs → demands CoW (eager copy of GB-sized AS would blow it).
- **Write latency SLO** (HFT, RT systems): p99 write ≤ 100 ns → CoW *hurts* this; such systems prefer eager copy or `mlockall` to avoid the fault tail.
- **Memory SLO** (cloud densification): need lots of forked workers per host → CoW is mandatory.
- **Heterogeneous SLOs across CoW vs eager**:
  - CoW favors *fork latency* + *memory*, sacrifices *write tail latency* and *failure-mode predictability*.
  - Eager favors *write tail* + *fail-fast OOM*, sacrifices *fork latency* + *memory*.
  - Implication: same workload may want different fork strategies in different code paths (e.g., `vfork` for shell pipes, `fork+exec` with CoW for daemons, full `clone` for threading).

---

## 8. Other VM Tricks (each is a "logical ≠ physical perms" lie)

### 8a. Lazy Allocation / Demand Paging
> **Tags:** `lazy allocation` `demand paging` `sbrk lazy` `not present trick`

- `sbrk(n)` extends `proc->sz` but does **not** kalloc pages.
- First access → page fault → handler kalloc's, zeros (or maps zero page), installs PTE, retries.
- Wins when programs `malloc` more than they use (typical).
- Risk: OOM at access time (commit accounting needed for safety).

### 8b. On-demand Zero-Fill (ZFOD)
> **Tags:** `zero fill on demand` `zfod` `bss` `anonymous mapping`

- New BSS / anonymous pages logically read as zero.
- Don't allocate physical frames at all until first access.

### 8c. Single Zero Page
> **Tags:** `single zero page` `shared zero frame` `kernel zero page`

- All ZFOD virtual pages share **one** physical zero frame, mapped **read-only**.
- On read: cheap, no allocation.
- On write: page fault → kalloc fresh zero frame → install RW.
- A single physical frame can back **millions of virtual pages** that are never written.

### 8d. Virtual Allocation / Oversubscription
> **Tags:** `virtual allocation` `oversubscription` `overcommit` `memory overcommit`

- Process can `sbrk`/`mmap` more virtual memory than physical RAM exists.
- Works as long as the **resident set** ≤ RAM.
- If too many processes touch their pages → swap or OOM-kill.
- Linux `vm.overcommit_memory` knob controls strictness.

### 8e. Shared Memory
> **Tags:** `shared memory` `shmem` `posix shm` `sysv shm` `many to one mapping`

- Multiple PTEs (different processes, different VAs) → same PA.
- Used for IPC, shared libs, mmap'd files (MAP_SHARED).

### 8f. Memory-Mapped Files (mmap)
> **Tags:** `memory mapped file` `mmap` `file backing` `page cache integration`

- File contents *appear* in process VA without `read()`.
- Page faults pull file pages from disk into the page cache; PTE made present and points to page-cache frame.
- Writes to MAP_SHARED pages eventually flush to disk (writeback); MAP_PRIVATE = CoW backing the file.

### 8g. Swap / Paging to Disk
> **Tags:** `swap` `paging to disk` `page out` `page in` `swap slot`

- When RAM pressure rises, kernel writes infrequently used pages to a swap area on disk and clears `PTE_P`.
- The PTE encodes the swap slot in the PFN field (since P=0, HW ignores the rest).
- On next access → fault → handler reads back from swap.
- **Slow tail**: ms-scale latency (disk) — a real-time death sentence.

### 8h. Lazy Zeroing (Security)
> **Tags:** `lazy zeroing` `kernel zero page` `security zero` `data leak prevention`

- Kernel zeros pages **before** handing them to userspace to prevent leaking another process's data.
- Can defer the zeroing to the first access (using ZFOD trick) → gets the security guarantee without burning CPU on pages the user never touches.

### 8i. Memory Backing
> **Tags:** `memory backing` `not always ram` `swap mmap backing`

- A virtual page need not be backed by RAM:
  - **Anonymous + present** → RAM frame
  - **Anonymous + swapped** → swap slot on disk
  - **File-backed** → file content (page cache or disk)
  - **Device-mapped** → MMIO region
  - **Shared zero** → the global zero frame

---

## 9. Linux Diagnostics (from slides)

> **Tags:** `linux memory tools` `pmap` `proc maps` `proc iomem` `free` `strace mmap`

| Tool | What it shows |
|---|---|
| `cat /proc/iomem` | Kernel's view of physical memory regions (RAM, ROM, MMIO) |
| `cat /proc/self/maps` | Caller's own VA layout (regions, perms, backing files) |
| `cat /proc/PID/maps` | Same for any process |
| `pmap PID` | Per-process VA→size→perms→file table |
| `free` | Total/free/used RAM, swap, buffers, cache |
| `strace -e trace=mmap,mprotect,brk` | See VM syscalls a program issues |

---

## 10. The Dirty CoW Exploit (CVE-2016-5195)

> **Tags:** `dirty cow` `CVE-2016-5195` `cow race condition` `privilege escalation` `linux cow bug`

- 9-year-old race in Linux's CoW implementation: an attacker could write to a *read-only* file (e.g., `/etc/passwd`, `/usr/bin/passwd`) by exploiting a TOCTOU between the page fault handler and the discard-private-mapping path.
- Affected the Linux kernel from 2007–2016; gives root via overwriting a setuid binary or `/etc/passwd`.
- Lesson: CoW is a **microcosm of concurrency-safe VM** — the lie of "it's read-only" must be *atomically* lifted; if a thread can race the handler, it can clobber the original (logically RO) page.
- Demonstrates why CoW is "deceptively simple" on slides but very subtle in practice.

---

## 11. Research Perspective (slides)

> **Tags:** `snowflock` `kaleidoscope` `on-demand-fork` `eurosys cow`

- **Snowflock** (EuroSys 2009, **Test-of-Time at EuroSys 2023**): "fork a VM in under a second to a networked cluster." Uses on-demand paging + CoW + selective page transfer to clone VM state across machines.
- **Kaleidoscope** (EuroSys 2011): efficient stateful VM replication via "VM state coloring."
- **On-Demand-Fork** (EuroSys 2021): drop-in `fork()` that does **PTP CoW** (page-table CoW). 65× faster than vanilla fork on 1 GB workloads, 99% reduction in fork-cost, 59–226% throughput gain on macro benchmarks. Motivated by huge memory footprints → millions of PTEs to clone is itself the bottleneck once data CoW removed the data-copy cost.

---

## 12. Quick Comparison: All Tricks vs Key Ideas

| Trick | Isolation | Multiplexing | Protection | Performance | Sharing |
|---|---|---|---|---|---|
| CoW fork | ✓ (private after write) | ✓ (1 PA, many VAs) | ✓ (RO trick) | ✓ (skip copy) | ✓ (until divergence) |
| Lazy alloc | — | ✓ (alloc on use) | — | ✓ | — |
| Single zero page | — | ✓ | ✓ (RO) | ✓ | ✓ (everyone shares it) |
| Shared memory | — | — | depends | ✓ (zero-copy IPC) | ✓ |
| mmap file | ✓ (per-process VA) | ✓ (page cache shared) | ✓ | ✓ (no `read` syscalls) | ✓ |
| Swap | ✓ | ✓ (RAM > installed) | — | ✗ (slow tail) | — |
| Oversubscription | — | ✓ | — | ± | — |

---


---

## L09 — Concurrency I (Interrupts & Traps)

*([→ xv6 implementation for this lecture](<#L09 — Concurrency I (Interrupts & Traps) — xv6>))*


> **Tags:** `concurrency1` `concurrency I` `L09` `lec9` `lecture 9` `interrupts` `exceptions` `syscalls` `system calls`
> `traps` `trap handling` `interrupt handling` `IDT` `IDTR` `lidt` `vector` `interrupt vector` `vectors`
> `IRQ` `IRQs` `irq` `INT` `INTR` `NMI` `INTA` `software interrupt` `hardware interrupt`
> `maskable` `non-maskable` `non maskable` `EFLAGS IF` `interrupt flag` `sti` `cli`
> `PIC` `8259A` `Programmable Interrupt Controller` `APIC` `IOAPIC` `LAPIC`
> `polling` `polling vs interrupts` `interrupt driven` `event driven`
> `clock algorithm` `swap clock` `second chance` `LRU approximation` `page eviction` `belady` `belady's anomaly`
> `swap wrap up` `swapping wrap up` `access bit` `accessed bit` `PTE_A`
> `pseudo concurrency` `concurrency safety` `interrupt + lock` `cli on lock`
> `trap frame` `trapframe` `alltraps` `trapret` `iret` `T_SYSCALL` `int 0x40` `int 64`
> `vector.S` `trapasm.S` `trap.c` `tvinit` `SETGATE` `usys.S`
> `gate descriptor` `interrupt gate` `trap gate` `DPL` `DPL_USER` `CPL`

> **Cross-reference:** Builds on **isolation.md** (rings/CPL, syscall boundary motivation), **kernel_org.md** (kernel/user split, monolithic vs microkernel), and **vm2.md / vm3.md** (page-fault handler is a specific trap path). Sets up **concurrency2.md** (locks, atomicity, multi-CPU).

---

## 1. Swapping Wrap-Up — Clock (Second-Chance) Algorithm

> **Tags:** `clock algorithm` `clock eviction` `second chance` `circular list eviction` `LRU approx`
> `swap` `page eviction` `which page to evict` `tracking LRU`

### Why Clock exists
- Goal: pick a page to **evict to disk** when RAM is full.
- **Belady's optimal** = evict the page accessed **furthest in the future** → impossible (oracle).
- **LRU** = evict the page accessed **least recently** → good approximation, but **expensive** to track exactly:
  - Would need a timestamp on **every load and store**.
  - Trapping every access = page fault per memory op (catastrophic).
  - Even the data structure would be O(n) updates without H/W help.
- **Random** is simple but ignores locality.
- **Clock** = **O(1) amortized LRU approximation** using one bit per page (the H/W-set **Accessed bit**, `PTE_A`).

### Mechanism
- Pages live in a **circular list** (the "clock face"); a single hand walks the ring.
- HW sets `a=1` (access bit) automatically on **read or write** to a page.
- **On evict request**, hand walks forward:
  1. If `a == 1` → page got a "second chance": **clear** `a=0`, advance.
  2. If `a == 0` → **evict** this page; place new page here with `a=1`.
- Hand position persists across evictions (does not reset).

### Worst case
- All pages have `a=1` (all hot) → hand sweeps entire ring once clearing bits, then sweeps again to find a victim. **O(n)** in the worst case but **O(1) amortized** if access patterns aren't pathological.

### Trapping question
- *"Do we trap on every read/write?"* — **No.**
- HW silently sets `PTE_A` in the PTE. Kernel only needs to **read/clear** it on its own schedule (eviction sweep, periodic scan).
- Kernel only **traps** (clears `PTE_P`) when it actually swaps the page out.

### Comparison: Eviction Policies

| Policy | Tracking cost | Hit rate | Worst case | Implementable? |
|---|---|---|---|---|
| **Belady (OPT)** | Oracle | Optimal | — | ❌ Needs future knowledge |
| **LRU exact** | Timestamp/list per access | ~Optimal | Pathological scans | Costly (HW trap per access) |
| **Clock / 2nd chance** | 1 access bit/page | Near-LRU | O(n) sweep when all hot | ✅ Cheap |
| **FIFO** | Just an arrival order | Poor (Belady's anomaly) | — | ✅ Trivial |
| **Random** | None | Mediocre | Unbounded variance | ✅ Trivial |

### Pareto frontier (eviction)
- Clock dominates LRU and FIFO on the (tracking-cost × hit-rate) plane → **pareto-optimal** for practical kernels.
- Belady is pareto-optimal in **hit rate** alone but not realizable.
- LRU exact is dominated by Clock (Clock matches it within ε at a fraction of the cost).
- Random is on the frontier only on the cost axis (cheapest, worst hit rate).

### Key-idea alignment
- Clock = **Multiplexing** (RAM among more processes than fits) + **Performance** (cheap approximation).

### Granularity tradeoff (eviction unit)
- **Per-page (4KB)** — what HW supports natively, fine balance between bookkeeping and waste.
- **Per-large-page (2MB/4MB)** — fewer access bits to scan, but evicting 2MB on a single hot byte is wasteful.
- **Per-region/segment** — coarse, simplifies sweep but bad miss penalty.
- **Per-byte** — absurd; would explode metadata (1 bit/byte ≈ 12% RAM overhead).

### CDF intuition (page-access latency under swap)
- Most accesses: ~ns (RAM hit).
- Small tail: ~ms (page fault → disk read → eviction handler) — **5+ orders of magnitude jump**.
- CDF is sharply bimodal: ~99% near-zero, then a **flat plateau** until a long disk-IO cliff.
- A good evictor (Clock) keeps the disk-IO mass thin; FIFO/Random fattens it.

### SLO framing
- "P99 memory access < 100ns" is **incompatible** with any swap-using workload (P99 will hit the disk tail).
- SLOs for swappy systems are necessarily **heterogeneous**: hot path (no swap) vs cold path (with swap).
- This is **different from non-swap kernels** (homogeneous: every access is RAM-only).

---

## 2. Interrupts & Exceptions — Why We Need Them

> **Tags:** `why interrupts` `unpredictable events` `keyboard input` `network rx` `timer` `events`
> `polling thought experiment` `polling vs interrupts`

### What needs interrupts
| Class | Examples |
|---|---|
| **Exceptions** | Page fault, divide-by-zero, GPF, machine-check, power/memory errors |
| **Hardware** | Timer tick, disk IO complete, NIC RX, keyboard, USB |
| **Debugging** | Software breakpoints (`int3`), single-step |
| **Communication** | Inter-Processor Interrupts (IPIs) for multi-core kick |
| **Control** | Watchdog timer, NMI for catastrophic failure |

### Polling thought experiment (keyboard without interrupts)
- Kernel must keep checking the keyboard buffer in a loop.
- **Frequent events:** wastes few cycles, OK throughput, but bad if you must do other work.
- **Infrequent events:** wastes >>99% of cycles spinning. Also you might **miss** an event (correctness bug) if poll period > event interarrival time.

### Polling vs Interrupts — Comparison

| | **Polling** | **Interrupts** |
|---|---|---|
| CPU cost when idle | High (loop spins) | Zero |
| CPU cost when busy | Low extra (already running) | Context-switch overhead per event |
| Latency | Up to one polling interval | ~µs (HW dispatch + handler entry) |
| Determinism | Predictable (bounded period) | Less predictable (preempts arbitrary code) |
| Concurrency hazard | Minimal — synchronous to your code | Huge — handler can fire mid-instruction |
| Overhead per event | None beyond the check | Save state, switch ring, IDT lookup, iret |

### Pareto frontier (event delivery)
- **High-rate uniform events** (e.g., 10Gb NIC at line rate) → polling wins on throughput; interrupts livelock (interrupt storm).
- **Low-rate / bursty events** (keyboard) → interrupts dominate.
- **Hybrid** (Linux NAPI, DPDK): interrupt to wake, then poll until quiet → pareto-optimal in practice.
- Pure polling is pareto-optimal only when events are **continuous and high-rate**.
- Pure interrupts are pareto-optimal when events are **rare and unpredictable**.

### Crossover formula — when does polling beat interrupts?

> **Tags:** `polling crossover` `interrupt crossover formula` `Ci Cp R` `interrupt rate threshold`
> `polling break-even` `R Ci` `R > Cp / Ci`

- Let `R` = events per second, `Ci` = CPU cost per interrupt (µs/event), `Cp` = polling cost per second (µs/sec, fixed regardless of R).
- **Cost(interrupts) = R · Ci** (per second).
- **Cost(polling) = Cp** (per second).
- **Polling wins when** `R · Ci > Cp`, i.e., `R > Cp / Ci`.
- **Crossover rate** `R* = Cp / Ci`. Below it interrupts are cheaper; above it polling is cheaper.
- **Worked numbers:** if `Ci = 2 µs`, `Cp = 100,000 µs/sec` (i.e. 10% of one core spent polling), then `R* = 50,000 events/sec` — typical NIC line-rate territory, which is exactly why DPDK/XDP go polling.

**eBPF / XDP as the third option:**
- Runs the packet-filter in the **driver**, *before* the skb / softirq path. Avoids per-packet softirq + alloc cost.
- Tradeoff vs polling: still uses interrupts (no idle CPU burn), but slashes `Ci` by handling the packet entirely at the lowest layer.
- Tradeoff vs vanilla interrupts: programmable, but constrained (verifier-bounded, no unbounded loops, restricted helper API).
- Pareto: XDP dominates plain interrupts on per-packet cost; loses to pure polling at line-rate but wins on idle efficiency.

### Key-idea alignment
- Interrupts = **Multiplexing** (one CPU shared between many event sources) + **Performance** (no idle spin) + **Protection** (HW forces ring-0 entry through controlled gate).

---

## 3. Interrupt Taxonomy

> **Tags:** `interrupt types` `INT INTR NMI` `software vs hardware` `maskable` `non maskable`
> `interrupt acknowledge` `INTA`

### Tree
```
                Interrupts
               /          \
          Hardware       Software (INT)
         /        \
     Maskable   Non-Maskable
      (INTR)       (NMI)
```

### Maskable (INTR)
- Issued by external HW via the **PIC** (or APIC).
- **Ignored when EFLAGS.IF = 0**.
- `sti` → set IF (allow); `cli` → clear IF (block).
- Most everyday IRQs: timer, disk, keyboard, NIC.

### Non-Maskable (NMI)
- Cannot be masked by `cli`; the CPU **must** handle it.
- Reserved for catastrophic events: power failure, parity/ECC error, hardware watchdog.
- **xv6:** if NMI fires → just die (no recovery path).
- x86: vector **2**.

### Software (INT N)
- `INT N` instruction triggers vector N (0–255) intentionally.
- Used for **system calls** in xv6: `INT 0x40` (`T_SYSCALL = 64`).
- Modern x86 has faster paths (`syscall`/`sysenter`) but xv6 sticks with `INT` for simplicity.
- **Entering**: `int N` ; **Exiting**: `iret`.

### INTA (Interrupt Acknowledge)
- Bus cycle/signal CPU sends back to PIC after taking an INTR, telling PIC the IRQ is being serviced (so PIC can lower the line and present the next).

### Comparison

| Type | Source | Maskable? | Vector(s) | xv6 use |
|---|---|---|---|---|
| **NMI** | HW (NMI pin) | No | 2 | Crash |
| **INTR (HW)** | PIC line | Yes (`cli`) | 32–47 (after remap) | Timer, disk, kbd |
| **INT (SW)** | `int N` instr | N/A | Any 0–255 | `int 0x40` syscall |
| **Exception** | CPU faults | No | 0–31 (Intel reserved) | PGFLT (14), GP (13), DBL (8) |

---

## 4. PIC — Programmable Interrupt Controller (8259A)

> **Tags:** `PIC` `8259A` `Programmable Interrupt Controller` `IRQ pins` `IR0..IR7` `cascading`
> `apic` `ioapic` `lapic`

- Real CPUs have **far fewer interrupt pins than devices** → need a multiplexer.
- The 8259A has **8 IRQ inputs** (`IR0–IR7`) and one `INT` output to the CPU's INTR pin.
- Two PICs are **cascaded** in PCs to give 15 usable IRQs (master + slave through `IR2`).
- PIC duties:
  - Latch incoming IRQs.
  - Apply masks (per-line enable/disable).
  - Resolve priority among simultaneous IRQs.
  - Drive CPU's `INTR` pin and answer with the **vector number** on `INTA`.
- Modern systems use **APIC / IOAPIC + LAPIC** instead — more vectors, MSI support, per-CPU steering. xv6 supports both (`lapic.c`, `ioapic.c`).

### Granularity (interrupt routing)
- **Per-pin** — what the 8259A gives you (coarse, 15 lines for the whole machine).
- **Per-vector** — IDT supplies 256 vectors, regardless of how many pins.
- **Per-CPU** (LAPIC) — IPIs and steered IRQs in SMP systems.

### Key-idea alignment
- PIC = **Multiplexing** (many devices → few CPU pins) + **Sharing** (one INT line shared by many IRQs).

---

## 5. Vectors & The IDT

> **Tags:** `IDT` `Interrupt Descriptor Table` `IDTR` `lidt instruction` `gate descriptor` `interrupt gate` `trap gate`
> `vector number` `256 entries` `8 byte entry` `vector dispatch`

### Vector
- An **8-bit number (0–255)** identifying *which kind* of interrupt fired.
- The vector indexes into the IDT to find the handler.
- Examples (xv6):
  - **14** → page fault handler (used in Lab 2)
  - **32** → clock/timer handler → scheduler (used in Lab 3)
  - **0x40 (64)** → `T_SYSCALL`

### IDT (Interrupt Descriptor Table)
- Array of **256 × 8-byte gate descriptors**.
- Each descriptor specifies a **protected entry point** into the kernel (CS:offset + flags).
- Located **anywhere in physical memory** — CPU finds it via the IDTR.

### IDTR register
- Holds (Base address, Limit) of the current IDT.
- Layout: `[47:16]` base, `[15:0]` limit.
- Loaded with the **`lidt`** instruction (takes a linear address pointing to a 6-byte limit/base struct).

### Boot-time ordering hazard — set up IDT *before* enabling interrupts

> **Tags:** `idt setup ordering` `cli before lidt` `interrupt before idt loaded` `protected mode bug`
> `interrupt fires during init` `garbage handler` `triple fault` `EFLAGS.IF boot`
> `disable interrupts during setup` `did not disable interrupts`

- After reset on x86, `EFLAGS.IF = 0` (interrupts masked) and CPU is in real mode — but firmware/UEFI may have already populated a real-mode IVT and left `IF=1` on handover.
- **The bug:** transitioning to protected mode **before** issuing `lidt` (or before populating the IDT entries you `lidt`'d to), with `IF=1`, means any pending or arriving IRQ during init dispatches through the **uninitialized / garbage IDT**:
  - Best case: descriptor `present=0` → `#NP` exception → faults that handler too → **triple fault → CPU reset**.
  - Worse case: descriptor looks plausible → CPU jumps to garbage `EIP` in ring 0.
- **Correct ordering** (xv6, Linux):
  1. `cli` (or trust BIOS/UEFI handed control with IF=0).
  2. Build the IDT in memory (`SETGATE` for every vector, even unused → point at a fault stub).
  3. `lidt` to load IDTR with the populated table.
  4. Initialize PIC/APIC (mask all IRQs at the controller, set offsets).
  5. Only then `sti` to allow interrupts.
- **Trap gate vs interrupt gate matters here too:** if you install the syscall vector as a *trap gate* (doesn't auto-clear IF) before the rest of the IDT is built, an IRQ that fires during the syscall will dispatch through whatever's in the still-uninitialized vector slot.
- **Why every IDT slot must be filled (even unused):** an unexpected IRQ to a `present=0` slot is fatal. Linux installs `ignore_int` stubs everywhere; xv6's `tvinit` populates all 256 entries.

### Gate descriptor fields (relevant for `SETGATE`)
| Field | Meaning |
|---|---|
| `off_15_0`, `off_31_16` | Offset of handler within code segment |
| `cs` (`sel`) | Code segment selector for the handler |
| `dpl` | Descriptor Privilege Level — **min CPL allowed to invoke via `int N`** |
| `p` | Present bit (1 = valid entry) |
| `type` | `STS_IG32` (interrupt gate) or `STS_TG32` (trap gate) |
| `s` | 0 for system descriptors |

### Interrupt gate vs Trap gate

| | Interrupt gate | Trap gate |
|---|---|---|
| Macro flag | `istrap = 0` (`STS_IG32`) | `istrap = 1` (`STS_TG32`) |
| Effect on `IF` | **Clears `EFLAGS.IF`** on entry (further IRQs masked) | **Leaves `IF` alone** |
| Use case | HW interrupts (don't reenter) | Software exceptions / syscalls (kernel can decide) |
| Reentrancy | Self-protected | Caller must mask if needed |

### `int N` step-by-step (what HW does)
1. Decide vector `N`.
2. Fetch the 8-byte descriptor at `IDTR.base + N*8`.
3. **Check `CPL ≤ DPL`** in the descriptor (only for `int` instr — HW interrupts skip).
4. If target segment selector's PL < CPL (ring change, e.g., user→kernel):
   - Save `ESP` and `SS` in CPU-internal scratch.
   - **Load `SS` and `ESP` from the TSS** (kernel stack for this CPU).
   - Push old user `SS`, then user `ESP`.
5. Push `EFLAGS`, `CS`, `EIP` (always).
6. Push **error code** (only for some exceptions: PF, GP, DF, etc.).
7. Clear some EFLAGS bits (notably `IF` if interrupt gate).
8. Set `CS:EIP` from the descriptor → start running handler in the kernel.

### `iret` — opposite direction
- Pops `EIP, CS, EFLAGS` (and `ESP, SS` if returning to lower CPL).
- Atomic restore — cannot be split into separate pops without race.

### Key-idea alignment
- IDT + vectors = **Protection** (controlled, kernel-defined entry points only) + **Isolation** (user code cannot pick arbitrary kernel addresses to jump to).

---

## 6. Trap Frame — What the Stack Looks Like

> **Tags:** `trapframe` `trap frame` `x86.h trapframe` `error code` `eip cs eflags esp ss`
> `pushal` `popal` `gs fs es ds` `padding`

### Layout (xv6 `struct trapframe` in `x86.h`, low → high)
```c
// pushed by alltraps.S
uint edi, esi, ebp, oesp, ebx, edx, ecx, eax;  // pushal
ushort gs, padding1, fs, padding2, es, padding3, ds, padding4;
uint trapno;

// pushed by HW (always)
uint err;       // error code (0 if vector has no err)
uint eip;
ushort cs, padding5;
uint eflags;

// pushed by HW only when crossing rings (user→kernel)
uint esp;
ushort ss, padding6;
```

- The HW fills the **bottom block** automatically on `int N`.
- **`alltraps`** in `trapasm.S` saves the rest (segment regs + `pushal` for all general-purpose regs).
- Kernel's `trap()` receives a pointer to this struct and dispatches by `trapno`.

### Why this structure
- **One unified frame** for all interrupts/exceptions/syscalls → single `alltraps` / `trapret` pair.
- Some vectors don't push an error code → `vector.S` pushes a dummy 0 to keep the layout uniform.
- `trapret` does the reverse: `popal` → pop seg regs → `addl $8` (skip trapno+err) → `iret`.

---

## 7. End-to-End Trap Flow in xv6

> **Tags:** `vectorN` `alltraps` `trap()` `syscall()` `trapret` `iret` `trap pipeline` `usys.S`
> `entry trap exit` `kernel entry path`

### Entry pipeline
```
user int 0x40  →  HW (per §5)  →  vectorN (vector.S)  →  alltraps (trapasm.S)
              →  trap() (trap.c)  →  syscall() / pgfault handler / etc.
```

### `vector.S` (auto-generated by `vectors.pl`)
- 256 stubs: each pushes its **trapno** (and a dummy err code if HW didn't), then `jmp alltraps`.
- One stub per vector keeps the dispatch register-free until `alltraps`.

### `alltraps` (trapasm.S)
```asm
pushl %ds ; pushl %es ; pushl %fs ; pushl %gs
pushal
movw  $SEG_KDATA<<3, %ax     # load kernel data segs
movw  %ax, %ds ; movw %ax, %es
pushl %esp                   # arg = pointer to trapframe
call  trap
addl  $4, %esp
jmp   trapret
```

### `trap()` (trap.c) — C dispatcher
- Reads `tf->trapno`, switches on it:
  - `T_SYSCALL` → `syscall()` (reads syscall number from `eax`).
  - `T_IRQ0+IRQ_TIMER` → tick + scheduler yield.
  - `T_IRQ0+IRQ_KBD/COM/IDE` → driver handler.
  - `T_PGFLT` → page-fault handler (Lab 2 CoW etc.).
  - default → kernel panic / kill process.

### `usys.S` — userspace syscall stubs
```asm
#define SYSCALL(name)            \
  .globl name;                   \
  name:                          \
    movl $SYS_##name, %eax;      \
    int  $T_SYSCALL;             \
    ret
SYSCALL(fork) ; SYSCALL(exit) ; ...
```
- Sets `eax` = syscall number, fires `int 0x40`. Return value comes back in `eax` (set by kernel into `tf->eax` before `trapret`).

### `trapret` (trapasm.S)
```asm
popal
popl %gs ; popl %fs ; popl %es ; popl %ds
addl $0x8, %esp        # discard trapno + err
iret
```

### IDT initialization — `tvinit()` in `trap.c`
```c
for (i = 0; i < 256; i++)
  SETGATE(idt[i], 0, SEG_KCODE<<3, vectors[i], 0);   // istrap=0, dpl=0
SETGATE(idt[T_SYSCALL], 1, SEG_KCODE<<3,
        vectors[T_SYSCALL], DPL_USER);                // trap gate, dpl=3
```
- Default: every vector is an **interrupt gate** with **DPL=0** (user cannot `int N` it directly).
- `T_SYSCALL` is special:
  - **Trap gate** (don't auto-clear `IF` — kernel keeps interrupts as they were).
  - **DPL=DPL_USER (3)** so user code is *allowed* to `int 0x40`.

---

## 8. Interrupts as Pseudo-Concurrency — The Bridge to Locks

> **Tags:** `pseudo concurrency` `interrupt safety` `concurrency safety` `interrupt disable lock`
> `cli on lock acquire` `pushcli` `popcli` `kernel + handler race` `shared variable race`

- An interrupt handler can fire **mid-instruction** of kernel code on the same CPU.
- Even on a **single CPU**, this creates **pseudo-concurrency** — two execution contexts (kernel-thread + handler) sharing kernel state.

### The race (slide example)
```
Kernel thread             Interrupt handler
Lock(L)                   Lock(L)        // arrives mid-section
shared = 7                X = shared
Unlock(L)                 Unlock(L)
```
- If the handler tries to acquire the same lock the kernel thread holds, on a uniprocessor → **deadlock** (handler will spin forever; thread can't release because it's preempted).
- *"Can't make the interrupt handler ignore the locks"* — the shared data is genuinely shared.

### Solution: disable interrupts while holding the lock
- **Whenever a kernel thread holds a lock**, mask interrupts (`cli`) → handler can't fire on this CPU until lock released.
- xv6 implements this with **`pushcli` / `popcli`** (nestable cli/sti) tied to `acquire`/`release`.
- Multi-CPU: `cli` only stops *this* CPU's handlers — still need a **spinlock** for cross-CPU mutual exclusion.

### Comparison: Synchronization vs Interrupts

| Approach | Single-CPU safe? | Multi-CPU safe? | Cost |
|---|---|---|---|
| `cli` only | ✅ | ❌ | Cheap (1 instr) |
| Spinlock only | ❌ (handler→deadlock) | ✅ | Atomic op + spin |
| `cli` + spinlock | ✅ | ✅ | Both costs |
| Disable handler entirely | ✅ | ✅ | Loses the device |

### Key-idea alignment
- Disabling interrupts = **Protection** of kernel invariants by suppressing concurrency.
- Spinlock = **Multiplexing** (many CPUs share the lock) + **Performance** (no sleep).

### Granularity (critical-section size)
- **Coarse** (whole syscall under `cli`) → simple, but **kills latency** for IRQs (timer skipped, missed packets).
- **Fine** (per-data-structure lock + brief `cli`) → great latency, but lots of locks → bug surface.
- **Lock-free** (atomics only) → best latency, hardest to write correctly.

### CDF — interrupt latency
- Without `cli` regions: tight gaussian around HW dispatch + handler ~µs.
- With long `cli` regions: a **fat right tail** as long as the longest `cli` window.
- Real-time SLOs ("IRQ serviced within 50µs P99") imply a hard cap on any `cli` region. Heterogeneous: not all interrupts have equal SLO — timer = strict, disk = lax.

---

## 9. Comparison: Mechanisms for Crossing the User/Kernel Boundary

| Mechanism | Trigger | Cost | Predictability | Use |
|---|---|---|---|---|
| **`int N`** (xv6) | User executes `int` | High (~hundreds of cycles, IDT lookup, ring change) | Synchronous | xv6 syscalls |
| **`syscall`/`sysret`** | Special instruction | ~½ of `int` | Synchronous | Modern Linux fast syscall |
| **`sysenter`/`sysexit`** | Special instruction | Same family as `syscall` | Synchronous | 32-bit fast syscall |
| **Hardware IRQ** | External pin | Same as int but async | Async, can preempt anything | Devices |
| **Exception** | CPU detects error | Same as int | Sync to faulting instr | PF, DIV0, etc. |
| **Polling (no boundary)** | Cooperative | Lowest per-op | Bounded | Drivers in tight loop |

### Pareto frontier (boundary crossing)
- `syscall`/`sysret` dominates `int` on **performance** with the same protection — `int` survives in xv6 only for **simplicity**.
- Pure polling has lowest cost but loses generality; only pareto-optimal for hot paths.

---

## 10. Performance Analysis — Trap Cost

> **Tags:** `trap cost` `interrupt latency` `syscall latency` `ring change cost`

- ~100s of cycles on modern x86 just for `int + iret`:
  - IDT load, segment register reload, stack switch, optional error code push.
  - Pipeline serialization (no speculative execution across the gate).
- Drives the design choice of **batching** syscalls (e.g., `readv`, `io_uring`, vDSO for `gettimeofday`).
- xv6 doesn't optimize this — uses `int 0x40` with full machinery for every syscall.

### CDF intuition (syscall latency, no contention)
- Tight unimodal at the trap-fixed cost (~µs).
- Adding work inside the syscall just shifts the whole curve right.
- Adding **lock contention** introduces a long flat tail (waiters).
- Adding **page faults inside syscall** adds a disk-IO tail (ms-scale jump).

---


---

## L10 — Concurrency II (Locks & Memory Models)

*([→ xv6 implementation for this lecture](<#L10 — Concurrency II (Locks & Memory Models) — xv6>))*


> **Tags:** `concurrency2` `concurrency II` `L10` `lec10` `locks` `locking` `mutual exclusion` `mutex`
> `spinlock` `atomic ops` `atomic exchange` `xchg` `cas` `compare and swap` `peterson` `peterson algorithm`
> `too much milk` `thread coordination` `data race` `DRF` `DRF0` `sequential consistency` `SC`
> `total store order` `TSO` `memory model` `memory barrier` `fence` `memory ordering`
> `volatile` `interrupt deadlock` `pushcli` `popcli` `acquire` `release` `dining philosophers`
> `lock ordering` `deadlock` `livelock` `starvation` `safety` `liveness` `c11 atomics` `lab2`
> `instruction reordering` `out of order execution` `compiler reordering` `cache coherence`

> **Cross-reference:** Builds on **concurrency1.md** (interrupts as pseudo-concurrency, syscall overlap).
> This sheet is the **mutual-exclusion / locking** half: how to *correctly* serialize shared state when
> multiple flows of control (interrupts, threads, CPUs) touch it. Recurring theme: *"Universal correctness
> must be assured — code must work ALL the time, not just MOST of the time."*

---

## 1. The Core Problem — Why Concurrency Is Hard

> **Tags:** `concurrency problem` `interleaving` `nondeterminism` `universal correctness` `race condition`
> `check then update` `TOCTOU` `time of check time of use`

- **Pseudo-concurrency** (interrupts on a single CPU) and **true concurrency** (multiple CPUs) both create the same hazard: arbitrary interleaving of memory accesses to shared state.
- **Universal correctness:** code must work for **ALL** schedules, not most. Bugs hide in the rare interleaving.
- The mental model for any mutual-exclusion design:
  - What is **checked**?
  - What is **updated**?
  - What other accesses can sneak in **between** check and update? (TOCTOU window.)
- Two correctness properties:
  - **Safety** — *nothing bad happens* (e.g., at most one buyer of milk; at most one writer in the critical section).
  - **Liveness** — *something good eventually happens* (e.g., milk does get bought; a waiter eventually enters CS).
- Race conditions are **hard to reproduce** — only some interleavings expose the bug.
- **Suggestion (slide):** *"better to overlock than underlock — correctness > performance."*

---

## 2. Interrupts vs Locks — The Reentry Problem

> **Tags:** `interrupt deadlock` `interrupt handler lock` `disable interrupts` `cli` `sti`
> `kernel code int handler` `acquire release` `interrupt mutual exclusion`

### Setup
- Kernel code holds a lock around `Shared = 7`.
- An interrupt fires on the **same CPU** while the lock is held; the handler also tries to `Lock()` the same lock → **self-deadlock** on a single CPU (handler spins waiting for the lock the interrupted code holds and will never release because it cannot run).

### Options considered
1. **Make handler ignore the lock** — *No.* Breaks mutual exclusion; defeats the purpose.
2. **Delay (disable) the interrupt while the lock is held** — *Yes.*

### The fix (the xv6 model)
```
Acquire():   interrupt_disable(); Lock();
Release():   Unlock(); interrupt_enable();
```
- Interrupts are **disabled on the local CPU** for the duration of the critical section.
- This **imposes an order**: the kernel CS finishes first, then the interrupt handler runs and can take the lock.
- Mutual exclusion *with an interrupt handler* is achieved by **interrupt disable**, not by the lock alone.

### Key-idea alignment
- **Protection** — prevents a handler from corrupting kernel-internal invariants mid-update.
- **Performance** — disabling interrupts is essentially free vs. blocking on a lock the handler can't release.

---

## 3. "Too Much Milk" — The Canonical Coordination Story

> **Tags:** `too much milk` `bob alice` `fridge note` `coordination problem` `naive lock`
> `leave a note` `producer-consumer canonical`

- Two roommates (Bob, Alice) each independently check the fridge. Both see "no milk", both go buy → **too much milk**.
- Formalized:
  - "Check fridge" = read shared variable.
  - "Put milk in fridge" = write shared variable.
  - **Safety:** at most one buys.
  - **Liveness:** someone buys when needed.
- **Naive fix** (leave a note before going) — fails: the **check-then-leave-note** sequence is itself non-atomic, so both can see no note, both leave one, both buy.
- Lesson: you cannot solve mutex with two ordinary loads/stores **and** a sane number of variables — you need either an atomic primitive (HW), or a clever multi-flag protocol (Peterson).

---

## 4. Peterson's Algorithm — Mutex from Pure Loads/Stores

> **Tags:** `peterson algorithm` `software mutex` `flag turn` `busy wait` `software lock`
> `mutex without atomic rmw` `flag[i]` `turn variable`

```c
// Process P0                          // Process P1
flag[0] = true;                        flag[1] = true;
turn = 1;                              turn = 0;
while (flag[1] && turn == 1) { }       while (flag[0] && turn == 0) { }
// critical section                    // critical section
flag[0] = false;                       flag[1] = false;
```
- **Idea:** each process announces *intent* (`flag[i]=true`); `turn` decides *who yields* in a tie.
- **Correct under sequential consistency** with only atomic loads/stores — no special HW.
- **Why it's "completely impractical":**
  - **Busy-waits** (CPU burning).
  - **Doesn't scale** beyond 2 processes (n-process generalizations exist but are gnarly).
  - **Breaks under TSO / weak memory** — the `flag = true; turn = 1` write order can be reordered as observed by the other thread, violating mutual exclusion. Needs explicit fences.
  - Compilers can also reorder loads/stores absent `volatile`/atomic.
- Verdict: textbook proof that mutex *can* be built without HW — but in practice we **want a HW atomic RMW** instead.

---

## 5. Hardware Atomic Primitives — The Real Way

> **Tags:** `atomic primitives` `atomic rmw` `atomic exchange` `xchg` `cas`
> `atomic_load` `atomic_store` `atomic_fetch_add` `atomic_compare_exchange` `c11 atomics`
> `lock prefix` `bus lock` `cache lock`

### What HW gives us
| Op | Semantics |
|---|---|
| `atomic_load(p)` | indivisible read |
| `atomic_store(p, v)` | indivisible write |
| `atomic_fetch_add(p, n)` | read-modify-write add, returns old |
| `atomic_exchange(p, v)` | swap: indivisibly returns old `*p`, writes `v` (a.k.a. xchg) |
| `atomic_compare_exchange(p, exp, new)` | if `*p == exp`, write `new`, atomically; bool return |

- All implemented on x86 via the `LOCK` prefix (`xchg` is implicitly locked) — locks the cache line / bus while the RMW completes.
- One **atomic load + store together** is the minimum HW capability needed for a lock.

### Building a spinlock from `xchg`
```c
// 1 = locked
int r = 1;
while (r != 0) {
    r = atomic_exchange(&lock, 1);
}
// critical section ...
atomic_store(&lock, 0);   // release
```
- **State diagram** of `(lock, r)` from slides:
  - `(0,1)` — lock free, my reg says locked → `xchg` flips to `(1,0)` = **lock acquired**.
  - `(1,1)` — lock held, my reg locked → `xchg` keeps it `(1,1)` = **spin**.
  - `(1,0)` — *the* successful state, exit loop.
  - `(0,0)` — never reachable from acquire path; only on release.
- **Invariant:** after a successful `xchg`, exactly one thread sees the prior `0` → only one enters CS.

### Key-idea alignment
- **Protection** — atomic RMW guarantees a single winner.
- **Performance** — no software-only n-process gymnastics; HW does it in O(1) on uncontended path.
- **Sharing** — the lock variable itself is shared; the CS contents are exclusive.

---

## 6. Comparison — Mutex Designs

> **Tags:** `mutex comparison` `lock design tradeoffs` `peterson vs spinlock vs disable interrupts`

| Mechanism | Pros | Cons | Tradeoff / When |
|---|---|---|---|
| **Disable interrupts only** | Simplest; cheap; sufficient on **single CPU** | Useless on SMP (other CPU still runs); breaks responsiveness if held long | Single-CPU kernel CS, very short |
| **Peterson (software-only)** | Pure loads/stores; no HW assumption | Busy-wait; 2-thread limit; **broken under TSO** without fences; theoretical only | Pedagogy; embedded systems w/o atomic RMW |
| **Spinlock (xchg)** | Tiny code; fast on short CS | Burns CPU while waiting; can deadlock with interrupts unless `cli` paired | Short CS, multiprocessor, kernel |
| **Spinlock + `cli` (xv6 acquire)** | Composes safely with int handlers | Slightly more state (`pushcli` depth) | Default xv6 mechanism |
| **Sleep/blocking lock** | No CPU burn during wait; long CS friendly | Cost: scheduler invocation, context switch | Long CS, user space, file I/O |
| **Lock-free / wait-free DS** | No blocking; fault tolerant | Hard to design; subtle ABA, memory ordering bugs | High-perf data structures |

### Pareto frontier
- Axes: **CS length** (x) vs **contention overhead** (y, lower better).
- **Spinlock** is Pareto-optimal at **short CS, low/medium contention**.
- **Sleep lock** is Pareto-optimal at **long CS** (any contention).
- **Disable-interrupts-only** is Pareto-optimal at **single-CPU + very short CS** (no atomic needed).
- **Peterson** is **Pareto-dominated** in practice by xchg-spinlock (slower, harder, less general).
- **Lock-free** dominates both spin and sleep at very high contention on small DS but at huge design cost — Pareto-optimal only when the engineering effort is justified.

### CDF intuition
- Spinlock acquire latency CDF: tight near zero (uncontended), fat tail under contention as cache line bounces between cores.
- Sleep lock CDF: bimodal — fast path on free lock, big jump (~µs) on context switch.
- Peterson CDF: similar to spin, plus reordering pathologies → occasional safety violations (not just slow).

---

## 7. Memory Models — Why `mov` Order Lies to You

> **Tags:** `memory model` `sequential consistency` `SC` `total store order` `TSO`
> `weak memory` `instruction reordering` `compiler reordering` `out of order execution`
> `store buffer` `eax ebx puzzle` `WR reorder` `load reorder`

### The classic puzzle
```
Initially x = y = 0
T1: movl $1, (x);    movl (y), %eax
T2: movl $1, (y);    movl (x), %ebx
```
Possible end states:
- `B: eax=0, ebx=1` — T1 reads y before T2 stores; T2 then runs to completion.
- `C: eax=1, ebx=0` — symmetric.
- `D: eax=1, ebx=1` — both stores, then both loads.
- `A: eax=0, ebx=0` — *should be impossible* under sequential consistency, but **is observable on real x86** (TSO).
- Answer: **{B, C, D, A}** — *all four can happen*.

### Memory-model spectrum
| Model | What's guaranteed | Where |
|---|---|---|
| **Sequential Consistency (SC)** | Some global interleaving consistent w/ each thread's program order | Idealized model; what programmers naively assume |
| **Total Store Order (TSO)** | **W→W**, **R→R**, **R→W** ordered. **W→R** can reorder (later loads bypass earlier stores via store buffer). | x86 / x86-64 |
| **Weak/Relaxed (ARM, POWER)** | Almost no order without explicit fences | ARM, RISC-V, POWER |

- **TSO mechanism:** each CPU has a **store buffer**. Stores wait there before becoming globally visible; subsequent loads can satisfy from buffer or read older values from memory → load appears to happen before store.
- The `(eax=0, ebx=0)` outcome happens because each CPU's store sits in its own buffer while it executes the load.

### Compiler reordering
- C/C++ compilers reorder freely under the as-if rule for **single-threaded** semantics.
- Multi-threaded code without atomics or fences gets undefined behavior on data races.

### Fixing it: fences
- `mfence` / `LOCK`-prefixed ops on x86 — drain the store buffer; subsequent loads see all prior stores globally.
- C11 atomics encode this with `memory_order_*` (`relaxed`, `acquire`, `release`, `acq_rel`, `seq_cst`).

### Granularity of ordering
| Granularity | Cost | Use |
|---|---|---|
| `relaxed` | Cheap (just atomicity) | Counters, stats |
| `acquire` (load) / `release` (store) | One-way fence | Lock acquire/release |
| `acq_rel` | Both directions | RMW (atomic_exchange in lock) |
| `seq_cst` | Full fence | Default; safest, slowest |
- **Tradeoff:** weaker order = faster but easier to write subtle bugs. Default to `seq_cst` unless profiling demands otherwise.

### Key-idea alignment
- **Performance** — TSO + store buffer hide store latency → faster pipelines.
- **Sharing** — relaxed models allow more aggressive cache behavior across cores.
- **Protection** — fences re-establish ordering needed for invariants.

---

## 8. DRF0 — The Programmer's Contract

> **Tags:** `DRF` `DRF0` `data race free` `data race definition` `sequentially consistent`
> `synchronization` `happens before`

- **Data race definition:** *> 1 access to the same memory location, at least one of which is a write, with no synchronization between them*.
- **DRF0 contract (C/C++11 onward):** *if your program is data-race-free, the language guarantees sequentially-consistent execution.*
- Practical implication:
  - Use locks / atomics around shared mutable state → DRF → SC → reasonable to reason about.
  - Touch shared state without sync → data race → undefined behavior.
- **Takeaway:** "Use provided synchronization primitives any time there's a possibility of having a data race." Think from first principles, use FSA, check safety + liveness.

### SLOs / objectives
- **Correctness SLO** — 0 data races (binary, hard).
- **Latency SLO** — *p99 acquire latency*; heterogeneous: short uncontended ~10 ns, contended cache-bouncing ~µs, sleep-lock context switch ~µs+.
- **Throughput SLO** — ops/sec under N threads; usually flat or **negative** scaling on a hot lock (Amdahl).
- These SLOs are **heterogeneous across mechanisms** — spinlock has a tight latency distribution but bad scaling; sleep lock has higher minimum but better tail under heavy contention.

---

## 9. `volatile` — The Most Misunderstood Keyword

> **Tags:** `volatile` `volatile considered harmful` `volatile not atomic` `mmio` `device driver`
> `volatile vs atomic`

- `volatile` tells the compiler: **"this variable may change unexpectedly — don't cache it in a register, don't elide reads/writes."**
- It does **NOT**:
  - Provide atomicity.
  - Insert memory barriers.
  - Stop CPU reordering.
  - Substitute for synchronization between threads.
- **When useful:** writing **memory-mapped I/O / device drivers** — when reading/writing a device register, the compiler must not optimize the access away.
- **In kernel code:** "almost never correct" (per `volatile-considered-harmful.html`).
- **Replacement:** use C11 atomics (`atomic_int`, `atomic_load`, `atomic_store`, etc.) — they have language-defined memory ordering.

---

## 10. Deadlock & Lock Ordering

> **Tags:** `deadlock` `dining philosophers` `lock ordering` `cycle of doom` `circular wait`
> `multiple locks` `lock hierarchy` `impose order`

### Necessary conditions (Coffman, classic)
1. Mutual exclusion.
2. Hold-and-wait.
3. No preemption.
4. Circular wait.

### Dining philosophers
- N philosophers around a table, N forks, each needs **2 forks** (left + right) to eat.
- All grab left fork simultaneously → all wait for right → **circular wait → deadlock**.
- **Fixes (slide):**
  - **Break the cycle of doom** — e.g., one philosopher grabs right first.
  - **Impose a (global) order** — number forks 1..N; always acquire **lower-numbered first**. Eliminates cycles by construction.
- Lock ordering is the standard kernel discipline.

### xv6 multi-lock cases
- xv6 holds **at most two locks** simultaneously.
- Examples:
  - `ideintr` holds the `ide` lock and calls `wakeup()` which acquires `ptable.lock`.
  - File system: must lock directory **and** file (parent before child).
- **Solution:** kernel programmer must know what locks should be held, and acquire them in a globally-consistent order.

### Spinlock shortfalls
- Complex call graphs (`allocproc` ↔ `fork` ↔ `userinit` ↔ `ptable.lock`) — if every function blindly acquires its lock, recursion + multi-acquire → deadlock.
- **Solutions:**
  - **Enforce locking rules** — caller documents what's held; callee assumes/asserts.
  - **Recursive (reentrant) locks** — same thread can re-acquire; counts depth. *Complex; xv6 avoids.*
- **Pipe read/write** is another classic: who holds the buffer lock during a blocking read?

### Granularity tradeoffs
| Granularity | Pros | Cons |
|---|---|---|
| **Coarse (1 big lock)** | Simple, deadlock-easy to reason | Awful contention; serializes everything |
| **Medium (per-subsystem)** | Better concurrency | Risk of deadlock between subsystems; need ordering |
| **Fine (per-object / per-bucket)** | Max concurrency | Many locks held at once; complex; cache-line ping-pong |
| **Lockless** | No blocking | Hardest to write correctly |

xv6 sits at coarse-medium (one `ptable.lock`, one `kmem.lock`, per-inode locks).

### Key-idea alignment
- **Protection** — mutual exclusion of invariants.
- **Performance** — granularity *is* the performance lever.
- **Sharing** — locks regulate which threads see consistent state.

---

## 11. Real-World Notes (from slide)

> **Tags:** `real world locks` `pthreads` `lock free` `cache line bouncing` `false sharing`

- Concurrency is an active research area; primitives like spinlocks/atomic ops are the **bottom** of the stack.
- Build **higher-level constructs** on top — *xv6 doesn't*; libraries like **pthreads** do (mutex, rwlock, cond, barrier, semaphore).
- Lock-free data structures and algorithms exist (Treiber stack, Michael-Scott queue, RCU) — high-perf option.
- Performance landmines:
  - **Cache-line bouncing** — lock variable's cache line ping-pongs between CPUs (MESI invalidations).
  - **False sharing** — unrelated variables on the same cache line accidentally cause invalidations.
  - **NUMA effects** — remote cache-line acquisition is slow.

---

## 12. Quick Lock Recipe

> **Tags:** `locking recipe` `how to lock` `acquire critical section release`

```c
// 1. identify shared state
// 2. identify all flows that touch it (threads, interrupt handlers)
// 3. choose a lock
// 4. acquire BEFORE first access, release AFTER last
acquire(&lock);     // disables interrupts on this CPU + xchg spin
// === critical section: read & write shared state ===
release(&lock);     // restore interrupts + atomic store 0
```
**Rules of thumb:**
- Hold lock the **minimum** time. Long CS = bad scalability.
- Never call into something that may sleep / re-acquire the same lock.
- Document **invariants** the lock protects.
- **Overlock > underlock** while learning.

---


---

## L11 — Schedulers

*([→ xv6 implementation for this lecture](<#L11 — Schedulers — xv6>))*


> **Tags:** `schedulers` `scheduler` `scheduling` `L11` `lec11` `cpu scheduling` `process scheduling`
> `multiplexing` `time sharing` `time slicing` `quantum` `timeslice` `context switch` `swtch`
> `yield` `sched` `scheduler thread` `kernel thread` `coroutine` `coroutines` `forkret`
> `round robin` `RR` `FCFS` `SJF` `SRTF` `priority scheduling` `MLFQ` `multilevel feedback queue`
> `min JCT` `MinJCT` `WFQ` `weighted fair queuing` `CFS` `completely fair scheduler` `nice` `nice value`
> `real time` `RTOS` `hard real-time` `soft real-time` `dispatch latency` `EDF` `rate monotonic`
> `SCHED_OTHER` `SCHED_IDLE` `SCHED_BATCH` `SCHED_FIFO` `SCHED_RR` `cpu-bound` `io-bound`
> `interactive` `batch` `throughput` `latency` `response time` `tail latency` `SLO` `QoS`
> `fairness` `starvation` `convoy effect` `gantt chart` `delayed scheduling` `power of two choices`
> `tetrisched` `spatio-temporal bin packing` `non work-preserving` `cdf` `cumulative distribution`
> `xv6 scheduler` `ptable.lock` `swtch.S` `cpu->scheduler` `proc->context` `RUNNABLE`
> `preemptive` `cooperative` `nonpreemptive` `elevator scheduling` `disk scheduling`

> **Big-picture:** Why does the OS even *need* a scheduler? **Multiplexing** — many resource consumers,
> a scarce shared resource (CPU). A scheduler is the *mechanism + policy* that decides "who runs next,
> and for how long." This sheet covers the **conceptual design space** (goals, tradeoffs, algorithms)
> first, then the **xv6 mechanism** (`swtch`, `yield`, `sched`, scheduler loop) at the end.

---

## 1. Why Schedulers Exist — The Multiplexing Argument

> **Tags:** `scheduling motivation` `why scheduler` `multiplexing rationale` `resource sharing`

- Trivial cases need no scheduler:
  - **1 process in the system** → just run it.
  - **2 processes & 2 CPUs** → one each, no contention.
- Scheduling is needed when **multiple consumers share a scarce resource** → **multiplexing** is the key idea.
- Scheduler is one of the OS mechanisms enabling:
  - **Process isolation** (no process monopolizes the CPU; fault containment via preemption).
  - **Resource multiplexing** — *fairness* and *resource utilization*.
- Schedulers are everywhere: **processes, disk, network, cloud schedulers (Borg/K8s), AI/GPU schedulers (token-level LLM serving)**.
- **Goal of any scheduler:** *maximize the amount of work we care about* — and "work we care about" is workload-specific.

### Key-idea alignment
- **Multiplexing** — primary purpose: share scarce CPU among many runnable threads.
- **Isolation** — preemptive scheduling prevents one runaway from starving others.
- **Performance** — chosen policy directly determines throughput, latency, tail latency.
- **Sharing** — fair allocation across users / cgroups / weights.
- **Protection** — only the kernel context-switches; user code can't pin itself on a CPU.

---

## 2. Scheduling Goals — The Optimization Setup

> **Tags:** `scheduling goals` `throughput` `latency` `response time` `slo` `cost` `objective function`
> `elevator scheduling` `actuation delay` `declarative requests` `coda elevators`

Scheduling is fundamentally an **optimization problem** with a workload-specific objective:

| Objective                         | Example workload                           | What you maximize/minimize    |
| --------------------------------- | ------------------------------------------ | ----------------------------- |
| **Throughput**                    | disk (elevator/SCAN), batch jobs           | jobs completed per unit time  |
| **Response time**                 | social-media feed, interactive UI          | time-to-first-byte            |
| **Tail latency / SLO attainment** | ad serving, LLM inter-token latency, AR/VR | P99 ≤ deadline                |
| **Cost**                          | cloud, datacenter                          | $/job, energy, $/SLO          |
| **Fairness**                      | shared multi-tenant systems                | min-max share, weighted share |

- **Elevator (SCAN) scheduling** assumes **non-trivial actuation delay** — moving the head dominates over thinking time. Order-of-magnitude perf differences as a function of access pattern.
- **Declarative requests** (e.g., Coda elevators, TetriSched) describe *what* you want (deadline, group, locality), not *how* to schedule — scheduler picks a feasible plan.
- **Tail latency:** the right tail of the latency CDF (e.g., P99). What matters for user-facing services.
- **SLO (Service Level Objective):** numeric target like "P99 ≤ 36 ms." A latency-CDF curve is the right visualization.

### CDF / PDF refresher (latency-distribution analysis)
- **PDF:** `y = P(X = x)` — density.
- **CDF:** `y = P(X ≤ x)` — fraction of requests faster than `x`.
- Reading a latency CDF:
  - x-axis = latency (ms), y-axis = fraction of requests.
  - **Steeper / further left** = better (lower latency).
  - **Long thin right tail** = bad tail latency (a few requests very slow).
  - Vertical line at the **SLO** (e.g., 36 ms) → CDF value at that x is the **SLO attainment** (e.g., 0.99 = 99% meet SLO).
- **Tail latency** = the right-tail point you care about, typically P99 or P99.9.

```
     CDF
1.0 |- - - - - - - - - - - - - ─────────  ← SLO miss = 1 - CDF(SLO)
    |                       ╱
0.9 |                   ╱
    |               ╱
0.5 |          ╱           ← median
    |     ╱
0.0 |╱_______________________│____________
                            SLO        latency
```

---

## 3. Scheduling Costs vs Benefits

> **Tags:** `scheduling costs` `context switch cost` `caching cost` `scheduler complexity`
> `predictability` `qos benefit` `priority allocation` `interposition cost`

### Costs
- **Context switching**:
  - **CPU switching computation** (save/restore registers, swap page table, swap kernel stack).
  - **Cache & TLB pollution** (warm caches lost; cold-start cost on the next CPU burst). Often dominates the direct cost.
- **Scheduler time complexity** — the decision itself runs on the critical path. `O(n)` linear scan vs `O(log n)` heap vs `O(1)` per-priority queue (O(1) Linux scheduler) vs `O(log n)` red-black tree (CFS).
- **Predictability** — tighter for RTOS; harder for general-purpose with feedback policies.

### Benefits
- **Better resource utilization** (overlapping CPU and I/O).
- **More work on important tasks** — priority allocation directs CPU at higher-value work.
- **Stronger QoS / SLO properties** — bound tail latency, isolate noisy neighbors, hit deadlines.

### Systems-conjecture triangle (pick at most two)
```
              simplicity
              /        \
     performance ───── cost
```
- e.g., **FCFS** is simple + cheap, but bad performance under burst.
- **MLFQ / CFS** are high performance but more complex.
- **Real-time + provably bounded** is performant + simple but expensive (over-provision to admission-control).

---

## 4. Scheduler Design Space — Axes

> **Tags:** `scheduling design space` `preemptive vs cooperative` `global vs local` `quantum granularity`
> `fairness epoch` `scalability` `realtime constraints` `qos priority` `nice` `1M processes`

| Axis | Choices | What it changes |
|---|---|---|
| **Throughput vs latency** | optimize one or the other | objective function |
| **Fairness** | time quota, epoch (in heterogeneous-task contexts) | who waits, who runs |
| **QoS / priority** | flat / nice / strict priority bands | preemption order |
| **Pre-emptive vs cooperative** | timer-driven vs voluntary `yield` | bounded latency vs simplicity |
| **Global vs local (resource state visibility)** | one runqueue vs per-CPU runqueues | scalability vs balance |
| **Scalability** | ready-queue data structure | feasibility at 1M procs/cores |
| **Granularity (quantum)** | 10 ms / 100 ms / dynamic | tail-latency vs CSW overhead |
| **Constraints** | realtime, deadlines (e.g., airplane) | hard guarantees vs best-effort |
| **Work-conserving?** | always run if work is ready, vs delayed scheduling | locality vs utilization |

Recurring point from the slides: **"contradicting / heterogeneous goals."** No universal/perfect policy:
- maximizing throughput vs minimizing latency
- minimizing response time vs maximizing scalability
- maximizing fairness vs maximizing scalability
- maximizing utilization vs minimizing power

> **Concept — fluidity / spatio-temporal granularity:** "sand or water" — finer-grained scheduling units pack more tightly into a fixed cluster, like water vs gravel. Spatio-temporal bin packing (TetriSched, EuroSys'16) treats jobs as 2-D bricks (cores × time) and stacks them.

> **Non-work-preserving** schedulers leave a CPU idle even when work is ready — *delayed scheduling* (EuroSys'10) waits for a more locality-friendly slot. Trades a tiny bit of utilization for big locality wins.

---

## 5. Granularity (Quantum / Timeslice) Tradeoff

> **Tags:** `quantum granularity` `timeslice` `dispatch quantum` `granularity tradeoff` `dynamic quantum`

| Quantum | Pros | Cons |
|---|---|---|
| **Very small (≤1 ms)** | low response latency; near-RT feel | huge CSW overhead; cache thrash; scheduler itself dominates CPU |
| **Medium (~10 ms — Linux default tick)** | balanced; good interactive feel | bursty CPU-bound jobs hold the CPU 10 ms before yielding |
| **Large (~100 ms+)** | minimal CSW cost; cache-friendly | poor interactive latency; "stuttering" UI |
| **Dynamic** (CFS-style virtual runtime) | adapts: short for many runnable, longer when few | complex; harder to reason about worst-case |

- **Tail-latency curves** flatten as quantum decreases (lower P99 wait), but mean throughput drops once CSW overhead dominates → there is a **U-shaped** sweet spot.
- RTOS quanta are tiny *and* deterministic; commodity OS use larger heuristic quanta.

### Worked example — picking quantum from a tail-latency SLO

> **Tags:** `quantum from SLO` `time quanta calculation` `inference time quantum` `100ms SLO`
> `tail latency budget` `serve time vs quantum` `ML inference quantum` `quanta sizing`

**Setup:** A request takes `S = 50–100 ms` to serve (e.g., ML inference). The SLO is **P99 tail latency ≤ 100 ms**.
- Worst-case wait under a non-preemptive scheduler with quantum `Q` ≈ `Q − ε` (one in-flight request you queued behind).
- Total tail latency ≈ `wait + S` ≤ SLO ⇒ `Q + S_max ≤ SLO`.
- With `S_max = 100 ms` and SLO = 100 ms, this is already saturated by service time alone — so the only way to meet it is `Q ≥ S_max` and **don't preempt mid-request**: set **Q = 100 ms** so each request runs to completion in one slice.
- **Why not smaller Q?** A 10 ms slice would preempt a 100 ms inference 9 times, paying 9× context-switch + cache-flush overhead and *increasing* tail latency.
- **Why not larger Q?** Doesn't help — once `Q ≥ S_max` you're run-to-completion; bigger Q just hurts other workloads behind you (head-of-line blocking).
- **General rule:** for **homogeneous, latency-tight workloads**, set quantum near the service-time upper bound. For **interactive workloads** with short bursts, set Q small (≪ service time) so the next interactive event preempts quickly.

**Homogeneous vs heterogeneous objective check** (ties to L22):
- **ML training**: throughput-oriented, long jobs, tolerates preemption — wants **large quantum** + SJF-like / SRTF avoided (no advantage on long jobs of similar length).
- **ML inference**: latency-oriented, short jobs, tail-bound — wants **quantum ≈ service time**, EDF-like / SlackFit, never preempted mid-request.
- **Mixed deployment** ⇒ **heterogeneous SLOs** ⇒ a single global quantum is wrong; need per-class queues (MLFQ-style) or a Pareto-aware policy (SlackFit, L22).
- **CFS works for training** (proportional-share, fair) but **fails for inference** (no notion of deadlines or service-time budget). **SJF works for inference** *if* you can predict service time (which SuperServe profiles offline). **RL for ML scheduling: bad** — too high decision latency for sub-100 ms inference deadlines, training itself has slow feedback signal.

---

## 6. Algorithms Compared (the "many potential solutions")

> **Tags:** `FCFS` `SJF` `SRTF` `priority` `round robin` `multilevel queue` `multilevel feedback queue`
> `MLFQ` `MinJCT` `WFQ` `CFS` `convoy effect` `gantt chart`

### 6.1 FCFS — First-Come First-Served
- Run-to-completion, queue order. Non-preemptive.
- **Convoy effect:** one long job blocks all short jobs behind it → terrible mean wait.
- Pro: simple, starvation-free, fair-by-arrival. Con: latency-blind, throughput-blind.

### 6.2 SJF / SRTF — Shortest Job First / Shortest Remaining Time First
- **Provably optimal** for **mean turnaround time / mean JCT** (when burst lengths are known).
- SRTF = preemptive variant.
- Cons: requires burst-length oracle (or estimator); long jobs **starve** under sustained short-job stream.

### 6.3 Priority scheduling
- Pick highest-priority RUNNABLE.
- **Starvation** of low priority → mitigated by **aging** (raise priority over wait time).
- Generalizes SJF (priority = inverse remaining burst).

### 6.4 Round-Robin (xv6's choice)
- Fixed quantum; cycle the runqueue.
- **Pros:** simple, **starvation-free**, no priority needed, easy to implement.
- **Cons:** doesn't distinguish urgency, deadline-unaware, doesn't reconcile throughput vs latency.
- Quantum tuning is critical (see §5).

### 6.5 Multi-Level Queue
- Multiple queues, each with its own discipline (e.g., interactive RR + batch FCFS). Strict priority between queues.

### 6.6 MLFQ — Multi-Level Feedback Queue
- *Learns* a job's class by behavior:
  - New job starts at top (highest) priority.
  - **Used full quantum** → demote (probably CPU-bound).
  - **Yielded early / blocked on I/O** → keep / promote (interactive).
- Periodic **priority reset (boost)** prevents starvation and reacts to phase changes.
- Approximates SJF without an oracle.

### 6.7 MinJCT
- Optimize for **minimum job completion time** — used in modern cluster/AI schedulers.

### 6.8 WFQ — Weighted Fair Queuing  →  CFS
- Each process has a **weight**; over a window, process gets `weight_i / Σweight_j` of CPU.
- **CFS (Linux):** WFQ implementation.
  - Tracks **virtual runtime (vruntime)**; always pick the process with the **smallest vruntime**.
  - Weight comes from **`nice`** value (`nice -20` … `nice 19`); each step ≈ 1.25× CPU.
  - Red-black tree of runnable tasks keyed by vruntime → `O(log n)`.
- **Sleep handling implication:** a process that sleeps doesn't accumulate vruntime → on wakeup it has the **smallest** vruntime → it preempts CPU-bound rivals → **interactive boost** falls out automatically.

### 6.9 Linux's "high-performance" Modern Idea (motivating CFS)
- *Observation:* "Processes that constantly use full CPU are likely lower priority than those that mostly sleep" (e.g., network servers spend most time sleeping but need fast turnaround).
- *Idea:* **Reduce priority from processes that always consume full CPU.**
- This is what MLFQ and CFS-via-vruntime both encode.

### Algorithm comparison table

| Algorithm | Preemptive? | Starvation-free? | Latency | Throughput | Complexity | Key idea |
|---|---|---|---|---|---|---|
| FCFS | No | Yes | Bad (convoy) | OK | O(1) | None |
| SJF | No | **No** | Good (mean) | Best mean JCT | Needs oracle | Pick shortest |
| SRTF | Yes | **No** | Best mean JCT | Best | Needs oracle | Preemptive SJF |
| Priority | Either | **No** (need aging) | Tunable | Tunable | O(log n) | Strict urgency |
| RR (xv6) | Yes (timer) | Yes | Bounded | OK | O(1) | Fixed quantum |
| Multi-Level | Yes | **No** between classes | Class-tunable | Class-tunable | O(1) per class | Class separation |
| MLFQ | Yes | Yes (with boost) | Good | Good | Moderate | Learn behavior |
| WFQ / CFS | Yes | Yes | Good (interactive bias) | Good | O(log n) | Proportional fairness |

---

## 7. Pareto Frontier — Where Each Sits

> **Tags:** `pareto frontier` `pareto optimal` `tradeoff frontier`

Axes used: **mean latency (lower better)** vs **implementation simplicity (higher better)**, with throughput roughly fixed.

```
simplicity
  ^
  | FCFS ●  RR ●
  |              ● Priority
  |                       ● MLFQ
  |                              ● CFS / WFQ
  |                                          ● SRTF (oracle)
  +-----------------------------------------------> low latency
```

- **Pareto-optimal** (no other point strictly dominates): **FCFS** (cheapest+simplest), **RR** (simplest preemptive), **MLFQ**, **CFS**, **SRTF** (best latency given oracle).
- **Pareto-dominated:** "priority without aging" (SRTF dominates it on latency, RR dominates it on starvation-freedom). Strict multilevel queue without feedback is dominated by MLFQ.
- General-purpose OSes converge on **CFS-like** because it offers near-best latency with reasonable simplicity *without* needing a burst oracle.

### Key-idea alignment of each algorithm

| Algorithm | Primary key idea served |
|---|---|
| FCFS | **Sharing** (raw fairness-by-arrival) |
| SJF/SRTF | **Performance** (min mean JCT) |
| Priority | **Performance / Protection** (urgency-based) |
| RR | **Multiplexing / Isolation** (no starvation, equal share) |
| MLFQ | **Performance + Multiplexing** (adapts to workload class) |
| CFS / WFQ | **Sharing + Performance** (proportional fairness) |
| RT (EDF/RM) | **Protection / Isolation** (deadline guarantees) |

---

## 8. Two CPU-Scheduling Scenarios — Why One Policy Doesn't Fit

> **Tags:** `long jobs vs short jobs` `fcfs short jobs` `preemptive short jobs` `workload mix`
> `delayed scheduling` `power of two choices` `tetrisched`

| Scenario | Best fit | Reason |
|---|---|---|
| **Long-running jobs** (batch, training) | **FCFS / non-preemptive** | CSW cost amortized over hours; preemption hurts caches/locality. |
| **Very short jobs** (RPCs, web requests) | **Preemptive SRTF / CFS** | Don't let a single 100 ms request block 10,000 sub-ms requests. |

Other modern scheduling techniques referenced in lecture:
- **Delayed scheduling (Zaharia, EuroSys'10)** — wait briefly for a locality-preserving slot. *Non-work-preserving*.
- **Power of two choices** — sample 2 random servers, pick less-loaded. Near-optimal global behavior with O(1) info.
- **Spatio-temporal bin packing (TetriSched, EuroSys'16)** — 2-D placement: cores × time × constraints.

---

## 9. Real-Time Scheduling

> **Tags:** `real-time scheduling` `RTOS` `hard real-time` `soft real-time` `dispatch latency`
> `priority scheduling RT` `urgency aware` `secondary storage RT` `virtual memory RT`

- **Hard real-time** — *missing a deadline = system failure* (avionics, ABS). Requires a **bounded worst-case execution time (WCET)** for everything on the path.
  - **Impractical with secondary storage / virtual memory** — page faults, disk seeks, swap → unbounded latency. Hard RT systems pin pages and avoid disk on critical paths.
- **Soft real-time** — critical tasks get *priority over less-critical*, but occasional misses are tolerated (audio, video, AR/VR).
  - **Two requirements:**
    1. **Priority scheduling** (urgency-aware, preemptive).
    2. **Low dispatch latency** — time from "wake" to "first instruction." Often missed because:
       - Kernel may not preempt syscalls in progress (need preemptible kernel).
       - Interrupt masking inside critical sections raises dispatch latency.
- Classical RT algorithms (not deeply covered but worth recognizing): **Rate Monotonic (RM)**, **Earliest Deadline First (EDF)**.

### Granularity for RT
- Quantum is usually irrelevant: a hard-RT scheduler is **event-driven** — preempt the moment a higher-priority task wakes; don't wait for a tick.

### SLO homogeneity in RT vs general-purpose
- **RT SLOs** are **homogeneous and explicit** per task (each has a deadline). Implies dedicated, often static, scheduling.
- **GP SLOs** are **heterogeneous and implicit** ("interactive should feel snappy", "batch can wait"). Implies feedback-based heuristics (MLFQ, CFS).
- Mixing RT + GP on one OS → split policies (Linux's SCHED_FIFO/SCHED_RR run *above* SCHED_OTHER).

---

## 10. Process Characterization — Class-Aware Scheduling

> **Tags:** `process classes` `cpu-bound` `io-bound` `interactive` `batch` `real-time process`
> `tbt` `qps` `inter-token latency`

| Class | Examples | Wants |
|---|---|---|
| **CPU-bound** | numeric kernels, compilers, training | throughput; long quanta |
| **I/O-bound** | DB server, web server | low dispatch latency; short quanta; preempt CPU jobs |
| **Interactive** | vim, emacs, shell | response time |
| **Batch** | cronjob, ETL | throughput, energy efficiency |
| **Real-time** | audio, video, AR/VR, chatbot/LLM | both **QPS** *and* **inter-token / TBT (time-between-tokens) deadline** — throughput **and** latency simultaneously |

- General-purpose schedulers don't *ask* the process its class — they **infer** it from observed behavior (CPU usage, blocking patterns), à la MLFQ / CFS sleep-handling.

---

## 11. Linux Scheduling Policies (per-process, set via `sched_setscheduler`)

> **Tags:** `SCHED_OTHER` `SCHED_NORMAL` `SCHED_IDLE` `SCHED_BATCH` `SCHED_FIFO` `SCHED_RR`
> `linux scheduling classes` `scheduling policies linux` `sched_setscheduler` `chrt`

| Policy | Class | Description |
|---|---|---|
| **`SCHED_OTHER`** (`SCHED_NORMAL`) | CFS | Default time-share / weighted fair; what almost every process uses. |
| **`SCHED_IDLE`** | CFS | Very low priority; only runs when nothing else wants CPU. |
| **`SCHED_BATCH`** | CFS | CPU-intensive, non-interactive; scheduler avoids interactive boost. |
| **`SCHED_FIFO`** | RT | Strict priority, **no quantum**, runs until it blocks/yields. |
| **`SCHED_RR`** | RT | Strict priority + RR within same priority (with quantum). |

- RT policies (FIFO/RR) trump all CFS classes — a runaway `SCHED_FIFO` task can lock up the system; root-only by default.

---

## 12. Mechanism — How the OS Actually Switches CPUs

> **Tags:** `context switch mechanism` `kernel context` `cpu scheduler thread` `scheduler thread`
> `swtch` `coroutine` `kstack` `kernel stack` `scheduler stack`

### What we **want** to do
- Logically: *"cleanly hand the CPU from process A to process B"* — a single kernel-context arrow from A's kstack to B's kstack.

### What we **have** to do
1. **User → kernel transition** in process A (timer interrupt or syscall trap).
2. **Context switch** from A's kernel thread → CPU's **scheduler thread** (saves callee-save regs onto A's kstack, jumps to scheduler stack).
3. Scheduler picks B (runnable).
4. **Context switch** from scheduler thread → B's kernel thread.
5. **Trap return** in B (kernel → user).

Important invariant: **xv6 never directly switches user-space → user-space.** Every CSW goes **through kernel** (and through the per-CPU scheduler thread).

### Two kinds of context switch in xv6
- **proc-kernel-thread → CPU scheduler thread** (giving up).
- **CPU scheduler thread → proc-kernel-thread** (granting).

### Why a per-CPU scheduler thread?
- A clean **rendezvous point**: the running thread always exits via `sched`, the scheduler always picks the next via the loop. This pattern is a **coroutine**.

### Implementation challenges (lecture summary)
| Challenge | Mechanism |
|---|---|
| Switch from one process to another | Context switching (`swtch`) |
| Make context switching **transparent** | Timer interrupts (preemption) |
| Switch among processes running concurrently on multiple CPUs | Locking (`ptable.lock`) |
| Coordinate processes (wait for events) | Sleep on events (pipe write, child exit) — covered in Concurrency I & Ordering+Waiting |

---


---

## L12 — Ordering, Waiting & Context Switch

*([→ xv6 implementation for this lecture](<#L12 — Ordering, Waiting & Context Switch — xv6>))*


> **Tags:** `ordering` `waiting` `L12` `lec12` `condition variable` `cv` `condvar` `monitor`
> `producer consumer` `bounded buffer` `signal` `broadcast` `wait` `spurious wakeup`
> `mesa semantics` `hoare semantics` `weak ordering` `relaxed consistency` `partial order`
> `happens before` `data race` `race condition` `ordering primitive` `liveness` `efficiency`
> `sleeplock` `sleep wakeup` `wait list` `wait queue` `waitlist` `chan` `wakeup1`
> `coroutine` `swtch` `sched` `yield` `scheduler` `context switch` `kernel context`
> `kstack` `callee saved` `voluntary preemption` `cooperative` `ptable.lock` `forkret`
> `SCHED_OTHER` `SCHED_FIFO` `SCHED_RR` `SCHED_IDLE` `SCHED_BATCH` `CFS` `lab3` `lab4`

> **Cross-reference:** Successor to **concurrency2.md** (mutex / mutual exclusion). That sheet
> answered *"how do we serialize?"*; this one answers *"how do we **order** events across threads
> and how do we **wait** efficiently when there is nothing to do?"* The scheduling-policy half
> (Linux CFS, MLFQ, lottery, RT priorities) lives in **schedulers.md** — this sheet only covers
> the **mechanism** (swtch / yield / sched / scheduler) that L12 introduces alongside CVs.

---

## 1. Locks Revisited — What Do They *Actually* Enforce?

> **Tags:** `mutex purpose` `mutual exclusion recap` `locks vs ordering`

- **Lock = Mutex = Mut**ual **Ex**clusion.
- A lock guarantees: at most one thread is **inside the critical section** at a time.
- It does **NOT** by itself guarantee:
  - **Which** thread enters first (no fairness, no priority).
  - **When** a thread enters (no liveness/wait time bound).
  - That a thread will *wait* for some external **condition** before proceeding.
- Implication: locks give us a tool, but lots of coordination problems (producer/consumer, barriers, pipelines) need *more* than mutual exclusion.

---

## 2. Data Races vs. Race Conditions

> **Tags:** `data race definition` `race condition` `unordered access` `TOCTOU recap`

| Term | Definition | Example |
|---|---|---|
| **Data race** | Two **unordered** accesses to the same memory location, at least one of which is a **write**. (HW-level, breaks memory model assumptions.) | Two threads `x++` with no lock. |
| **Race condition** | Logic-level bug where the program's outcome depends on scheduling order, **even if every individual access is properly synchronized**. | Consumer `if (!q.empty()) pop()` after another consumer drained the queue between check and pop. |

- **Locks fix data races** (provide mutual exclusion → ordered accesses).
- **Locks alone do NOT fix race conditions** — you also need to *re-check* invariants after any blocking call (hence the `while` loop around `cv.wait`).

---

## 3. Weak Ordering / Relaxed Consistency

> **Tags:** `weak ordering` `relaxed consistency` `memory model` `reorder` `partial order`
> `acquire release semantics` `happens before`

- HW + compiler may **reorder** loads/stores **as long as the *executing thread* sees a consistent result**. Other threads can observe stores out of order.
- Without explicit synchronization, **almost no cross-thread ordering guarantees** exist.
- A thread may even see another thread's writes to *different* variables at *different* times (no global clock).
- **Locks are an ordering mechanism**:
  - **acquire** → all subsequent reads/writes in current thread happen *after* the acquire (hoists nothing past it forward).
  - **release** → all preceding reads/writes in current thread happen *before* the release (hoists nothing past it backward).
- This gives a **partial order** (a.k.a. *happens-before* relation):
  - Within one thread: program order.
  - Across threads: only `release(L) → acquire(L)` pairs supply edges.

### Three points on the ordering spectrum

| Level | Example | What you see | Cost |
|---|---|---|---|
| **Unordered** | No locks, no fences. | All interleavings possible (Rt₁,Rt₂,Wt₁,Wt₂ in any order). | Free, but unsound. |
| **Partially ordered** (locks) | Two CSes; either `[Rt₁ Wt₁][Rt₂ Wt₂]` or `[Rt₂ Wt₂][Rt₁ Wt₁]`. | Critical sections do not interleave; *outside* the CS still racy. | Cheap (lock contention only). |
| **Fully ordered** (sequential consistency / strong memory model) | All threads observe one global serialization. | Exactly one globally visible sequence of all ops. | Expensive (every load/store fenced). |

- Locks *reduce* the space of possible interleavings; they do **not** eliminate it (still 2^N orderings of N CSes).

---

## 4. Why Mutex Alone Is Not Enough — Producer/Consumer

> **Tags:** `producer consumer` `bounded buffer` `mutex insufficient` `waiting motivation`
> `safety liveness efficiency`

Three properties to evaluate any synchronization scheme:

1. **Safety** — invariants hold (no popping an empty queue).
2. **Liveness** — every well-formed request eventually completes.
3. **Efficiency** — CPU does productive work while waiting.

### Attempts (the slide's incremental build)

| Attempt | Code (consume) | Safety | Liveness | Efficiency |
|---|---|---|---|---|
| **A. lock + unconditional pop** | `lock; v=q.pop(); unlock` | ✗ pops empty queue | ✗ no wait at all | n/a |
| **B. lock + `if (!empty) pop`** | `lock; if(!empty) v=q.pop(); unlock` | ✓ | ✗ caller never knows it failed; nothing to wake on | ✓ no spin |
| **C. spin-wait (busy poll)** | `while(empty){unlock;lock;}; pop` | ✓ | ✓ | ✗ burns CPU 100% |
| **D. CV wait (final)** | `while(empty){cv.wait(lk);}; v=q.pop()` | ✓ | ✓ (if signaled) | ✓ sleeper yields CPU |

→ We need a primitive that **blocks efficiently** AND **provides ordering** (P→C: producer's push *happens-before* consumer's pop).

---

## 5. Condition Variables (CV)

> **Tags:** `condition variable` `cv` `wait` `signal` `broadcast` `notify` `notify_all`
> `monitor` `mesa` `spurious wakeup` `while loop wait`

### Interface (must memorize)

```c
cv.wait(lock *lk);   // atomically: release lk, sleep, re-acquire lk on wake
cv.signal();         // wake ONE waiter (no-op if none)
cv.broadcast();      // wake ALL waiters
```

- **Atomicity of `wait`**: the release-sleep step is atomic — no lost wakeups (a `signal` between unlock and sleep can't be missed).
- **Spurious wakeups**: `wait` may return without an explicit signal (HW glitches, broadcast races, OS reasons). **Always re-check the condition.**
- **C++11 `condition_variable::wait`** *forces* a predicate or a `while`-style usage to bake this in.

### The canonical pattern (memorize verbatim)

```c
// Waiter:
lock(lk);
while (!condition) {     //  WHILE, never IF
    cv.wait(lk);
}
// ...consume...
unlock(lk);

// Notifier:
lock(lk);
// ...produce / make condition true...
cv.signal();             // (or broadcast)
unlock(lk);
```

### Why `while`, not `if`?

> **Tags:** `while not if` `c1 c2 race` `wakeup race`

Slide's exact race: `P1: signal+unlock` → `C1: wakes from wait, returns, calls pop` → `C2: was just *entering* the function, sees `!q.empty()` ... wait — actually the bug is:

- Thread `P1` produces & signals.
- Thread `C1` (the woken one) is on its way back from `wait`.
- A *third* thread `C2` sneaks in between `P1.unlock` and `C1.reacquire`, takes the lock, sees `!q.empty()`, and **steals the item** (this is legal — the lock was free).
- `C1` re-acquires lock, runs `q.pop()` on an **empty queue** → safety bug.
- `if` would fall through; `while` re-checks `q.empty()` and goes back to sleep. Fixed.

This is a **race condition**, not a data race — every access is locked, but the predicate became stale while the waiter was off-CPU.

### Mesa vs Hoare semantics

| Style | Semantics on `signal` | Used by |
|---|---|---|
| **Mesa** (default everywhere real) | Signaler keeps lock + CPU; waiter is just marked runnable. Waiter races with everyone else for the lock when it wakes. **Predicate may be false again** → need `while`. | POSIX, C++, Java, xv6 |
| **Hoare** | Signaler immediately hands lock+CPU to waiter; predicate guaranteed true at wake. `if` would suffice. | Theoretical / textbook |

→ All real systems are Mesa → always `while`.

### Where to put `signal()` — three placements

| Placement | Holds lock during signal? | Correct? | Tradeoff |
|---|---|---|---|
| **Inside CS, before unlock** | yes | ✓ | Slightly more lock contention (woken thread immediately blocks on lock). Safest. |
| **Inside CS, after the work, then unlock** (same as above with signal last in CS) | yes | ✓ | Same. |
| **Outside CS, before lock** | no | ✗ in general | If queue mutation hasn't happened yet, woken thread sees empty queue and goes back to sleep — but worse, with `broadcast` you can lose wakeups in some CV implementations. |
| **After unlock** | no | ✓ but subtle | "Wakeup hurry" — woken thread can run sooner; but a re-acquiring caller can race in. Common in Linux for performance. |

The lecture's `Happens-before` diagram:

```
P: q.push  ──────▶  C: q.pop
   │                   ▲
   ▼                   │
  signal  ──────────▶  wait (returns)
```

→ Producer's `push` *happens-before* consumer's `pop` because `signal` happens-before `wait`'s return.

### `signal()` vs `broadcast()`

| | `signal` | `broadcast` |
|---|---|---|
| Wakes | one waiter | all waiters |
| Use when | one event satisfies one waiter (1 item ↔ 1 consumer) | state change satisfies many (e.g., barrier reached, "queue refilled with N items") |
| Risk if wrong | broadcast → thundering herd, wasted wake/relock cycles | signal → **lost wakeup** if multiple waiters need the event |

---

## 6. Pareto Analysis — Wait Strategies

> **Tags:** `pareto` `spin vs sleep vs cv` `wait strategies tradeoff`

Axes: **Latency-to-resume** (lower = better) vs **CPU-efficiency-while-waiting** (higher = better) vs **Implementation complexity**.

| Strategy | Resume latency | CPU efficiency | Complexity | Pareto? |
|---|---|---|---|---|
| **Busy spin** (raw spinlock) | ~0 (already on CPU) | 0% (burns core) | trivial | ✓ optimal **only for very short waits** (μs) |
| **Yield-loop** (`while(!cond) sched_yield()`) | small (one rescheduling) | medium (lets others run, but still polls) | low | dominated by CV in most cases |
| **CV / sleeplock / blocking** | high (context switch on wake) | ~100% (off-CPU entirely) | high (kernel waitlist) | ✓ optimal **for long / unknown waits** |
| **Adaptive / hybrid** (spin briefly, then sleep) | small→high | medium→high | very high | ✓ frontier between the two |

- Spin and sleep are both Pareto-optimal at opposite ends; the **adaptive** hybrid (Linux futex, Java `LockSupport`, glibc adaptive mutex) lies on the frontier between them.
- Yield-loop is **dominated** by adaptive in nearly every case — it's the worst of both worlds for long waits.

### Granularity analysis — how long do you wait?

| Wait duration | Best strategy | Why |
|---|---|---|
| < ~100 cycles | spin | context switch costs ~1000+ cycles; not worth sleeping |
| 100 cycles – ~10 μs | adaptive (spin then sleep) | amortize switch cost only if needed |
| 10 μs – ms | sleep / CV | switch cost dwarfed by wait |
| > ms (I/O, network, child exit) | sleep, definitely | CPU should run other work |

### CDF of wait time (mental picture)

```
P(wait ≤ t)
1.0 ┤                ┌──────────  ← sleep/CV: long flat tail (some waits truly are long)
    │             ╱──┘
    │          ╱──
0.5 ┤       ╱──
    │     ╱──         ← spin: steep early rise; collapses past spin budget (timeout/yield)
0.0 ┤───╱─────────────────────────────▶  t
    └ μs ── 10μs ── 1ms ── 100ms ──
```

Adaptive's CDF tracks spin's at the left and sleep's at the right.

---

## 7. SLO Analysis — Heterogeneous Goals

> **Tags:** `SLO` `service level objective` `latency p99` `throughput` `homogeneous heterogeneous`

| Workload | Primary SLO | Implication for CV / wait |
|---|---|---|
| Interactive (UI, RPC server) | **p99 latency** of wakeup | Prefer `signal` over `broadcast` (less herd), short critical sections after wake |
| Throughput batch | **jobs/sec**, CPU utilization | OK to broadcast, OK to delay wakeup until batch ready |
| Real-time | **deadline miss rate** | Avoid CV at all (unbounded wakeup latency); use priority-inheriting locks + dedicated wait queues |

SLOs are **heterogeneous** across these workloads — the same kernel CV implementation (e.g., Linux's `wait_queue_head_t`) services all three but is tuned (priority-aware queues) only when scheduler class demands it.

---

## 8. Key-Idea Alignment

> **Tags:** `isolation multiplexing protection performance sharing`

| Mechanism | Primary idea | How |
|---|---|---|
| **Lock** | **Protection** (of an invariant) + **Sharing** (controlled) | Mutual exclusion over shared state |
| **CV** | **Multiplexing** (CPU among waiting threads) + **Performance** | Sleep instead of spin → other work runs |
| **Wait list / sleep queue** | **Multiplexing** | One CPU services many sleepers via O(1) wake |
| **swtch / context switch** | **Multiplexing** (CPU) + **Isolation** (per-thread state) | Each thread has its own kstack & saved regs |
| **Happens-before via release/acquire** | **Performance** | Lets HW reorder freely except at sync points |

Locks → *sharing*; CVs → *multiplexing*; both → *protection* of correctness invariants.

---

## 9. Waiting Mechanism — How Does Sleep Actually Work?

> **Tags:** `sleep mechanism` `wakeup mechanism` `waitlist` `wait queue`
> `kernel context` `user context` `address space save`

### What happens to the CPU when a thread blocks?
1. CPU **switches to another runnable process**, OR
2. CPU **idles** (`hlt`) — power-saving, woken by interrupt.

→ Either way, *we do not waste cycles spinning*. This is the fundamental win over a spinlock.

### What state must be saved to put a thread to sleep?

| State | Where saved | Saved by |
|---|---|---|
| **User address space** | proc's pagetable (already there) | implicit — we just don't load it |
| **User context (regs)** | trap frame on kernel stack | trap entry (already saved when we entered kernel) |
| **Kernel address space** | shared kernel mapping | nothing to do |
| **Kernel context (callee-saved regs, %esp, %eip)** | `struct context` on kernel stack | **explicitly via `swtch`** ← the only thing we have to do |

→ Sleep cost is dominated by saving/restoring the **kernel context** + a TLB flush if user pagetable changes.

### Wait list / sleep queue

- Sleeping process is parked on a **wait list** keyed by some identifier (a CV, a pipe, a child's `proc*`, etc.).
- `wakeup(chan)` walks the list and marks every sleeper on `chan` as RUNNABLE.
- Two designs:
  - **Per-condition wait list** (Linux, glibc): each CV/futex has its own queue. O(1) wake.
  - **Global proc table scan** (xv6): one global list; wakeup linear-scans for matching `chan`. Simpler, scales poorly.

### Granularity of wakeup

| Granularity | Behavior | Pro | Con |
|---|---|---|---|
| **Single waiter** (signal) | wake one | minimal CPU spent on wake | risk lost-wakeup if state suits multiple |
| **All waiters** (broadcast) | wake all | safest correctness; waiters re-check | thundering herd: N-1 wake just to relock and resleep |
| **K-of-N** (e.g. semaphore with count) | wake exactly K | optimal in theory | rare in implementations |

---

## 10. Sleeplock — A "Smarter" Lock Built on Sleep+Wakeup

> **Tags:** `sleeplock` `blocking lock` `mutex impl` `acquire sleep release wake`

```c
struct lock { struct spinlock *l; int locked; List waitlist; };

void lock(struct lock *lk) {
    acquire(lk->l);              // short spinlock guards the bookkeeping
    while (lk->locked == 1)
        sleep(&lk->waitlist, lk->l);  // atomically release l, sleep on waitlist
    lk->locked = 1;
    release(lk->l);
}

void unlock(struct lock *lk) {
    acquire(lk->l);
    lk->locked = 0;
    wake_one(&lk->waitlist);     // hand-off to one sleeper
    release(lk->l);
}
```

Key points:
- A **short spinlock** (`l`) protects the metadata (`locked`, waitlist).
- The *sleeplock itself* is a long-held lock; threads that can't get it **sleep** instead of spin.
- `sleep(chan, spinlock)` atomically releases the spinlock and goes to sleep — same atomicity property as `cv.wait`.

### Spinlock vs Sleeplock

| | Spinlock | Sleeplock |
|---|---|---|
| Wait strategy | busy-loop | block & yield CPU |
| Hold duration | microseconds | can be **arbitrarily long** (held across I/O, page faults) |
| Can yield/sleep while holding? | **NO** (would deadlock interrupts on same CPU) | **YES** |
| Interrupt-context safe? | ✓ (with `pushcli`) | **NO** — can't sleep in IRQ handler |
| Kernel/user | both | kernel only (or user mutex via futex) |
| Cost when uncontended | ~1 atomic xchg | atomic xchg + branch |
| Cost when contended | wasted CPU per wait | 2 context switches (sleep + wake) |

→ **Use spinlock for short, contention-rare CSes**; **sleeplock for long-held resources** (file inode, disk buffer, pipe).

---

## 11. Context-Switching Mechanism — `swtch` / `sched` / `yield` / `scheduler`

> **Tags:** `swtch` `sched` `yield` `scheduler` `context switch` `kernel thread` `coroutine`
> `voluntary preemption` `cooperative scheduling` `kstack`

This is the *mechanism* L12 introduces; **scheduler policy** (CFS, MLFQ, lottery) lives in `schedulers.md`.

### The cast

| Function | Caller | Job |
|---|---|---|
| `swtch(old, new)` | low-level asm | swap callee-saved regs + stack pointer; "magic" thread switch |
| `sched()` | `yield`, `sleep`, `exit` | sanity-check invariants, then `swtch` to per-CPU scheduler thread |
| `yield()` | trap handler (timer IRQ) | mark self RUNNABLE, call `sched` |
| `scheduler()` | per-CPU, infinite loop | scan ptable for RUNNABLE, `swtch` into it |

### Two kinds of context switch in xv6

xv6 **never** switches user→user directly. Every user-mode preemption becomes:

```
user A ──trap──▶ kernel A ──swtch──▶ scheduler ──swtch──▶ kernel B ──iret──▶ user B
```

Steps:
1. **user → kernel transition** (syscall / interrupt / timer) — saves user trapframe.
2. **kernel A → scheduler** via `swtch` — saves kernel callee-saved regs.
3. **scheduler picks B**, calls `swtch` again — restores B's kernel callee-saved regs.
4. **trap return** (`iret`) restores B's user trapframe.

### Why does `swtch` only save *callee-saved* regs?

- `swtch` is **voluntary preemption** = a normal C function call.
- C calling convention says **caller-saved** regs (eax/ecx/edx) are already on the caller's stack if needed. Only **callee-saved** (ebp/ebx/esi/edi) must be preserved by the called function.
- The trap handler, by contrast, is invoked by **interrupt** — there's no caller in the language sense. It must save *all* regs in the trap frame.

### `swtch` x86-32 essence

```asm
swtch:                              ; void swtch(struct context **old, struct context *new)
    movl 4(%esp), %eax              ; eax = old (a context**)
    movl 8(%esp), %edx              ; edx = new
    pushl %ebp ; pushl %ebx
    pushl %esi ; pushl %edi         ; push callee-saved
    movl %esp, (%eax)               ; *old = current %esp  (saves "context")
    movl %edx, %esp                 ; %esp = new           (switch stacks!)
    popl %edi ; popl %esi
    popl %ebx ; popl %ebp           ; pop callee-saved (from NEW stack)
    ret                             ; uses NEW stack's saved %eip
```

The "magic" is line `movl %edx, %esp`: from this instruction onward we are on a **different thread's stack**, and `ret` pops a **different return address**.

### `yield` / `sched` rules

When a thread gives up the CPU, it MUST:
1. Hold `ptable.lock` (so its state transition + the scheduler's view are atomic).
2. Have released *every other* lock (else deadlock — another thread might need that lock to become runnable).
3. Update its own state (`RUNNABLE` for yield, `SLEEPING` for sleep, `ZOMBIE` for exit).
4. Call `sched()`, which calls `swtch(&p->context, mycpu()->scheduler)`.

```c
void yield(void) {
    acquire(&ptable.lock);
    myproc()->state = RUNNABLE;
    sched();
    release(&ptable.lock);
}
```

### `yield`, `sleep`, `exit` — same skeleton, different state

| Verb | Sets state to | Meaning |
|---|---|---|
| `yield` | RUNNABLE | "I'm willing to keep running but you go first." |
| `sleep` | SLEEPING | "I have nothing to do until event X." |
| `exit` | ZOMBIE | "I'm done; reap me." |

All three then call `sched()` → identical mechanism downstream.

### Coroutine pattern

`sched ↔ scheduler` is a **coroutine** pair:
- A kernel thread always *gives up the CPU at `swtch` inside `sched`*.
- The scheduler always *resumes that exact spot in `sched`* when it picks the thread again.
- Symmetric: scheduler also always blocks at *its* `swtch` inside its loop.

Exception: `forkret` — a freshly forked process is "born" partway through `scheduler`'s loop with a hand-crafted context that returns into `forkret` instead of mid-`sched`.

---

## 12. Pareto: Wait List Designs

| Design | Wake latency | Memory | Wakeup precision | Pareto |
|---|---|---|---|---|
| **Global ptable scan** (xv6) | O(N) procs | O(1) extra | wakes exactly the procs on `chan` after scan | ✓ at small N |
| **Per-CV wait queue** (Linux `wait_queue_head_t`) | O(K waiters) | O(1) per CV | exact | ✓ optimal at scale |
| **Futex** (userspace addr → kernel queue) | O(K) | O(1) per addr (lazy) | exact | ✓ optimal for userspace mutex |
| **Hash table of (chan → queue)** | O(K + collisions) | O(table) | exact (modulo collisions) | dominated by per-CV at scale |

xv6's choice trades scan-cost for simplicity — fine for ≤64 procs, awful for thousands.

---

## 13. Linux Scheduling Classes (slide name-drop only — full detail in schedulers.md)

> **Tags:** `SCHED_OTHER` `SCHED_IDLE` `SCHED_BATCH` `SCHED_FIFO` `SCHED_RR` `CFS`

| Class | Purpose | Policy |
|---|---|---|
| `SCHED_OTHER` | normal proc (default) | CFS — fair share by `vruntime` |
| `SCHED_IDLE` | very low priority | only runs when nothing else is runnable |
| `SCHED_BATCH` | CPU-bound, latency-insensitive | like OTHER but penalizes interactivity boost |
| `SCHED_FIFO` | hard real-time, no time slice | runs until blocks/yields/preempted by higher prio |
| `SCHED_RR` | real-time round robin | FIFO + quantum within same priority |

→ All five share the **same `swtch` mechanism**; they differ only in *which* RUNNABLE thread `scheduler()` picks next. **Mechanism / policy separation** is the whole point.

---

## 14. Summary Cheat Block (paste-into-margin)

```
LOCKS         → mutual exclusion (safety)
CV            → ordering + efficient waiting (liveness + efficiency)
wait()        → atomic: release-lock + sleep + reacquire-on-wake
ALWAYS        → while(!cond) cv.wait(lk)   (Mesa, spurious wakeups)
signal()      → wake one      broadcast() → wake all
sleeplock     → spinlock-protected metadata + waitlist
swtch         → save callee-saved + switch stacks + ret to new EIP
yield/sleep/exit  → ptable.lock + state= + sched()
xv6 path      → user→trap→kernel→swtch→scheduler→swtch→kernel→iret→user
```

---

## 15. Quick Self-Check Questions

> **Tags:** `practice problems` `self test`

1. **Why must `wait()` atomically release the lock and sleep?** — Otherwise: caller releases → signaler runs → signal lost → caller sleeps forever.
2. **Why `while`, not `if`?** — Mesa semantics + spurious wakeups + a third thread could steal the resource between signal and re-acquire.
3. **Why does `signal` not require holding the lock?** — Correctness allows it; but signaling without the lock can race with `wait` deciding to sleep, in some impls causing lost wakeups. **Convention: hold the lock during signal.**
4. **Why must `sched()` hold `ptable.lock`?** — The state transition (`RUNNING` → `RUNNABLE/SLEEPING`) must be atomic w.r.t. `scheduler()` reading the table on another CPU.
5. **Why does `swtch` not save eax/ecx/edx?** — Voluntary preemption; the C calling convention treats them as caller-saved, so they were already saved (or dead) before the call.
6. **What's the difference between data race and race condition?** — Data race = unsynchronized memory access (HW level). Race condition = correctness depends on schedule (logic level). Locks fix data races; only re-checking invariants (the `while`) fixes race conditions.
7. **When to spin vs sleep?** — Wait < context-switch cost (~1k cycles) → spin. Wait > tens of μs or unknown → sleep. In between → adaptive.

---


---

## L13 — User & Kernel Threads

*([→ xv6 implementation for this lecture](<#L13 — User & Kernel Threads — xv6>))*


> **Tags:** `threads` `threading` `L13` `lec13` `user threads` `kernel threads` `user-space threading`
> `kernel-space threading` `1:1 threading` `one-to-one` `M:1 threading` `many-to-one` `M:N threading`
> `many-to-many` `hybrid threading` `lightweight process` `LWP` `pthreads` `pthread_create` `clone`
> `clone()` `clone syscall` `fork vs clone` `task` `linuxthreads` `NPTL` `futex` `scheduler activations`
> `upcall` `semantic gap` `concurrency vs parallelism` `abstraction of concurrency` `cooperative scheduler`
> `event-based system` `multi-processing` `shared memory parallelism` `responsiveness` `economy`
> `thread context switch` `swtch threads` `lab3` `thread_create` `thread_wait` `mutex park unpark`

> **Cross-reference:** Sits between **schedulers (L11)** / **ordering+waiting (L12)** and **security (L14+)**.
> Threads are a **mechanism** for the **abstraction of concurrency**; locks (concurrency2.md) and waiting
> primitives (ordering.md) are how we make threading correct. **Lab 3** is the implementation deck for
> 1:1 kernel threads in xv6 (`clone`, `thread_create`, `thread_wait`, mutex `park/setpark/unpark`).

---

## 1. Why Threading? Motivation

> **Tags:** `why threads` `threading benefits` `responsiveness` `resource sharing` `economy`
> `multiprocessor parallelism` `shared memory parallelism` `single core threading`

- **Performance is *not* the only reason** — multi-processing also gets performance.
- **Threading benefits** (Silberschatz):
  - **Responsiveness** — interactive apps stay responsive (UI thread + background workers).
  - **Resource sharing** — threads share *address space* and resources by default; processes don't.
  - **Economy** — thread create/destroy/switch is *cheaper* than process create/destroy/switch (no new pgdir, no full PCB).
  - **Multiprocessors** — multiple threads can run **truly in parallel** on separate cores (instead of single-CPU illusion).
- **Pre-2004 (single-core era)** people still used threads — the win was *organization* and the *abstraction of concurrency*, not perf.
- **Threading challenge:** **synchronization** (the whole point of concurrency1/2 + ordering decks).

### Key-idea alignment
- **Sharing** — threads share memory *by design*; that's the defining property.
- **Performance** — cheap creation, cheap context switch, true parallelism on multiprocessors.
- **Multiplexing** — multiplex multiple flows of execution onto an address space (and onto CPUs).
- **Isolation** — *deliberately broken* between threads of one process; isolation is preserved *between* processes.

---

## 2. What Is a Thread? Definitions

> **Tags:** `thread defined` `thread definition` `lightweight process` `thread ID` `program counter`
> `register set` `stack` `shared memory main property`

- **Wikipedia def.:** "the smallest sequence of programmed instructions that can be **managed independently by a scheduler**."
- **Silberschatz def.:** "a thread, sometimes called a **lightweight process**, is a basic unit of CPU utilization; it comprises a **thread ID, a program counter, a register set, and a stack**."
- **Main property:** **shared memory** with sibling threads in the same address space.
- Operationally: *two independent entities, doing computation, sharing memory.*
- Per-thread private state: **stack**, **registers (incl. PC)**, **TID**.
- Per-process shared state (across all its threads): **heap, code, globals, file descriptors, page table**.

---

## 3. Mechanisms of Concurrency — Design-Space Map

> **Tags:** `mechanisms of concurrency` `multi-processing vs threading vs events` `event-based`
> `voluntarily preemptive` `cooperative` `node js` `nginx` `single threaded event loop`

Concurrency is an **abstraction**; it has multiple **mechanisms**:

| Mechanism | Memory model | Preemption | Parallelism on SMP | Isolation |
|---|---|---|---|---|
| **Multi-processing** | Each proc has *own* address space; share via IPC | Kernel-preemptive | Yes (multiple processes on multiple CPUs) | **Strong** (HW-enforced) |
| **Threads** | Threads in a proc *share* address space | Kernel-preemptive (1:1) or cooperative (M:1) | Depends on model — yes for 1:1 / M:N, no for M:1 | **Deliberately broken** within a process |
| **Event-based system** | 1 process, 1 thread; explicit event loop | **Voluntarily preemptive** (yields between events) | **No** (single thread of execution) | N/A — only one flow |

### Pareto frontier (concurrency abstraction)
- **Multi-processing** — Pareto-optimal on **isolation/safety** axis (separate address spaces).
- **Threads (1:1)** — Pareto-optimal on **shared-memory throughput** axis (parallelism + cheap data exchange).
- **Event-based** — Pareto-optimal on **simplicity / no-sync-needed** axis (no races since single thread, but no parallelism).
- **M:1 user threads** — *dominated* by 1:1 on parallelism *and* by events on simplicity → **rarely Pareto-optimal today** (legacy/low-power niches).

### Takeaway
**Threading gives you a convenient abstraction of concurrency** — but it's one of three mechanisms; pick deliberately.

---

## 4. Threading Models — 1:1, M:1, M:N

> **Tags:** `threading model` `one to one` `1:1` `kernel threading` `many to one` `M:1`
> `user space threading` `many to many` `M:N` `hybrid threading` `green threads`

### 4.1 One-to-One (1:1) — "Kernel Threading"
- Every user thread is backed by **its own kernel thread**.
- Kernel scheduler sees and schedules each thread independently.
- **Pros:**
  - Improved concurrency, true **parallelism** on multiprocessor.
  - Blocking syscall in one thread does **not** block siblings (kernel reschedules another).
  - **Preemption** works (kernel preempts via timer).
- **Cons:**
  - **Kernel overhead** for every thread (TCB, kernel stack, syscall to create).
  - Heavier creation, more memory.

### 4.2 Many-to-One (M:1) — "User-Space Threading"
- Many user threads multiplexed onto **one** kernel thread (entire user-space scheduler in libc).
- **Pros:**
  - **Simple, efficient** context switch (just stack swap in user space).
  - **No syscall** to create/switch threads → tiny per-thread cost.
  - **Cache locality** (no kernel pollution on switch).
  - **Semantically aware** scheduling (app picks who runs next).
- **Cons:**
  - **No true parallelism** — only one kernel thread → only one CPU at a time.
  - **One blocking syscall blocks ALL user threads** in the proc (kernel sees one entity).
  - Kernel can't preempt individual user threads → **cooperative** only.

### 4.3 Many-to-Many (M:N) — "Hybrid Threading"
- M user threads multiplexed over N kernel threads (typically N ≈ #CPUs).
- **Pros:**
  - User threads **can run in parallel** (over the N kernel threads).
  - **Fewer context switches** than 1:1.
  - **Lightweight** user-space thread cost.
- **Cons:**
  - **Still subject to kernel-thread stalls** — a blocked kernel thread can pin its user threads.
  - Still **not cooperative** at kernel boundary → **semantic gap** between user-sched and kernel-sched persists.
  - **Complex** to implement and tune.

### 4.4 Comparison Table — Tradeoffs

| Property | 1:1 (kernel) | M:1 (user) | M:N (hybrid) |
|---|---|---|---|
| True parallelism (SMP) | ✅ Yes | ❌ No | ✅ Yes |
| Blocking syscall blocks siblings | ❌ No | ✅ Yes (all blocked) | ⚠️ Sometimes (per kernel thread) |
| Preemption available | ✅ Yes (timer IRQ) | ❌ Cooperative only | ✅ Yes (between kernel threads) |
| Thread-create cost | High (syscall + TCB) | Low (libc-only) | Medium |
| Context-switch cost | Medium (kernel switch) | Very low (user switch) | Mixed |
| Kernel info about threads | Full | None (kernel sees 1 proc) | Partial (sees N kthreads) |
| Semantic awareness in sched | ❌ Kernel-only | ✅ App-defined | ⚠️ Both, with semantic gap |
| Cache locality on switch | Worse | Best | In-between |
| Implementation complexity | Simple | Simple | **Hard** |

### 4.5 Pareto frontier of threading models
- **1:1** — Pareto-optimal on **parallelism + correctness-under-blocking-syscalls** axis.
- **M:1** — Pareto-optimal on **per-thread cost + semantic-awareness** axis (when you don't need parallelism).
- **M:N** — *In theory* Pareto-optimal: tries to combine both. *In practice* dominated by 1:1 because kernel stalls + complexity beat the win → **most modern OSes abandoned M:N for 1:1** (NetBSD, Solaris, FreeBSD all moved to 1:1).
- A pure M:1 with a cooperative scheduler is the lineage that → **modern coroutines / async-await / Go goroutines** (which are actually M:N over a runtime), so the user-space idea isn't dead, just rebranded.

### 4.6 Modern OS choices (lecture table)

| OS | Model |
|---|---|
| Linux (NPTL, since ~2003) | **1:1** |
| Linux (LinuxThreads, 1996) | 1:1 |
| Windows | 1:1 |
| macOS / iOS | 1:1-ish (atop Mach threads) |
| FreeBSD (since 2006) | 1:1 default (M:N selectable) |
| DragonFly BSD | 1:1 |
| NetBSD (since 5.0, ~2009) | 1:1 |
| OpenBSD (since ~2012) | 1:1 |
| Solaris | M:N → moved to 1:1 |
| HP-UX | M:N or 1:1 |

> **Verdict from history:** **1:1 won.** Kernel-side knowledge of threads beat user-side semantic awareness once kernels got fast at thread management.

---

## 5. User-Space Threading: How It Actually Works

> **Tags:** `user space threading library` `cooperative scheduler` `swtch user space`
> `context switch user space` `stack swap` `no privileged instructions` `green threads`

- **Key observation:** the threading mechanism is designed assuming **cooperation** between threads.
- **Implication:** a **cooperative scheduler is sufficient** — no preemption needed.
- A user-space cooperative scheduler can switch between user-space threads **without** any preemption mechanism in/from the kernel.
- **Why it works in user space:**
  - Thread context, stacks, and register state are all **user-space data structures** — accessible without privilege.
  - You can **swap stacks in user space** (just a `mov %rsp` — no privileged instr needed).
  - **Concurrency primitives** (atomic CAS/xchg, queues) are user-space-buildable on x86 (`lock cmpxchg`).
- The user-space `swtch` is structurally identical to xv6's kernel `swtch` — same idea, different ring.
- **Anything that *does* need the kernel?** Sleep/wakeup (timer, I/O completion), signals, real preemption, page faults.

---

## 6. Concurrency vs Parallelism — Don't Confuse Them

> **Tags:** `concurrency vs parallelism` `true parallelism` `simultaneous execution`
> `illusion of progress` `event based parallelism`

| Concurrency | Parallelism (True) |
|---|---|
| **Abstraction** | **Act** of executing |
| Multiple mechanisms (threads, multi-proc, events) | Simultaneous execution of multiple streams |
| Illusion of progress on multiple streams | Requires multiple physical execution units (cores) |
| Achievable on **single core / process / thread** (event-loop) | Requires hardware parallelism |
| Can be done without parallelism | Requires concurrency mechanism to expose it |

- An **event-based system** has *concurrency* (multiple in-flight requests progressing) but **no parallelism** (one core, one thread).
- **M:1 user threads** have concurrency, no parallelism.
- **1:1 / M:N threads on SMP** have both.

---

## 7. User-Space vs Kernel-Space Threading — Final Tradeoff Recap

> **Tags:** `kernel vs user threading` `semantic gap` `application awareness`
> `cache locality threading` `thread aware sched`

### Kernel-space wins:
- **Parallelism** (the big one).
- **Preemption** possible (timer IRQ).
- **More info available to kernel** → smarter overall scheduling, can balance across CPUs.
- **Ability to control resource utilization** (cgroups, priorities, etc).
- **Thread-aware process scheduling** — the kernel knows about every thread.

### User-space wins:
- **Semantically-aware scheduling** — the app knows which thread should run next (e.g., who holds a lock, who's on the critical path).
- **No context-switch syscall overhead** — switch is a function call.
- **Cache locality** preserved on switch (no kernel pollution of TLB/L1).
- **Lighter weight** than kernel thread creation.
- **Cheap thread creation** — no kernel TCB, no kernel stack.

### The "semantic gap"
- Kernel sees **processes**, app sees **user threads** — kernel's scheduling decisions can be wrong because it doesn't know app-level priorities.
- This is the **fundamental motivation** for scheduler activations and for moving primitives into user space (futex).

### Granularity analysis (where to put threading)
- **Coarse: kernel-only (1:1)** — every thread goes to kernel. Wins parallelism + preemption. Loses cheap creation + semantic awareness.
- **Fine: user-only (M:1)** — never tell the kernel. Wins everything cheap. Loses parallelism + blocks-all-on-syscall.
- **Mid: hybrid (M:N)** — try both. Wins some of both, loses simplicity. **Empirically loses overall** in modern OSes.
- **Modern compromise: 1:1 + futex** — kernel does scheduling; user-space does sync (lock, cv, sem) without syscalls in the fast path. **Best of both** for most workloads.

---

## 8. Modern Threading Libraries — `futex` and the User/Kernel Split

> **Tags:** `futex` `fast userspace mutex` `pthread implementation` `NPTL` `lock fast path`
> `kernel sleep wakeup` `user space lock`

- Modern POSIX threads (e.g., **NPTL** on Linux) are **mostly 1:1 kernel threads**.
- But many *primitives* live in **user space** for speed:
  - **`futex` (Fast Userspace muTEX)** syscall.
  - User-space code does the **fast path** (atomic CAS on the lock word) — no syscall.
  - Only on **contention** does it call into the kernel (`futex(WAIT)`) to sleep.
  - Wakeup also goes through `futex(WAKE)`.
- **Trade-off split:**
  - **Kernel manages:** I/O sleeping, process sleeping, scheduling, thread creation.
  - **User-space manages:** lock, condition variable, semaphore (uncontended path).
- This is the practical resolution of the user-vs-kernel debate: **kernel threading + user-space sync primitives**.

### Performance-analysis CDF (lock acquire latency, NPTL/futex)
- **Uncontended path** (vast majority): dozens of cycles — pure user-space CAS. CDF rises near-vertical at ~10–50 ns.
- **Contended path** (long tail): syscall + sleep + wakeup → microseconds. CDF flattens out into a long tail.
- The CDF is **bimodal** — a steep cliff at the cheap path, then a long tail for sleepers.

---

## 9. Scheduler Activations — The "Right Way" That Wasn't

> **Tags:** `scheduler activations` `anderson 1991` `upcall` `M:N realized`
> `kernel notify userspace` `address space scheduler`

- **Anderson et al., 1991** — proposed mechanism to *close* the semantic gap in M:N.
- **Concept:** introduce a **bidirectional communication channel** between kernel scheduler and user-space scheduler.
  1. Kernel **upcalls** the user-space scheduler when scheduling-relevant events happen (a thread blocks, a CPU is granted/revoked).
  2. User space can **downcall** to notify the kernel.
- A "scheduler activation" **vectors control from kernel to user-space thread scheduler** on a kernel event; the user-thread scheduler can then run, modify thread structures, request kernel actions.
- **Implemented in NetBSD** — *abandoned*. Tried in Linux 2.4 (Marcel library, patches) — *abandoned*.
- **Why it died:** complexity, fragile semantics, NPTL's 1:1 + futex was simpler and "good enough."

### Key-idea alignment
- **Performance** — close the gap so user-space sched can react to kernel events efficiently.
- **Sharing** — share scheduling state between user and kernel.

---

## 10. Thread API — `clone()`, `pthread_create()`

> **Tags:** `clone syscall` `clone flags` `task_struct` `linux task` `pthread create`
> `fork vs clone` `thread create xv6`

### 10.1 Linux `clone()` — the unifying primitive
- In Linux, **`clone()`** is the underlying syscall for **both** thread and process creation.
- Unifying construct: **task** (every schedulable entity is a task; `task_struct`).
  - Every task is schedulable.
  - Tasks may share more or fewer resources via flags.
  - `fork()` → new memory space (still uses `clone()` under the hood).
  - `clone()` with `CLONE_VM` → new task that **shares** memory ⇒ a thread.
- Linux syscall:
```c
long clone(unsigned long flags, void *child_stack,
           void *ptid, void *ctid, struct pt_regs *regs);
```
- glibc wrapper:
```c
int clone(int (*fn)(void *), void *child_stack,
          int flags, void *arg, ...);
```
- **Insight:** "thread vs process" is just **a set of CLONE_* flags** — `CLONE_VM | CLONE_FS | CLONE_FILES | CLONE_SIGHAND | …`.

### 10.2 POSIX (`pthread_create`)
```c
int pthread_create(pthread_t *thread,
                   const pthread_attr_t *attr,
                   void *(*start_routine)(void *),
                   void *arg);
```
- Standardized; portable; under the hood usually = `clone()` with thread flags on Linux.

### 10.3 xv6 (lab3) — simplified API
```c
int clone(void *stack, int size);
thread_create(void *(*start_routine)(void*), void *arg);
```
- Implementation: like `fork()`, **except reuse parent's address space entirely (no COW)** — child shares pgdir.
- Caller must supply user stack memory (the parent allocates a stack for the child thread).

---

## 11. Lab 3 — Goal & Synchronization Primitives

> **Tags:** `lab3` `xv6 threads` `xv6 1:1` `thread_wait` `mutex` `park setpark unpark`
> `cond_wait cond_signal` `spinlock acquire release`

- **Goal:** add **1:1 kernel-thread support** to xv6.
- Allow threads to be scheduled.
- Retain perf advantages of threads (shared memory; cheap-ish creation).
- Synchronization primitives:
  - **Waiting** — `waitpid`, `thread_wait`.
  - **Spinlocks** — `init`, `acquire`, `release` (already in xv6).
  - **Mutexes** — `park`/`setpark`/`unpark`, `mutex_init/acquire/release` (lab3 builds these).
  - **Condition variables** — `cond_wait`, `cond_signal`.

### SLO analysis (heterogeneous between threading models)
- **1:1 kernel threads SLO:** "p99 thread creation < tens of µs"; "blocking syscall on thread T does not affect throughput of thread U on a different CPU."
- **M:1 user threads SLO:** "p99 thread switch < 1 µs (no syscall)"; "but blocking syscall on T blocks all siblings — SLO breach risk."
- **Heterogeneous:** the SLOs themselves differ — M:1 commits to *latency* of switch; 1:1 commits to *isolation* between threads' blocking behavior.
- **Implication:** workload-dependent — choose 1:1 for parallel compute / mixed I/O; choose M:1 (or modern coroutines) when you have *many* short tasks and want sub-µs switching.

---


---

## L14 — Security I (Goals, Threats, Memory Safety)

*([→ xv6 implementation for this lecture](<#L14 — Security I (Goals, Threats, Memory Safety) — xv6>))*


> **Tags:** `security` `security1` `L14` `lec14` `cybersecurity` `infosec`
> `security defined` `security definition` `negative goal` `active adversary`
> `security goals` `threat model` `policy` `mechanism` `policy vs mechanism`
> `CIA triad` `confidentiality` `integrity` `availability` `2FA` `MFA`
> `Kerckhoff` `Kerckhoffs` `kerckhoff principle` `enemy knows the system` `security through obscurity` `obscurity`
> `Stuxnet` `airgap` `air gap` `Farewell dossier` `xcodeGhost` `Reflections on Trusting Trust` `Ken Thompson` `trusting trust`
> `supply chain attack` `supply chain` `npm leftpad` `left-pad` `chrome extension malware` `Apple v FBI`
> `bad policies` `bad threat model` `bad mechanism` `mechanism failure` `trust boundary` `privilege elevation` `priv esc`
> `memory safety` `memory unsafety` `buffer overflow` `buffer overread` `use-after-free` `UAF` `stack smashing`
> `strcpy` `strncpy` `EIP` `RIP` `EBP` `RBP` `saved return address` `ret2libc` `shellcode` `code injection`
> `Eternal War in Memory` `Szekeres` `ASLR` `DEP` `NX` `W^X` `stack canary` `stack guard` `bounds checking`
> `Rust` `memory safe languages` `memory-safe` `ONCD` `White House memory safety`
> `syscall security` `syzkaller` `kernel bug` `device drivers` `456 syscalls` `40M lines linux`
> `password` `passwords` `plaintext password` `hash` `hash function` `MD5` `SHA256` `SHA-256` `SHA3` `SHAKE`
> `collision resistance` `one-way` `preimage resistance` `digest`
> `rainbow table` `rainbow tables` `brute force password` `precomputation`
> `salt` `salted hash` `bcrypt` `slow hash` `KDF` `password hashing` `Adobe breach` `xkcd 1286`
> `quantum computer` `Shor` `RSA` `DES`

> **Big-picture:** Security is the design of systems that achieve **some property** against an **active adversary**.
> A coherent system has three things: (1) **goals/policy** — what we want to be true; (2) **threat model** — what
> the adversary may do; (3) **mechanism** — the actual hardware/software that enforces the policy. Failures come
> from any of the three being wrong. Security is a **negative goal** — the defender must close *every* path,
> the attacker only needs *one*.

---

## 1. What Is Computer Security?

> **Tags:** `define security` `security as systems design` `security as ecosystem` `medicine vs public health`

- **Two definitions** (slide 5):
  1. Security as **systems design** — akin to *medicine* (treat one patient/system).
  2. Security as **ecosystem analysis** — akin to *public health* (population-level effects).
- **For this class:** focus on definition #1 — security as **systems design**.

### Security Defined (slide 8)
> *Security is the design of systems that achieve some property against an active adversary.*

**Process:**
1. **Define** the system.
2. Provide a set of **security goals**.
3. **Prove** the system follows those goals.

### Why security is *hard* (slides 9, 12)
- Like a bridge collapsing, or the Death Star — many parts, one weak point ends it all.
- **Security is a NEGATIVE goal:** "no bad thing happens." Allowing badness is a failure in *any* of N ways.
- Defender must cover all paths; attacker needs **one**.

### Key-idea alignment
- **Protection** — primary: stop bad actors from doing privileged things.
- **Isolation** — separate trust domains so a breach is contained.
- **Multiplexing** — security goals must hold *while* sharing CPU/memory/disk among mutually distrusting principals.
- **Sharing** — controlled sharing (file perms, capabilities) is the policy surface.
- **Performance** — every check is a tax; security mechanisms compete with perf.

---

## 2. The Three Components — Goals, Threat Model, Implementation

> **Tags:** `goals` `threat model` `policy` `mechanism` `CIA` `in-scope out-of-scope`

### Goals (slide 10)
- **What** you want to achieve. Examples:
  - "You shouldn't be able to read my files."
  - "No process should read another process's memory."
- Often expressed as **CIA triad** categories:
  - **Confidentiality** — secrets stay secret.
  - **Integrity** — data not tampered.
  - **Availability** — the system stays up / responsive.

### Threat Model (slide 10)
- **Assumptions** about what the attacker **can** and **cannot** do.
- E.g., "attacker can guess passwords," "attacker can sniff traffic," "attacker has physical access."
- **Threat model defines what's in/out of scope.** Goal defines what to achieve.
- Without a threat model, "secure" is meaningless ("secure against whom?").

### Implementation = Policy + Mechanism (slide 11)
| Component | Definition | Example |
|---|---|---|
| **Policy** | *Rules* — technical statements of who may do what | file permissions, "must use 2FA" |
| **Mechanism** | *Hardware/software* enforcing the policy | user accounts, encryption, kernel-mode bit, page tables |

> **Mechanism vs policy** is the same separation we saw in scheduling: mechanism = generic enforcement primitive,
> policy = the rules plugged into it. **Mechanism is policy-free**; policy is mechanism-agnostic.

---

## 3. Three Failure Modes — What Could Go Wrong

> **Tags:** `failure modes` `bad policies` `bad threat models` `bad mechanisms` `where security fails`

| Failure | What's wrong | Canonical example |
|---|---|---|
| **1. Bad Policy / Goals** | Rules don't actually exclude the bad outcome | Fairfax County "teachers can do anything" |
| **2. Bad Threat Model** | Wrong assumption about attacker | Stuxnet airgap, "trust your hardware" |
| **3. Bad Mechanism** | Implementation bug / impl ≠ spec | Buffer overflow, weak crypto |

---

## 4. Bad Policies / Goals

> **Tags:** `incorrect policy` `policy failure` `Fairfax County` `transitive trust` `management cases`
> `audit logs` `backups` `revocation`

- **Fairfax County (slide 16):** 9-yr-old student gets superintendent access. Stated policy looked fine,
  but composed: "teachers can change student passwords" + "teachers can add anyone as student" ⇒
  **teacher → can change *anyone's* password → effectively root**. The *composed* policy was wrong.
- Lesson: policies have **transitive consequences**. The bad outcome was reachable through legal moves.

### Where policies fail (slide 17) — "management/maintenance cases"
- Who can change permissions / passwords?
- Who can read **audit logs**?
- Who can read/write **backups**?
- Who can **upgrade software / change configuration**?
- Who can manage the **servers** themselves?
- Who **revokes** privileges of former admins?
- These meta-questions are the usual pivot point for real attacks.

---

## 5. Bad Threat Models

> **Tags:** `Kerckhoff` `obscurity` `Stuxnet` `airgap` `Farewell dossier` `xcodeGhost` `Trusting Trust` `bad assumption`
> `quantum` `Shor` `DES` `computational assumption`

### Kerckhoff's Principle (slide 21)
> **The enemy knows the system.**
> A system is only secure if the adversary knows *everything* about it, and it is **still secure**.
- **Inverse — "security through obscurity" — DOES NOT WORK.**
- Implication: secrets should be **keys**, not **algorithms** or **architecture**.
- Why: algorithms get reverse-engineered (silicon is etched, binaries are read). Only short, rotatable
  keys are realistic to keep secret.

### Bad threat model: "adversary doesn't know how my system works"
- Inverse of Kerckhoff. Common, recurring, always loses eventually.

### Bad threat model: airgaps (slide 23 — Stuxnet)
- Iranian nuclear centrifuges destroyed; network was **airgapped**.
- Assumption: malware can't jump the airgap. **Wrong** — propagated via **USB**.
- Lesson: physical isolation ≠ logical isolation when humans + portable media exist.

### Bad threat model: computational assumptions (slide 23)
- **DES** broken once compute caught up (56-bit key brute force).
- **Quantum + Shor's algorithm** breaks **RSA** (and ECC). PQ crypto migration is happening for this reason.
- Crypto threat models have an **expiration date** tied to compute & math advances.

### Bad threat model: "just trust your hardware" (slide 24 — Farewell dossier)
- Cold War: Soviets stole US tech. US planted **deliberately defective chips/turbines/plans** via the supply chain.
- Hardware can be **subverted upstream**.

### Bad threat model: "just trust your software" (slide 25 — xcodeGhost, 2015)
- Chinese iOS devs pulled Xcode from local mirrors (faster than the US download).
- Some mirrors served **malware-injecting Xcode**. Apps built on those mirrors shipped malware.
- **Compiler is in the TCB.**

### Reflections on Trusting Trust — Ken Thompson, 1984 (slide 26)
- A trojaned compiler can detect when it's compiling itself or `login`, and inject a backdoor — even if
  the compiler **source** is clean. Once the binary exists, the source-level audit cannot find it.
- "**You can't trust code you didn't totally create yourself.**"
- Implication: the **trusted computing base (TCB)** runs all the way down to the toolchain & hardware.

### Bad threat model: "just trust updates" (slide 27)
- **Apple v. FBI** — government pressure to ship a malicious signed update.
- **NPM left-pad** — yanking one tiny package broke half the JS ecosystem; supply-chain ownership matters.
- **Chrome extensions** sold by original devs to **malware vendors**, who then push "updates" with adware.
- Lesson: every auto-update path is a **remote-code-execution channel** scoped by who owns the signing key.

---

## 6. Bad Mechanisms — Mechanism Failures

> **Tags:** `mechanism failure` `bug becomes vuln` `trust boundary` `priv elevation` `buffer overflow`
> `use-after-free` `timing attack` `randomness` `code injection`

### Rule of thumb (slide 29)
> **Any bug can potentially be a security issue.**
- Examples:
  - **Buffer overflows / overreads / writes**
  - **Use-after-free (UAF)**
  - **Code-injection failures** (SQLi, XSS, command injection, format-string)
  - **Poor randomness** for cryptography (Debian OpenSSL'08, Sony PS3 ECDSA)
  - **Timing attacks** (data-dependent branches, cache timing)
- **Bad** when the bug lets an attacker **cross a trust boundary** and **elevate privileges**:
  - "Remote attacker controlling input → ends up controlling the program."
  - "Unprivileged process → ends up with admin/root."

---

## 7. Memory Safety — The Canonical Bad-Mechanism Class

> **Tags:** `memory safety` `unsafe c` `stack frame` `saved EIP` `saved EBP` `return address` `strcpy`
> `vulnerable_function` `shellcode` `ret2libc` `ROP` `Szekeres Eternal War` `ASLR` `DEP` `NX`
> `stack canary` `bounds checking` `Rust` `memory-safe language` `ONCD memory safe`

### The walkthrough (slides 30–38)
```c
void vulnerable_function(char *input) {
    char buffer[10];
    strcpy(buffer, input);   // no bounds check
}
int main(int argc, char *argv[]) {
    vulnerable_function(argv[1]);
    return 0;
}
```
**Stack layout when `vulnerable_function` runs (grows down on x86):**
```
+----------------+
|     buffer[10] | <- writes go forward (toward higher addrs)
+----------------+
|   Saved EBP    | <- prev base pointer
+----------------+
|   Saved EIP    | <- return address (back to main)  ← OVERWRITE TARGET
+----------------+
|     args ...   |
```

- Input `"1234567890"` → fits exactly in buffer (no NUL byte → still UB but no overflow yet).
- Input `'A'*100` → writes 0x41 over Saved EBP, Saved EIP, and beyond.
  - On `ret`, CPU pops Saved EIP = `0x41414141` and jumps there → **attacker controls EIP/RIP**.

### Once the attacker controls EIP/RIP (slide 39)
- **Return to code on the stack** (classic shellcode; mitigated by **DEP/NX**).
- **Return to known functions** (e.g., `system("/bin/sh")` in libc → **ret2libc**, **ROP**;
  mitigated by **ASLR**).
- **"Game is generally over."** With EIP and a primitive, full RCE is the default outcome.

### Family of memory-safety bugs (slide 40)
- **Buffer overreads / overwrites** (stack & heap).
- **Use-after-free**.
- **Double free**.
- **Type confusion**.
- Read: *Szekeres et al., "SoK: Eternal War in Memory," IEEE S&P 2013.*

### Why memory safety is bad in OS code (slides 41–42)
- Linux ≈ **456 syscalls**, **~40 M lines** of kernel code.
- Each syscall is a **trust boundary** — user-controlled args reach kernel code.
- **Device drivers** (OEM-written, often poorly) are the worst offenders.
- **syzkaller** continuously fuzzes the syscall surface and finds steady streams of UAF / OOB / KASAN bugs.

### Solutions (slide 43)
- **Bounds checking** — `strncpy` instead of `strcpy`, `snprintf` instead of `sprintf`.
- **Compiler/OS helpers:**
  - **Stack canaries** (SSP) — random word before saved EIP; check on return.
  - **DEP / NX (W^X)** — pages are W xor X; can't execute the stack/heap.
  - **ASLR** — randomize base addresses → known-libc ret2libc harder.
  - **CFI** (control-flow integrity), **shadow stacks**, **PAC** (ARM pointer auth).
- **OS primitives** (privilege separation, sandboxing, seccomp).
- **The real solution: memory-safe languages (Rust > C).**
  - White House ONCD (Feb 2024): "*Future Software Should Be Memory Safe*."

### Comparison: Memory-safety mitigations vs language-level safety

| Approach | Pros | Cons | Tradeoffs |
|---|---|---|---|
| **`strncpy` / careful C** | No deps, no perf cost | Programmer-discipline only; one mistake ⇒ vuln; `strncpy` itself has gotchas (no NUL guarantee) | **Cheapest, weakest** |
| **Stack canary** | ~0% perf hit; catches contiguous overflows | Doesn't stop UAF / non-contiguous writes; bypassable if leaked | Cheap, partial |
| **DEP / NX** | Stops shellcode-on-stack | Doesn't stop ret2libc / ROP | Forced ROP era |
| **ASLR** | Probabilistic defense vs ret2libc/ROP | Bypassed by info-leaks; 32-bit entropy weak | Probabilistic |
| **CFI / shadow stacks** | Strong control-flow guarantees | Real perf cost, deployment complexity | Strong, expensive |
| **Memory-safe lang (Rust)** | Eliminates the *entire bug class* | Rewrite cost; `unsafe` blocks; learning curve | Strongest, highest upfront cost |

### Pareto frontier (memory-safety mitigations)
- Axes: **safety strength** (how many classes of bugs eliminated) vs **deployment cost** (perf + dev effort + rewrite).
- **Pareto-optimal points:**
  - **Plain C with `strncpy`** — lowest cost, weakest safety. *Pareto-optimal* on cost.
  - **Stack canary + DEP + ASLR** (today's default) — sweet-spot for legacy C/C++. Pareto-optimal mid-point.
  - **Rust / safe-language rewrite** — strongest, highest cost. *Pareto-optimal* on safety.
- **Dominated:** "C with no mitigations" (strict subset of canary+DEP+ASLR for ~0% cost) — no reason to deploy.
- **Dominated:** "DEP only, no ASLR" (ret2libc trivially defeats DEP-only).

### Granularity tradeoff: where do you put the safety check?

| Granularity | Where check happens | Pros | Cons |
|---|---|---|---|
| **Per-instruction (HW MTE / CHERI)** | CPU tags every load/store | Strongest, transparent | Hardware cost; deployment story |
| **Per-allocation (ASan / GWP-ASan)** | Runtime guards each `malloc` | Catches UAF, OOB | 2-3× slowdown (ASan), sampling for prod |
| **Per-function (canary)** | Check on `ret` | Cheap | Coarse; misses many bug classes |
| **Per-language (Rust borrow ck)** | Compile-time | Free at runtime | Rewrite cost; `unsafe` escape hatch |
| **Per-process (sandbox)** | OS isolates blast radius | No source change | Doesn't fix the bug; just contains |

- **Finer-grained checks → stronger safety but higher overhead.** Same shape as the scheduler quantum tradeoff.

### Key-idea alignment (memory safety)
- **Protection** — prevent attacker-controlled code from running.
- **Isolation** — keep one corrupted process from leaking to others (sandbox = isolation backstop).
- **Performance** — every check is overhead; this is *the* tension.

---

## 8. Passwords — How to Store Them

> **Tags:** `password storage` `plaintext` `hash password` `salt` `salted hash` `bcrypt` `scrypt` `argon2`
> `rainbow table` `Adobe breach` `xkcd 1286` `Encryptic` `slow hash` `KDF` `pepper`

### Solution #1: Store plaintext (slide 46) — **terrible**
- Anyone who reads the DB has every user's password. One leak = total compromise.
- Users **reuse** passwords across sites → cross-site cascade.

### Hash functions (slides 47–48)
- `h: {0,1}* → {0,1}^d` — maps any-length input to fixed `d`-bit output.
- **Goals:**
  - **Efficient** — fast to compute.
  - **Deterministic** — same input → same output.
  - **Random-looking** — output indistinguishable from random.
  - **Public** — algorithm is open (Kerckhoff).
- **Other goals (security):**
  - **Collision resistance:** given `x`, hard to find `x' ≠ x` with `h(x)=h(x')`.
  - **One-wayness (preimage resistance):** given `y = h(x)` for random `x`, hard to find any `x'` with `h(x')=y`.
- **Examples:**
  - **MD5** — 128-bit (broken: collisions trivially findable).
  - **SHA-256** — 256-bit (current default).
  - **SHA3-256** — 256-bit (Keccak).
  - **SHAKE** — variable-length output (XOF).

### Solution #2: Store `h(password)` (slide 49) — still bad
- **Brute-force / dictionary attack:**
  1. Build candidate password list `P = {p_1, ..., p_n}`.
  2. Compute `{(h(p_1), p_1), ..., (h(p_n), p_n)}`.
  3. For each leaked hash, look up in this table.
- **Rainbow tables** — exploit time/space tradeoff (chained reductions) so even huge `|P|`
  fits in feasible storage.
- Once the table exists, breaking *any* user is `O(1)`.

### Real example: Adobe 2013 breach (slides 50–53)
- ~150M user records leaked.
- Adobe **encrypted** (not hashed) and **misused block-mode 3DES** → identical passwords ⇒ identical ciphertexts.
- Combined with **plaintext password hints**, the dataset became *literally a crossword puzzle* (xkcd #1286, "Encryptic").

### Solution #3 (real): Hash + Salt (slide 54)
- Generate per-user random `r ←$ {0,1}^d`. Store `(h(password ‖ r), r)`.
- **Why salt works:** the attacker can't precompute *one* table that breaks all users — they'd need
  `2^|r|` × `|P|` table entries. A unique salt per user **forces re-keying the attack** for every user.
- **Slow hash functions** (intentionally expensive) raise the per-guess cost:
  - **bcrypt** — work factor (cost parameter), tunable as compute improves.
  - **scrypt** — memory-hard.
  - **Argon2** — current standard (PHC winner, memory-hard).
- **Pepper** (optional) — site-wide secret added to hash, kept *off* the DB (in HSM/env). Defends if
  attacker steals only the DB.

### Comparison: Password storage strategies

| Strategy | Security | Cost (server) | Tradeoff |
|---|---|---|---|
| **Plaintext** | ~0 | trivial | DB leak = game over for all users + cross-site reuse fallout |
| **Encrypted (e.g., AES/3DES)** | weak — key in same place as DB; deterministic encryption leaks equals (Adobe) | low | Worst of both worlds: false sense of security |
| **Fast hash (`SHA256(pw)`)** | weak — rainbow tables, fast brute force | very low | Defeats casual leaks; not a determined attacker |
| **Salted fast hash (`SHA256(pw‖salt)`)** | medium — no precomputation, but GPU brute force fast | low | Big jump from plain hash; still vulnerable to billion-guess/sec |
| **Salted slow hash (bcrypt/scrypt/Argon2)** | strong — cost factor scales with hardware | moderate (intentional) | Standard; the right answer in 2026 |
| **Salt + pepper + slow hash** | strong + DB-only-leak resilient | moderate + HSM | Defense in depth; deployment complexity |
| **No password at all (passkey / WebAuthn)** | strongest — no shared secret to steal | high (UX + infra) | Eliminates the entire bug class; deployment friction |

### Pareto frontier (password storage)
- Axes: **security** vs **server cost / deployment effort**.
- **Pareto-optimal:**
  - **Plaintext** — minimum cost (degenerate; useful only for the chart).
  - **Salted slow hash (bcrypt/Argon2)** — modern sweet spot.
  - **Passkey / WebAuthn** — eliminates the threat entirely.
- **Dominated:**
  - **Plain hash (no salt)** — strictly worse than salted hash for trivial extra cost.
  - **Encrypted password** (key co-located with DB) — strictly worse than salted slow hash (Adobe-shaped failure mode).

### Granularity tradeoff: salt scope

| Salt scope | Pros | Cons |
|---|---|---|
| **No salt** | simple | one rainbow table breaks all users |
| **Site-wide salt** | one secret to manage | rainbow table specific to site, but still works once built |
| **Per-user salt** (standard) | rainbow tables infeasible; attacker must re-do work per user | slightly more bytes stored |
| **Per-user salt + pepper** | additionally defends DB-only theft | requires separate secret store |

### Key-idea alignment (passwords)
- **Protection** — keep credentials usable only by the legitimate user.
- **Isolation** — a compromised hash for user A shouldn't break user B (this is what salts buy).
- **Performance** — slow hashes deliberately *trade* server cost for attacker cost (asymmetric warfare).
- **Sharing** — public hash function (Kerckhoff) shared across the world; secret = the password + salt.

---

## 9. SLO / Objective Analysis — Are Security SLOs Homogeneous?

> **Tags:** `security slo` `security objective` `homogeneous heterogeneous` `negative goal slo`

- Security SLOs are usually **negative**: "no successful exploit / breach in window W."
- **Heterogeneous across mechanisms:**
  - Memory safety SLO: "0 RCEs from untrusted input" (binary).
  - Password SLO: "after a DB leak, ≥ X% of accounts uncompromised after T days" (probabilistic).
  - Crypto SLO: "no key recovery in < 2^k operations against a Q-qubit adversary."
- **Implications:**
  - Heterogeneous SLOs ⇒ each subsystem needs its **own** threat model and proof.
  - You **cannot compare** them on one axis; defense in depth = stack independent SLOs.
- A useful **security CDF** view exists for **brute-force attacks**:
  - x-axis = guesses (or wall-clock); y-axis = `P(broken)`.
  - **Plain hash** → CDF rises steeply early (fast cracking).
  - **Salted slow hash** → CDF stays flat for billions of guesses, then rises.
  - **Goal:** push the CDF to the right (and flatten) so attacker spends >> defender's response time.

```
   P(account broken)
1.0|  ___________ plain hash (fast)
   | /
   |/                       ___________ salted SHA-256 (medium)
0.5|                       /
   |                      /
   |                     /            ____ bcrypt + salt (slow)
0.0|____________________/____________/____________
                                                     guesses (log)
```

---

## 10. Comparison: Where the Three Failure Modes Lie

| Failure | Detectable by? | Fixable by? | Typical lifetime |
|---|---|---|---|
| **Bad policy** | Threat-modeling, red-team, formal models | Re-write rules; restrict transitive privs | Years (institutional inertia) |
| **Bad threat model** | Reality (attacker shows up) | Update assumptions; new class of defenses | Decades (DES → AES → PQ) |
| **Bad mechanism** | Fuzzing, static analysis, formal verif | Patch / rewrite in safe language | Months for a CVE; class lifetime decades |

### Pareto frontier — "where to spend your security budget"
- Axes: **bug-class coverage** vs **engineering cost**.
- **Mechanism hardening (canary/ASLR/DEP)** — cheap, partial coverage.
- **Memory-safe rewrite (Rust)** — expensive, eliminates entire class.
- **Threat-model audit / red-team** — moderate cost, catches whole-design errors that no mechanism fixes.
- **Policy review + RBAC** — cheap, but only catches the *policy* failure mode.
- All four are **complementary** — defense in depth — none dominates the others alone.

---

## 11. Common Exam Gotchas

> **Tags:** `security exam tricks` `security gotchas`

- **Security is a NEGATIVE goal** — defender must close every path; attacker needs one.
- **Policy ≠ Mechanism.** "Only TA changes grades" is **policy**; Canvas's auth code is **mechanism**.
- **Threat model is not optional.** "Is X secure?" is meaningless without "against whom?"
- **Kerckhoff:** assume the enemy knows the system. Secret = **key**, not algorithm.
- **Security through obscurity does not work** — but obscurity as defense in depth is fine,
  *as long as* you'd still be secure without it.
- **Trusting Trust:** the TCB extends to your **compiler, hardware, supply chain, update channel.**
- **Any bug can be a security bug** if it crosses a trust boundary.
- **Buffer overflow on the stack overwrites Saved EIP** — that's the canonical exploitation primitive.
- **DEP** stops shellcode-on-stack; **ASLR** stops ret2libc-with-known-addresses; together they force ROP + info-leak.
- **`strncpy` is *not* a safe `strcpy`** — it does not guarantee NUL termination if `n == strlen(src)`.
- **MD5 is broken (collisions)**; SHA-1 is broken (collisions); **SHA-256 / SHA-3 are current**.
- **Hash without salt = rainbow table game over.**
- **Encrypted password ≠ hashed password.** Encryption is reversible — the key is in the same DB.
- **Salt is not secret** — it's stored next to the hash. Salts defeat **precomputation**, not brute force per se.
- **Pepper IS secret** and stored separately — defends against DB-only theft.
- **bcrypt / Argon2** are intentionally **slow** — that's the feature.
- **Adobe used 3DES in ECB-like mode + plaintext hints** — all three failures (mechanism, policy, threat model).
- **Stuxnet jumped an airgap via USB** — physical isolation ≠ logical isolation.
- **ONCD (Feb 2024)** — White House said "future software should be memory safe." Cite this for "why Rust."
- **Kernel = ~40 M LOC, 456 syscalls** — every syscall is a trust boundary; that's why fuzzers (syzkaller) find so much.
- **Memory safety eliminates a *class* of bugs** — that's qualitatively different from per-bug mitigations.

---

## 12. Quick Reference

| Term | Meaning |
|---|---|
| **Goal** | What the system should achieve security-wise |
| **Threat model** | Assumptions about the adversary's capabilities |
| **Policy** | Technical rules expressing the goal |
| **Mechanism** | Hardware/software enforcing the policy |
| **TCB** | Trusted Computing Base — everything you must trust |
| **CIA triad** | Confidentiality, Integrity, Availability |
| **Kerckhoff's principle** | "The enemy knows the system" |
| **Security through obscurity** | Hiding the design as your defense — does not work |
| **Active adversary** | Attacker who can act, not just observe |
| **Negative goal** | "No bad thing happens" — covers infinite paths |
| **Trust boundary** | Interface between two trust levels (user/kernel, net/host) |
| **Privilege escalation** | Bug lets attacker cross a trust boundary upward |
| **Rule of thumb** | Any bug *can* be a security issue |
| **Buffer overflow** | Write past array end, often onto saved EIP |
| **Saved EIP / RIP** | Return address on stack — overwrite target |
| **Use-after-free** | Use a pointer after `free()` — heap corruption primitive |
| **ret2libc** | Overwrite return to point at libc function (e.g., `system`) |
| **ROP** | Return-Oriented Programming — chain "gadgets" ending in `ret` |
| **DEP / NX / W^X** | Pages are W xor X — no executing the stack |
| **ASLR** | Randomize base addresses to defeat hardcoded addrs |
| **Stack canary** | Random word before saved EIP; check on `ret` |
| **CFI** | Control-Flow Integrity — restrict indirect-jump targets |
| **Memory-safe language** | Compiler/runtime guarantees no UB (Rust, Go, Java, …) |
| **`strcpy` vs `strncpy`** | Bounded variant; still has gotchas re: NUL |
| **Hash function** | `h: {0,1}* → {0,1}^d` — fixed-size digest |
| **Collision resistance** | Hard to find `x ≠ x'` with `h(x)=h(x')` |
| **Preimage resistance** | Hard to invert `h` (one-wayness) |
| **MD5 / SHA-256 / SHA-3 / SHAKE** | Hash families (MD5/SHA-1 broken) |
| **Salt** | Per-user random value mixed into hash; not secret |
| **Pepper** | Site-wide secret mixed into hash; stored separately |
| **Rainbow table** | Time/space tradeoff precomputed hash table |
| **bcrypt / scrypt / Argon2** | Slow / memory-hard password hashes |
| **Stuxnet** | Airgap-jumping malware against Iranian centrifuges |
| **xcodeGhost** | Malicious Xcode mirrors injected malware into iOS apps |
| **Trusting Trust** | Ken Thompson's trojaned-compiler attack |
| **Farewell dossier** | Cold-War US supply-chain sabotage of Soviet imports |
| **ONCD (2024)** | White House call for memory-safe languages |
| **syzkaller** | Coverage-guided syscall fuzzer for Linux |

---


---

## L15 — Security II (Access Control, Sandboxing)

*([→ xv6 implementation for this lecture](<#L15 — Security II (Access Control, Sandboxing) — xv6>))*


> **Tags:** `security2` `security II` `L15` `lec15` `Specter` `solutions to security`
> `access control` `on-device access control` `untrusted code` `untrusted app` `sandbox` `sandboxing`
> `DAC` `discretionary access control` `MAC` `mandatory access control` `DAC vs MAC` `combine MAC DAC`
> `unix permissions` `unix file permissions` `rwx` `UID` `GID` `ACL` `inode metadata` `ls -l`
> `setuid` `setuid binary` `set-uid` `passwd binary` `/etc/passwd` `/etc/shadow`
> `confused deputy` `Norm Hardy` `KeyLogic` `KeyKos` `compiler confused deputy`
> `Android` `Android sandboxing` `SELinux` `context tag` `selinux policy` `per-app UID`
> `seccomp` `seccomp-bpf` `eBPF` `syscall filter` `non-turing complete`
> `system decomposition` `privilege separation` `privsep` `Chrome sandbox` `renderer process` `OKWS`
> `capabilities` `capability` `capability based security` `cap-based` `access keys` `unforgeable token`
> `fuzzing` `fuzzer` `AFL` `libfuzzer` `syzkaller` `oss-fuzz` `coverage guided`
> `microcorruption` `CSAW CTF` `Grey Hat` `WREKCTF` `smashing the stack`
> `voting` `election security` `e-voting` `voting system goals` `verifiability` `E2E-V`
> `coercion resistance` `receipt freeness` `correctness` `usability` `privacy ballot`
> `paper ballot` `optical scanner` `risk-limiting audit` `RLA` `statistical audit` `certification`
> `2000 election` `Bush v Gore` `Florida` `hanging chad` `swinging chad` `dimpled chad` `pregnant chad` `butterfly ballot` `Palm Beach` `ES&S Votmatic` `Buchanan vote`
> `Kirchoff principle` `Kerckhoffs`

> **Big-picture:** L14 defined the *problem* (goals, threats, mechanisms, attacks).
> L15 is **solutions** — concrete OS-level mechanisms that make a *running* program less dangerous.
> Themes: **access control** (DAC/MAC), **sandboxing** (SELinux + seccomp), **system decomposition**
> (split untrusted work into a tiny RCE-safe component), **capabilities** (replace ambient authority
> with unforgeable keys), **fuzzing** (find bugs at scale), and a real-world worked example: **elections**.

---

## 1. The On-Device Access Control Problem

> **Tags:** `on-device access control` `runtime access control` `limit running program` `multiple users ssh`
> `untrusted web renderer` `untrusted code from internet`

- **Question:** *Once a program is running on a system, how do we limit what it can do?* (slide 5)
- Examples where it matters:
  - Multi-user systems (many users `ssh`'d into one box)
  - Untrusted apps installed locally
  - **Untrusted web renderer** (every browser loads adversary JS — wildly aggressive threat model)
- Aside: "running random untrusted code from the internet" sounds insane in any other context — yet this is the web (slide 5–6).

### Key-idea alignment
- **Protection** — primary; the kernel must mediate what the running program can touch.
- **Isolation** — different programs/users must not interfere.
- **Sharing** — the policy surface (who can read/write what).

---

## 2. Strategies: DAC vs MAC

> **Tags:** `DAC` `MAC` `discretionary` `mandatory` `owner sets policy` `org sets policy`
> `chmod` `transferable rights`

### Discretionary Access Control (DAC) (slide 7)
- **Owner** of a resource defines its access properties.
- Owner can **transfer ownership / control** (rights are *delegable*).
- Mental model: "my file, my rules."

### Mandatory Access Control (MAC)
- Policy is set at the **organizational level** (the system/admin), not by the owner.
- Users **cannot override** policy even on resources they "own."
- Mental model: "the org's rules, no exceptions."

### Comparison Table — DAC vs MAC

| Axis | DAC | MAC |
|---|---|---|
| Who sets policy | Resource owner | Org / system admin (compile-time or central) |
| Override-ability | Owner can transfer/relax | Users cannot loosen |
| Flexibility | High — per-file tweaks | Low — global policy |
| Default behavior | Allow unless denied | **Deny unless allowed** (whitelist) |
| Failure mode | Confused deputy, accidental over-share, setuid abuse | Misconfigured policy → denial of legitimate use |
| Typical impl | Unix `rwx` bits, ACLs | SELinux, AppArmor, Android contexts |
| Granularity | Per-file owner/group/other | Per-process *context* + operation type |

### Pareto frontier (DAC vs MAC vs combined)
- **DAC alone** — high flexibility, low protection (vulnerable to confused deputy). *Not Pareto optimal* once MAC is available; dominated on protection.
- **MAC alone** — high protection, painful UX (every change needs admin). Pareto optimal *if* you can tolerate rigidity.
- **MAC + DAC combined** (**real world** — slide 13) — *Pareto optimal*: defense in depth, both must allow. Cost is policy authoring complexity.

### Key-idea alignment
- **DAC** — Sharing (owner controls who shares); weak Protection.
- **MAC** — Protection + Isolation (org enforces invariants).

---

## 3. DAC Example — Unix Files

> **Tags:** `unix files` `unix permissions` `ls -l` `rwx` `user group other` `inode`
> `/etc/passwd permissions` `read write execute bits`

- **Each user has:**
  - A **User ID (UID)**.
  - Any number of **Group IDs (GIDs)**.
- **Each file has ACL metadata:**
  - User owner.
  - Group owner.
  - **Read / Write / eXecute** bits for `{user, group, other}`.
- Stored in **inode metadata** (slide 8).

### `ls -l` decode (slide 9)
```
-rw-r--r-- 1 root root 885 Mar 12 11:27 /etc/passwd
 │└┬┘└┬┘└┬┘   │    │
 │ │  │  │   user  group
 │ │  │  └── other rwx
 │ │  └───── group rwx
 │ └──────── user  rwx
 └────────── file type (- = regular)
```

### Granularity tradeoff (Unix DAC)
| Granularity | Pros | Cons |
|---|---|---|
| Per-bit per-{user,group,other} (Unix classic) | Tiny inode metadata, fast checks | Coarse — only 3 principals |
| Full ACL (POSIX ACL, NTFS) | Per-user/per-group rules | Bigger metadata, slower lookup |
| MAC label (SELinux context) | Whole-system policy, deny-by-default | Author cost, brittle |
| Per-syscall (seccomp) | Exact behavior limit | Hard to reason about, per-process |

---

## 4. The SetUID Problem & Confused Deputy

> **Tags:** `setuid` `passwd binary` `priv elevation` `confused deputy` `Norm Hardy`
> `compiler debug flag` `inherent DAC problem`

### Why setuid exists (slide 10)
- *Q:* How do I let a normal user change their **own** password?
  - `/etc/passwd` and `/etc/shadow` are root-owned (`-rw-r--r--`).
  - If users can write them, they can change *anyone's* password.
- **Solution:** **setuid bit** — when a binary has `s` in user-execute slot, it runs **as the file's owner**, not as the invoker:
  - `-rwsr-xr-x 1 root root /usr/bin/passwd`
  - User runs `passwd`; the process executes as **root**, can edit `/etc/shadow`, but is constrained by the program's own logic.

### What goes wrong: Confused Deputy (slide 12)
- **Confused Deputy:** trick a privileged process into doing something on the attacker's behalf.
- Classic example (Norm Hardy, **KeyLogic / KeyKos**, slide 22):
  - Compiler has a `--debug-output FILE` flag.
  - Compiler runs with elevated rights to write its own logs.
  - User invokes: `compiler --debug-output /etc/passwd src.c` → compiler writes to `/etc/passwd` *as itself* — rights it has, but the *user* did not.
- **The deputy is "confused"** about whose authority it acts under (its own ambient rights vs. the caller's).
- **Inherent problem with DAC-only systems** — ambient authority + delegation = confused deputy waiting to happen.
- This is *the* historical motivation for **capabilities** (§7).

### Key-idea alignment
- setuid: **Protection** via privilege elevation, but at the cost of new **trust boundary** that's easy to abuse.

---

## 5. Real World: Combine MAC + DAC

> **Tags:** `MAC plus DAC` `defense in depth` `combined access control` `belt and suspenders`

- Every modern OS does both (slide 13). Example pipelines:
  - Linux: `rwx` (DAC) + **SELinux/AppArmor** (MAC) + **seccomp** (syscall filter) + **namespaces/cgroups** (isolation).
  - macOS: `rwx` (DAC) + **TCC/Sandbox** (MAC).
  - Android: per-app UID (DAC) + **SELinux** (MAC) + **seccomp**.
- **Both must allow** — attacker must defeat *both*.

---

## 6. Worked Example — Android Application Sandboxing

> **Tags:** `android sandbox` `application sandbox` `per-app UID` `selinux android` `context tag`
> `seccomp android` `eBPF` `system decomposition` `EIP != owning OS`

### Goals (slide 15)
- **Maximally limit** untrusted applications.
- Apps may be in **any language** → cannot rely on PL primitives (no Java/Rust safety guarantees from the runtime).
- Apps **can** be malicious (assume the worst).
- **System Decomposition** of the OS itself: separate media processing, wifi, bluetooth, etc.
- **Mantra:** "Getting EIP on *one* component ≠ Owning the OS."

### Layered mechanisms

| Layer | Mechanism | What it does |
|---|---|---|
| DAC | **Linux file perms; each app gets its own UID** | App `A` cannot read app `B`'s files (different UID). |
| MAC | **SELinux** with **context tags** per process | Kernel ships compile-time policy: which contexts can access which files & operations. **Everything else is *disallowed***. (slide 16) |
| Syscall filter | **seccomp / seccomp-bpf** with **eBPF** | Filter *specific* kernel calls; R/W/Open/IOCTL are too coarse (slide 17). eBPF is **non-Turing-complete** (terminates), can filter or block syscalls per-process. |

### SELinux key idea (slide 16)
- All processes get a **context tag**.
- Compile-time config says: "context X may read these files and do these ops."
- **Default deny:** everything not allowed is forbidden (a "root" process can have a context with access to *nothing*).
- **MAC** in spirit: org sets policy at compile, owner cannot override.

### Seccomp / eBPF
- Coarse syscalls like `read`, `open`, `ioctl` aren't enough — e.g. allow `read` only on specific FD ranges.
- **eBPF**: small, verified, in-kernel programs that inspect syscall args. Per-process filter, injected on entry into the sandbox.

### Key-idea alignment
- **Isolation** — each app in its own UID + context.
- **Protection** — MAC default-deny over DAC.
- **Performance** — seccomp/eBPF runs in kernel; small constant cost per syscall.

---

## 7. System Decomposition — Chrome

> **Tags:** `chrome sandbox` `chrome renderer` `OKWS` `privsep` `privilege separation`
> `attacker finds multiple vulns` `multi-renderer` `site isolation`

### Theory (slide 19)
- **Make the attacker find multiple vulnerabilities** to get full compromise.
- Decompose the system so the *exposed* component has *minimal* privilege.

### Chrome's renderer pipeline (slide 19–20)
The **renderer** runs vast quantities of untrusted JS — by far the most attack-exposed code.
For every new page Chrome:
1. **Fork** a fresh process.
2. **Drop UID** to a new limited UID.
3. Apply a new **SEPolicy context**.
4. Apply a **seccomp filter**.
5. *Only now* render.

Result: even with EIP in renderer, attacker is in a UID with no FS access, no network, in a context that can't escape to the **browser process** without a second exploit (browser↔renderer IPC).

### OKWS (Maxwell Krohn) — reading
- Web service split into many small Unix processes, each running a different fragment as a different UID, with minimal capabilities. RCE in one cannot reach the others.

### Key-idea alignment
- **Isolation** — multi-process, distinct security contexts.
- **Protection** — defense in depth.
- **Performance** — cost: process spawn per page, IPC overhead.
- **Sharing** — controlled IPC over a narrow interface.

### Granularity tradeoff — system decomposition
| Granularity | Pros | Cons |
|---|---|---|
| Monolithic (one big process) | Fast, simple | One vuln = total compromise |
| Per-tab / per-site (Chrome site isolation) | Strong isolation between sites | Memory + IPC overhead per tab |
| Per-component (renderer / network / GPU / browser) | Privilege-minimal per role | Complex IPC; attack surface across IPC boundary |
| Per-task (OKWS) | Maximal privsep | High developer cost; hard to design |

### Pareto frontier
- "Per-tab + per-component" (modern Chrome) is **Pareto optimal** for browsers given the threat model — strictly better than monolithic on isolation, with acceptable perf.

---

## 8. Capabilities

> **Tags:** `capabilities` `capability based` `KeyKos` `unforgeable key` `object capability` `ocap`
> `cap as fd` `compiler example` `eliminating ambient authority`

### Theory (slide 21)
- A **capability** is an **MAC system** where the OS provides explicit access **keys**.
- A key gives a process the ability to perform an **action** on a **specific object**.
- Possessing the key = having the right. No key = no right (no ambient authority).

### Why capabilities? (slide 22 — Norm Hardy, KeyKos)
The compiler example fixed:
- Compiler is invoked: `compile --debug-output FILE src.c`.
- Instead of compiler "having ambient ability to write," the **caller** passes a capability `{output_fd, RW}` for `FILE`.
- OS checks **at delegation time**: does the invoker have the right to give this cap?
- If user can't write `/etc/passwd`, they can't *give* the compiler a cap to write `/etc/passwd` → confused deputy is **eliminated by construction**.

### Capabilities vs ACL (DAC) vs MAC labels

| Axis | ACL/DAC | MAC labels (SELinux) | Capabilities |
|---|---|---|---|
| Who carries the right | Listed on the resource | Carried as process tag | **Held by the process** as an unforgeable token |
| Delegation | Possible but ambient | None | Native — pass the cap |
| Confused deputy? | **Yes** (ambient authority) | Possible | **No** (caller must hold cap to delegate) |
| Revocation | Edit ACL | Recompile policy | Revoke key (often hard) |
| Adoption | Universal | Common (Linux/Android) | Niche (KeyKos, seL4, Fuchsia, Capsicum, browser FDs) |
| Mental model | "the file lists who can" | "process is in role X" | "no right without a key" |

### Pareto position
- Capabilities dominate ACL on the **confused-deputy axis** but lose on **legacy compatibility & revocation simplicity**. Not strictly Pareto optimal because of the revocation cost; *Pareto optimal* in highly-decomposed systems (Fuchsia, browsers).

### Key-idea alignment
- **Protection** — no ambient authority means narrower attack surface.
- **Sharing** — caps are *the* sharing primitive; passing a cap = sharing exactly that right.
- **Isolation** — without a cap, a process is fully isolated from an object.

---

## 9. Aside — Finding Bugs (Fuzzing)

> **Tags:** `fuzzing` `AFL` `libfuzzer` `syzkaller` `oss-fuzz` `microcorruption` `CSAW CTF`
> `Grey Hat` `WREKCTF` `coverage guided fuzzing`

- **Fuzzing** = send random/mutated data to a program to make it crash. (slide 23)
- Strategies: maximize **coverage**, prefer **novel** inputs (coverage-guided).
- Tools:
  - **AFL**, **libfuzzer** — userspace, coverage-guided.
  - **Syzkaller** — fuzzes Linux kernel from userspace via syscalls. Live bug list: `https://syzkaller.appspot.com/`
  - **OSS-Fuzz** (`github.com/google/oss-fuzz`) — Google's continuous fuzzing infra for OSS.
- Practice: `microcorruption.com`, **CSAW CTF**, GT clubs **Grey Hat / WREKCTF**.

### CDF for fuzzer bug-finding (mental model)
```
P(found ≤ t)
  1.0 ┤                    ┌─────────────  (easy bugs)
      │              ┌─────┘
  0.5 ┤         ┌────┘                   (most bugs found early)
      │       ┌─┘
      │     ┌─┘
  0.0 ┤___╱_______________________→  fuzzer-time
        seconds  minutes  hours  days     weeks
```
- **Heavy front-loaded** finding rate; long tail of deep bugs needing structure-aware fuzzing.

### Key-idea alignment
- **Protection** — discover failures *before* attackers do.

---

## 10. Worked Example — Voting Systems

> **Tags:** `elections` `voting` `voting system` `ballot` `e-voting` `election security`
> `voting goals` `voting requirements`

### What we *want* (slide 25) — Goals (SLO-flavored)

| Goal | Definition |
|---|---|
| **Correctness & Usability** | Ballots are **counted as cast**, **cast as intended**, accessible to **all eligible voters**. |
| **Privacy** | Attacker cannot learn a voter's selections. |
| **Coercion Resistance** | Voter cannot **cooperate** with an attacker to prove how they voted. |
| **Receipt Freeness** | No voter can prove (after the fact) how they voted. |
| **Verifiability** | Voters have proof their vote was counted correctly. **End-to-End Verifiable (E2E-V)** = crypto version. |

### SLO heterogeneity
- These SLOs are **heterogeneous and partially in tension**:
  - **Verifiability** wants proof of inclusion; **Receipt Freeness** forbids any proof of *content*.
  - **Coercion Resistance** > Receipt Freeness (stronger: holds even if voter wants to prove).
  - **Privacy** ⟂ **Verifiability** — must reveal "your vote counted" without revealing "what it was."
- Other systems (banking) have *homogeneous* goals (correctness alone). Voting is **uniquely hard** because privacy and verifiability fight.
- Implication: cryptographic protocols (E2E-V, mixnets, ZK) are required to satisfy all five simultaneously.

### Key-idea alignment
- **Isolation** — voter ↔ ballot ↔ tally must be unlinkable in ways but linked in others.
- **Protection** — adversary model includes voters, officials, and external attackers.
- **Sharing** — public auditability without revealing contents.

---

## 11. How Voting Is Done Today (Ideally)

> **Tags:** `paper ballot` `optical scanner` `risk-limiting audit` `RLA` `statistical audit`
> `certification ceremony` `polling place` `secret booth`

### Polling place layout (slide 29–32, real photo)
1. **Voting booths** (privacy curtain) — voter marks paper alone.
2. **Optical scanner** in the booth or at the table — instant initial tally.
3. **Poll worker tables** — check in voters (eligibility, registration).

### General Elections Process (slide 37)
1. **Print ballots; setup & testing** (logic & accuracy tests).
2. **Casting & tallying** by voters at the polling place.
3. **Optical scanners** give an initial **"reported"** outcome.
4. **Statistical audit** of cast paper ballots **by hand** — confirm or disprove the reported outcome.
   - Modern flavor: **risk-limiting audit (RLA)** — sample size scales inversely with margin.
5. **Certification ceremony** — formal acceptance of result.

### Why paper + statistical audit is great
- **Paper ballot** is a tamper-evident, voter-verifiable record.
- Optical scanner is *fast* but a piece of software (potentially buggy).
- Hand audit on a **sample** gives statistical confidence without recounting all.

---

## 12. What Can Go Wrong — 2000 Election & Usability Failures

> **Tags:** `2000 election` `Bush v Gore` `Florida` `recount` `SCOTUS election`
> `hanging chad` `swinging chad` `tri chad` `dimpled chad` `pregnant chad`
> `butterfly ballot` `Palm Beach` `Buchanan vote` `ES&S Votmatic` `Judge Rosenberg`
> `usability failure` `mechanism failure`

### Bush v. Gore (2000) — slides 39–40
- Incredibly close race; Florida decided it.
- Margin **~500 votes, 0.009%**.
- Many recounts → **SCOTUS** ruled on it.

### Failure 1: ES&S Votmatic punch-card (slide 41–42)
- Voter punches out **chads** to mark choice.
- Mechanical failures led to ambiguous ballots:
  - **Hanging chad** — partially detached.
  - **Swinging chad** — attached on one corner.
  - **Tri chad** — attached on three corners.
  - **Dimpled chad** — pushed but not punched.
  - **Pregnant chad** — bulging without separation.
- **Mechanism failure** — voter intent indeterminable.
- "Can't you find somebody else?" — Judge Rosenberg, holding a ballot up to the light (slide 44).

### Failure 2: Palm Beach Butterfly Ballot (slide 45)
- Layout interleaved candidates between two columns connected by punch holes.
- Many Gore-intending voters punched **hole #4 → Pat Buchanan** (Reform Party), or punched both → over-vote.
- **Usability failure** — implementation defeated voter intent.

### What L15 wants you to take away
- Even with paper + audit, **mechanism design** (chad geometry, ballot layout) can subvert the goals.
- **Security includes usability** — a system that frustrates intent fails *correctness*.

---

## 13. Final Thoughts (slide 47)

1. Security as a discipline can be **fun and impactful**.
2. **Goals, threat model, policies** — **Kerckhoff's principle** ("the enemy knows the system").
3. Designing for security can be **subtle**.
4. Mechanisms **can and will fail** — **learn to design around them** (defense in depth, decomposition, capabilities).

---

## 14. Quick Pareto / SLO / Granularity Reference

### Sandboxing techniques — Pareto frontier

```
   Protection ↑
     │
     │      ● Per-task privsep / capabilities (KeyKos, OKWS)
     │   ● Per-process MAC + seccomp (Android, Chrome)
     │ ● MAC alone (SELinux)
     │ ● MAC+DAC
     │● DAC + ACL
     │● DAC alone (legacy Unix)            ● No sandbox
     └──────────────────────────────→  Flexibility / Dev cost
```
- **DAC alone** — dominated by DAC+MAC.
- **MAC+DAC** — Pareto optimal for general systems.
- **Per-task privsep + caps** — Pareto optimal for high-assurance systems (cost: dev effort).

### Voting goals — heterogeneity table

| Goal | In tension with | Why |
|---|---|---|
| Verifiability | Receipt-freeness | Proof of inclusion threatens proof of content |
| Privacy | Verifiability | Hidden contents vs. checkable counting |
| Coercion-resistance | Usability | Strong protocols are user-hostile |
| Correctness | Usability | Strict marking rules vs. real human behavior |

---


---

## L16 — Networking

*([→ xv6 implementation for this lecture](<#L16 — Networking — xv6>))*


> **Tags:** `networking` `network` `L16` `lec16` `os and networking` `nic` `network interface card`
> `network card` `network driver` `network stack` `networking stack` `tcp ip stack` `tcp/ip`
> `osi 7 layer` `OSI model` `7 layer model` `osi vs tcp/ip` `4 layer model` `layers of network`
> `physical layer` `data link layer` `link layer` `network layer` `internet layer` `transport layer`
> `application layer` `frame` `packet` `segment` `frame header` `frame footer` `FCS` `MAC address`
> `ethernet` `IEEE 802.3` `802.11` `wifi` `IP` `IPv4` `IPv6` `ip address` `routing`
> `host addressing` `tcp` `udp` `port` `ports` `socket` `socket interface` `BSD sockets` `INET sockets`
> `stream interface` `byte stream` `reliable transport` `unreliable transport` `multiplexing nic`
> `naming` `domain name` `url` `dns` `point to point` `p2p` `streaming` `flow` `connection`
> `reliability` `reorder` `drop` `retransmission` `timeout` `sequence number` `seq num` `ack`
> `checksum` `OUI` `unicast` `multicast` `globally unique` `locally administered` `host network gap`
> `netfilter` `netfilter framework` `NF_IP_PREROUTING` `NF_IP_LOCAL_IN` `NF_IP_LOCAL_OUT`
> `NF_IP_POSTROUTING` `NF_IP_FORWARD` `packet rx` `packet tx` `softirq` `ring buffer` `DMA engine`
> `ip_rcv` `tcp_v4_rcv` `tcp_rmem` `tcp_wmem` `qdisc` `txqueuelen` `dev_queue_xmit` `hard_start_xmit`
> `eBPF` `extended berkeley packet filter` `XDP` `express data path` `bpf verifier` `JIT bytecode`
> `xdp_drop` `xdp_pass` `kernel module` `IX` `IX OSDI 14` `IX dataplane` `dataplane os`
> `software defined network` `SDN` `vm networking` `container networking` `orthogonality` `composability`
> `lab4 network option`

> **Cross-reference:** Networking is the **next big mechanism** after VM/scheduling/threading — the OS exposes a *reliable, named, multiplexed, protected* communication abstraction on top of an *unreliable, MAC-only, single-NIC, unprotected* hardware substrate. The "host-network gap" is the analogue of the "user-kernel gap" (isolation.md, kernel_org.md) and the "VA-PA gap" (vm1.md). eBPF revisits the **monolithic vs microkernel** tension (kernel_org.md) by giving us **safe, JIT'd in-kernel extensions** without the cost of a full kernel module.

---

## 1. The Big Picture — What HW Gives, What OS Must Build

> **Tags:** `hw vs os abstraction` `host network gap` `bare bones nic` `point to point hw`
> `internet abstraction` `gap to fill`

- **NIC ↔ NIC communication** is **point-to-point**, **frame-based**, **unreliable**. That's all the hardware ships with.
- The user/application wants an **"internet" abstraction**: anywhere-to-anywhere, named, multiplexed, streamed, reliable.
- The **gap between HW and user abstraction is the entire networking stack**. That gap is *the* topic of this lecture.

### Hardware (NIC) provides
- A **single network interface** per card.
- **Unreliable transport** — packets can be **reordered**, **dropped**, **duplicated**, **corrupted**.
- Communication addressed to a **MAC address**.
- **No security**.
- Tagline: *"Bare bones, frame based, unreliable p2p comm system."*

### OS must provide (host-network gap)
- **Reliable transport** — no errors, no drops, no duplicates, in-order.
- **Naming** — hostname/URL → IP (e.g. `gatech.edu`).
- **Multiplexing** — many ports per NIC; many connections per port.
- **Protection** — secure transport (TLS, kind of — at the OS boundary).
- **Streaming** — semantically continuous flow, not discrete packets.

### Key-idea alignment
- **Multiplexing** — 1 NIC → many ports → many connections (the dominant story of L16).
- **Naming** — DNS / URL / IP — global address space.
- **Reliability / Performance** — retransmission + ordering + flow control.
- **Protection / Isolation** — secure transports, netfilter, firewalling, eBPF sandboxing.
- **Sharing** — many processes share one NIC.

---

## 2. Orthogonality and Composability — Building-Block Principles

> **Tags:** `orthogonality` `composability` `design principle` `primitives combine`

- **Orthogonality** — a small set of primitive constructs combine in a small number of ways to build large systems. Each primitive does *one thing* and doesn't overlap with others.
- **Composability** — components can be selected and assembled in various combinations to satisfy specific user requirements.
- **Why it matters here:** to go from NIC↔NIC point-to-point → world-wide anywhere-to-anywhere comms, the building blocks (link, IP, transport, app) **must** be orthogonal (each layer does its own job) and composable (you can swap Ethernet ↔ WiFi at the link layer without touching IP).
- This is the **moral justification** for layering.

---

## 3. Network Abstractions: Faults

> **Tags:** `network faults` `router failure` `path failure` `reroute` `path redundancy`
> `fault tolerance network`

- The fundamental fault: a **router/link in the path dies**.
- **Two-step fault response** (slides):
  1. **Detect** the failed router/link.
  2. **Reroute** around it (red path → green path in slides).
- The internet's defining property: **graceful path failover** without endpoints noticing.
- Reliability at the **transport** layer (TCP) handles the *transient effects* (drops, reorders) the rerouting causes.

---

## 4. The Network Stack — Layers

> **Tags:** `osi 7 layer` `tcp ip 4 layer` `layering` `physical link network transport application`
> `frame packet segment` `protocol equals header` `encapsulation`

### Two layering models
- **OSI 7-layer model** — formal standard (Physical, Data Link, Network, Transport, Session, Presentation, Application).
- **TCP/IP 4-layer model** (what we actually use) — Link, Internet, Transport, Application (+ Physical implied).

### Layer-by-layer (what we care about)

| Layer | Examples | Unit | Address | Who processes |
|---|---|---|---|---|
| **Application (L7)** | HTTP, FTP, SSH | message | hostname/URL | user process |
| **Transport (L4)** | TCP, UDP | **segment** | port | **OS** |
| **Internet/Network (L3)** | IP (v4/v6) | **packet** | IP address | **OS** (typically) |
| **Link (L2)** | IEEE 802.3 (Ethernet), 802.11 (WiFi) | **frame** | MAC address | NIC |
| **Physical (L1)** | Ethernet cable, fiber, radio | bits | — | NIC/PHY |

### Encapsulation (frame > packet > segment > data)
```
[Frame hdr | [IP hdr | [TCP hdr | DATA] ] | Frame footer/FCS]
   L2          L3        L4        L7         L2
```
- **Frame** = L2 unit (Ethernet) — has src/dst **MAC**.
- **Packet** = L3 unit (IP) — has src/dst **IP**.
- **Segment** = L4 unit (TCP) — has src/dst **port**.
- **(Approx.)** *"protocol == header"* — each layer is just a header wrapped around the layer above.

### Who processes what
- **NIC** processes **PHY/MAC** (L1/L2).
- **OS** processes **Network + Transport** (L3 + L4) — typically.
- **Application** is user-space.

### End-to-end stack propagation
- **Link layer** communicates on a *single link* (one Ethernet cable).
- **Internet layer** manages **multiple hops** across links — handles **host addressing (IP)** and **routing**.
- **Transport layer** manages **data reliability** (host-to-host stream).
- **Application layer** is process-to-process.
- A frame **goes down** the stack at the sender, **up** at each router (only to L3) and back **up** to L7 at the destination.

---

## 5. Data Link Layer — MAC Addresses

> **Tags:** `mac address` `48 bit mac` `6 octets` `OUI` `organisationally unique identifier`
> `unicast bit` `multicast bit` `globally unique bit` `locally administered`

- **MAC address** = **6 octets (48 bits)**, written as `01:23:45:67:89:AB`.
- Split as **OUI (3 octets) | NIC-specific (3 octets)**.
- **Special bits in OUI's first octet:**
  - **bit 0 (LSB):** `0 = unicast`, `1 = multicast`.
  - **bit 1:** `0 = globally unique (OUI enforced)`, `1 = locally administered`.
- MAC operates at L2 — only meaningful **within a single link / LAN segment**.

---

## 6. Internet Layer (L3) — IP

> **Tags:** `internet layer` `L3` `ip address` `routing` `host addressing` `darpa`
> `large scale distributed system`

- **Two jobs of L3:**
  1. **Host addressing** — IP address space (IPv4 / IPv6).
  2. **Routing** — pick a path through routers between source and dest.
- The internet routing fabric is *itself* a **large-scale distributed system** (BGP, OSPF, etc.) — out of scope for OS class; take Networking for depth.
- Historical note: built on **DARPA**-funded research.

---

## 7. Transport Layer (L4) — The OS-Critical Layer

> **Tags:** `transport layer` `L4` `tcp` `udp` `stream interface` `byte stream`
> `reliable transport` `point to point` `tcp goals`

- **L4 is the layer of particular interest to OS** — it's where the OS *manufactures* the user-visible abstractions.

### TCP abstractions (goals)
- **Stream interface** — data is a *stream*, not packets. Apps `write(fd, buf, n)` arbitrary-sized chunks.
- **Reliability** — packets aren't lost, corrupted, duplicated, or reordered (from the app's view).
- **Point-to-point** — direct logical pipe between two endpoints.

### How do we provide a stream from packets?
- We're given **packets (~1500 bytes MTU)**. App writes arbitrary sizes.
- Two-way fragmentation/coalescing:
  - **Multiple packets per write** (large write → many segments).
  - **Multiple writes per packet** (small writes → coalesced via Nagle).
- But packets can be **reordered** or **dropped** — TCP must hide this.

### TCP correction mechanisms
- **Out-of-order packets** → **sequence number** in TCP header → reorder at receiver.
- **Dropped packets** → **retransmission**, triggered by **ACK timeout**.
- **Duplicates** (slow router, retransmission storm) → seq-num-based dedup.
- **Errors** → **checksum**.

### Three pillars of stream interface support
1. **Detection** mechanism — detect a failure mode happened (missing seq#, bad checksum).
2. **Correction** mechanism — handle duplicates / reordering / drops.
3. **Timeout** mechanism — bound how long we wait before retransmitting.

---

## 8. TCP vs UDP — Transport Tradeoffs

> **Tags:** `tcp vs udp` `transport tradeoffs` `udp` `user datagram protocol` `tcp` `reliable vs unreliable`
> `byte stream vs datagram` `streaming media` `dns over udp` `voip` `gaming` `low latency`

### Comparison table

| Property | **TCP** | **UDP** |
|---|---|---|
| **Interface** | Byte-**stream** | **Datagram** (discrete msgs) |
| **Reliability** | No errors, no drops, no dupes, in-order | **Only "no errors"** (checksum). Drops/dupes/reorders allowed. |
| **Connection** | Connection-oriented (3-way handshake) | Connectionless |
| **Headers** | ~20+ bytes, complex | 8 bytes, minimal |
| **Latency overhead** | Higher (acks, RTO, congestion ctrl, ordering) | Very low |
| **Use cases** | HTTP, SSH, file transfer, DB, RPC | DNS, VoIP, gaming, video streaming, NTP |
| **App must handle?** | Nothing (OS does it) | Drops, ordering, dupes — *if it cares* |

### Pros / cons / tradeoffs
- **TCP pros:** correct out-of-the-box, hides all faults, fair under congestion.
- **TCP cons:** **head-of-line blocking** (a single dropped packet stalls *all* later data); higher latency; large state per connection.
- **UDP pros:** minimal overhead, app picks its own reliability story (e.g. FEC, partial reliability), no HoL blocking.
- **UDP cons:** app re-implements reliability if it needs it.
- **Tradeoff:** **completeness/ordering** ↔ **latency/flexibility**. TCP gives you correctness *for free*, UDP gives you **control** at the cost of complexity in the app.

### Pareto frontier
- **TCP** — Pareto-optimal on the **"correct + ordered"** axis (best for bulk, correctness-first traffic).
- **UDP** — Pareto-optimal on the **"low-latency + flexible"** axis (real-time, custom protocols).
- Neither dominates — both are Pareto-optimal under different objectives.
- **QUIC** (modern, built on UDP) sits between — reliable + ordered streams *without* HoL blocking — arguably pushes the frontier outward.

### Why is UDP useful?
- **Streaming media** — a 30-ms-late frame is useless; just skip it.
- **DNS** — single request/response; full TCP handshake would dominate latency.
- **Real-time gaming / VoIP** — old data hurts more than missing data.
- **Apps that want their own reliability** — QUIC, custom RPC, multicast.

### Key-idea alignment
- TCP → **Reliability**, **Performance** under loss (congestion control), **Multiplexing** (ports).
- UDP → **Performance** (raw latency), **Sharing** (cheap to multiplex many low-overhead flows).

---

## 9. SLO Analysis (Transport Objectives)

> **Tags:** `SLO networking` `latency slo` `throughput slo` `loss slo` `tail latency` `tcp vs udp slo`

| Workload | Latency SLO | Throughput SLO | Loss SLO | Best fit |
|---|---|---|---|---|
| Bulk file transfer | seconds OK | maximize | 0% (TCP makes it 0) | TCP |
| Web (HTTP/1.1) | <100 ms p99 | medium | 0% | TCP / QUIC |
| VoIP / video conf | <150 ms p99 | medium | <1% acceptable | UDP/RTP |
| Online gaming | <50 ms p99 | low | <5% acceptable | UDP |
| DNS query | <50 ms p99 | low (1-2 pkts) | recoverable via retry | UDP |
| Database / RPC | <10 ms p99 | high | 0% | TCP / QUIC |

- **SLOs are heterogeneous** across applications — that's *exactly why* both TCP and UDP exist. A homogeneous SLO would justify a single transport.
- The heterogeneity implies the OS must expose **both** — the OS cannot pick one for the app.

---

## 10. Performance — CDF Shapes

> **Tags:** `latency cdf` `tcp latency cdf` `udp latency cdf` `tail latency` `head of line blocking cdf`
> `retransmit cdf`

- **UDP latency CDF** — sharp, narrow, rises ~vertically near the median; **short tail** (no retransmit, no reorder buffering). Shape: ▕▏ steep step.
- **TCP latency CDF** — similar median to UDP, but **long, heavy tail** caused by:
  - **Retransmission timeout (RTO)** events — each adds ≥1 RTO worth of latency (~hundreds of ms).
  - **Head-of-line blocking** — a single drop stalls everything queued after it.
  - **Congestion control** kicking in (slow start, cwnd halving).
- **CDF intuition:** at p50 they look similar; **at p99/p99.9** TCP can be **10–100×** worse than UDP for small messages.
- For OS designers: **tail-latency-sensitive services** (search, ads, RPC) often pick UDP-based protocols (gRPC over QUIC, HTTP/3) for this reason.

---

## 11. Granularity Analysis — Where Does Reliability Live?

> **Tags:** `granularity reliability` `link layer reliability` `transport reliability`
> `application reliability` `end to end argument` `end-to-end principle`

| Granularity of reliability | Pros | Cons |
|---|---|---|
| **Per-link (L2 ARQ, e.g. WiFi)** | Quick recovery on the lossy hop | Doesn't help with router/path failures; redundant when end-to-end already does it |
| **Per-hop network layer** | Could de-bloat L4 | Not done in IP — IP is *intentionally* unreliable (keep core simple) |
| **End-to-end transport (TCP, L4)** | Single retry path covers all faults; *the* "end-to-end argument" | Higher latency cost on long RTT |
| **Application layer (UDP + custom)** | Tailored to workload (FEC, partial reliability) | Re-implementing is bug-prone |

- **End-to-end argument (Saltzer/Reed/Clark '84):** correctness must be **enforced at the endpoints**; lower-layer reliability is at most a **performance optimization**.
- This is *why* IP is unreliable and TCP/QUIC carry the burden.

---

## 12. Multiplexing — Granularity of Connections

> **Tags:** `multiplexing nic` `port multiplexing` `connection multiplexing` `5 tuple` `socket tuple`
> `(srcip, srcport, dstip, dstport, proto)` `socket dispatch`

- **1 NIC** → many **ports** (16-bit, 0–65535) → many **connections per port**.
- A connection is uniquely identified by the **5-tuple**:
  `(protocol, src_ip, src_port, dst_ip, dst_port)`
- **Listening socket** binds (proto, *, *, dst_ip, dst_port) — accept spawns child sockets per connection.
- **Granularity tradeoffs:**
  - **Coarse (1 connection per port)** — no multiplexing; wastes the 16-bit port space; trivial dispatch.
  - **Fine (many connections per port via 5-tuple)** — what the world actually does; small per-connection overhead in kernel; needs hash table for dispatch on each packet.
  - **Ultra-fine (per-stream within a connection, e.g. HTTP/2, QUIC)** — even more sharing of the same TCP/UDP flow; eliminates per-connection setup; needs application-level demux.
- Frontier shifts toward **finer** granularity over time as overhead drops and workloads become bursty/many-flow.

---

## 13. The Linux Networking Stack — Internals

> **Tags:** `linux networking stack` `socket interface` `bsd sockets` `inet sockets`
> `netfilter framework` `netfilter hooks` `host network gap`

- **Top-down structure (Linux):**
  1. **User space:** processes call socket syscalls (`socket`, `bind`, `connect`, `send`, `recv`).
  2. **Host-Network Gap:** syscalls + callbacks span user/kernel boundary.
  3. **Socket Interface:** **BSD Sockets** (generic) over **INET Sockets** (IPv4/IPv6).
  4. **Transport Layer:** TCP, UDP modules.
  5. **Network Layer:** IP module.
  6. **Datalink Layer:** PPP, SLIP, **Ethernet** drivers.
  7. **Hardware:** NIC.

### Netfilter framework
- **Hooks** placed throughout the IP stack to allow packet inspection/modification:
  - **`NF_IP_PREROUTING`** — packet just received, before routing decision.
  - **`NF_IP_LOCAL_IN`** — destined for this host, after routing.
  - **`NF_IP_LOCAL_OUT`** — generated locally, before routing.
  - **`NF_IP_POSTROUTING`** — about to leave the box, after routing.
  - **`NF_IP_FORWARD`** — pass-through (this host is a router).
- **iptables / nftables** are user-space tools that load rules into these hooks.
- Use cases: **firewalling**, **NAT**, **packet logging**, **load balancing**.

---

## 14. Packet RX/TX Path in Linux

> **Tags:** `packet rx` `packet tx` `softirq` `napi` `dma engine` `ring buffer` `interrupt handler`
> `ip_rcv` `tcp_v4_rcv` `tcp_rmem` `tcp_wmem` `qdisc` `txqueuelen` `dev_queue_xmit`
> `hard_start_xmit` `tcp_transmit_skb` `ip_queue_xmit` `completion queue`

### Packet **reception** (RX, ingress)
1. **Incoming packet** → NIC's on-card memory.
2. NIC's **DMA engine** writes packet into a kernel **ring buffer** (in main memory).
3. NIC's **interrupt generator** raises an IRQ → **interrupt handler** runs (top half).
4. Top half schedules a **softirq** (NAPI poll list — bottom half) to do the heavy lifting.
5. Softirq pulls from the ring buffer → **`ip_rcv()`** at the IP layer.
6. After IP processing → enqueues onto **socket backlog** → **`tcp_v4_rcv()`** runs TCP processing.
7. Data lands in the **TCP recv buffer (`tcp_rmem`)** for that socket.
8. App calls **`read()`** → data is copied into user space.

### Packet **transmission** (TX, egress)
1. App calls **`write()`** → data copied into **TCP send buffer (`tcp_wmem`)**.
2. **TCP process** segments and adds TCP header → **`tcp_transmit_skb()`**.
3. **`ip_queue_xmit()`** at IP layer → IP header → routing decision.
4. **`dev_queue_xmit()`** enqueues onto **qdisc (`txqueuelen`)** — the queueing discipline (FIFO, fq_codel, etc.).
5. **`hard_start_xmit()`** hands the packet to the driver.
6. Driver's **DMA engine** pushes packet bytes into NIC memory → onto the wire.
7. NIC raises a TX-completion IRQ → **softirq frees the packet descriptor** (completion queue).

### Why softirqs / why not handle in the IRQ?
- IRQ handlers must be **fast** (other IRQs are masked). Heavy parsing in IRQ would tank latency for unrelated devices.
- **Softirq / NAPI** does **batched, polled** processing in a deferred context — amortizes per-packet overhead under high load.

### Key-idea alignment
- **Performance** — DMA, ring buffers, NAPI batching, softirqs all chase throughput.
- **Multiplexing** — one NIC, many sockets, dispatched via 5-tuple at `tcp_v4_rcv`.
- **Isolation** — each socket has its own `tcp_rmem`/`tcp_wmem`; kernel mediates.

---

## 15. eBPF — Extended Berkeley Packet Filter

> **Tags:** `ebpf` `extended berkeley packet filter` `bpf` `xdp` `express data path`
> `bpf verifier` `in kernel verifier` `bpf jit` `bytecode jit` `xdp_drop` `xdp_pass`
> `kernel module alternative` `safe kernel extension` `sandboxed program`
> `network tracing` `observability` `block ipv6 example` `lab4 ebpf`

### Problem
- Custom **kernel modules** are **painful to write** — easy to crash the kernel, security/robustness landmines, hard to ship across distros.
- But we want **high-performance** in-kernel functionality (packet filtering, tracing, observability).

### Solution
- **eBPF**: enable **sandboxed programs** to run inside the kernel **safely**.
- **Workflow:**
  1. User writes program in C (e.g. network tracing, packet filter).
  2. Compiles to **eBPF bytecode**.
  3. **In-kernel verifier** statically checks for safety (no unbounded loops pre-5.3, bounded memory access, no arbitrary kernel pointer deref).
  4. **JIT-compiled** to native machine code.
  5. Attached to a **kernel hook** — syscall entry, network device, kprobes, sockets, tracepoints, etc.

### Hook surface (where eBPF can attach)
- **Sockets / TCP/IP** (filter, monitor flows).
- **Network device (XDP)** — earliest possible packet hook, runs in driver before SKB allocation.
- **VFS / File descriptor / Block device** (storage observability).
- **Syscalls, kprobes, tracepoints** (general tracing).

### Example: block all IPv6
- **Old way (kernel module / iptables stack):**
  - Allocate SKB for each packet, walk it up the network stack, parse IP, drop.
  - **Problem:** slow — exactly the latency footprint exploited by **DDoS attacks**.
- **eBPF / XDP way:**
  - Write a tiny eBPF program: read eth header, if `is_ipv6(eth)` → return `XDP_DROP`; else `XDP_PASS`.
  - Attach to NIC via `SEC("xdp")` annotation.
  - Triggered upon packet arrival **at the driver**, before SKB allocation → **massive perf win** under load.

```c
SEC("xdp")
int filter_ipv6(struct xdp_md *ctx) {
    void *data = (void *)(long)ctx->data;
    struct ethhdr *eth = data;
    /* OOB and validation checks */
    if (is_ipv6(eth)) return XDP_DROP;
    else return XDP_PASS;
}
```

### Comparison: kernel module vs eBPF

| Property | **Kernel module** | **eBPF** |
|---|---|---|
| **Safety** | None — bug crashes kernel | **Verified** — bug-class-free if verifier accepts |
| **Performance** | Native | Near-native (JIT'd) |
| **Surface** | Anything | Restricted (no arbitrary kernel API; helper functions only) |
| **Deployment** | `insmod`, distro/kernel-version specific | Load at runtime, portable across kernels (CO-RE) |
| **Debugging crashes** | Kernel panic | Verifier rejects at load — crash impossible |
| **Attack surface** | Huge | Sandboxed, restricted helpers |

- **Pros of eBPF:** safety, observability, portability, dynamic loading.
- **Cons of eBPF:** restricted (no general-purpose computation; bounded loops; bounded stack); verifier can reject valid-but-complex code.
- **Tradeoff:** **expressiveness** ↔ **safety**. Kernel modules are infinitely expressive but unsafe; eBPF is restricted but provably safe.

### Pareto frontier (in-kernel extension)
- **Kernel module** — Pareto-optimal on **expressiveness/raw perf** axis only when you trust the code completely.
- **eBPF** — Pareto-optimal on **safety + perf** axis. Has largely **dominated** kernel modules for *new* networking/tracing extensions.
- **Userspace (e.g. DPDK)** — Pareto-optimal on **flexibility + perf** when you can dedicate CPUs/NICs to a single app, but loses **multiplexing** across apps.

### Key-idea alignment
- **Protection** — verifier enforces sandboxed safety; eBPF can't escape its restricted machine.
- **Performance** — JIT, attached at the lowest possible layer (XDP at driver).
- **Multiplexing** — many eBPF programs compose at the same hook chain.

---

## 16. Beyond the Lecture (Out-of-Scope but Mentioned)

> **Tags:** `dataplane os` `IX` `IX OSDI 14` `software defined networking` `SDN`
> `vm networking` `container networking` `advanced nics` `smartnic` `dpdk` `kernel bypass`

- **Dataplane OSes (IX, OSDI'14)** — separate **control plane** (Linux, ring 0 root) from **dataplane** (libix in ring 0 non-root) for protected, low-latency packet processing in the same address space as the app. Adaptive batch processing of packets (interleave protocol + app code).
- **VM/container networking** — virtual NICs, vSwitches, bridges, network namespaces.
- **Software-Defined Networks (SDN)** — programmable control planes (OpenFlow, etc.).
- **Advanced NICs / SmartNICs** — offload TCP, crypto, RDMA, even DPI to NIC hardware.

---

## 17. Comparison: TCP vs UDP vs QUIC vs Raw NIC

| Property | **Raw NIC / Ethernet** | **UDP** | **TCP** | **QUIC** |
|---|---|---|---|---|
| **Layer** | L2 | L4 (over IP) | L4 (over IP) | L4 (over UDP) |
| **Reliability** | None | None (just checksum) | Full | Full (per-stream) |
| **Ordering** | None | None | Per-connection | Per-stream (no HoL) |
| **Multiplexing** | MAC only | Port | Port + 5-tuple | Port + connection ID + streams |
| **Connection setup** | None | None | 1.5 RTT (3-way handshake) | 0–1 RTT (built-in TLS) |
| **Encryption** | None | App-defined | App-defined (TLS) | **Built-in (TLS 1.3 mandatory)** |
| **HoL blocking?** | n/a | n/a | **Yes** | **No** (per-stream) |
| **Where it runs** | NIC | Kernel | Kernel | Userspace (typically) |

- **Pareto note:** QUIC pushes the frontier — it gives **TCP-style reliability** with **UDP-style flexibility** and **no head-of-line blocking**, at the cost of **userspace CPU** and a less mature ecosystem.

---


---

## L17 — File Systems I

*([→ xv6 implementation for this lecture](<#L17 — File Systems I — xv6>))*


> **Tags:** `file systems` `filesystem` `FS` `L17` `lec17` `lec20` `xv6 chapter 6` `inode` `i-node`
> `dinode` `superblock` `super block` `boot sector` `block bitmap` `data blocks` `log` `direct blocks`
> `indirect blocks` `NDIRECT` `NINDIRECT` `dirent` `directory entry` `link count` `nlink` `iget` `iput`
> `ilock` `ialloc` `iupdate` `balloc` `bfree` `buffer cache` `bcache` `bio.c` `bread` `bwrite` `brelse`
> `bget` `B_BUSY` `B_VALID` `B_DIRTY` `LRU buffer` `disk driver` `ide.c` `ide_rw` `IDE` `narrow waist`
> `VFS` `procfs` `/proc` `/sys` `/dev` `/afs` `data plane control plane` `data control separation`
> `byte interface` `block interface` `naming` `flat names vs hierarchy` `file descriptor` `fd table`
> `inode link count` `multi-link` `sysfile.c` `fs.c` `fs.h` `mkfs.c` `block size` `BSIZE`
> `disk block` `sector` `crash recovery` `storage trends` `NVM` `RAMdisk` `SSD vs RAM` `pareto fs`

> **Cross-reference:** L17 (this) ↔ **L18 File Systems II** (path resolution, log, recovery cont'd) ↔
> **L19/L20 FS Atomicity** (logging, transactions, crash safety) ↔ **L21 Distributed FS** (NFS/AFS/HDFS).
> Builds on **kernel_org (L05)** narrow-waist syscall interface, **concurrency (L09/10)** bcache locks,
> **ordering+waiting (L12)** for `bget` sleep/wake, **threads (L13)** ide kernel thread.
> Lab connection: **Lab4-fs** — extending the xv6 file system (large files, symbolic links, etc.).

---

## 1. What Is a File System? Motivation

> **Tags:** `what is FS` `FS definition` `manage state` `narrow waist FS` `FS not equal disk`
> `FS ≠ persistent storage` `manage user data` `multiplex storage` `data resource isolation`

- **Wikipedia def.:** *"A filesystem controls how data is stored or retrieved."*
- **Lecture take:** FS is an **abstraction to manage *state* in general** — not tied to persistent data, not tied to disk.
- **Five canonical roles** (slide 5, key-idea aligned):
  1. **Manage user data**
  2. **Multiplex** data resources (one disk → many files; spatio-temporal)
  3. **Isolation** of data resources (per-user, per-process)
  4. **Protection** of data resources
  5. **Data management** — naming + organization
- **Used to export data to user space through a *narrow-waist* interface** (à la `read`/`write`).
  - Same interface re-used for **procfs** (`/proc`, `/sys`), **devfs** (`/dev`), pipes, sockets, **/afs**.
  - **Linux control plane** (process info, perf counters, NUMA zones, PCI devs, hugepages, `lsof` data) all flows through FS interface.
- **Takeaway:** **file system ≠ persistent storage.** RAMfs, tmpfs, procfs are FSes with no disk.

### Key-idea alignment (this whole deck)
| Service | Mechanism |
|---|---|
| **Isolation** | Per-user file ownership, per-process FD table, mount-namespace boundaries |
| **Protection** | Mode bits / ACLs at inode granularity; kernel mediates every syscall |
| **Multiplexing** | One disk → many files (space); FS scheduler/lock orders concurrent access (time) |
| **Performance** | Buffer cache, large blocks, indirect-block layout |
| **Sharing** | One file → many users/processes; multiple links → one inode |
| **Naming** | Hierarchical paths over flat inum space |

---

## 2. OS Services Provided by FS (L17 slide 6)

> **Tags:** `FS OS services` `granularity matters` `space multiplexing` `time multiplexing`
> `naming abstraction`

- **Isolation**
- **Protection** — *granularity matters* (users / files / blocks).
- **Multiplexing** — **spatio-temporal**:
  - **Space-mux:** different parts of disk usable simultaneously.
  - **Time-mux:** order accesses correctly when they collide (locks, log).
- **Naming** — higher-level abstractions (paths) on top of inum space → user-friendly interface.

---

## 3. Why Disk-Based FSes (L17 slide 9–10)

> **Tags:** `byte interface` `block interface` `facade pattern` `hide heterogeneity` `hide topology`
> `look and feel of memory` `flock` `IPC via FS`

Abstractions disk-based FSes provide:
- **Naming** — paths instead of LBAs.
- **Byte-level interface** (instead of block/sector):
  - **Façade**: translate device-native ↔ process-native interface.
  - **Hides complexity:** heterogeneous storage devices, device availability/failure.
  - **Hides topology:** local vs remote (NFS/AFS look like local FS).
  - Gives data the **"look and feel" of memory**.
- **Protection / Isolation** of user accesses.
- **Concurrency** — file-level locks (e.g. `flock`).
- **Multiplexing** — one disk, many files.
- **Data sharing** — many users access one file (basis for FS-as-IPC).

### What else is FS good for? (besides persistence)
- **Device interfacing** (`/dev/`: cameras, `/dev/mem`, raw disk, serial).
- **System metadata** (`/proc`, `/sys`: CPU info, memory, kernel config, NUMA, PCI).
- **Process info** (open FDs via `lsof`).
- **Hugepage allocation control**.
- → **FS is the universal narrow-waist interface to I/O & state.**

---

## 4. FS Design Considerations — High-Level API

> **Tags:** `FS API design` `granularity` `file content` `flat vs hierarchy` `synchronization`
> `multi-version` `transaction rollback`

| Design knob | Choices |
|---|---|
| **Granularity** | files / virtual disks / DB records (RDBMS) |
| **File content** | byte array / records / B-tree / key-value |
| **Organization** | hierarchical names (paths) / flat names (object IDs, S3-style) |
| **Synchronization** | none / locks / transactional rollbacks / multi-version (MVCC) |

### Comparison: byte-array vs records vs B-tree content

| | **Byte array (UNIX)** | **Records** | **B-tree / KV** |
|---|---|---|---|
| **Pros** | Simple, generic, app-defined structure | Native record I/O, no parsing | Indexed lookups O(log n), range queries |
| **Cons** | App parses everything | Schema-rigid, less generic | Complex impl, write amplification |
| **Tradeoff** | Generality vs structure-aware perf | Perf vs flexibility | Lookup speed vs write cost |
| **Example** | xv6, ext4 | VMS Files-11, mainframe | NTFS, BTRFS, ZFS, modern KV stores |

### Comparison: hierarchical vs flat naming

| | **Hierarchical (paths)** | **Flat (object IDs)** |
|---|---|---|
| **Pros** | Human-friendly; locality; permission inheritance | Trivially parallel/distributed; simpler metadata |
| **Cons** | Path resolution = N inode lookups; rename hot-spots | No grouping, hard for users |
| **Tradeoff** | UX vs scalability | Scale vs UX |
| **Example** | UNIX, NTFS | S3, Ceph RADOS |

---

## 5. API Implications: FD Table & Inode

> **Tags:** `file descriptor` `fd table` `inode link count` `file independent of name` `nlink`
> `open fd count` `deferred deallocation` `unlink while open`

- **File descriptor (fd)** must keep pointing even if filename changes/is deleted → file ID must be **independent of name**.
- A file can have **multiple links** (multiple directory entries pointing to it) → file metadata cannot live *inside* a directory.
- → File state lives in an **inode**:
  - `nlink` — # of directory entries pointing to it (free when 0).
  - **In-memory open-fd count** — # of fds referring to it.
  - **Deallocation deferred** until *both* `nlink==0` AND `open_fd_count==0`.
  - Hence `unlink` while open works (deletion happens on `close` of last fd).

---

## 6. FS Software Stack

> **Tags:** `VFS` `virtual file system` `FS layers` `disk driver layer` `log layer` `bcache layer`
> `path resolution`

```
User:    Process
         ───────────────────────────────
OS:      File system call interface       ← syscalls (open/read/write/...)
         File system (block, inode,       ← VFS + concrete FS
           directory, path resolution)
         Log                              ← (lab/L19)
         Buffer cache                     ← bio.c
         Disk driver                      ← ide.c
         ───────────────────────────────
Disk:    Disk firmware
```
- **VFS** (Virtual File System): the OS-internal narrow-waist that lets ext4/XFS/procfs/NFS coexist.
- xv6 has a single concrete FS (no VFS layer) — see §11.

---

## 7. On-Disk Layout

> **Tags:** `on-disk layout` `boot sector` `super block` `superblock fields` `inode table`
> `block bitmap` `data blocks` `log region` `block 0 1 2`

```
| boot | super | log | inodes | bit map | data ........ data |
   0      1      2     ...
```

- **Boot sector** — bootloader code (block 0).
- **Super block** — FS metadata: total blocks, # inodes, log size, bitmap start (`bmapstart`), inode start, etc.
- **Log** — write-ahead log region for crash recovery (covered L19/L20).
- **Inode table** — packed array of `dinode` structs; one per file/dir.
- **Block bitmap** — 1 bit per data block: 0 = free, 1 = in-use.
- **Data blocks** — file contents + directory contents.

### Granularity: sector vs multi-sector blocks

| | **Single-sector block (xv6)** | **Multi-sector block (4 KB = 8 sec; ext4)** |
|---|---|---|
| **Pros** | Simple; less wasted space for small files | Less bookkeeping, fewer seeks, batching |
| **Cons** | More book-keeping, more seeks | Internal fragmentation for tiny files |
| **Tradeoff** | Simplicity vs throughput | Throughput vs space efficiency |
| **Use case** | Pedagogical xv6 | Real OSes |

#### Granularity tradeoff spectrum (block size)
- **Tiny (1 sector / 512 B)** — minimum waste; max metadata overhead; worst seq throughput.
- **Small (4 KB)** — sweet spot on most workloads; matches page size → mmap-friendly.
- **Medium (16–64 KB)** — better seq throughput; some internal frag; modern HDDs/SSDs prefer.
- **Huge (1 MB+)** — extents, log-structured FSes — great for big files / video, terrible for many tiny files.
- **Tradeoff axes:** throughput ↑ with size, internal-frag ↑ with size, # seeks ↓ with size, metadata cost ↓ with size.

---

## 8. The Inode

> **Tags:** `inode struct` `dinode` `type free file directory device` `addrs[12+1]` `inumber`
> `inum to inode` `direct block` `indirect block` `NDIRECT` `NINDIRECT` `BSIZE` `max file size`
> `byte address on disk`

### On-disk inode (xv6 dinode)
- `type` — free / file / dir / device.
- `major`, `minor` — for device files.
- `nlink` — number of directory entries pointing to inode.
- `size` — file size in bytes.
- `addrs[NDIRECT+1]` — block pointers: NDIRECT direct + 1 indirect.

### "Meta-data" definition
- *Everything on disk other than file content*: super block, inodes, bitmap, directory contents.

### Direct + indirect (xv6 numbers)
- `NDIRECT = 12` direct entries → `12 * 512 B = 6 KB` directly addressable.
- Last entry = pointer to **indirect block** (one disk block of pointers).
- `NINDIRECT = BSIZE / sizeof(uint) = 512/4 = 128` pointers in the indirect block.
- → Indirect range: `128 * 512 B = 64 KB`.
- **Max file size = NDIRECT*BSIZE + NINDIRECT*BSIZE = 6 KB + 64 KB = 70 KB** in stock xv6.
- (Lab4-fs commonly extends this to **doubly-indirect** for "large files".)

### Find file's byte 8000 (worked example)
- `logical_block = floor(8000 / 512) = 15`.
- Entry 15 ≥ 12 → indirect: `index = 15 − 12 = 3` (3rd indirect entry).

### inum ↔ inode location
- Each inode has an **i-number** (inum); inode is **64 bytes** long.
- Byte address on disk = `2 * 512 + 64 * inum` (boot+super = 2 blocks before inode region in lecture's example).
- E.g., root `/` has `inum=0` → offset 1024.

### Comparison: addressing schemes for file blocks

| | **All direct (no indirect)** | **xv6 12+1 (direct + 1 indirect)** | **Multi-level (UNIX 12+1+1+1)** | **Extents (ext4, NTFS)** |
|---|---|---|---|---|
| **Pros** | Simplest; small inode | Small files cheap; medium files OK | Huge files (TBs) | Compact for contiguous files; few metadata reads |
| **Cons** | Tiny max file size | Hard cap (~70 KB) | Many indirect lookups for big files | Hurts very-fragmented files |
| **Tradeoff** | Simplicity vs scale | Inode size vs max file size | Lookup cost vs max size | Compactness vs frag-friendliness |
| **Pareto** | Dominated | Pareto-optimal at small scale | Pareto-optimal at huge scale | Pareto-optimal for large contiguous files |

#### Granularity (inode block-pointer scheme)
- **Coarse (single huge extent)** — minimal metadata, brittle to fragmentation.
- **Medium (12+1+1+1 multi-level)** — lookup cost grows logarithmically with file size.
- **Fine (every block has a pointer in a flat array)** — uniform but huge metadata for big files.

### Storage efficiency (worked formulas)

> **Tags:** `storage efficiency` `metadata overhead` `internal fragmentation` `block size tradeoff`
> `useful data bytes` `metadata bytes` `512B vs 4KB blocks` `inode overhead` `pointer overhead`
> `data ÷ data + metadata` `efficiency formula` `efficiency calculation`

**Definition:** `efficiency = useful_data_bytes ÷ (useful_data_bytes + metadata_bytes_for_this_file)`

Metadata charged to a file = `inode_size + (#indirect_blocks_used × block_size)`. Pointers inside the inode are already accounted for in `inode_size`.

**General formulas (12 direct + 1 indirect, ptr=4 B):**
- Block size `B`, pointers per indirect block = `B / 4`.
- **Max file size** = `12·B + (B/4)·B`.
  - `B = 512` → `12·512 + 128·512 = 6 KB + 64 KB = 70 KB` (xv6).
  - `B = 4096` → `12·4096 + 1024·4096 = 48 KB + 4 MB ≈ 4.05 MB`.
  - With **doubly-indirect** added: `+ (B/4)² · B` → at 4 KB: `+ 1024² · 4096 = 4 GB` total.

**Worked example — 4 KB file, inode = 64 B:**

| Design | Direct blocks used | Indirect block? | Metadata bytes | Efficiency |
|---|---|---|---|---|
| 512 B blocks | 8 (need 8 × 512 = 4096) | No | 64 (inode only — 8 ptrs in direct, no indirect block allocated) | 4096 / (4096+64) = **98.5%** |
| 4 KB blocks | 1 | No | 64 | 4096 / (4096+64) = **98.5%** |

For **small files**, the two designs tie on efficiency — but 512 B suffers from **8× more pointer dereferences per read** and 4 KB pays **internal fragmentation** for files <4 KB (a 100-byte file uses a full 4 KB block → 100/4096 ≈ 2.4% utilization at the block level).

**Worked example — 1 MB file, 4 KB blocks:**
- Need `1 MB / 4 KB = 256` blocks. 12 direct + indirect (holds 1024 ptrs) → fits in 12 + 244 indirect entries.
- Metadata = `inode (64) + 1 indirect block (4096)` = 4160 B.
- Efficiency = `1,048,576 / (1,048,576 + 4160) = 99.6%`.
- (12 direct + 1 indirect **is sufficient** since 256 ≤ 12 + 1024.)

**Doubly-indirect tradeoff:**
- Adds one more pointer slot to the inode → tiny inode size bump.
- **New max** at 4 KB blocks: `48 KB + 4 MB + 4 GB ≈ 4 GB`.
- **Cost:** small files pay nothing (still 0 indirect blocks); but **medium files get an extra level of indirection on the read path** for blocks beyond `12 + B/4`.
- **Pareto:** doubly-indirect dominates "12+1" once max-file-size is a constraint; otherwise it's a pure superset.

**Pareto-optimal block-size choices for the IoT mostly-small workload:**
- **4 KB blocks** — Pareto-optimal for *fewer pointer hops, faster reads of medium files*; trades off internal fragmentation on tiny files.
- **512 B blocks** — Pareto-optimal for *minimum internal fragmentation*; trades off lookup cost.
- **4 KB + doubly-indirect** — strictly dominates plain 4 KB once 1 MB logs are a requirement.

---

## 9. Inode Operations (xv6 in-memory side)

> **Tags:** `iget` `iput` `ilock` `iunlock` `ialloc` `iupdate` `inode ref count` `kernel inode cache`
> `ip` `concurrent ialloc` `bread brelse`

### API
| Call | Effect |
|---|---|
| `ialloc(dev, type)` | Scan inode region for one with `type==free`, mark non-free, return locked inode. |
| `iget(dev, inum)` | Return in-memory inode struct, **inc ref count** (does NOT lock or read from disk). |
| `iput(ip)` | **Dec ref count**, free if `ref==0` AND `nlink==0`. |
| `ilock(ip)` / `iunlock(ip)` | Sync access to inode (and read on-disk fields if not yet loaded). |
| `iupdate(ip)` | Write modified in-memory inode back to disk. |

### Why split `iget` from `ilock`?
- `iget` is **cheap reference acquisition** — does not block on disk I/O.
- `ilock` does the actual disk read + sync — can block / sleep.
- Caller can hold a *reference* without holding the *lock* → enables looking up a path without serializing on every component.

### Standard usage idiom
```c
ip = iget(dev, inum);    // ref++
ilock(ip);               // sync
... examine and modify ip->xxx ...
iunlock(ip);
iput(ip);                // ref--
```

### Concurrent `ialloc`?
- Both threads call `bread` → that **locks the bitmap/inode block** in the buffer cache.
- One waits inside `bread` until other does `brelse`.
- After acquiring the block: re-check, find a *different* free inode → both succeed without conflict.
- *Mutual exclusion comes from the buffer-cache block lock, not an inode-table lock.*

---

## 10. Directories & Path Resolution

> **Tags:** `dirent` `directory entry` `14 byte name` `inum 0 means free` `directory like a file`
> `path lookup` `inodes accessed in path` `namei`

- A **directory** is *just like a file* — except user can't `write()` it directly (kernel-mediated).
- Content = **array of `dirent`**:
  ```c
  struct dirent {
      ushort inum;
      char   name[14];     // 14-byte filename
  };
  ```
- `inum == 0` → **free dirent** (tombstone).
- **Path resolution** for `/foo/bar/baz`:
  - Inodes touched: `/` (root) → `foo` → `bar` → `baz` = **4 inodes**.
  - General formula: 1 (root) + (# components in path).

---

## 11. Block Bitmap & Allocator

> **Tags:** `block bitmap` `bmapstart` `balloc` `bfree` `readsb` `bit per block` `0 free 1 used`
> `bit math` `(blockNum % 8)`

- xv6 maintains free bitmap on disk — **one bit per data block**, starts at `sb->bmapstart`.
- Bit value: `0 = free`, `1 = in use`.
- Test if block free: `(buf[blockNum/8] & (0x1 << (blockNum % 8))) == 0`.
- `balloc()` — allocate new disk block:
  1. `readsb()` to load superblock into memory.
  2. Iterate over bitmap blocks looking for a 0-bit.
  3. Set bit, log-write block, return block number.
- `bfree(b)` — clear the relevant bit.

### Comparison: allocator structures

| | **Bitmap (xv6)** | **Free list** | **Buddy / extent map** |
|---|---|---|---|
| **Pros** | Compact (1 bit/blk); scan-friendly | O(1) alloc/free | Allocates contiguous extents; reduces frag |
| **Cons** | O(N) scan to find free | List itself takes blocks; bad locality | Complex code |
| **Tradeoff** | Space vs alloc speed | Alloc speed vs locality | Code complexity vs perf |
| **Best for** | Small/teaching FSes | Old UNIX | Modern (ext4, XFS) |

---

## 12. Buffer Cache (`bio.c`)

> **Tags:** `buffer cache` `bcache` `bio.c` `B_BUSY` `B_VALID` `B_DIRTY` `binit` `bread` `bwrite`
> `brelse` `bget` `LRU buffer cache` `doubly linked list buf` `one block one buffer` `caching popular blocks`

### Two jobs
1. **Synchronize access to disk blocks** — kernel invariant: *one in-memory buf per disk block, one kernel thread holds it at a time*.
2. **Cache popular blocks** in fixed buffers → avoid repeated disk I/O.

### Structure
- Doubly-linked list of `struct buf` (xv6 v6 uses fixed pool, e.g. 30 bufs).
- Each `buf` holds a cached copy of one disk block.

### Flags
- `B_BUSY` — buffer is locked (held by a kernel thread).
- `B_VALID` — buffer has been read from disk (data is current).
- `B_DIRTY` — buffer was modified, must be written back.

### Interface
| Call | Behavior |
|---|---|
| `binit()` | Called by `main` — set up bcache linked list. |
| `bread(dev, blockno)` | Get buffer for block; read from disk if not `B_VALID`; returns held (`B_BUSY`). |
| `bwrite(b)` | Write buffer to disk (sets `B_VALID`, clears `B_DIRTY`). |
| `brelse(b)` | Release: clear `B_BUSY`, **move to head of list** (LRU mark), wake sleepers. |

### `bget` algorithm (the heart)
```
loop:
  for each buf b in list:
    if b cached for (dev, blockno):
        if !B_BUSY:  set B_BUSY; return b
        else:        sleep(b);     goto loop      # ← why goto?
  for each buf b in list (back→front, LRU victim):
    if !B_BUSY and !B_DIRTY:
        re-tag b for (dev, blockno); set B_BUSY; clear B_VALID; return b
  panic("no buffers");
```
- **Why `goto loop` after sleep?** When woken, another thread may have re-tagged the buffer for *a different block*; we have to re-search from scratch.

### Replacement policy
- **LRU** via doubly-linked list:
  - On `brelse` (clearing `B_BUSY`), move the buffer to the **front**.
  - **Eviction starts from the back (LRU end)**.

### Performance / CDF analysis (block hit latency)
- **CDF of `bread` latency** is bimodal:
  - Big steep step at ~10–100 ns (cache hit, just memory access + lock).
  - Long tail at ~5–10 ms (cache miss → disk seek + transfer on HDD), or ~100 µs on SSD.
  - p50 sits at hit latency; p99/p99.9 sits at disk latency → *cache hit ratio is the dominant performance lever*.

#### Granularity (cache line granularity)
- **Per-byte cache** — finest, infeasible in OS (huge tag overhead).
- **Per-block (xv6)** — natural, matches disk I/O unit; what every OS does.
- **Per-file** (page cache + inode cache stacked) — Linux model; better for mmap, worse for raw block I/O.

### SLOs
- **Read latency:** p99 < 10 ms (HDD) / < 200 µs (SSD) — **heterogeneous** across media classes (SSD vs HDD vs NVM).
- **Hit ratio:** target ≥ 95% on warm system.
- **Throughput:** ≥ device-saturation bandwidth on sequential reads.
- **Implication of heterogeneous SLOs:** users on different storage tiers see *very* different tail latencies → *one bcache, many policies* (per-device tuning).

### Comparison: write-through vs write-back (B_DIRTY)

| | **Write-through (bwrite immediately)** | **Write-back (B_DIRTY, sync later)** |
|---|---|---|
| **Pros** | Strong durability; simple recovery | Big throughput win, write coalescing |
| **Cons** | Slow on burst writes | Data loss on crash; needs log/journal |
| **Tradeoff** | Durability vs perf | Perf vs durability |

**xv6 today:** Uses **log layer** (L19/L20) — gets *both* via WAL.

---

## 13. Disk Driver (`ide.c`)

> **Tags:** `disk driver` `ide.c` `ideinit` `ide_rw` `idelock` `ideintr` `IRQ_IDE` `ioapicenable`
> `disk 0 disk 1` `request queue` `IDE`

- `ideinit()` — initializes IDE, registers interrupt:
  - `ioapicenable(IRQ_IDE, ncpu - 1)` — route IDE interrupts to **the last CPU**, so disk I/O doesn't compete with CPU 0 for boot/scheduler work.
  - Probes whether **disk 1** is present (xv6 boots from disk 0, FS lives on disk 1).
- `ide_rw(b)` — read or write a `buf`:
  - Append `b` to the per-device **request queue** under `idelock`.
  - If queue head, kick the device.
  - Sleep on `b` until I/O complete.
- `ideintr()` (interrupt handler) — completes head request, wakes waiter.
- **One lock (`idelock`)** for multiple invariants: queue ordering, request/response sharing between `iderw` and `ideintr`.
- **Single processor + interrupts:** if interrupt fires while we hold `idelock`, deadlock → driver disables interrupts on that CPU while holding the lock.

---

## 14. Putting It Together — Disk-Trace Walkthroughs

> **Tags:** `create file trace` `delete file trace` `log_write replaces bwrite` `block 34` `block 59`

These traces are the *whole* point of the lecture: the **same on-disk data structures** (inodes, dirents, bitmap) get touched in a deterministic sequence.

### `echo > a` — file creation (in-log writes)
```
write 34   ialloc   (sysfile.c create)   — mark inode non-free in inode block 34
write 34   iupdate  (create)              — initialize nlink, type, size = 0 in same block
write 59   writei   (dirlink, fs.c)       — append "a" dirent to parent directory data block 59
```
- **Why two writes to block 34?** Block 34 is the inode block; first write marks the inode non-free, second writes the initialized fields. (Could be coalesced — xv6 doesn't.)
- **What's in block 59?** A data block of the parent directory (contains its dirent array).

### `rm a` — file deletion
```
write 59   writei   (sys_unlink)          — remove dirent from parent dir
write 34   iupdate  (sys_unlink)          — decrement nlink in inode block
write 58   bfree    (itrunc, iput)        — clear bitmap bit for the file's data block
write 34   iupdate  (itrunc)              — zero the data-block pointers in inode
write 34   iupdate  (iput)                — mark inode free (type=0)
```
- Note `log_write` replaces direct `bwrite` everywhere → atomicity (L19/L20).

### Big-file read pipeline
1. Disk → buffer cache (via `bread`/`ide_rw`).
2. Buffer cache → user space (`copyout`).
- **Why two copies?** Synchronization + caching invariants. Bypassing (passing user buf to driver) breaks both isolation and the bcache lock invariant.
- **How much RAM for bcache?** Tradeoff: more bufs → higher hit ratio but less RAM for apps. Linux uses **all spare RAM** as page cache (gives back on demand).

---

## 15. Pareto Frontier — File-System Design

```
              SAFETY ↑  (durability + crash-consistency)
                 |
     [logging-FS] ────── dream
        ●            ↗
                   ↗
        ●        ↗     [NoCopy / NoSync ext4]
     [sync-FS]  ↗        ●
                       /
              ────────────→ PERFORMANCE / USABILITY
   [naive overwrite] = bad design (slow AND unsafe)
```
- **Sync-FS (write-through)** — Pareto on safety axis; loses on perf.
- **No-sync FS** — Pareto on perf axis; loses on safety.
- **Logging / journaling FS** — *closest to dream*: WAL gets both ≈ Pareto-optimal.
- **Naive overwrite (no log, no fsync)** — dominated; just bad.

### Cost vs throughput frontier (storage media)
| Media                     | $/GB    | Throughput                     | Pareto?                          |
| ------------------------- | ------- | ------------------------------ | -------------------------------- |
| **Tape**                  | < $0.01 | ~100 MB/s seq, terrible random | Pareto on cost                   |
| **HDD**                   | ~$0.02  | ~150 MB/s seq                  | Pareto on cost/perf middle       |
| **SSD**                   | ~$0.10  | ~3 GB/s seq                    | Pareto in middle                 |
| **NVM** (Optane / NVDIMM) | ~$1+    | ~6 GB/s, byte-addressable      | Pareto, persistence ≈ DRAM speed |
| **DRAM**                  | ~$5     | ~50 GB/s                       | Pareto on speed (volatile)       |

- **Lecture insight:** "Memory getting faster to feed CPU; HDDs cheaper but not faster — gap is widening." NVM partially closes the gap.
- **Even with RAMdisks/NVM**, *none of it is useful without an efficient file system* — perf without isolation/protection/naming/sharing isn't a system.

---

## 16. Intellectual Merit — What Makes FS Hard

> **Tags:** `FS challenges` `crash recovery` `data plane control plane` `API for sharing`
> `multi-process multi-user security` `abstraction generality` `distributed FS` `NFS AFS HDFS`

- **Crash recovery** — fsck, journals, log replay.
- **Performance** — *data-vs-control-plane separation* (control: open/stat; data: read/write).
- **API design for sharing state** — semantics under concurrent open/read/write/unlink.
- **Security** for multi-process / multi-user sharing.
- **Abstraction generality** — same API across pipes, devices, /proc, /afs.
- **Networked / distributed FS** — AFS (Andrew FS), NFS, HDFS, Ceph.

### Performance: data plane vs control plane separation
- **Control plane:** path resolution, permissions, allocation decisions — infrequent, complex.
- **Data plane:** raw block reads/writes — frequent, must be fast.
- Modern designs (DPDK-style, SPDK, kernel-bypass FSes) push data plane out of kernel, leave control in kernel.

---

## 17. Storage Trends Sidebar

> **Tags:** `storage hierarchy` `NVM` `Optane` `RAMdisk` `SSD vs RAMdisk benchmark` `StorePak`
> `gap is widening`

- HDDs cheaper but not faster; gap with DRAM widens.
- **NVM (non-volatile memory)** sits between SSD and DRAM — fast persistent storage but more expensive.
- **SSD vs RAMdisk benchmark** (lecture's reference numbers, MB/s):

| Op | SSD | RAMdisk |
|---|---|---|
| Seq 4 KB write | 199 | 859 |
| Rand 4 KB write | 80 | 140 |
| Seq 256 KB write | 296 | 1502 |
| Rand 256 KB write | 318 | 2190 |

  - SSDs **don't** close the gap to RAM — RAMdisk is still 4–7× faster.
- **High-perf NVM (e.g., StorePak)** approaches 2.5 GB/s and provides reliable persistent storage — used in real-time sensor recording.

---


---

## L18 — File Systems II

*([→ xv6 implementation for this lecture](<#L18 — File Systems II — xv6>))*


> **Tags:** `file systems II` `FS2` `L18` `lec18` `xv6 chapter 6 part 2` `inode layer` `dinode`
> `i-node layer` `direct block` `indirect block` `NDIRECT` `NINDIRECT` `12+1` `addrs[12+1]`
> `largest file size` `71680` `139 blocks` `8MB file support` `bmap` `accessing byte offset`
> `dirent` `directory entry` `14-byte filename` `13 dirents` `inum 0 free` `T_DIR` `T_REG`
> `T_DEV` `directory walk` `dirlookup` `namex` `pathname walk` `path resolution`
> `directory race` `delete-while-walk` `data race on inode` `coarse-grained locking`
> `inode cache lock` `**hand-over-hand locking**` `crab walk` `lock coupling` `chain locking`
> `lock-the-next-release-the-prev` `directory structure` `array vs b-tree` `b-tree dirents`
> `btrfs` `ext4 htree` `lab4-fs` `lab4 inode layout` `0x00 type 0x02 major 0x04 minor`
> `0x06 nlink 0x08 size 0x0c owner 0x0e perms 0x10 addrs` `64-byte inode` `2*512+64*inum`
> `inode write-through` `iupdate-required` `kernel inode cache vs dinode` `struct inode`
> `struct dinode` `inode reference count` `iget refcnt` `mkfs` `boot|sb|log|inodes|bitmap|data`
> `T_DIR vs T_REG` `dirlink` `T_DEV major minor` `iput zero links truncate` `ialloc concurrency`
> `large file lab` `double indirect` `triple indirect` `permission bits PROT_R PROT_W`
> `pathname-walk PROT_R intermediate` `O_CREATE PROT_W parent`

> **Cross-reference:** L18 (this) builds on **L17 File Systems I** (FS abstraction, narrow waist,
> bcache details, balloc/bfree, ialloc, FS layers diagram). For things already covered there
> (buffer cache LRU, B_BUSY/B_VALID/B_DIRTY, ide.c disk driver, block bitmap layout,
> create/write/delete syscall traces) **see file_systems1.md sections 5–14.** This sheet focuses on the
> **inode layer**, **directory layer**, **path resolution**, **hand-over-hand locking**, and
> the **Lab4-fs** inode layout. → forward to **L19/L20 FS Atomicity** (logging — already
> referenced via `log_write`) and **L21 Distributed FS**.

---

## 1. xv6 FS Layered Recap (slide 9)

> **Tags:** `7 layers` `FS stack` `layer responsibility` `bottom-up`

The xv6 FS is **layered**, each layer building abstraction on the next:

```
File descriptor   ← per-process FD table (capability-like; see L17)
Pathname          ← namex / dirlookup (this lec)
Directory         ← dirents (this lec)
Inode             ← iget/ilock/iput (this lec)
Logging           ← begin_op/end_op (L19/L20)
Buffer cache      ← bread/bwrite/brelse (L17)
Disk              ← ide.c (L17)
```

Disk image layout (left→right, also see L17):
`[boot | super | log | inodes | bitmap | data]`
- Inode `inum` → byte address on disk `= 2*512 + 64*inum` (boot+sb skip, 64-byte inodes).
- Read transition (lab slide): `sys_read → fileread → readi → bread → iderw`.

**Source files:**
| File | Role |
|---|---|
| `sysfile.c` | syscall stubs (`sys_open`, `sys_read`, …) |
| `file.c` | VFS-style file ops (`fileread`, `filewrite`) |
| `fs.c` | inode + dir + bmap (`ialloc`, `iupdate`, `readi`, `writei`, `bmap`, `itrunc`, `ilock`) |
| `log.c` / `ilog.c` | journaling (`begin_op`, `end_op`, `log_write` — replaces raw `bwrite`) |
| `bio.c` | buffer cache |
| `ide.c` | disk driver |
| `mkfs.c` | offline tool that builds initial `fs.img` |

---

## 2. Inode Layer

> **Tags:** `inode` `i-node` `metadata` `dinode` `64-byte` `addrs[12+1]` `direct + indirect`
> `ip pointer` `inum` `inode region` `ialloc` `iget` `ilock` `iupdate` `itrunc` `iput`

### 2.1 What an inode IS / IS NOT

- **Inode = file/directory metadata** ONLY. **No data** — only **pointers** to data blocks.
- One **i-number** (`inum`) per inode. `inum → byte addr` is **constant-time** (`2*512 + 64*inum`).
- **dinode** (on-disk, 64 bytes) vs **struct inode** (in-memory; cached, refcounted, with sleeplock).

### 2.2 Canonical xv6 dinode (book layout)

| Field | Purpose |
|---|---|
| `type` | `T_FREE` / `T_FILE` / `T_DIR` / `T_DEV` |
| `major`, `minor` | device numbers if `T_DEV` |
| `nlink` | # directory entries pointing to this inode (when 0 ⇒ free on `iput`) |
| `size` | file size in bytes |
| `addrs[NDIRECT+1]` | **12 direct** block pointers + **1 indirect** block pointer |

Indirect block stores **128 block addresses** (4-byte ptrs in 512-byte block).

### 2.3 Largest file size (book xv6)

```
Max bytes = (NDIRECT + NINDIRECT) * BSIZE
         = (12 + 128)            * 512
         = 140                   * 512
         = 71 680 bytes  (~ 70 KB)
```

### 2.4 Lab4-fs **MODIFIED** dinode layout (slide 14 — exam-critical!)

> **Tags:** `lab4 inode` `owner uid` `perms` `permission bits inode` `139 blocks max` `lab4fs slide 14`

| Offset | Bytes | Field | Notes |
|---:|---:|---|---|
| 0x00 | 2 | `type` | file type |
| 0x02 | 2 | `major` | device major |
| 0x04 | 2 | `minor` | device minor |
| 0x06 | 2 | `nlink` | # links |
| 0x08 | 4 | `size` | file size in bytes |
| **0x0c** | **2** | **`owner`** | UID of owner (Lab4 addition) |
| **0x0e** | **2** | **`perms`** | permission bits (Lab4 addition) |
| 0x10 | 48 | `addrs` | data block ptrs + indirect (48/4 = 12 entries; with indirect → **11 direct + 1 indirect**) |

⚠ **In Lab4 source the direct count is 11 (not 12)** — owner+perms ate 4 bytes:
- max blocks = `11 + 128 = 139 blocks` (lab slide explicitly says **"max file size is 139 blocks"**).
- Lab goal: support **8 MB** files (= 8·1024·1024 / 512 = 16384 blocks) **without growing the inode**.
  - ⇒ chain a **double-indirect** (or repurpose pointers) — inode stays 64 B.

### 2.5 Accessing file byte N (`bmap`)

> **Tags:** `bmap` `byte to block` `byte 8000` `find logical block`

> See [L17 — File Systems I §8](<#L17 — File Systems I>) for the `bmap` algorithm and the byte-8000 worked example.

### 2.6 Inode API + usage idiom

```
ip = iget(dev, inum);   // get cached inode, ++ref
ilock(ip);              // sleeplock; bread inode block if !valid
... read/modify ip->xxx ...
iunlock(ip);
iput(ip);               // --ref; if last+nlink==0 → itrunc + free dinode
```

| Call | Job |
|---|---|
| `ialloc(dev, type)` | scan inode region, mark a free dinode → returns locked inode |
| `iget` | look up cached struct, **++refcnt** (does not read from disk) |
| `ilock` / `iunlock` | sleeplock + lazy `bread` of dinode block (sets `valid`) |
| `iupdate(ip)` | write modified in-mem inode back to disk (cache is **write-through-on-demand**) |
| `itrunc(ip)` | free all data + indirect blocks; `size=0` |
| `iput` | dec refcnt, possibly trigger truncate + dinode-free |

> ⚠ Inode cache is **write-through** in spirit but writes are **explicit** — every modification of `ip->size`/`addrs` MUST be paired with an `iupdate` (or it's lost).

### 2.7 Concurrency in `ialloc`

> See [L17 — File Systems I §9](<#L17 — File Systems I>) for the concurrent-`ialloc` analysis (mutual exclusion is inherited from the buffer-cache block lock).

---

## 3. Directory Layer

> **Tags:** `directory` `dirent` `directory entry` `T_DIR` `dirlookup` `dirlink` `T_REG` `dirent free`
> `inum 0 means free` `14 byte filename` `directory file` `dir is a file`

### 3.1 Directory = a file (with `type=T_DIR`)

- Content of a directory file = **array of `dirent` structs** packed back-to-back.
- xv6 root dir slide says **13 dirents** (per illustration); real xv6 has as many as the directory file is large.
- A `dirent` is **free** when its `inum == 0`.

### 3.2 `struct dirent` (xv6)

| Field | Bytes | Notes |
|---|---:|---|
| `inum` | 2 | inode number; 0 ⇒ slot free |
| `name` | 14 | NUL-terminated/space-padded filename, **max 14 chars** |

Total **16 bytes** per entry.

### 3.3 Directory walk ( `namex` / `dirlookup` )

Path `/bar/baz/foo.txt` walked by:
1. Start at **root inode** (`/`).
2. `dirlookup("bar")` → linear scan dirents → returns inode for `bar`.
3. Repeat with `bar`'s data → `dirlookup("baz")` → `baz` inode.
4. Repeat → `foo.txt` inode.
5. Return final inode (or `0` if not found).

Pathname walk lives in `namex` (used by `namei` / `nameiparent`).

### 3.4 Permission rules over a path walk (Lab4)

> **Tags:** `pathname permission` `PROT_R intermediate` `PROT_W parent dir` `O_CREATE`

- Walking through `/a/b/c/file` requires **PROT_R on every intermediate dir** (`a`, `b`, `c`).
- Creating a new file (`O_CREATE`) only needs **PROT_W on the immediate parent dir**, not the whole chain.
- Owner of file or root can supersede normal perm checks (Lab4 design rule).

---

## 4. The Concurrency Problem in Directory Walks

> **Tags:** `directory walk race` `delete during walk` `inode race` `dangling traversal` `data race`

**Scenario (slide):**
- Process 0 walking `/bar/baz/foo.txt`, currently at `baz`.
- Process 1 calls `unlink baz` (delete).

If unsynchronized:
- P1 frees `baz`'s inode, decrements `nlink`, frees data blocks.
- P0 reads stale dirent → goes to inum that may now point to a different file or free inode.
- ⇒ **memory/disk corruption** or **information leak**.

**Invariant required:** *while a thread is reading directory `D`'s contents, nobody can mutate `D`'s inode/data.* → directory walk needs **exclusive access to the inode** at each step.

---

## 5. Locking Granularity Spectrum (THE big design choice of L18)

> **Tags:** `granularity tradeoff` `coarse grained locking` `fine grained locking`
> `hand over hand` `crab walk` `lock coupling` `chain locking` `lock the next then release prev`
> `tree concurrency` `b-link tree`

### 5.1 Three points on the spectrum

| Granularity | What is locked | Concurrency |
|---|---|---|
| **Coarse** | one global lock for **whole inode cache** (or whole FS) | none — serialized |
| **Hand-over-hand** | one lock **per inode**, held in a moving window of 2 along the path | high — many walks in parallel |
| **Lock-free / optimistic** | path-traversal with versioning (RCU-style) | highest, but complex (Linux dcache/RCU-walk) |

### 5.2 Coarse-Grained Locking

> **Tags:** `inode cache lock` `single global lock`

```
acquire(big_inode_lock);
walk /bar/baz/foo.txt;
release(big_inode_lock);
```

- ✅ Trivially correct.
- ❌ **No concurrency**: only one path walk active globally; readers serialize on writers and *each other*.
- ❌ Even processes touching disjoint subtrees serialize.

### 5.3 Hand-Over-Hand (a.k.a. lock-coupling, crab-walk)

> **Tags:** `hand over hand` `lock chain` `walking lock window` `crab walk` `coupling` `xv6 namex`

**Protocol:**
```
ilock(parent);
child = dirlookup(parent, "name");
ilock(child);          // acquire next BEFORE letting go of prev
iunlock(parent);       // now release previous
parent = child;        // shift the window
... repeat ...
```

- At any moment **at most 2 locks held** along the path; the window slides as the walk advances.
- ✅ A different process can lock a *disjoint* part of the tree → **true concurrent path lookups**.
- ✅ Prevents the delete-during-walk race: deleter can't acquire the inode you currently hold.
- ❌ Implementation must release-before-`iput` correctly (deadlock risk if cycles existed — directories form a tree so OK).
- **Naming:** also called **lock coupling** (databases) or **crab locking**; same idea in B-link trees.

### 5.4 Granularity tradeoff table

| Property | Coarse (big lock) | Per-inode coarse | **Hand-over-hand** | Optimistic / RCU |
|---|---|---|---|---|
| Implementation effort | trivial | easy | moderate | hard |
| Throughput on disjoint paths | 1× | high | **high** | highest |
| Throughput on same path | 1× | 1× | 1× | sometimes high (versioned) |
| Memory overhead | 1 lock | 1 lock/inode | 1 lock/inode | 1 lock + version/inode |
| Correctness reasoning | trivial | easy | medium (window invariant) | hard (versioning / retry) |
| Deadlock risk | none | none if total order | none in tree (no cycles) | depends on retry |

**Pareto frontier (axes: concurrency ↑ vs. impl-complexity ↓):**

```
concurrency
  ▲
  │             optimistic/RCU      ← most concurrent, hardest
  │           ●
  │      hand-over-hand             ← Pareto-OPTIMAL ★ (xv6 picks this)
  │      ●
  │   per-inode coarse
  │   ● (Pareto-optimal-ish; loses on same-path)
  │
  │● big global lock                ← Pareto-OPTIMAL only on simplicity
  └────────────────────────────► simplicity
```

- **Big global lock**: Pareto-optimal *only* on the simplicity axis (nothing simpler).
- **Hand-over-hand**: ★ Pareto-optimal — best concurrency/complexity sweet spot; **xv6's choice**.
- **Per-inode coarse (lock first, walk inside)** is **dominated** by hand-over-hand for path traversal (same complexity, less concurrency on long paths).
- **Optimistic/RCU**: Pareto-optimal on concurrency, dominated on complexity.

### 5.5 Key-idea alignment

| Choice | Key idea(s) served |
|---|---|
| Per-inode lock | **Isolation** of inode state across concurrent ops |
| Hand-over-hand | **Performance** + **Multiplexing** (many walkers); preserves **Isolation** of in-flight walks |
| Coarse lock | **Protection** (correctness) at expense of multiplexing/perf |
| Inode refcount (`iget`/`iput`) | **Sharing** — multiple FDs/threads pin same inode |
| `nlink` | **Sharing** at the namespace level (hardlinks) |

---

## 6. Directory **Structure** Choice: Array vs. Tree

> **Tags:** `dir structure` `linear scan` `b-tree dir` `b+tree dir` `htree` `ext4 htree` `btrfs`

### 6.1 Why xv6 (and many simple FSes) use a flat array

- **Simplicity.** Iterate `readi` block-by-block, scan dirents.
- **Small directories dominate** in the wild (most dirs have tens, not millions, of entries).
- O(n) scan is fine for n ≈ 13 (xv6 root) or even thousands (page-resident).
- **Locking is trivial** under hand-over-hand: one lock on the dir inode is enough.

### 6.2 When trees win

| Structure | Pro | Con | Used by |
|---|---|---|---|
| Linear array | simple, locality, fast tiny dirs | O(n) lookup; no balance | xv6, ext2 |
| **B-tree / B+tree** | O(log n) lookup; good for huge dirs | complex split/merge, more locks | btrfs, ZFS |
| **Hashed (htree)** | O(1) avg lookup | rehash on collisions/growth | ext3/ext4 (htree) |

### 6.3 Granularity tradeoff (directory structure)

```
            small-dir perf    huge-dir perf    code complexity
linear      best              worst            lowest
htree       good              good             medium
b-tree      worst (constant)  best             highest
```

xv6 lives in the **upper-left** corner (small dirs, simple code) — picks linear; modern Linux FSes pick trees for the large-dir tail.

---

## 7. SLO / Performance / CDF Hooks

> **Tags:** `path lookup latency CDF` `dir scan latency` `inode lock contention` `latency tail`

### 7.1 What event would have a CDF?

- **Path lookup latency** (open with N components):
  - Coarse-lock CDF: long tail under load — every path serialized; tail dominated by queueing.
  - Hand-over-hand CDF: tight body, but tail spikes when two walkers cross at the same intermediate inode.
  - Optimistic/RCU: nearly flat hot path, **fat retry tail** under high mutator load.

```
P(latency ≤ x)
1 ──────────────────────  ← optimistic (no contention common case)
│       ▄▀▀▀▀▀▀
│      ▄         ──── hand-over-hand
│     ▄    ▄▀▀▀
│    ▄    ▄        ───── coarse (long tail)
│   ▄    ▄
│  ▄    ▄
0 ─┴────┴───────────────► latency
```

### 7.2 SLO objective analysis

For a metadata-heavy workload, define:
- **p50 lookup ≤ 5 µs** (cache hit)
- **p99 lookup ≤ 100 µs**
- **p999 lookup ≤ 1 ms**

These SLOs are **heterogeneous** between mechanisms:
- Coarse: p50 ok, p99 blows up under multi-tenant.
- HoH: p50 ≈ same, p99 much tighter.
- Optimistic: p50 best, p99 depends on retry rate (heterogeneous *across workloads*).

Implication: SLO heterogeneity ⇒ **picking the locking design is workload-driven.** Single-tenant educational kernel? Coarse is fine. Multi-tenant prod? HoH or RCU.

### 7.3 Directory size granularity

| Dir size | Best structure | Why |
|---|---|---|
| ≤ 64 entries | linear array | no metadata overhead |
| 64 – 64 K | hash / htree | constant lookup, reasonable splits |
| ≥ 64 K | B-tree / B+tree | bounded depth, range scans |

---

## 8. Putting It Together — In-Memory Inode Cache

> **Tags:** `kernel inode cache` `struct inode` `vs dinode` `refcnt` `valid bit` `iget no read`

| Aspect | `struct dinode` (disk) | `struct inode` (memory) |
|---|---|---|
| Lifetime | persistent | lives while `ref > 0` |
| Sync | authoritative on disk | needs `iupdate` to flush |
| Concurrency | bcache block lock during read/write | per-inode sleeplock (`ilock`) + cache lock |
| Extra fields | none | `ref`, `valid`, `dev`, `inum`, sleeplock |

**Lifecycle:** `iget` returns cached struct **without** I/O (just bumps ref). `ilock` **lazily** reads dinode into memory on first lock (`bread` of inode block). `iput` decrements ref; if `ref == 0 && nlink == 0` ⇒ `itrunc` + free dinode.

---

## 9. Key-Idea Alignment (whole L18)

| Mechanism | Key idea served |
|---|---|
| Inode (vs storing data inline) | **Sharing** (multiple links → one inode), **Multiplexing** (12+1 indirection multiplexes 1 inum over many blocks) |
| `addrs[12+1]` indirect | **Performance** (small files cheap; big files possible) |
| Directory as an inode | **Naming** layered on the same FS abstraction (uniformity) |
| `T_DIR` / `T_REG` / `T_DEV` | **Protection** (kernel checks before allowing ops) |
| `dirent.inum == 0` ⇒ free | **Multiplexing** (slot reuse without compaction) |
| Per-inode locks | **Isolation** between concurrent file ops |
| **Hand-over-hand locking** | **Performance** + **Multiplexing** of namespace traversal |
| inode `nlink` | **Sharing** — multi-named identity |
| Owner+perms (Lab4) | **Protection** + **Isolation** between users |

---


---

## L19 — FS Atomicity I

*([→ xv6 implementation for this lecture](<#L19 — FS Atomicity I — xv6>))*


> **Tags:** `file system atomicity` `FS atomicity` `atomicity I` `L19` `lec19` `lec22 in pdf`
> `ordering` `atomicity` `crash consistency` `crash safety` `crash recovery` `power-loss`
> `partial write` `torn write` `disk head haywire` `indeterminate data` `unclean shutdown`
> `persisted to disk` `data corrupted` `metadata corrupted` `mkdir then open race` `mkdir before open`
> `dirent before inode` `dangling dirent` `lost block` `orphan inode` `reordering scenarios`
> `directory + file reorder` `disk interface` `read block` `write block` `flush` `fsync` `barrier`
> `happens-before` `partial order` `cardinality reduction` `n! k! proof` `Pascal triangle proof`
> `binomial coefficient` `space of orderings` `imposing partial order` `ordering primitive`
> `atomic multi-block update` `atomic commit` `make a copy commit copy` `update-in-place forbidden`
> `shadowing` `shadow paging` `shadow bit` `shadow page` `current vs shadow` `bit-flip atomicity`
> `single boolean bit flip` `shadow breakdown` `2x space` `separate disk block for bit`
> `shadow multiple updates` `serialized shadowing` `pipeline shadow` `logging` `journaling`
> `journal` `log records` `committed log record` `log supersedes` `redo log` `WAL`
> `write-ahead log` `log replay` `recovery via log` `crash safety mechanisms` `Lab4-fs atomicity`

> **Cross-reference:** L19 (this) is the *conceptual* foundation for **L20 File System Atomicity II**
> (xv6 logging implementation, `begin_op`/`end_op`, group commit, recovery). Builds on
> **file_systems1.md (L17)** for FS layers + bcache, **file_systems2.md (L18)** for inode/dir/`log_write`
> hookpoint, **ordering_waiting.md (L12)** for happens-before + flush semantics, and
> **concurrency1/2.md** for the broader "atomic multi-step update" mental model. → forward to
> **L21 Distributed Systems** (where atomicity becomes 2PC/Paxos).
>
> Lab connection: **Lab4-fs** uses xv6's existing log. Atomicity bugs surface as orphan inodes,
> dangling dirents, or wrong file size after `make qemu-nox` reboot.

---

## 1. The Problem — Why Crashes Corrupt FSs

> **Tags:** `why atomicity` `crash semantics` `metadata corruption` `data corruption`
> `unexpected shutdown` `dirty FS` `fsck` `inconsistent FS state`

Two questions every persistent FS must answer:

1. **As a user** — *how do I know my data was persisted to disk?* (durability)
2. **As the FS** — *how do I ensure metadata + data isn't left **inconsistent** when the box dies mid-write?* (atomicity + ordering)

Two primitives the FS designer has to enforce:

| Primitive | Definition | Why we need it |
|---|---|---|
| **Ordering** | Updates land on disk **in a chosen order** (happens-before) | FS invariants depend on relative order: e.g. inode-allocated **before** dirent points to it |
| **Atomicity** | A multi-step update **happens entirely, or not at all** — never partially | Crash mid-write must leave a *valid* FS state, not a half-written one |

> *"I need ordering and atomicity to keep a sane system."* (slide 3)

### 1.1 Crash scenarios (whiteboard, slide 4)

```
write(); CRASH; recover; read(); ?     ← what does read() see?

WRITE(fd1, "A"); CRASH; read(fd1) → ?  ← did 'A' make it? all of it?
                                         did inode size update?
                                         do data blocks point to right place?
WRITE(fd1, …); WRITE(fd2, …); CRASH    ← which one survived?
                                         maybe both? maybe neither? maybe one?
```

### 1.2 Motivating example (slide 5)

```c
mkdir("./x");
open ("./x/y", O_CREAT | …);
```

Things that can go wrong if updates aren't atomic + ordered:

| Failure mode | Cause |
|---|---|
| `mkdir` synced **after** `open` | Order violated → `open` references parent that doesn't exist on disk |
| Metadata corrupted for `y` | Partial inode write left half-old, half-new bytes |
| Dir block `x` written **before** `y`'s inode/data | Dangling dirent → on recover, `ls x` shows `y` but inode is garbage / type 0 |

**Take-away:** without ordering + atomicity, valid syscalls can leave the FS in states *no syscall sequence could legally produce*.

### 1.3 Directory representation refresher (slide 7) — *bridge to L18*

Directory data block = array of `dirent {inum: 2B, name: 14B}`. `inum == 0` ⇒ free slot.
The reorder in §1.2 is dangerous because **the dirent and the inode it names live in different disk blocks** — they cannot be updated atomically with the raw block interface.

---

## 2. The Disk Interface — What the Hardware Gives Us

> **Tags:** `disk interface` `read block` `write block` `flush` `barrier` `fsync semantics`
> `not atomic` `not ordered` `buffered writes` `request reordering` `disk head haywire`
> `partially written block` `torn sector`

| Op | Semantics |
|---|---|
| `read(blk)` | returns block contents (eventually consistent w.r.t. our writes) |
| `write(blk, buf)` | issues a write — **may be buffered, reordered, or coalesced**; **not atomic** |
| `flush` | **blocks** until **all pending** read/writes are durably synced |

⚠ Crash semantics:
- A write in flight at crash time → **indeterminate** content on that block (partial sector, old, new).
- Disk head can **"go haywire" after power-off** → can leave **incorrect data on adjacent blocks** being written too.
- ⇒ We can NOT assume *anything* about a block whose write was in flight.

### 2.1 Ordering = composing flushes

The ONLY primitive the disk gives us to impose order is **`flush`** — a *barrier*.
Inside a flush-bounded group, writes can land in any order.

```
write 47           ┐
write  2           │  group A — any permutation
write 48           ┘
flush              ← barrier
write 49              group B
```

Disk now guarantees: *all* of {47, 2, 48} reach durable storage **before** 49 starts.

---

## 3. Cardinality of the Ordering Space (slides 10–11)

> **Tags:** `partial order cardinality` `(n+k)! >= n!*k!` `imposing order shrinks options`
> `binomial proof` `Pascal triangle` `happens-before reduces options`

**Claim:** *imposing partial order via flushes shrinks the space of possible execution orderings — strictly* (or at worst equally).

| Schedule | Possible disk orderings |
|---|---:|
| `W47 W2 W48 W49` (no flush) | `4! = 24` |
| `W47 W2 W48  FLUSH  W49` | `3! · 1! = 6` |
| **General**: group of `n` writes, FLUSH, group of `k` writes | **`n! · k!`** |

**Proof that `(n+k)! ≥ n!·k!`** (slide 11):

```
C(n+k, k) = (n+k)! / (n!·k!)        [Pascal triangle entry, ∈ ℕ]
⇒ C(n+k, k) ≥ 1
⇒ (n+k)! = n!·k! · (positive integer)
⇒ (n+k)! ≥ n!·k!                    ∎
```

**Take-away (slide 10 box):** *happens-before is the **only** primitive that reduces the cardinality of the ordering set.* Every flush is a deliberate trade of throughput for predictability.

> **Granularity tradeoff (flush frequency):**
> - **Coarse / few flushes** → fewer barriers, more reordering, higher throughput, **larger crash window**.
> - **Fine / many flushes** → strict order, low throughput (each flush costs ≥1 disk rotation / SSD program), **tight crash window**.
> - **Per-write flush** (max fine) ≈ synchronous FS — correct but slow.
> - **Sweet spot:** 1 flush per *transaction* (commit boundary), not per-write. This is what journaling buys us.

---

## 4. Atomicity — Two Primary Methods

> **Tags:** `atomicity methods` `atomic update strategies` `shadowing vs logging` `commit point`
> `cannot update in place` `make a copy` `commit the copy`

The disk *cannot* give us atomic multi-block updates directly. So we **don't update in place** — instead:

> **General recipe:** *Make a copy, atomically "commit" the copy.*

Two industry-standard realizations:

1. **Shadowing** (a.k.a. **shadow paging** — see *btrfs*, ZFS COW, WAFL).
2. **Logging / Journaling** (see *ext3/4*, NTFS, xv6, JFS, ReiserFS).

---

## 5. Shadowing (a.k.a. Shadow Paging / COW)

> **Tags:** `shadowing` `shadow paging` `copy-on-write FS` `shadow bit` `shadow data` `current data`
> `bit flip atomic` `single boolean decision` `proxy large updates with one bit`
> `btrfs` `zfs` `wafl` `netapp` `2x storage` `shadow multiple updates`

### 5.1 Idea (slide 13)

Reduce the multi-block update problem to a **single Boolean bit-flip**, which the disk *does* perform atomically:

- Keep **two** copies of the data: **current** and **shadow**.
- Keep a **shadow bit** (on a *separate* disk block!) that selects which copy is "live".
- To update:
  1. **Copy** live → shadow.
  2. **Mutate** shadow.
  3. **Flip** the shadow bit.

The atomic point is step 3 — one bit, one block, atomic.

### 5.2 Single-update protocol (slides 14–18)

```
   ┌────────┐  copy  ┌────────┐
   │current │ ─────► │shadow  │
   │X=1     │        │X=1     │
   │Y=2     │        │Y=25  ◄─── update
   │Z=42    │        │Z=42    │
   └────────┘        └────────┘
        ▲                ▲
        └────[shadow bit]┘  ← atomic flip
```

Disk schedule: `{1, 2}  FLUSH  {3}` — i.e. **2 writes + a flush**:
- **Write 1+2:** copy & mutate (one fused write to shadow region).
- **Flush:** ensures shadow is durable on disk **before** the bit flip.
- **Write 3:** flip the shadow bit.

> Q (slide 17): *Does the copy have to be atomic?* **No** — only the bit-flip must be atomic. If we crash during step 1/2, shadow is garbage, bit still points at the (intact) old copy. ⇒ Recover by ignoring shadow.

### 5.3 Crash analysis (slide 19) — what survives?

| Crash at step | On-disk state | What recovery sees |
|---|---|---|
| During 1 (copy) | shadow partial, bit=old | bit=old → use **old current** ✓ (lose update — but consistent) |
| During 2 (mutate) | shadow partial, bit=old | same — **old current** ✓ |
| Between 2 & 3 | shadow complete, bit=old | **old current** ✓ (we lose the update, but FS is consistent) |
| During 3 (flip) | bit-flip is one block / atomic; either old or new | EITHER old or new is consistent — never partial |

**Invariant:** the FS is *always* in a self-consistent state — either the pre- or post-update version. This is the crash-consistency win.

### 5.4 Multiple updates (slide 20)

To do **two** sequential updates (Y=25 then Y=27), repeat the cycle:

```
copy+mutate → flush → flip → copy+mutate → flush → flip
   1+2          f      3       4+5         f       6
```

Each flip is an independent commit. Roles of "current" and "shadow" swap each round.

### 5.5 Shadowing breakdown (slide 21)

| Property | Cost / Tradeoff |
|---|---|
| **Atomic?** | ✅ Yes — Boolean bit can't be partial |
| **Storage** | ❌ ≥ **2× space** — every block needs a shadow twin |
| **Writes per update** | ≥ 2 (copy+mutate, then flip bit) **plus** a flush in between |
| **Shadow bit placement** | Must be **own disk block** (need atomic single-block write to flip it) |
| **Wasted space** | High — much of shadow region cold most of the time |
| **Random-write throughput** | Hurts — copy step amplifies write traffic |
| **Read throughput** | Decent — direct read of "current" copy |

### 5.6 Why shadowing usually **isn't** the *primary* FS mechanism (slide 22)

- 2× space is a hard sell on commodity disks.
- Each user write triggers full block-copy → write amplification.
- Bit-flip granularity is per-block, not per-FS-operation → updates that touch many blocks need many shadow chains.
- Used heavily where **snapshots are first-class** (btrfs/ZFS) — the "old current" naturally becomes a free snapshot.
- For a teaching kernel like xv6 → **logging is simpler & cheaper** ⇒ go to §6.

---

## 6. Logging (a.k.a. Journaling) — Intro

> **Tags:** `logging` `journaling` `journal` `WAL` `write-ahead log` `redo log`
> `log records` `commit log` `log supersedes` `recovery replay` `log read fallback`
> `ext3 ext4 jbd2` `xv6 log.c`

### 6.1 Idea (slide 23)

Instead of two physical copies, keep a **log** (a separate region of disk) of *what the new data should be*.

- Every modification is **first written to the log**.
- A **commit record** in the log is the atomic point ("the bit flip").
- *After* commit, the FS later **applies** log entries to their real homes (the "install" or "checkpoint" phase).
- On reboot: **replay** committed log records, **discard** uncommitted ones.

### 6.2 Read path semantics

For any block **B** during normal operation:

```
if B has a committed log record:
    return log's version of B    (log SUPERSEDES the FS)
else:
    return the in-place FS block
```

This means: as soon as a transaction commits, its effect is *visible* even if the FS hasn't installed the changes yet.

### 6.3 Anatomy of a log transaction (preview — full detail in L20)

```
┌──────── transaction ────────┐
│  log_write(block A)         │   (data first, in log region)
│  log_write(block B)         │
│  log_write(block C)         │
│  ─── flush ───              │   (durable in log)
│  COMMIT record              │ ← atomic point
│  ─── flush ───              │   (commit durable)
│  install A,B,C in place     │
│  ─── flush ───              │
│  free log                   │
└─────────────────────────────┘
```

### 6.4 What logging buys us vs shadowing (preview)

| Aspect | Shadowing | Logging |
|---|---|---|
| Storage overhead | ~2× whole FS | ~ log region only (small, e.g. xv6: 30 blocks) |
| Write amplification | Full copy of touched block | Block written ~2× (log + install) |
| Atomic primitive | Shadow-bit flip | Commit record write |
| Multi-block atomicity | Hard (chain of flips) | **Native** — any group in one transaction |
| Snapshots | Free (old "current" *is* a snapshot) | Not free (need extra mechanism) |
| Used by | btrfs, ZFS, WAFL | ext3/4, NTFS, xv6, JFS |

---

## 7. Side-by-side Comparison: Shadowing vs Logging

| Dimension | **Shadowing (COW)** | **Logging (Journaling)** |
|---|---|---|
| Atomic point | Single shadow-bit flip | Commit record write (single sector) |
| Space overhead | ≥ 2× (per-block twin) | small fixed log region |
| Write amplification | 1× block copy + 1 bit flip | 2× (write to log, then install) |
| Multi-block atomicity | Chained / awkward | First-class transactions |
| Random write perf | Bad (copy whole block) | OK (sequential log appends) |
| Crash recovery | Trivial — just trust shadow bit | Replay/discard log records |
| Snapshot support | Trivial (cheap, first-class) | Add-on, often hard |
| Implementation complexity | Subtle (bit placement, chaining) | Moderate (transaction state machine) |
| Used in | btrfs, ZFS, WAFL, log-structured FS variants | ext3/4, NTFS, xv6, JFS, JBD2 |

### 7.1 Pareto frontier

Plot **(space overhead, write amplification, snapshot cost)**:

```
            ▲ snapshot cost (low = good)
            │
   Shadow ●─┼─────────              ← cheap snapshots, costly storage
            │
            │
            │      ● Logging       ← cheap storage, costly snapshots
            │
            └──────────────────►  storage overhead (low = good)
```

**Both are Pareto-optimal** — neither strictly dominates:
- Shadow wins on **snapshot cost** (snapshots free).
- Logging wins on **storage overhead** + **multi-block atomicity ergonomics**.

A **dominated** point would be e.g. "synchronous write per block, no log" — high write cost, no atomicity, no snapshots. (It exists in toy FSs and is universally rejected.)

### 7.2 Granularity spectrum (commit unit)

| Commit unit | Pros | Cons |
|---|---|---|
| **Per byte / per write** | Smallest crash window | Insane flush cost; serialized I/O |
| **Per syscall** | Crash-safe at user-visible boundary | Many small log txns; lots of flushes |
| **Per group of syscalls** (xv6 group commit) | Amortizes flush across batch | Latency for first writer to see commit |
| **Per checkpoint / minute** | Best throughput | Up to a minute of work lost on crash |

xv6 sits at **per-group-of-syscalls** (`begin_op`/`end_op` grouping — see L20).

### 7.3 Key-Idea Alignment

| Mechanism | Key idea(s) |
|---|---|
| `flush` barrier | **Performance** trade for **Protection** of FS invariants (forces ordering) |
| Happens-before / partial order | **Performance** (more parallelism than total order) + **Protection** of invariants |
| Shadowing | **Isolation** of in-flight update from live data; **Protection** via atomic bit; **Sharing** (multiple snapshots see consistent views) |
| Shadow-bit on separate block | **Protection** — needed because atomicity is a per-block property |
| Logging | **Atomicity** of multi-block update = **Protection** of FS invariants; **Performance** via group commit (multiplexes many ops onto one flush) = **Multiplexing** |
| Log-supersedes-FS read rule | **Multiplexing** of "true value" lookup across two storage tiers |
| Recovery / replay | **Protection** under failure (crash safety = a form of isolation from power loss) |

---

## 8. Performance Analysis — CDFs

> **Tags:** `latency CDF atomicity` `crash window CDF` `commit latency` `flush cost`

### 8.1 Single-write commit latency

```
P(latency ≤ x)
1 ─────────────────────────────  ← async (no flush)   — fast tail, bad crash semantics
│   ▄▀▀▀▀▀
│  ▄         ──── logging (group commit)              — moderate p50, tight p99
│ ▄    ▄▀▀▀
│▄    ▄         ──── shadowing                        — write amp lengthens body
│    ▄
│   ▄    ▄▀▀▀▀▀
│  ▄    ▄        ──── synchronous (flush per write)   — slow + tight CDF
0─┴────┴─────────────────────────► latency
```

### 8.2 SLOs — homogeneous? heterogeneous?

A reasonable durability SLO contract:

| SLO | Async | Shadow | Log (group) | Sync |
|---|:-:|:-:|:-:|:-:|
| Commit p50 ≤ 1 ms | ✓ | ✗ | ✓ | ✗ |
| Commit p99 ≤ 50 ms | ✓ | ✗ | ✓ | ✓ |
| **Window of un-durable data ≤ 0** (post-`fsync`) | ✗ | ✓ | ✓ | ✓ |
| Multi-block atomic | ✗ | ✓ | ✓ | per-block only |

⇒ SLOs are **heterogeneous** across mechanisms:
- *async* trades **durability** for **latency** — different SLO axis dominates.
- *shadow* + *log* both meet durability but differ on **latency** and **storage** axes.
- ⇒ **Choice depends on workload's primary SLO**: snapshot-heavy → shadow; throughput-heavy → log; cache-only / scratch → async OK.

### 8.3 Crash-window (data-loss) CDF

`P(data older than x seconds at crash)`:
- **Sync per write:** vertical line at 0.
- **Logging w/ group commit:** step at the commit interval (e.g. every 30 ms).
- **Shadowing:** similar — step at flip frequency.
- **Async writeback:** long tail (could be tens of seconds).

---


---

## L20 — FS Atomicity II

*([→ xv6 implementation for this lecture](<#L20 — FS Atomicity II — xv6>))*


> **Tags:** `file system atomicity II` `FS atomicity 2` `L20` `lec20` `ordering atomicity FS part 2`
> `shadowing` `shadow paging` `shadow bit` `current vs shadow copy` `flip shadow bit` `shadow consecutive writes`
> `logging` `journaling` `journal` `journal commit` `commit record` `log entry`
> `Entry Type Location Data` `COMMIT block` `committed entry` `uncommitted entry`
> `log supersedes` `read from log` `read from data block` `if it's in the log take log`
> `properties of log` `implicit ordering` `append-only` `sequential reads on recovery`
> `happens-before entry_i entry_{i+1}` `log atomicity via commit records`
> `commit mechanism 1` `separate 1-block commit` `w → flush → w_c` `w_c happens-before next entry`
> `commit mechanism 2` `checksum commit` `piggyback commit on validation` `partial-write detection`
> `out-of-order writes` `entry committed iff all prior committed`
> `checkpoint in design space` `space and time savings over checksum`
> `log merge` `log full` `iterate committed entries` `overwrite normal version` `clear log`
> `crash during merge` `idempotent log entries` `op(x) = op op op (x)` `at-least-once semantics`
> `log merge nits` `clear log atomically` `invalidate first entry`
> `recovery` `replay log` `stop at first uncommitted` `then clear log`
> `logging advantages` `sequential writes` `disk efficient` `few syncs` `general atomicity` `general ordering`
> `logging costs` `~2x writes` `double writes` `periodic merge` `read from log first` `predictability`
> `tail latency CDF` `latency CDF logging` `worst case probabilistic log scan`
> `modern FS modes` `journaling off` `metadata-only` `ordered` `full` `Linux default ordered` `ext3 ext4`
> `POSIX weak semantics` `data corruption` `metadata corruption` `protect metadata at minimum`
> `ext4 ordering` `data writes ordered before metadata` `ext4 default`
> `full journaling disadvantages` `2GB write 64B inode` `log capacity diminished` `expensive recovery`
> `expensive reads` `unpredictable read latency`
> `head-of-line blocking` `HOL blocking metadata` `gcc perf` `responsiveness of metadata`
> `ordered mode mechanism` `data_w + metadata_w → flush → commit_w` `no stale data`
> `journal modes` `writeback` `ordered` `journaled` `data=writeback` `data=ordered` `data=journal`
> `journaling design tradeoff` `safety vs performance pareto`
> `POSIX FS interface` `read write mkdir create unlink chmod chown stat fcntl flock fsync`
> `fsync` `file system memory barrier` `persisted to disk` `cached write no guarantee`
> `fsync interaction with log` `combine all FS data into one log` `total ordering on data`
> `flushing any file flushes whole log` `fsync REALLY expensive` `bottleneck`
> `user-level atomicity` `atomic file updates POSIX` `app-level logging`
> `make log file` `store updates in log` `update actual file` `delete log`
> `Create(log) Write(log) fsync(log) fsync(./)` `Write(file) fsync(file) Unlink(log) fsync(./)`
> `why so many syncs` `ordering vs persistency` `conflate ordering and persistency`
> `Optimistic Crash Consistency` `OCC` `SOSP 2013` `Pillai Chidambaram` `osync` `dsync`
> `osync ordering primitive` `dsync durability primitive`

> **Cross-reference:** Builds directly on **L19 File System Atomicity I** (the other crib sheet —
> partial-sector writes, atomic disk units, fsck, why update-in-place breaks). This sheet picks up
> at the **two solutions to atomicity** (shadowing vs logging) and goes through commit mechanisms,
> recovery, ext4 modes, fsync semantics, app-level atomicity, and the OCC research idea.
> Pulls heavily from **L17/L18 file_systems1.md / file_systems2.md** for buffer cache, inode
> layout, and xv6's `log.c` (`begin_op`/`end_op`/`log_write` — re-examined here as a concrete
> instance of the journaling design). → next: **L21 Distributed Systems**.

---

## 1. The Atomicity Problem (Recap)

> **Tags:** `atomicity problem` `partial-sector write` `multi-block update` `data + inode update`
> `cannot update-in-place` `make a copy commit copy`

- Disk gives a **partial-sector write interface with flushes**; FS needs **atomic multi-block** (data + inode + bitmap) updates.
- **Cannot update-in-place** — disk doesn't support it atomically across multiple blocks.
- **Strategy:** make a copy, then **atomically "commit"** the copy.
- **Two primary methods:** (1) **Shadowing**, (2) **Logging / Journaling**.

---

## 2. Shadowing (Shadow Paging)

> **Tags:** `shadowing` `shadow paging` `two copies` `shadow bit` `current copy` `shadow copy`
> `update shadow flip bit` `consecutive shadowing`

### 2.1 Mechanism (5 steps)

1. Maintain **two copies** of the data.
2. A **shadow bit** records which copy is "current".
3. **Reads** go to the *current* copy.
4. **Writes** go to the *shadow* copy.
5. After write completes, **flip the shadow bit** — single-bit flip is the atomic commit.

### 2.2 Consecutive writes (recap from board)

- After flip, roles swap: the *old* current is the *new* shadow.
- Each write: copy current→shadow, modify shadow, flush, flip bit.
- Sequence: `1+2 → flush → 3 (flip) → 4,5 (next write) → flush → 6 (flip)`.

### 2.3 Properties

- **Atomicity:** yes — the bit flip is the linearization point.
- **Ordering:** implicit per-object only.
- **Cost:** **2× space** (two copies of every datum); also writes still need a flush before the flip.

---

## 3. Logging / Journaling

> **Tags:** `logging` `journaling` `journal` `commit record` `log entry` `Type Location Data`
> `log supersedes data block` `read from log if present`

### 3.1 Mechanism

1. **Write the change to the journal** (an entry).
2. **Write a "commit"** record to atomically commit the section.
3. (Eventually) **merge** the log into the actual data blocks ("checkpoint").

### 3.2 Entry format

| Type | Location | Data |
|---|---|---|
| dblock / metadata | block # (e.g. 7) | new bytes ("Hello World") |

### 3.3 Read path with logging

- **For any committed log record, the log SUPERSEDES the on-disk block.**
- Algorithm:
  - If block is in the log AND committed → return **log version**.
  - Else → return on-disk **data block**.
- **Uncommitted entries are NOT considered valid** — read goes to disk.

### 3.4 Properties of the log

| Property | Provided? | How |
|---|---|---|
| **Implicit ordering** | ✅ | append-only writes; sequential, ordered reads on recovery; `Entry_i happens-before Entry_{i+1}` |
| **Atomicity** | ❌ inherently — ✅ via commit records | a "commit" delimiter makes a group of writes appear atomic |

---

## 4. Commit Mechanisms

### 4.1 Mechanism 1 — Separate Commit Block

> **Tags:** `commit mechanism 1` `separate commit block` `w → flush → w_c` `1 block per commit`

- Layout: `[ Entry | COMMIT | Entry | COMMIT | Entry ]` — each commit is its **own block**.
- Sequence: `write entry (w) → flush (f) → write commit (w_c) → flush (f) → next entry`.
- `w` happens-before `w_c`; `w_c` happens-before next `w`.
- **Cost:** one flush between entry and commit, one flush between commit and next entry → **2 flushes per commit**.

### 4.2 Mechanism 2 — Checksum Commit

> **Tags:** `commit mechanism 2` `checksum` `piggyback commit on validation` `out-of-order writes`
> `entry committed iff all prior committed`

- **Idea:** piggyback commit on a **checksum** of the entry — validates *and* commits in one shot.
- Multiple entries on the **same disk block**, **written in one op**.
- Commit/checksum is one write. **If checksum doesn't match → not committed** (handles partial writes).
- **Out-of-order rule:** entry is "committed" only if **all entries before it** are committed (handles disk reorderings).
- **Result:** drop the explicit COMMIT block, drop the flush between entry-and-commit.

### 4.3 Comparison

| Aspect | Mech 1 (sep. block) | Mech 2 (checksum) |
|---|---|---|
| Space overhead | +1 block per commit | 0 (piggybacked) |
| # flushes per commit | 2 (`w f w_c f`) | 1 |
| Partial-write detection | trust block atomicity | explicit checksum |
| Out-of-order tolerance | needs strict flush ordering | enforced via "prior all committed" rule |
| Implementation | simpler | trickier (checksum + validation logic) |

> **Checkpoint in design space (slide):** with checksum commit we gain ordering, atomicity, AND **space + time** improvement over separate commits (no shadow area, fewer flushes). "Are we done? Can we do better?" → modern FS modes below.

### 4.4 Pareto frontier — commit mechanisms

```
        ↑ Atomicity correctness
        |  Mech 2 (checksum)  ★ Pareto-optimal
        |  Mech 1 (separate)  ✓ on frontier (simpler, more flushes)
        |  Shadow paging      ✓ on frontier (2× space, but per-object only)
        |  No commit / fsck   ✗ dominated
        +────────────────────────→  Performance / space
```

- **Mech 2 dominates Mech 1** in space and time, weakly dominates in correctness — Mech 1 stays useful only as a simpler reference design.
- **Shadowing vs logging:** different axes (space-vs-time vs flush-cost-vs-recovery-cost). Both Pareto-optimal in different regions.

---

## 5. Recovery & Log Merge

> **Tags:** `log merge` `log full` `iterate committed` `overwrite normal version` `clear log`
> `recovery on startup` `idempotent` `at-least-once`

### 5.1 Log merge (when log fills)

1. Iterate **all committed entries** of the log.
2. For each entry, **overwrite the "normal" version** of the data with the log version.
3. Once the **last committed entry is processed**, **clear the log**.

### 5.2 Crash during merge

- Log merge is **multiple disk I/O ops**, not atomic. Possible outcomes after crash:
  - Full / no merge.
  - Entries merged partially, blocks fully updated.
  - Entries merged partially, **some blocks corrupted (partial sector)**.
- **Recovery: just traverse the log again.**
- **Required assumption: log entries are IDEMPOTENT** — `op(x) = op(op(op(x)))`.
  - Idempotence ⇒ "**at-least-once**" semantics is enough; replaying a partial merge is safe.

### 5.3 Atomic log clearing

- If log clearing isn't atomic, a partial clear could lose committed work.
- **Trick:** the log only goes up to the **first uncommitted entry**, so just **invalidate the first entry** (one-block write) — that's the atomic head pointer.

### 5.4 Recovery on startup

- On boot: **merge log up to the first uncommitted entry** (guarantees newest data wins).
- Clear the log → FS ready.

---

## 6. Logging — Pros / Cons

> **Tags:** `logging benefits` `logging costs` `tail latency` `predictability`

### 6.1 Benefits

- **[performance]** Logs are **sequential writes** — extremely disk-efficient (especially HDD).
- **[correctness]** General-purpose **atomicity** via commit records.
- **[correctness]** General-purpose **ordering** — entries committed in order ⇒ intended op order preserved.
- **[performance]** Far **fewer syncs/flushes** than naïve "write everything in place + flush each".

### 6.2 Costs

- **~2× writes** — once into the log, once again from the log into the actual FS data on merge.
- **Periodic log merge** required (e.g. when full).
- **Reads may need to consult log first** — increases unpredictability.
- **Predictability / tail latency** worsens (see CDF below).

### 6.3 Performance CDF — what reads look like

```
P(latency ≤ x)
  1.0 |─────────●●●●●●●●●●  ← in-place / writeback (low, tight tail)
      |   ╱
      |  ╱   ●●●●●●●●●●     ← logging hits w/ short log (small p99 bump)
  0.5 | ●●●
      |╱
      |   long tail ──────────●●  ← p99: linear scan of long log on read miss
  0.0 |__________________________________→ latency
        fast              slow
```

- Logging adds a **right tail** to the read CDF (probabilistic log traversal on each read).
- Full journaling (data in log) makes this **worse** — log is enormous → every read potentially scans more.

---

## 7. Modern FS Journaling Modes (ext3 / ext4)

> **Tags:** `data=writeback` `data=ordered` `data=journal` `journaling off` `metadata-only`
> `Linux default ordered` `ext4 default`

### 7.1 The 4 options

| Mode | What's logged | Data ordering | Safety | Speed |
|---|---|---|---|---|
| **off** | nothing | none | ✗ FS can corrupt | fastest |
| **metadata-only / writeback** | metadata | data unordered wrt metadata | metadata safe; data corrupt visible | fast |
| **ordered** | metadata | **data written BEFORE metadata** | metadata safe; no stale-pointer-to-garbage | medium ★ **Linux default** |
| **journaled / full** | metadata + data | data atomic with metadata | strongest | slowest |

### 7.2 Pareto plot (slide: "Journaling Design Tradeoff")

```
  ↑ Safety
  |   journaled  ★
  |        ╲
  |         ordered  ★      (←   Linux default — best knee)
  |             ╲
  |              writeback  ✓ (Pareto, low safety)
  |
  |   bad design  ✗ (dominated: low safety AND low perf)
  +─────────────────────────────→ Performance
```

- **journaled / ordered / writeback** are all on the **Pareto frontier** — choosing among them is a safety/perf tradeoff.
- **off** and "**bad design**" are **dominated**.
- "**dream**" point (top-right, both high) is the research goal → see **OCC** (§11).

### 7.3 ext4 defaults (ordered mode) — what it gives

- **Metadata is always journaled** (no FS corruption).
- **Data writes are *ordered* before metadata** writes.
- "**happens-before**": `Data writes ⇒ metadata journal commit`.
- Still **possible bad behaviour** with data alone (e.g. partial writes in middle of a file are visible) — but FS structure is intact.

### 7.4 Ordered mode — mechanism breakdown

- **Goal:** at any moment when an inode update is **visible**, the corresponding data **must be written**.
- **Practical sequence:** `{data_w, metadata_w} → flush → commit_w`.
- **Result:** `commit_w visible ⇒ metadata_w visible ⇒ data_w visible` → **no stale data possible**.
- Conceptually = enforcing a **happens-before relationship** between data & metadata.

### 7.5 Full-journaling disadvantages

- E.g. **2 GB data write** followed by a **64 B inode update** → both go to log = doubled I/O on the 2 GB.
- **Log capacity diminished** → more frequent merges, expensive recovery.
- **Expensive reads** — must consult log; latency CDF gets long tail.
- **Head-of-line (HOL) blocking** for metadata: tiny inode update stuck behind giant data write → kills responsiveness (e.g. **gcc perf** drops).
- Failure probability ~ proportional to time-to-disk → big writes increase risk.

> **HOL solution = "ordered" mode** (journal metadata only; sequence data-then-metadata).

---

## 8. POSIX FS Interface

> **Tags:** `POSIX FS interface` `read write mkdir create unlink chmod chown stat`
> `fcntl flock funlock` `fsync` `file system memory barrier`

| Category | Calls |
|---|---|
| Standard I/O | `read`, `write`, `mkdir`, `create`, `unlink`, `chmod`, `chown`, `stat` |
| File control | `fcntl`, `flock`, `funlock` |
| Persistency | **`fsync`** — syncs a file to disk; "**file-system memory barrier**" |

```c
fd = open(...);
write(fd, ...data...);   // Cached. NO guarantee data is on disk.
...
fsync(fd);               // ~ FS memory barrier
// data is now on disk and persisted.
```

- **Before fsync:** file contents could be corrupt / missing on crash.
- **After fsync:** contents are durable.
- POSIX gives **very weak guarantees** — must be consistent with all reasonable FSs.

---

## 9. fsync ↔ Log Interaction (the BIG gotcha)

> **Tags:** `fsync interaction with log` `combine all FS data into one log` `total ordering`
> `flushing any file flushes whole log` `fsync REALLY expensive`

- **Downside of journaling:** all FS writes funnel into **ONE shared log**.
- This places a **total order** on ALL data in the FS.
- **Consequence:** `fsync(fd_2)` must flush the **entire log up to that point** — including unrelated `write(fd_1)` data!
- Example:
  ```
  write(f1, 2GB)    ; goes into log
  write(f2, 1B)     ; goes into log
  fsync(fd2)        ; flushes log, which means flushing f1's 2 GB too!
  ```
- **Takeaway:** `fsync` ops are **REALLY expensive** because of this entanglement.

### 9.1 SLO implication (heterogeneous)

- Naïve assumption: latency of `fsync(small_file)` ~ size of small file. **Wrong.**
- Real SLO: tail-bounded by the **largest pending write in the global log**.
- This makes per-file SLOs **heterogeneous & non-isolated** — small flushes get penalized by big writers (a **performance-isolation failure**).

---

## 10. User-Level Atomic File Updates (POSIX-only)

> **Tags:** `atomic file update POSIX` `app-level logging` `make log file` `update actual file` `delete log`

### 10.1 The plan (4 steps)

1. **Make a log file**.
2. **Store updates in the log**.
3. **Update the actual file**.
4. **Delete the log**.

### 10.2 Full POSIX sequence (with required syncs)

```
Create(log)
Write(log, "offset, size, data, cksum")
fsync(log)         ← entry persisted
fsync("./")        ← directory entry for log persisted
Write(file, ...update data...)
fsync(file)        ← payload persisted
Unlink(log)
fsync("./")        ← otherwise log not actually unlinked!  PHEW
```

- **Each fsync enforces a happens-before edge** between adjacent steps.
- Logically:
  - `write(log)` ⇒ `fsync(log)` ⇒ `fsync(./)` ⇒ `write(file)` ⇒ `fsync(file)` ⇒ `unlink(log)` ⇒ `fsync(./)`.

### 10.3 Why so many syncs? Persistency? **NO — Ordering!**

- The user does **not** actually need data persisted *right now*.
- They need the **happens-before order** preserved across crashes.
- **Problem:** in POSIX, `fsync` is the **only** primitive available, and it conflates **ordering** with **persistency** (durability).

---

## 11. Optimistic Crash Consistency (OCC, SOSP 2013)

> **Tags:** `Optimistic Crash Consistency` `OCC` `SOSP 2013` `Pillai Chidambaram` `osync` `dsync`
> `split fsync` `ordering primitive` `durability primitive` `conflate ordering and persistency`

### 11.1 The insight

- "**The issue is, we conflate ordering and persistency.**"
- Most user atomicity protocols want **ordering for correctness**, not **persistency right now**.
- A flush forces both ⇒ paying durability cost just to get an ordering edge.

### 11.2 The fix

- **Split `fsync` into two operations:**
  - **`osync(fd)`** — **ordering** primitive. Ensures preceding writes happen-before subsequent ones (no actual disk-flush needed if hardware can guarantee order).
  - **`dsync(fd)`** — **durability** primitive. Forces data to be persisted now.

### 11.3 Rewritten POSIX atomic update with OCC

```
Create(log)
Write(log, "offset, size, data, cksum")
osync(log)        ← ordering only — cheap
osync("./")       ← ordering only
Write(file, data)
osync(file)       ← ordering only
Unlink(log)
fsync("./")       ← only here do we *actually* need durability
```

- Most heavy `fsync`s become cheap `osync`s.
- One real `fsync` at the end provides the durability commit point.

### 11.4 Pareto improvement

- OCC pushes toward the "**dream**" point on the Safety×Performance diagram (§7.2): same crash-consistency safety, much higher performance.
- Pareto-dominant over plain ordered/journaled if the FS exposes the split primitives.

---

## 12. Comparison Table — All Atomicity Designs

| Design | Atomicity | Ordering | Space cost | Time cost | Recovery cost | Pareto? |
|---|---|---|---|---|---|---|
| **Update in place + fsck** (L19) | weak | none | 0 | flush per write | **scan whole disk** | dominated by all below |
| **Shadow paging** | per-object | per-object | **2× capacity** | 1 flush + bit flip | trivial (read bit) | ✓ (space cost regime) |
| **Logging (separate commit)** | strong | strong | log space | 2 flushes / commit | replay log | ✓ |
| **Logging (checksum commit)** | strong | strong | log space | **1 flush / commit** | replay + verify ck | ★ dominates separate-commit |
| **Metadata-only (writeback)** | metadata only | none for data | small log | low | replay metadata log | ✓ (perf regime) |
| **Ordered (Linux default)** | metadata only | **data → metadata** | small log | medium | replay metadata log | ★ knee |
| **Full / journaled** | data + metadata | strong | **2× writes** | high (HOL) | replay full log (slow) | ✓ (safety regime) |
| **OCC (osync/dsync)** | strong | strong (cheap) | small log | **near writeback** | replay log | ★ dream (research) |

---

## 13. Granularity Analysis — What to Log At

> **Tags:** `log granularity` `byte-level` `block-level` `transaction-level` `file-level`

| Granularity | Log entry size | Pros | Cons |
|---|---|---|---|
| **Byte-level / op-level** | tiny (e.g. "+1 to inode.size") | least space; fastest small updates | complex replay logic; must be idempotent at op-level |
| **Block-level** ★ xv6 | one block per change | matches disk unit; simple replay (overwrite) | wasteful for tiny diffs (whole block per 1B change) |
| **Transaction-level** | group of blocks per syscall | natural atomic unit (begin_op/end_op) | bigger log; needs commit boundaries |
| **File-level** | whole file | simplest semantics | absurd cost for big files |

- **xv6 picks block-level + transaction grouping** (a sweet spot for a teaching FS — replay = `bwrite(b)` for each).
- **ext4 ordered** also block-level; **journaled** mode adds whole-block data entries.
- **Sweet spot:** block-level entries grouped into transactions — gets ordering atomicity at the FS unit while keeping replay trivial.

---

## 14. Key-Idea Alignment

| Design choice | Primary system-design principle |
|---|---|
| **Shadow paging** | **Isolation** of versions; **Atomicity** via single-bit flip (linearization point) |
| **Logging (journal)** | **Ordering** (append-only ⇒ implicit happens-before); **Atomicity** (commit records); **Performance** (sequential writes amortize seeks) |
| **Checksum commit** | **Performance** (1 flush, not 2); **Protection** of writes against partial-sector corruption |
| **Idempotent log entries** | **Correctness under partial replay** (at-least-once); enables crash-during-recovery safety |
| **Metadata-only journaling** | **Performance** (avoid HOL blocking on metadata); **Sharing** of one log among many files at acceptable safety |
| **Ordered mode** | **Protection** (no stale-pointer-to-garbage); **Performance** (data not journaled twice) |
| **Full journaling** | **Strongest atomicity / consistency**; sacrifices Performance & Predictability |
| **fsync as memory barrier** | **Multiplexing**: one primitive serves both ordering and durability — but conflation **hurts isolation** (§9 HOL) |
| **OCC (osync/dsync)** | **Separation of concerns** — split conflated primitive into two; restores **performance isolation** between ordering-only and durability-needing apps |

---

## 15. SLO Analysis — Are They Homogeneous?

| Op (mode) | SLO | Homogeneous? | Implication |
|---|---|---|---|
| `read` (writeback) | ~1 disk seek | ✅ across files | predictable |
| `read` (full journal) | 1 seek + log scan | ❌ depends on log size & contents | **tail-latency unpredictable** |
| `fsync(small)` (any journal mode) | ~ size of pending log | ❌ entangled with other writers | **hetero per file** — small flush penalized by big writer |
| `fsync(small)` (OCC `osync`) | barrier only | ✅ near-homogeneous | restores isolation |
| Recovery time | bounded by log length | ❌ between modes (writeback ≪ ordered ≪ journaled) | governs reboot SLO |

- **Heterogeneous SLOs** ⇒ a single global log violates per-file performance isolation; this is exactly what OCC and per-file logs aim to fix.
- **Homogeneous after OCC** ⇒ apps can reason locally about latency.

---


---

## L21 — Distributed Systems

*([→ xv6 implementation for this lecture](<#L21 — Distributed Systems — xv6>))*


> **Tags:** `distributed systems` `distributed` `dist sys` `L21` `lec21` `multi-pc os` `many nodes`
> `working together` `single task` `no shared memory` `no shared clock` `independent clock`
> `coordination over unreliable comm` `ordering atomicity concurrency` `partial information`
> `think like a vertex` `message passing` `causality` `happened-before`
> `two generals problem` `2 generals` `byzantine generals` `byzantine` `byzantine fault`
> `consensus` `consensus algorithm` `agreement` `flp` `flp theorem` `flp impossibility`
> `fischer lynch paterson` `asynchronous network` `asynchronous consensus` `synchronous network`
> `synchronous rounds` `rounds` `round based protocol` `proposal phase` `decision phase`
> `acceptance phase` `2f+1` `2f plus 1` `f failures` `fail-stop` `fail-stop failure` `crash failure`
> `paxos` `multi-paxos` `paxos made simple` `part-time parliament` `lamport` `leslie lamport`
> `time clocks ordering of events` `leader election` `leader` `proposer` `acceptor` `learner` `listener`
> `multi-phase commit` `cap theorem` `cap` `consistency` `availability` `partition tolerance`
> `pick 2 of 3` `cp system` `ap system` `ca system` `dynamo` `amazon dynamo` `weak consistency`
> `eventual consistency` `quorum` `replication` `liveness` `safety` `termination`
> `3f+1` `bft` `byzantine fault tolerance` `pbft` `raft` `zookeeper` `chubby` `etcd`

> **Cross-reference:** Distributed systems = **OS abstractions extended across machines** that share *neither memory nor clock*. Where single-node concurrency (concurrency1.md, concurrency2.md, ordering_waiting.md) used **shared memory + atomics + locks**, dist-sys must use **message passing + consensus**. The classic problems carry over (ordering, atomicity, concurrency) but the *mechanisms* are entirely different. Lamport's "Time, Clocks, and the Ordering of Events" (the Two-Generals/causality paper) is also the conceptual root of vector/logical clocks (referenced in ordering_waiting.md). FLP and CAP are **fundamental impossibility results** — like the halting problem of distributed computing — and every real system is a *negotiated compromise* against them.

---

## 1. Definition — What is a Distributed System?

> **Tags:** `definition` `distributed system definition` `silberschatz` `os concepts`
> `many nodes single task` `multi-pc os`

- **Silberschatz definition:** "A distributed system is a collection of processors that **do not share memory or a clock**."
- Intuitive definition: **Many nodes, working together, on a single task.**
- Each node has its **own RAM, own CPU, own clock** — coordination must happen via **messages over a network**.
- **Multi-PC OS analogy:** distributed systems aim to make many computers **look like one** — exactly the abstraction game an OS plays for many cores/processes on one box.
- **Same goals + properties** as OS (sharing, multiplexing, isolation, protection); **different mechanisms** because the medium is unreliable communication, not shared memory.

### Motivation — Why distributed systems?

| Goal | What it buys | OS analogue |
|---|---|---|
| **Resource sharing** | Aggregate disks/CPUs/data across nodes | Filesystem, scheduler |
| **Computation speedup** | Parallelism across nodes | Multicore concurrency |
| **Reliability** | Survive single-machine failure | RAID, replication |

### Key-idea alignment
- **Sharing** — many users / nodes share one logical service.
- **Multiplexing** — one logical service multiplexed over many physical nodes.
- **Isolation** — partial-failure isolation (one node dies, the rest survive).
- **Protection** — authentication / authorization across an *untrusted* network.
- **Performance** — horizontal scale-out, throughput.

---

## 2. Single-Node OS vs Distributed System — Properties

> **Tags:** `properties` `single node vs distributed` `failure model` `clock source`
> `mindset shift` `monolithic global mindset` `think like a vertex`

| Property | Single-Node OS | Distributed System |
|---|---|---|
| **Failures** | None (hardware faults are catastrophic, rare) | **Routine** — partial failures of nodes/links are *expected* |
| **Clock source** | Single shared clock | **Independent clocks per node** — no global "now" |
| **Mindset** | *Monolithic / global* — see all state, use shared memory | *"Think like a vertex"* — each node sees only **partial** info, coordinates via messages |
| **Coordination primitive** | Shared memory + atomics + locks | Message passing |
| **Source of time / order** | Wall clock, instruction order | **Causality / happened-before** (Lamport) |
| **What's hard** | Race conditions, deadlock | Consensus, partition, asynchrony, partial failure |

### Pareto framing
- The "global memory / single clock" mindset is **dominated** in any setting where a node *can* fail or a partition *can* occur — it gives more programmer convenience but **breaks** as soon as the assumption is violated.
- "Think like a vertex" is **Pareto-optimal for fault-tolerance** at the cost of programmer ergonomics.

---

## 3. The Difficulty — Two Generals Problem

> **Tags:** `two generals` `2 generals problem` `mongol hoard` `attack at dawn` `messenger`
> `unreliable channel` `agree on something` `coordinated action`

### The story
- Two armies (Gen1, Gen2) on hills; the Mongol horde is in the valley between them.
- They must **attack together** — if either attacks alone, they die.
- Their **only communication is messengers** running through the valley, who **can be captured (dropped messages)**.
- **Question:** can they reach **certainty** that they will both attack at the same time?

### The naive protocols (and why each fails)

```
Round 1: Gen1 → Gen2  "Attack @ 2"
        ↑ Gen1 doesn't know if it arrived

Round 2: Gen2 → Gen1  "ACK"
        ↑ Gen2 doesn't know if its ACK arrived
        ↑ if it didn't, Gen1 won't attack and Gen2 dies attacking alone

Round 3: Gen1 → Gen2  "ACK ACK"
        ↑ now Gen1 doesn't know if its ACK-ACK arrived...
        ...infinite regress.
```

### Proof of impossibility (inductive)
- Assume there is a protocol that solves the problem in **N messages**.
- The **N-th message** could always be dropped (channel is unreliable).
- If the protocol still works after dropping it, then we actually had a protocol in **N-1 messages** — contradicts minimality.
- Inductively shrinks to **0 messages**, which obviously cannot solve the problem.
- **Conclusion:** No finite protocol can guarantee consensus over an **unreliable channel** with **drops**.

### Implication
- Two computers **cannot** reach certain consensus over an unreliable network with no prior knowledge — even just **two of them**, even on a **single bit**.
- This is the *baseline* impossibility before we even add asynchrony or failures.

---

## 4. FLP Theorem — Asynchronous Consensus is Impossible

> **Tags:** `flp` `flp theorem` `flp impossibility` `fischer lynch paterson` `1985`
> `asynchronous consensus` `fail-stop` `crash failure` `liveness` `termination`
> `no consensus algorithm` `guaranteed to terminate`

### Statement
> In an **asynchronous** network where **messages may be delayed but not lost**, there is **no consensus algorithm** that is **guaranteed to terminate** in every execution for all starting conditions, **if at least one node may fail-stop**.

### Decoding the statement
- **Asynchronous** = no bound on message delivery time. No timeouts, no notion of "late."
- **Messages may be delayed but not lost** — this is *strictly stronger* than Two Generals (Two Generals also drops messages). FLP holds even when the channel is reliable!
- **No consensus algorithm** = no algorithm that **all** of: agrees, decides, and **terminates**.
- **Fail-stop failure** = a node simply stops operating (no messages, no state changes). The friendliest possible failure model.

### Why it's worse than 2 Generals
- 2 Generals: drops kill consensus.
- FLP: even with **no drops** but **asynchrony + 1 crash**, you still can't have a deterministic, always-terminating consensus algorithm.
- Intuition: you can never tell apart **"node is slow"** vs **"node is dead"**.

### What you *can* do (escape hatches)
- Give up **liveness/termination** in some executions (Paxos: terminates "eventually" with some synchrony).
- Add **synchrony** assumptions — bounded message delay, timeouts.
- Use **randomization** to break the deterministic impossibility.

### CDF intuition (performance lens)
- Paxos latency CDF: **steep rise around RTT × 2** (proposer→acceptors→proposer), then a **long heavy tail** corresponding to leader-failure / re-election episodes that FLP guarantees you *cannot* upper-bound.
- The tail is the price of liveness under FLP.

---

## 5. Escape Route 1 — Synchronous Rounds + Timeouts

> **Tags:** `synchronous rounds` `rounds` `timeout` `2f+1` `f failures` `quorum`
> `proposal round` `decision round` `acceptance round` `over-estimate` `conservative timeout`

### The setup
- Assume **2f + 1** nodes total, of which up to **f may fail-stop**.
- Note **2f+1 = f + (f+1)**: even with f failures, **f+1 honest nodes form a strict majority**.
- A **round** = a "reasonable amount of time" for a message to travel point-to-point. Has to be a **conservative over-estimate**.

### Round-based consensus sketch (3 nodes, f=1)
- **Round 1 — Proposal:** every node broadcasts its proposed value (`o1`, `o2`, `o3`) to every other.
- After Round 1, each node has a set of received proposals (`{o1, o2, o3}`, possibly `{o2, o3}` if a node crashed and dropped its msg).
- **Decision:** each node deterministically picks (e.g. lowest, or majority) from its received set.
- **Round 2 — Acceptance:** broadcast chosen value; once each honest node sees a **majority (f+1)** agreeing, decide.

### The lecture whiteboard example (N=3, f=1)
- 3 nodes (N1, N2, N3), each proposes one of `o1`, `o2`, `o3`.
- N3 fails after sending some messages → some nodes see only `{o1, o2}`.
- After **decision** round each surviving node has a consistent set; in **acceptance** round they confirm and decide.
- **2f+1 = 3 = f + (f+1) = 1 + 2** → 2 honest nodes is always a majority.

### Problems with synchronous rounds

| Problem | Why it hurts |
|---|---|
| **Round must be a conservative over-estimate** | If you under-estimate, late-but-alive nodes look dead → wrong decisions. |
| **Slow** | Algorithm pace = **worst-case** message delivery, not average. Throughput tanks. |
| **Brittle to network variability** | One slow link slows the whole protocol. |
| **Wastes time** | Even when no failures occur, every round runs to completion. |

### Granularity of the round timer

| Round timeout | Pro | Con |
|---|---|---|
| **Tight (~RTT)** | Fast progress when healthy | Frequent false-positives → spurious failure handling, oscillation |
| **Conservative (≫ RTT)** | Safe — almost never wrong about "dead" | Throughput dominated by worst case; bad tail latency |
| **Adaptive (RTO-style)** | Tracks observed RTT | Complex; can still mis-track during partitions |

**Takeaway:** synchronous rounds **trade throughput for safety**. The pareto frontier here is **(latency, safety)** — tighter timeouts gain latency but lose safety; you can't have both.

### Key-idea alignment
- **Performance** vs **Protection (correctness)** is the central tradeoff — round size is the knob.
- **Sharing**: every node participates equally → uniform load.

---

## 6. Escape Route 2 — Paxos

> **Tags:** `paxos` `paxos made simple` `part-time parliament` `leslie lamport`
> `multi-phase commit` `leader election` `proposer` `acceptor` `learner` `listener`
> `mostly asynchronous` `synchronous leader election`

### High-level
- **Paxos** = the canonical consensus protocol for **fail-stop** failures with **2f+1** nodes (tolerates **f** failures).
- Original paper: *"The Part-Time Parliament"* (Lamport, notoriously dense).
- Simpler version: *"Paxos Made Simple"* (Lamport).
- **Mostly asynchronous** (no waiting in the steady state) — uses a **leader** to coordinate.
- **Cannot be fully asynchronous** (FLP forbids it) → uses a **synchronous protocol for leader election + failure detection** (timeouts).

### Roles
- **Proposer / Leader** — receives client requests, broadcasts to acceptors.
- **Acceptors** — vote on proposals; must form a majority quorum.
- **Listener / Learner** — observes leader liveness, returns final committed value to client.

### High-level flow
1. Client submits request to **leader**.
2. Leader **broadcasts** to all nodes (proposers/acceptors).
3. Acceptors respond back to the leader.
4. **Listener** verifies leader liveness, returns response to client.
5. Up to **f** nodes may die without compromising consensus.
6. Result: **fully asynchronous consensus while healthy, given synchronous leader election**.

### Paxos design choices vs synchronous-rounds

| Property | Sync Rounds | Paxos |
|---|---|---|
| Steady-state latency | Per-round (worst case) | ~1.5 RTT (mostly async) |
| Leader needed? | No | Yes |
| Synchrony assumption | Always | **Only during leader election / failure** |
| Failures tolerated | f of 2f+1 | f of 2f+1 |
| Termination guarantee | Yes (within bounded rounds) | Yes if leader election eventually succeeds (FLP-compatible) |
| Complexity | Simple | Complex (multi-phase, ballot numbers) |
| Throughput | Low (round-pacing) | High (pipelined, async) |

### Paxos's weakness — leader-death drop
- When the leader dies, **in-flight requests are dropped** until a new leader is elected.
- During election, the cluster is **unavailable**.
- **Paxos sacrifices availability for consistency** during leader changes — directly the motivation for CAP.

### Variants worth knowing (outside lecture)
- **Multi-Paxos** — pipelined Paxos for streams of decisions (one election per epoch).
- **Raft** — Paxos's friendlier cousin: same guarantees, *much* simpler protocol explanation; the basis for **etcd, Consul, CockroachDB**.
- **PBFT** — Byzantine-tolerant Paxos.

### Key-idea alignment
- **Protection (correctness/safety)** — never disagrees on a decided value.
- **Performance** — fast common case, slow rare-failure case.
- **Sharing** — replicated state machine; every node sees the same log.
- **Multiplexing** — one logical decision sequence multiplexed over 2f+1 nodes.

### CDF — Paxos latency
- **Body**: thin spike near `~1.5 × RTT` (proposer → quorum → proposer).
- **Knee**: jumps at the **leader-election timeout** when the leader has crashed but not yet been re-elected.
- **Tail**: heavy and FLP-unbounded under repeated failure / partition.

---

## 7. CAP Theorem

> **Tags:** `cap theorem` `cap` `consistency availability partition tolerance` `pick two`
> `brewer` `eric brewer` `cap triangle` `cp ap ca` `network partition`

### Statement
> A distributed system can provide **at most 2 of 3** properties simultaneously: **Consistency**, **Availability**, **Partition Tolerance**.

### The three properties

| Property | Definition |
|---|---|
| **Consistency (C)** | All machines have the **same view** of the data (i.e. linearizable reads). |
| **Availability (A)** | The system **stays live** in the presence of machine failures (every request receives a non-error response). |
| **Partition Tolerance (P)** | The system **continues to function** even if subsets of machines cannot communicate (network partitions). |

### Why you can only have 2
- A partition splits the cluster into two groups that cannot communicate.
- **Either** both groups answer (preserving A) but possibly disagree (losing C),
- **Or** at least one group refuses to answer (preserving C) but loses A.
- **P is non-negotiable** in real distributed systems (partitions *will* happen) → in practice the choice is **CP vs AP**.

### Where systems live on the CAP triangle

| System | Choice | What you give up | When to pick |
|---|---|---|---|
| **Paxos / Raft / Spanner / Chubby / etcd / ZooKeeper** | **CP** | Availability during partition / leader loss | Bank ledgers, lock services, config stores — must never disagree |
| **Amazon Dynamo / Cassandra / Riak** | **AP** | Strong consistency (eventual instead) | Shopping carts, social timelines — *always* be online, fix divergence later |
| **Single-node DBs** | **CA** | Partition tolerance — only works because there's no partition | Same-rack RDBMS, mainframe |

### Pareto framing
- **All three points (CP, AP, CA) are Pareto-optimal** under different workload assumptions — none dominates.
- The non-Pareto-optimal choice is to claim "I have all three" — that's a lie.

### Granularity — CAP applies per-operation
- A system can be **CP for writes** and **AP for reads** (e.g. read replicas).
- A system can be **CP for one bucket** and **AP for another** (multi-tenant Dynamo-style).
- The CAP choice is at the **per-operation / per-shard** granularity, not whole-system.

### SLO implications

| System | SLO type | Homogeneous? |
|---|---|---|
| **CP (Paxos)** | "p99 latency < X **except during leader election** (no SLO during partition)" | **Heterogeneous** — different SLOs in healthy vs partitioned mode |
| **AP (Dynamo)** | "100% availability, eventual consistency within Y seconds" | **Homogeneous availability**, heterogeneous consistency-time |
| **CA (single-node)** | "p99 latency < X" | Homogeneous, but **brittle** — SLO violated *catastrophically* under partition |

The heterogeneity tells you what the system *prioritizes*. CP systems publish availability SLAs in nines; AP systems publish "staleness" SLAs in seconds.

### Key-idea alignment
- **Sharing** — replication is what makes the question interesting.
- **Protection** — consistency is the "data integrity" half of CAP.
- **Performance** — availability is the "always-up" half.

---

## 8. Amazon Dynamo — A+P System

> **Tags:** `dynamo` `amazon dynamo` `shopping cart` `eventual consistency`
> `weak consistency` `vector clocks` `merge conflicts` `read repair` `quorum tunable`

- Amazon's shopping cart needs **~100% availability** — every "add to cart" must succeed even during partition.
- **Dynamo gives up strong C for A + P.**
- Concurrent writes during a partition lead to **divergent replicas**; Dynamo **merges** them later (e.g. **union of carts** — items "come back" sometimes).
- Trade-off accepted: **occasional weird UX** (item reappearing in cart) >>> **lost sale due to outage**.
- Inspired Cassandra, Riak, DynamoDB.

### Why this is sensible at Amazon scale
- Outage = lost revenue, lost trust, paged engineers.
- Inconsistent cart = recoverable at checkout (final consistency check).
- **Asymmetric cost of failure** drives the design choice.

---

## 9. Byzantine Generals — Active Sabotage

> **Tags:** `byzantine` `byzantine generals` `byzantine fault` `byzantine fault tolerance` `bft`
> `pbft` `3f+1` `malicious node` `arbitrary failure` `adversarial`

### The escalation
- **Fail-stop failure**: node simply stops (friendliest model).
- **Byzantine failure**: node may **send arbitrary, lying, or contradictory** messages — actively **sabotage** the protocol.
- Examples: hardware bit flips, malicious nodes, compromised replicas, software bugs sending bad data.

### The bound
- Solvable with **3f + 1 nodes** to tolerate **f** Byzantine failures (vs **2f + 1** for fail-stop).
- Intuition: you need a majority of *honest* nodes that exceeds the Byzantine vote — ⌈2/3⌉ honest required.
- "Well outside scope of this lecture" — but **PBFT (Castro & Liskov 1999)** is the canonical algorithm; **Tendermint, HotStuff** are modern blockchain BFT variants.

### Comparison

| Failure model | Quorum needed | Mechanism | Where used |
|---|---|---|---|
| **No failures** | 1 | Trivial | Single-node DB |
| **Fail-stop** | **2f+1** | Paxos / Raft | Most internal infra (etcd, Spanner, Chubby) |
| **Byzantine** | **3f+1** | PBFT / HotStuff | Blockchains, untrusted multi-tenant, military, aerospace |

---

## 10. Quick-Reference Comparison Table — All Consensus Strategies

> **Tags:** `consensus comparison` `protocol comparison` `summary table`

| Strategy | Failure Tolerance | Synchrony Assumption | Throughput | Latency (steady state) | Availability under partition | Complexity |
|---|---|---|---|---|---|---|
| **Two Generals naive** | None (impossible) | — | — | — | — | Trivial |
| **Synchronous rounds** | f of 2f+1 fail-stop | Bounded message delay | Low (round-paced) | Slow (worst case) | Fails | Low |
| **Paxos** | f of 2f+1 fail-stop | Synchronous leader election | High | ~1.5 RTT | Fails (CP) | High |
| **Raft** | f of 2f+1 fail-stop | Synchronous leader election | High | ~1.5 RTT | Fails (CP) | Medium |
| **Dynamo (AP)** | f of 2f+1 fail-stop | Async, gossip | Very high | <1 RTT | **Available** (eventual) | Medium |
| **PBFT (Byzantine)** | f of 3f+1 Byzantine | Synchronous leader election | Lower (more msgs) | ~3 RTT | Fails (CP) | Very high |

### Pareto frontier
- **Paxos / Raft (CP)**: Pareto-optimal for **strong consistency + crash tolerance + reasonable throughput**.
- **Dynamo (AP)**: Pareto-optimal for **always-on + horizontal scalability + low-latency writes**.
- **PBFT**: Pareto-optimal under **adversarial / Byzantine** threat model — strictly more general, strictly more expensive.
- **Synchronous rounds**: dominated by Paxos in throughput; only "wins" on **conceptual simplicity** and **bounded termination**.
- **CA (single-node)**: dominated as soon as you actually need scale or fault-tolerance — only Pareto-optimal in the trivial "no partition possible" regime.

---

## 11. Granularity of Consensus

> **Tags:** `granularity` `consensus granularity` `coarse vs fine consensus`
> `total order broadcast` `per-key consensus`

| Granularity | Example | Pros | Cons |
|---|---|---|---|
| **Per-bit** | "Did Gen2 get my message?" | Smallest unit, precise | Useless on its own (Two Generals) |
| **Per-operation** | Paxos for each op | Strong serializability | Latency per op = consensus cost |
| **Per-batch / Multi-Paxos** | Pipeline N ops | Amortizes consensus cost | Complex log compaction |
| **Per-shard / per-key** | Spanner, Dynamo partition | Horizontal scale | No cross-shard atomicity (need 2PC) |
| **Per-epoch (leader term)** | Raft term | One election → many decisions | Long leader = stale leader risk |
| **Whole-cluster** | Old single-master DBs | Simple model | Doesn't scale |

The pareto-optimal point depends on **workload write rate** and **cross-shard transaction frequency**.

---

## 12. SLO Analysis Across Distributed Systems

> **Tags:** `slo` `service level objective` `availability slo` `consistency slo`
> `homogeneous slo` `heterogeneous slo` `latency tail`

| Design choice | Primary SLO | Secondary SLO | Homogeneous across operations? |
|---|---|---|---|
| **CP (Paxos/Raft)** | p99 latency, "no stale reads" | Availability nines (4–5 nines typical) | **Heterogeneous** — read SLO ≠ write SLO; SLO violated during election |
| **AP (Dynamo)** | 100% availability ("five 9s+") | Time-to-convergence (e.g. < 1s) | **Heterogeneous** — every key may have its own staleness window |
| **BFT (PBFT)** | Same as CP + integrity | Cost-per-tx | **Homogeneous safety**, heterogeneous latency by client trust level |
| **Sync rounds (academic)** | Bounded termination round count | None | Homogeneous (everyone runs at slowest pace) |

**Heterogeneity reveals what the system optimizes for.** A system whose latency SLO and availability SLO are *both* tight is almost certainly lying about partitions.

---

## 13. Where the Concepts Map to Earlier Lectures

> **Tags:** `cross reference` `connection to other lectures` `dist sys vs os`

| Distributed concept | Single-node analogue | Lecture |
|---|---|---|
| Consensus | Atomic operation / lock acquisition | concurrency1.md, concurrency2.md |
| Happened-before / causality | Memory ordering, TSO, DRF0 | concurrency2.md |
| Leader election | Mutual exclusion winner | concurrency2.md |
| Replication for fault tolerance | Journaling / FS atomicity | file_systems2.md, L19/L20 atomicity |
| Network partition | Lost interrupt / dead CPU | concurrency1.md |
| 2f+1 / 3f+1 quorum | Majority-vote spinlock contention | concurrency2.md |
| FLP impossibility | Halting problem of dist-sys | (none — fundamental) |
| CAP | Tradeoff between safety + liveness | ordering_waiting.md (semantically) |
| Byzantine fault | Adversarial attacker | security1.md, security2.md |
| Paxos leader | Kernel scheduler | schedulers.md |
| Dynamo eventual consistency | Lazy / write-back caching | vm2.md (lazy design philosophy) |

---


---

## L22 — Efficient AI Stack

*([→ xv6 implementation for this lecture](<#L22 — Efficient AI Stack — xv6>))*


> **Tags:** `efficient ai stack` `ai stack` `L22` `lec22` `tumanov` `sail` `systems for ai lab`
> `producing dnns` `consuming dnns` `ml inference` `inference serving` `inference serving system`
> `dnn serving` `model serving` `edge ai` `edge inference` `latency-sensitive` `accuracy-sensitive`
> `resource constrained` `tri-partite matching` `applications x models x hardware` `app x model x hw`
> `r1 latency` `r2 accuracy` `r3 resource efficiency` `r1 r2 r3 trade-off` `slo attainment`
> `latency slo` `bursty workloads` `bursty traffic` `burst` `azure functions trace` `maf trace`
> `microsoft azure functions` `cv squared` `coefficient of variation` `ingest rate` `lambda`
> `clipper` `inferline` `clockwork` `infaas` `gen1 serving` `gen2 serving` `swayam` `gemel` `alpaserve`
> `cold start` `cold starts` `cpu-gpu swap` `model loading` `gpu memory scarce` `static model choice`
> `dynamic model choice` `coarse-grained scheduling` `fine-grained scheduling` `model switching`
> `superserve` `super serve` `nsdi 25` `subnetact` `subnetwork activation` `near-instantaneous switching`
> `slackfit` `slack fit` `slack-based scheduling` `edf` `earliest deadline first` `slack`
> `pareto-optimal subnets` `pareto frontier` `accuracy-latency frontier` `compofa` `unfoldml`
> `superfed` `des` `holmes` `dsched` `sushi` `mlsys` `nas` `neural architecture search`
> `supernetwork` `supernet` `weight sharing` `shared layers` `non-shared layers` `subnet`
> `batch size` `batching` `ilp` `np-hard` `oracular knowledge` `ilp formulation` `placement constraints`
> `timing constraints` `dnn` `deep neural network` `specialized dnn` `hardware-aware dnn`
> `gpu` `fpga` `tpu` `ml inference hardware` `latency profile` `accuracy profile` `profiler`
> `router` `dispatcher` `worker` `result queue` `subnetwork in-place activation`

> **Cross-reference:** This is the *capstone research lecture*. It pulls together every key idea
> from the course: **scheduling** (schedulers.md, EDF), **granularity** (coarse vs fine — like
> page-table granularity in vm1.md), **SLOs** (heterogeneous QoS targets), **isolation/multiplexing**
> (one supernet multiplexed across many subnet "models"), **batching tradeoffs**
> (concurrency1.md / ordering_waiting.md — batching = throughput vs latency), **CDFs and tail latency**
> (networking.md / file_systems.md). The R1–R3 trade-off is a **3-axis Pareto frontier**, and
> SuperServe's central claim is that **fine-grained reactive scheduling on a Pareto-optimal subnet
> set strictly dominates static and coarse-grained baselines** under bursty traffic.

---

## 1. Motivation — Surge in AI Applications

> **Tags:** `motivation` `ai surge` `ai applications` `self-driving` `chatbot` `surveillance`
> `health monitoring` `language translation` `ml market` `inference demand`

- AI everywhere: **self-driving cars, chatbots, surveillance cameras, EEG/ECG health monitoring, language translation**.
- **Trends:**
  - U.S. AI market: ~\$103B (2022) → ~\$594B (2032) — *6×* in 10 years.
  - **ML inference demand** at Facebook DCs: ~3.5× over 8 quarters.
  - Edge AI hardware market: ~\$5B (2018) → ~\$21B (2028).
- **Inference**, not training, dominates production deployment.

---

## 2. Edge-AI Application Characteristics

> **Tags:** `edge ai` `application characteristics` `latency sensitive` `accuracy sensitive`
> `resource constrained` `tight deadlines` `interactive` `real-time decisions`
> `power constraints` `memory constraints`

Three characteristics define edge-AI workloads:

| # | Characteristic | What it implies | Examples |
|---|----------------|-----------------|----------|
| 1 | **Latency-sensitive** | Strict latency SLOs, tight deadlines | Self-driving real-time decisions, chatbot interactivity |
| 2 | **Accuracy-sensitive** | Need correct predictions | Heart-failure detection, language translation |
| 3 | **Resource-constrained** | Limited memory/power/HW | GPU in a car, solar-powered cameras |

---

## 3. The Three Goals (R1, R2, R3)

> **Tags:** `goals` `r1` `r2` `r3` `maximize accuracy` `maximize latency slo`
> `maximize slo attainment` `meet resource constraints` `resource efficiency`
> `tri-partite matching problem` `application x model x hardware`

- **(R1) Maximize Latency-SLO attainment** — fraction of queries completing within deadline.
- **(R2) Maximize Accuracy** — predictive quality.
- **(R3) Meet resource constraints / Resource Efficiency** — fit on given GPU/CPU memory budget.

### How each goal is met
| Goal | Solution direction |
|---|---|
| (R2) Accuracy | Use accurate AI models — **Deep Neural Networks (DNNs)** |
| (R1) Latency | Use **specialized hardware** (GPUs, FPGAs, TPUs) |
| (R3) Resource Eff. | Build **efficient backend systems** (this lecture) |

### Tri-partite matching problem
- The technical challenge = **Applications × Models × Hardware** matching:
  - Each app has a **latency-SLO + accuracy target**.
  - Each model has a **(latency, accuracy)** profile that depends on HW.
  - Each HW has its own throughput/memory constraints.
- **Specialized DNNs** are produced via Neural Architecture Search (NAS).

### Key-idea alignment (R1–R3 ↔ course concepts)
- **Performance** — R1 (latency) + throughput.
- **Sharing** — one HW serves many apps; one supernet shares weights across subnets.
- **Multiplexing** — time-multiplex models (subnets) on a GPU.
- **Isolation** — per-query latency budget; one slow query shouldn't tank others.
- **Protection** — not central to this lecture (no adversaries in scope).

---

## 4. The Fundamental Trade-off (R1 ↔ R2 ↔ R3)

> **Tags:** `tradeoff` `trade-off` `r1 r2 r3 tradeoff` `accuracy-latency tradeoff`
> `accuracy-throughput tradeoff` `pareto frontier` `r1 r2 r3 pareto`

```
More Accuracy (R2)            ⇒   Less Latency / Less SLO attainment (R1)
More Latency / SLO atn. (R1)  ⇒   Less Resource Efficiency (R3)
```

- **Bigger model** → more accurate but slower → worse SLO attainment.
- **Tighter SLO** → need more headroom / replicas → worse R3.
- **3-axis Pareto frontier** in (R1, R2, R3) space: improving any axis costs another.
- **The challenge:** "How to navigate the trade-off space between R1–R3?" — *especially* under **bursty workloads**.

### ML training vs ML inference — homogeneous or heterogeneous objectives?

> **Tags:** `ml training vs inference` `training inference homogeneous` `training inference heterogeneous`
> `inference SLO` `training SLO` `mixed AI workload` `scheduling ML` `SJF vs CFS for ML`
> `SLO ml inference` `ML scheduling tradeoff` `is RL good for ML scheduling`

**Verdict: heterogeneous.** Different objectives, different metrics, different scheduling policies. ([→ L11 §5 worked example](<#L11 — Schedulers>) for the quantum derivation.)

| Axis | **ML Training** | **ML Inference** |
|---|---|---|
| Primary metric | Throughput / time-to-accuracy / GPU utilization | P99 / P999 tail latency under SLO |
| Job length | Hours–weeks (long, predictable) | 10s of ms (short, bursty) |
| Preemptibility | Tolerates preemption + checkpointing | **Don't preempt mid-request** |
| Quantum | Large (seconds–minutes); CFS fair-share is fine | ≈ service time (50–100 ms); EDF / SlackFit |
| Scheduling policy | CFS / gang-scheduling / SLURM | Profile-driven (SubNetAct), SLO-aware (SlackFit) |
| Resource elasticity | Scale up — more GPUs = faster training | Scale out — more replicas = lower tail |
| Failure cost | Restart from checkpoint | Drop request / serve degraded model |

**Scheduling implications:**
- **Co-locating training + inference** on the same fleet has **R1↔R3 tension**: training wants high utilization (R3), inference wants headroom for bursts (R1). Heterogeneous SLOs ⇒ separate queues or strict priority.
- **SJF works for inference** when service time is predictable per (model, hardware) pair (this is exactly what SuperServe's offline profiler gives — see §11 latency heat-map).
- **CFS works for training** (proportional fairness across long jobs) but **fails for inference** (no SLO awareness, no notion of deadline).
- **Splitting compute across model sizes** (SubNetAct subnets) is the way to *make* the workload effectively homogeneous within each class — pick a subnet whose service time matches the slack budget.
- **Is RL good for ML scheduling? No.** RL needs a reward signal with reasonably fast feedback; inference deadlines are sub-100 ms (way too fast for RL inference itself), and training rewards arrive after hours. Plus the action space (which subnet, which GPU) is small enough that hand-tuned heuristics (SlackFit) and ILP solutions dominate.

**Tradeoff cheat:**
- *Treat as homogeneous* ⇒ underprovisioning either training (slow) or inference (SLO violations). Always wrong at scale.
- *Treat as heterogeneous, separate hardware* ⇒ wastes GPUs, hurts R3.
- *Treat as heterogeneous, shared hardware with priority* (the SuperServe answer) ⇒ inference preempts training; training fills idle slack. Pareto-optimal.

---

## 5. Bursty Workloads — Why Static Choices Fail

> **Tags:** `bursty workloads` `burstiness` `traffic burst` `azure functions` `maf`
> `microsoft azure functions trace` `cv squared` `cv^2` `coefficient of variation squared`
> `ingest rate` `qps` `q/s` `arrival rate` `lambda` `throughput trace`

- Real production traces (e.g., **Microsoft Azure Functions / MAF trace**) show **bursts**: throughput swings between ~6k and ~8k q/s on short timescales.
- **Bursty traffic** is parameterised by:
  - **λ (lambda)** — mean ingest / arrival rate.
  - **CV²ₐ** — squared coefficient of variation of inter-arrival times. CV²>1 ⇒ bursty.
- Burstiness *fundamentally breaks* any **single static choice** of model.

### CDF intuition
- **Latency CDF** under static high-accuracy model on bursts: long right tail — many queries miss the SLO line ⇒ **low SLO attainment**.
- **Latency CDF** under static low-accuracy model: tight CDF (meets SLO) but **accuracy CDF** is poor.
- The "right" CDF dynamically tracks the load: tight at peaks, accurate at troughs.

---

## 6. Prior Inference Serving Systems (Generations)

> **Tags:** `prior systems` `inference serving generations` `gen1` `gen2` `clipper` `inferline`
> `clockwork` `infaas` `swayam` `gemel` `alpaserve` `cold start` `model swap`
> `cpu gpu swap` `coarse grained scheduling`

### Generation 1 — Static, single model
- **Examples:** Clipper, InferLine, Clockwork.
- **Approach:** Choose **one static point** in (R1, R2, R3) space; serve a single model.
- **Failure mode:** Sub-optimal under bursty workloads — picks either *high-acc/low-tput* (SLO violations on peaks, fails R1) or *low-acc/high-tput* (fails R2 by leaving accuracy on the table during troughs).

### Generation 2 — Auto model selection (InFaaS)
- **Approach:** Auto-pick from a *zoo of models* based on load.
- **Two failure modes** when navigating R1 vs R3:
  1. **Keep all models in GPU memory** → solves R1 (instant switch) but fails R3 (memory blown).
  2. **Swap from CPU → GPU** on demand → solves R3 but fails R1 (**cold-start latency** dwarfs inference latency, see *Swayam*).
- **Coarse-grained scheduling policy** that *minimizes switching* — not optimal for R1+R2 on bursty traffic.

### Comparison

| System / Gen | Choice granularity | R1 (SLO) | R2 (Acc) | R3 (Mem) | Burst-friendly? |
|---|---|---|---|---|---|
| **Gen1 (Clipper, etc.)** | Static (1 model) | ❌ on peaks | ❌ on troughs | ✅ | ❌ |
| **Gen2 (InFaaS) — all in GPU** | Coarse swap | ✅ | ~ | ❌ | partial |
| **Gen2 (InFaaS) — CPU↔GPU** | Coarse swap | ❌ (cold start) | ~ | ✅ | ❌ |
| **SuperServe (Gen3)** | Fine-grained, instant | ✅ | ✅ | ✅ | ✅ |

### Pareto framing
- Gen1 is **dominated** for any non-trivial burstiness — picks one corner of the Pareto box.
- Gen2 is on the Pareto frontier *if you accept coarse-grained switching*, but the cold-start tax pushes it off the *useful* part of the frontier.
- **SuperServe pushes the frontier outward** by making switching ~free.

---

## 7. SuperServe — Proposed Inference Serving System

> **Tags:** `superserve` `super serve` `nsdi 25` `subnetact` `slackfit` `proposed system`
> `near-instantaneous switching` `fine-grained reactive` `c++ implementation`

Two components:
1. **SubNetAct** — *enables* near-instantaneous model switching with **low memory overhead**.
2. **SlackFit** — *uses* fine-grained switching as a new policy design space; reactive scheduler that maximizes R1 + R2.

- Implementation: ~17.5k LOC C++; reactive system, minimal overhead.

---

## 8. SubNetAct — Near-Instantaneous Model Switching

> **Tags:** `subnetact` `sub net act` `subnetwork activation` `subnetwork in-place activation`
> `weight sharing` `supernetwork` `supernet` `shared layers` `non-shared layers`
> `superfed` `compofa` `des` `nas` `neural architecture search` `weight reuse`

### Idea
- Train a single **supernetwork** (via SuperFed / CompOFA / DES — all Tumanov group NAS work) whose **subnets share layers**.
- At serve-time, *activate* a particular subnet **in-place** within the supernet (just gate which layers participate).
- **No model reload, no weight copy** — switching = flipping an activation mask.

### Prior usage vs SubNetAct

| | Prior (Subnet zoo) | SubNetAct |
|---|---|---|
| Storage | One full subnet **per** latency target deployed independently | One supernet — subnets share weights via **shared layers + a few non-shared layers** |
| GPU memory (example) | ResNets: 397 MB; Subnet-zoo: 531 MB | **200 MB** for S1–S500 |
| Switching time | **~10–55 ms** (linear in #params, ≈ model loading) | **<1 ms** (subnet activation flat in #params) |
| Flexibility | Fixed N targets | Hundreds of subnets across the Pareto frontier |

### Why it works (key-idea alignment)
- **Sharing** — weights shared across subnets eliminate memory blow-up (R3).
- **Multiplexing** — one supernet multiplexes ≫1 "models" on the same GPU.
- **Performance** — switch latency goes from 10s of ms (model loading) to <1 ms (flag flip).

### Granularity tradeoffs (SubNetAct)
| Granularity | Pros | Cons |
|---|---|---|
| **Per-request switch** (ultra-fine) | Optimal accuracy/latency match per query | Decision overhead may exceed inference time |
| **Per-batch switch** (fine — what SuperServe does) | Adapts to load on each batch decision | Slight queueing-aware lag |
| **Per-time-window** (coarse, InFaaS) | Few switches | Lags bursts; can't track sub-second peaks |
| **Static** (Gen1) | Zero switch cost | Cannot handle bursts at all |

Sweet spot: **per-batch** — small enough to track bursts, large enough that per-decision overhead amortizes.

### Performance / CDF
- Switch-latency CDF for **model loading**: roughly linear with #params (10 → 50+ ms over realistic range).
- Switch-latency CDF for **subnetwork activation**: a near-vertical line near 0 ms, **independent of #params**.

### Key-idea alignment
- **Sharing**: yes — weight sharing.
- **Multiplexing**: yes — N subnets time-multiplexed on 1 GPU.
- **Performance**: 1000× faster switching.
- **Isolation**: per-query subnet choice, but they all live in the same supernet (no isolation between subnets — that's the *trick*).

---

## 9. SlackFit — Fine-Grained Reactive Scheduling

> **Tags:** `slackfit` `slack fit` `fine-grained scheduling` `reactive scheduling` `online policy`
> `slack` `edf` `earliest deadline first` `slack-based decision making` `pareto-optimal subnets`
> `batch size` `subnet selection` `phi` `B` `ilp` `np-hard` `placement constraints`
> `timing constraints` `central scheduler` `online scheduler`

### Goal
Central **online** scheduling policy that, for each batch, picks:
- **Subnet** φ (which model variant to use).
- **Batch size** B (how many queued queries to bundle).

…to maximize R1 (SLO attainment) and R2 (accuracy) jointly.

### Optimal formulation — ILP
- Maximize: `Σ_t Σ_n Σ_{φ∈Φ} Σ_{B∈𝔹} Acc(φ) · |B| · I(B,t,n,φ)`
- Subject to **placement** + **timing** constraints (each query served once; per-worker slot limits; deadlines respected).
- **NP-hard** *even with oracular knowledge* of the future trace ⇒ must use a heuristic.

### SlackFit heuristic (two principles)
1. **Operate on Pareto-Optimal Subnets only** — pre-compute the (latency, accuracy) Pareto frontier from a profiler; ignore dominated subnets.
2. **Slack-Based Decision Making** with an **EDF queue**:
   - **Slack** = time remaining for the *most urgent* query in the queue (deadline − now).
   - **More slack** (low queueing delay) ⇒ pick **higher-accuracy subnet, lower batch size**.
   - **Less slack** (high queueing delay) ⇒ pick **lower-accuracy subnet, higher batch size**.

### Slack ⇄ decision policy table

| Queue state | Slack | Subnet choice | Batch size | Why |
|---|---|---|---|---|
| Light load / trough | High | High-accuracy (Pareto top-right) | Small | Plenty of time → spend it on accuracy |
| Heavy load / peak burst | Low | Low-accuracy (Pareto bottom-left) | Large | Must drain queue → trade accuracy for throughput |

### Granularity tradeoffs (SlackFit)
| Granularity | Pros | Cons |
|---|---|---|
| **Per-query scheduling** | Best R1/R2 navigation | Sched overhead |
| **Per-batch scheduling** *(SuperServe)* | Cheap; reacts each batch (~ms) | Slight intra-batch staleness |
| **Per-window scheduling** (InFaaS) | Almost free | Misses sub-window bursts |

### Pareto framing
- SlackFit deliberately confines its decision space to the **Pareto-optimal subnets**.
- Choosing a dominated subnet is *never* optimal under any slack — equally bad accuracy *or* equally bad latency vs the frontier point.

### Key-idea alignment
- **Performance** — reactive, per-batch, EDF-driven.
- **Multiplexing** — N apps share queue + GPU.
- **Sharing** — supernet weights (via SubNetAct).
- **Isolation** — per-query deadline → per-query slack budget.

### SLO analysis — homogeneous vs heterogeneous

| Setting | SLO type | Implication for SlackFit |
|---|---|---|
| **Homogeneous SLO** (one app, e.g., 36 ms) | All queries same deadline | Slack is uniform — schedule looks like classic load-aware batching |
| **Heterogeneous SLO** (many apps) | Different deadlines | EDF + per-query slack is *necessary*; tighter-deadline queries dominate the front of the queue and force lower-accuracy/larger-batch decisions |

Heterogeneous SLOs **strictly imply** finer-grained scheduling — you cannot make one global decision that respects every deadline simultaneously.

---

## 10. SuperServe System Architecture

> **Tags:** `superserve architecture` `router` `edf queue` `scheduler` `dispatcher` `worker`
> `supernetwork profiler` `latency profile` `accuracy profile` `result queue`
> `prediction` `subnetwork activation worker` `ms latency` `36ms slo`

### Components
| Component | Role |
|---|---|
| **Router** | Receives requests with SLO, places into **EDF queue** sorted by absolute deadline `D = arrival + SLO` |
| **Scheduler (SlackFit)** | On each batch, computes slack θᵢ = Dᵢ − now; uses latency profile + Pareto-optimal subnets to pick (B, φ) |
| **Dispatcher** | Sends `(B, φ)` decision to a Worker |
| **Worker (SubNetAct)** | Activates subnet φ on GPU in <1 ms, runs inference for batch B |
| **Supernetwork Profiler** | Pre-computes (batch_size × subnet) → (latency, accuracy) heat-map; feeds into Scheduler |
| **Result Queue** | Returns predictions to user |

### Data flow (numbered as in slide 70)
1. Request arrives (SLO 36 ms) → Router → EDF queue.
2. Scheduler reads slack + profile.
3. Decides (B, φ); Dispatcher routes.
4. Worker activates subnet (in-place).
5. Predictions computed.
6. Returned via Result Queue.
7. User receives reply.

### Latency / Accuracy heat-map (profiler)
- Axes: **batch size** (1–32) × **subnet** (S1–S6 by accuracy 73.82% → 80.16%).
- Cells: inference latency in ms (4.4 ms cheapest, 62 ms most expensive).
- The Scheduler picks any cell whose latency ≤ slack ∧ accuracy = max feasible.

---

## 11. Experimental Results

> **Tags:** `experiments` `results` `evaluation` `slo attainment` `accuracy` `bursty traffic`
> `cv squared` `lambda` `mean serving accuracy` `clipper plus` `infaas baseline`
> `5 nines` `99.999 percent` `2.85x` `4.67 percent` `maf trace`

### Key results
- **SuperServe System Dynamics on MAF trace:**
  - Throughput tracks bursts (6–8k q/s).
  - Accuracy stays ~79% on average, dipping to ~77% only during peaks.
  - Batch size dynamically rises (14 → 16) on bursts.
  - Takeaways: *fine granularity*, *automatic & transparent trade-off navigation*, *opportunistic accuracy maximization*.

- **Bursty traffic sweep (λ ∈ {2950, 4900, 5550} QPS × CV²ₐ ∈ {2, 4, 8}):**
  - SuperServe **dominates** all Clipper⁺ static-accuracy points and InFaaS.
  - Wins shrink and grow predictably with λ and CV²ₐ.

- **Real-world MAF trace:**
  - **99.999% SLO attainment (five 9's)**.
  - Up to **+4.67% accuracy** at iso-SLO, or **2.85× SLO attainment** at iso-accuracy vs baselines.

### Pareto interpretation
- Each Clipper⁺ point sits at one (accuracy, SLO-attainment) corner.
- InFaaS sits low on accuracy.
- SuperServe sits **above and to the right** of the entire baseline frontier ⇒ Pareto-dominant in (R1, R2) at fixed R3.

---

## 12. SAIL Stack — The Bigger Picture

> **Tags:** `sail` `systems for ai lab` `efficient ai stack solution` `holmes` `dsched`
> `compofa` `unfoldml` `superfed` `des` `sushi` `mlsys 23` `iclr 21` `kdd 20`
> `eccv 24` `neurips 22` `nsdi 25`

```
┌────────────────────────────────────────────────────────┐
│ AI Software   │ Holmes (KDD'20), SuperServe (NSDI'25), │
│ App × Models  │ DSched                                  │
├────────────────────────────────────────────────────────┤
│ AI Algorithms │ CompOFA (ICLR'21), UnfoldML (NeurIPS'22)│
│ Models × HW   │ SuperFed (ECCV'24), DES (ECCV'24)       │
├────────────────────────────────────────────────────────┤
│ AI Hardware   │ Sushi (MLSys'23)                        │
└────────────────────────────────────────────────────────┘
```

- The talk's *production* layer = NAS systems (CompOFA / SuperFed / DES) that train the supernetwork.
- The talk's *consumption* layer = SuperServe (this lecture).
- Together: **Produce hardware-aware DNNs** (NAS) → **Consume them efficiently** (serving).

---

## 13. Key-Idea Alignment Summary

| Key idea | Where it shows up in this lecture |
|---|---|
| **Isolation** | Per-query deadline isolation; bursts must not violate trough queries' SLOs |
| **Multiplexing** | One supernet ⇒ N subnets time-multiplexed on 1 GPU |
| **Protection** | (Out of scope — no adversaries) |
| **Performance** | Whole point: latency-SLO + throughput + accuracy under bursts |
| **Sharing** | Weight sharing across subnets; HW shared across apps |

---

## 14. Granularity Spectrum (Summary)

> **Tags:** `granularity` `granularity spectrum` `coarse vs fine` `scheduling granularity`
> `model switching granularity`

```
             coarse ⇐⇒ fine
   Static ── Window ── Per-batch ── Per-query
   (Gen1)   (InFaaS)   (SlackFit)   (theoretical)
```

| Granularity | R1 (SLO) | R2 (Acc) | R3 (Mem) | Switch overhead | Bursty fit |
|---|---|---|---|---|---|
| Static | Bad on peaks | Bad on troughs | Best (1 model) | 0 | ❌ |
| Window (coarse) | OK | OK | OK | Cold start ms | partial |
| Per-batch (SuperServe) | **Best** | **Best** | OK | <1 ms (SubNetAct) | ✅ |
| Per-query | (theoretically best) | (theoretically best) | Same | sched cost may exceed inference | impractical |

**Sweet spot** = per-batch, *only because* SubNetAct made switch cost ~free. Pre-SubNetAct, per-batch was *infeasible* — that's the systems contribution.

---

## 15. SLO Analysis — Homogeneous vs Heterogeneous

> **Tags:** `slo analysis` `slo` `homogeneous slo` `heterogeneous slo` `multi-tenant`
> `multi-app inference` `deadline` `edf scheduling`

| | Homogeneous SLO | Heterogeneous SLO |
|---|---|---|
| Definition | All queries share one deadline (e.g., 36 ms) | Different apps have different deadlines (5 ms voice, 200 ms image) |
| Slack distribution | Tight; all queries equally urgent | Skewed; tightest deadlines dominate |
| Scheduler implication | Batched FIFO sufficient | **EDF strictly required**; static batching breaks fairness |
| What it implies | Single-tenant case ⇒ Gen1 *can* work if static = right choice | Multi-tenant ⇒ Gen1 fundamentally inadequate; SlackFit needed |

Real production = **heterogeneous** (multi-tenant FaaS, MAF) ⇒ Gen1 is dead on arrival.

---

## 16. Performance / CDF Cheatsheet

> **Tags:** `cdf` `performance analysis` `latency cdf` `tail latency` `slo attainment cdf`

| Quantity | What its CDF looks like |
|---|---|
| **Inference latency, static high-acc model on bursts** | Wide right tail past SLO line — many violations |
| **Inference latency, static low-acc model on bursts** | Tight CDF (SLO met) but accuracy CDF poor |
| **Inference latency, SuperServe** | Tight CDF *and* high mean accuracy — Pareto win |
| **Switch latency, model loading** | ~10–55 ms, linear in #params |
| **Switch latency, SubNetAct activation** | <1 ms, flat in #params (essentially Dirac at 0) |
| **Per-batch slack distribution** | Bimodal — one mode at trough (high slack), one at peak (low slack); SlackFit branches accordingly |

---

## 17. Comparison Table (Master)

| System | Switch granularity | Switch cost | Multi-model in GPU | SLO under burst | Accuracy under burst | Pareto-optimal? |
|---|---|---|---|---|---|---|
| **Clipper / Gen1 static** | None | 0 | No (1 model) | Bad on peaks | Bad on troughs | ❌ dominated |
| **InFaaS — all-resident** | Coarse window | ~0 (resident) | Yes (mem cost) | OK | OK | partial (fails R3) |
| **InFaaS — CPU↔GPU swap** | Coarse window | **Cold start** ≫ inference | No | ❌ on swap | OK | ❌ dominated |
| **SuperServe** | **Per-batch fine** | **<1 ms (SubNetAct)** | Yes (1 supernet) | ✅ (5 nines) | ✅ (+4.67%) | ✅ |

---


---

# Part 2 — xv6 Implementation


## L03 — x86 Architecture — xv6

*([→ back to concept](<#L03 — x86 Architecture>))*

## 12. xv6 Implementation
> **Tags:** `xv6` `bootasm.S` `bootmain` `entry.S` `seginit` `kvmalloc` `kinit1` `trap.c` `trapasm.S` `vectors.S` `usys.S` `IDT initialization` `page directory` `KERNBASE` `TSS` `flat GDT` `xv6 memory map`

### Boot: `bootasm.S`
- Entry at `0x7C00`; CPU in 16-bit real mode
- Sets up **bootstrap GDT** (3 entries: null, code `base=0 limit=0xFFFFFFFF STA_X|STA_R`, data `base=0 limit=0xFFFFFFFF STA_W`)
- `lgdt [gdtdesc]` — loads GDT register
- Sets `CR0 |= 1` (PE bit) → protected mode
- Far jump `ljmp $(SEG_KCODE<<3), $start32` — flushes pipeline, sets CS
- Reloads all segment registers with data selector
- Sets `ESP = start` (stack pointer), calls `bootmain()`

### Boot: `bootmain()` (C)
- Reads kernel ELF from disk sector 1+ using BIOS I/O
- Parses ELF program headers, loads each segment to physical address
- Jumps to kernel entry point (`entry` symbol in ELF header)

### Kernel Entry: `entry.S`
- Sets up **bootstrap page directory** `entrypgdir`:
  - `PDE[0]`: VA `0x00000000–0x003FFFFF` → PA `0x00000000` (identity, large page)
  - `PDE[512]`: VA `0x80000000–0x803FFFFF` → PA `0x00000000` (kernel high-VA mapping)
- Writes `entrypgdir` physical address to CR3
- Sets `CR0.PG` → paging enabled
- Immediately executes from high VA (KERNBASE = `0x80000000`)
- Calls `main()`

### GDT: `seginit()` in `vm.c`
- Sets up **per-CPU GDT** with 4 segments (all flat: base=0, limit=0xFFFFFFFF):
  - `SEG_KCODE` (index 1): execute+read, DPL_KERN
  - `SEG_KDATA` (index 2): write, DPL_KERN
  - `SEG_UCODE` (index 3): execute+read, DPL_USER
  - `SEG_UDATA` (index 4): write, DPL_USER
- Also sets up TSS entry in GDT for kernel stack on trap entry
- Logical = Linear = Virtual in xv6 (flat segmentation)

### IDT: `trap.c` + `vectors.S`
- `vectors.S` generated at build time: 256 stub functions (one per vector) that push vector number and jump to `alltraps`
- `tvinit()` in `trap.c`: initializes IDT using `SETGATE` macro for each vector
  - Syscall vector `0x40` uses **trap gate** (istrap=1, leaves IF set)
  - All others use **interrupt gate** (istrap=0, clears IF)
- `idtinit()`: loads IDT into IDTR via `lidt`

### Syscalls: `usys.S`
- Each syscall: pushes syscall number into `EAX`, executes `INT 0x40`
- `alltraps` in `trapasm.S`: saves all registers → builds trapframe → calls `trap()`
- `trap()` dispatches: syscall → `syscall()`, hardware interrupt → device handler, exception → kill process or panic

### Virtual Memory: `vm.c`
- `kinit1()`: initializes physical page allocator for first 4MB
- `kvmalloc()`: creates full kernel page table mapping all physical memory above KERNBASE
- `KERNBASE = 0x80000000` — kernel and user share one page table; kernel half mapped in every process
- `switchuvm()`: loads process page table into CR3 (context switch) + loads TSS with kernel stack pointer

### xv6 Memory Map Summary
| Virtual Address | Contents | Permissions |
|---|---|---|
| `0x0–PAGESIZE` | Unmapped (null dereference trap) | — |
| `PAGESIZE–KERNBASE` | User: text, data, heap, stack | RWU |
| `KERNBASE + 0x100000` | Kernel text | R (no write, no user) |
| Above kernel text | Kernel data, free pages | RW (no user) |
| `0xFE000000–0xFFFFFFFF` (VA) | Device memory | RW (no user) |

---

## L04 — Isolation — xv6

*([→ back to concept](<#L04 — Isolation>))*

## 20. xv6 Implementation

> **Tags:** `xv6` `xv6 isolation` `GDT` `bootstrap GDT` `per-CPU GDT` `paging xv6` `scheduler xv6` `traps.h` `syscall macro` `usys.S` `trap.c` `switchuvm` `swtch`

> **Note:** This section covers how xv6 specifically implements the concepts above. Keep it disjoint from the conceptual sections.

### CPL in xv6 — Bootstrap GDT (`bootasm.S`)
```asm
# Bootstrap GDT (used before per-CPU GDT is set up)
gdt:
    SEG_NULLASM                             # null seg
    SEG_ASM(STA_X|STA_R, 0x0, 0xffffffff)  # code seg (flat)
    SEG_ASM(STA_W, 0x0, 0xffffffff)        # data seg (flat)
```

### Per-CPU GDT Initialization (`main.c` / `proc.c`)
```c
c = &cpus[cpunum()];
c->gdt[SEG_KCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, 0);       // CPL=0, kernel code
c->gdt[SEG_KDATA] = SEG(STA_W,       0, 0xffffffff, 0);       // CPL=0, kernel data
c->gdt[SEG_UCODE] = SEG(STA_X|STA_R, 0, 0xffffffff, DPL_USER); // CPL=3, user code
c->gdt[SEG_UDATA] = SEG(STA_W,       0, 0xffffffff, DPL_USER); // CPL=3, user data
c->gdt[SEG_KCPU]  = SEG(STA_W, &c->cpu, 8, 0);                // per-CPU private data
lgdt(c->gdt, sizeof(c->gdt));
loadgs(SEG_KCPU << 3);
```
- xv6 uses a **flat memory model** (segments span all of memory, isolation done by paging)
- `SEG_KCODE/KDATA`: DPL=0 → only ring 0 can use
- `SEG_UCODE/UDATA`: DPL=3 → ring 3 accessible

### Boot Sequence and Isolation Setup
1. **`bootasm.S`**: Disables interrupts; configures minimal GDT; exits real mode → 32-bit protected mode
2. **`bootmain.c`**: Loads kernel ELF into physical `0x00100000`; jumps to `entry`
3. **`entry.S`**: Enables paging; sets up bootstrap page directory (entry 0: identity map; entry 512: `KERNBASE`→phys 0)
4. **`main.c`**: Sets up full page tables; isolates kernel virtual space (`0x80000000+`) from user space; spawns first process `init`

### VM Paging Isolation in xv6
- **Two layers of isolation**:
  1. **Paging**: each process has its own page directory (CR3 points to it)
  2. **PDE/PTE U/S bits**: kernel pages marked Supervisor (U/S=0), user pages marked User (U/S=1)
- Switching address spaces = writing new CR3 in `switchuvm(p)`:
```c
lcr3(v2p(p->pgdir));  // load process's page directory physical address into CR3
```

### Per-CPU Preemptive Scheduler (`proc.c`)

> See [L11 — Schedulers — xv6 §13](<#L11 — Schedulers — xv6>) for the full per-CPU `scheduler()` loop. Key isolation point: `switchuvm(p)` writes `p->pgdir` into CR3 (user VM); `switchkvm()` swaps back to the kernel-only page table — this is where address-space isolation between processes is *enforced* every quantum.

### System Call Flow in xv6

```
User program (e.g., sh)
    → usys.S: SYSCALL(fork) → movl $SYS_fork, %eax; int $T_SYSCALL
    → vector.S: Trap Vector entry
    → trap.c: Trap Handler (saves user context, loads kernel context)
    → syscall.c: System Call Table dispatch
    → sysproc.c / sysfile.c: sys_fork(), sys_read(), etc.
    → return: restore user context, iret
```

### Syscall Macro (`usys.S`)
```asm
#define SYSCALL(name) \
.globl name; \
name: \
    movl $SYS_## name, %eax; \
    int $T_SYSCALL; \
    ret

SYSCALL(fork)
SYSCALL(exit)
SYSCALL(read)
// ... etc.
```
- `T_SYSCALL = 64` (defined in `traps.h`)
- Syscall number goes in `%EAX`

### Trap Numbers (`traps.h`)
```c
#define T_DIVIDE    0   // divide error
#define T_DEBUG     1   // debug exception
#define T_NMI       2   // non-maskable interrupt
#define T_BRKPT     3   // breakpoint
#define T_OFLOW     4   // overflow
#define T_BOUND     5   // bounds check
#define T_ILLOP     6   // illegal opcode
#define T_DEVICE    7   // device not available
#define T_DBLFLT    8   // double fault
#define T_SYSCALL   64  // system call
#define T_DEFAULT   500 // catchall
```

### xv6 Kernel Thread Model
- **One-to-One**: each user process has its own kernel stack and context
- Concurrent syscalls possible across CPUs
- Each CPU runs its own scheduler loop (`for(;;)` above)
- Lock (`ptable.lock`) protects the process table from concurrent modification

### xv6 Memory Map (Isolation Boundary)
```
0xFFFFFFFF ─────────────────────────────
           Device memory-mapped I/O
0xFE000000
           ...
0x80000000 ─── KERNBASE ── kernel lives here (virtual)
           User heap grows up ↑
           User stack grows down ↓
0x00000000 ─────────────────────────────
```
- Kernel virtual space: `≥ KERNBASE (0x80000000)` — U/S=0 on PTEs → user cannot access
- Physical kernel: loaded at `0x00100000`; mapped to `0x80100000` via paging

---

## L05 — Kernel Organization & APIs — xv6

*([→ back to concept](<#L05 — Kernel Organization & APIs>))*

## 21. xv6 Implementation

> **Tags:** `xv6` `xv6 kernel org` `syscall.c` `sysfile.c` `sysproc.c` `usys.S` `syscall number`
> `xv6 syscall flow` `xv6 threading` `xv6 one to one` `kernel stack per process xv6`
> `add syscall xv6` `vector.S` `entryother.S` `trap.c`

> **Note:** This section covers how xv6 specifically implements the design choices above. Keep disjoint from conceptual sections.

### xv6 Is a Monolithic Kernel

- **Architecture**: Monolithic — fs, scheduler, memory manager, process manager all in ring 0
- **Syscall count**: 21 (see table in §4)
- **No glibc**: xv6 syscalls are called directly (no wrapping library)

### File Organization of Syscall Implementation

| File | Purpose |
|------|---------|
| `usys.S` | User-space stub: generates `INT 0x40` (T_SYSCALL=64) for each syscall |
| `vector.S` | Trap vector table: entry points for all 256 IDT entries |
| `entryother.S` + `trap.c` | Trap handler: saves context, dispatches |
| `syscall.h` | Syscall number definitions (`#define SYS_fork 1`, etc.) |
| `syscall.c` | Syscall dispatch table: `syscalls[]` array mapping number → function |
| `sysfile.c` | Implementations of file-related syscalls (`sys_read`, `sys_write`, `sys_open`, etc.) |
| `sysproc.c` | Implementations of process-related syscalls (`sys_fork`, `sys_exit`, `sys_exec`, etc.) |

### xv6 Syscall Flow (from user to handler)

```
User program (e.g., sh)
    → usys.S: SYSCALL(read) macro
        movl $SYS_read, %eax   // syscall number in eax
        int  $T_SYSCALL        // INT 0x40 → ring 0 transition
    → vector.S: IDT entry for 0x40 → trap vector
    → trap.c: alltraps → trap()
        if(tf->trapno == T_SYSCALL)
            proc->tf = tf;
            syscall();
    → syscall.c: syscall()
        num = proc->tf->eax;
        syscalls[num]();       // dispatch to sys_read
    → sysfile.c: sys_read()
        ...
    → iret: restore user context, return to user space
```

### How to Add a Syscall to xv6

1. Write `sys_mycall(void)` in `sysproc.c` or `sysfile.c`
2. Add `extern int sys_mycall(void);` in `syscall.c`
3. Add `[SYS_mycall] sys_mycall,` to the `syscalls[]` array in `syscall.c`
4. Add `#define SYS_mycall <next_number>` in `syscall.h`
5. Add `SYSCALL(mycall)` in `usys.S` to generate the user-space stub
6. Add prototype in `user.h` so user programs can call it

### xv6 Threading Model: One-to-One

- Each process has its **own kernel stack** (allocated in `proc.c` during `allocproc()`)
- When process traps, it uses its own stack — no contention with other processes
- Multiple CPUs each run their own scheduler loop → multiple processes can be in syscalls concurrently on different CPUs
- `ptable.lock` protects the process table from concurrent modification

```c
// proc.c: allocproc() — gives each new process its own kernel stack
p->kstack = kalloc();         // allocate 1 page for kernel stack
sp = p->kstack + KSTACKSIZE; // stack pointer starts at top
```

### xv6 echo Hello | cat — What Actually Happens

```
sh (user space):
  1. fork() + exec("echo") → creates echo process
  2. pipe(p) → creates a pipe (two FDs: p[0]=read end, p[1]=write end)
  3. fork() + exec("cat") → creates cat process
  4. sh wires: echo's stdout → p[1]; cat's stdin → p[0]
  5. close() on unused ends

echo (user space):
  write(p[1], "Hello\n", 6)  → sys_write → kernel pipe buffer

cat (user space):
  read(p[0], buf, n)         → sys_read → kernel pipe buffer → returns "Hello\n"
  write(1, buf, n)           → sys_write → stdout → console
```

- The kernel's **pipe** implementation (in `pipe.c`) manages the in-kernel buffer connecting write end to read end
- No data ever goes to disk; the file descriptor abstraction unifies files and pipes

### xv6 Syscall in sysfile.c (example: sys_read)

```c
int sys_read(void) {
    struct file *f;
    int n;
    char *p;
    if(argfd(0, 0, &f) < 0 ||  // arg 0: fd → file struct
       argint(2, &n) < 0 ||    // arg 2: n bytes
       argptr(1, &p, n) < 0)   // arg 1: buf pointer (VALIDATED to be in user space)
        return -1;
    return fileread(f, p, n);
}
```

- **`argptr`** validates that the user-supplied pointer is within user address space
- This is the **argument sanitization** that prevents users from reading/writing kernel memory

---

## L06 — Virtual Memory I (Basics) — xv6

*([→ back to concept](<#L06 — Virtual Memory I (Basics)>))*

## 10. xv6 — Detailed Implementation

> **Tags:** `xv6 vm` `xv6 paging` `xv6 entrypgdir` `kvmalloc` `setupkvm` `mappages` `walkpgdir`
> `kalloc kfree` `kmem freelist` `kinit1 kinit2` `kmap` `KERNLINK` `PHYSTOP` `DEVSPACE`

### Boot flow (recap)
```
bootasm.S  →  bootmain  →  entry (entrypgdir, enable paging)  →  main()
                                                                  ├── kinit1()      // tiny phys allocator
                                                                  ├── kvmalloc()    // build full kernel PT
                                                                  ├── ... drivers ...
                                                                  └── kinit2()      // grow allocator
```

### Physical page allocator (`kalloc.c`)
- xv6 stores **free-page metadata inside the free pages themselves** (no separate page-info table → **no page sharing**).
- Free list is a singly-linked stack:
```c
void kfree(char *v) {
  ...
  memset(v, 1, PGSIZE);       // poison to catch dangling refs
  r = (struct run*)v;
  r->next = kmem.freelist;
  kmem.freelist = r;
}
```
- `kalloc()` pops the head, returns its VA.
- **Two-phase init:**
  - `kinit1(vstart, vend)` — runs before MP, before lock needed; uses just the 4MB mapped by entrypgdir.
  - `kinit2(...)` — runs after `kvmalloc`; freelist now holds *all* physical pages.

### Kernel page table (`vm.c`)
- `kmap[]` describes the kernel's permanent mappings (present in *every* process's page table):

| virt | phys range | perm | purpose |
|---|---|---|---|
| `KERNBASE` | `[0, EXTMEM)` | W | I/O space |
| `KERNLINK` | `[V2P(KERNLINK), V2P(data))` | RO | kernel text + rodata |
| `data` | `[V2P(data), PHYSTOP)` | W | kernel data + free RAM |
| `DEVSPACE` | `[DEVSPACE, 0)` | W | memory-mapped devices |

- `setupkvm()` — `kalloc` a fresh PD, then `mappages` each `kmap[]` entry. Returns the new PD.
- `kvmalloc()` — calls `setupkvm`, loads CR3 with the result.

### Core helpers
- **`mappages(pgdir, va, size, pa, perm)`** — for each page in `[va, va+size)`: walk-and-create PTE, set `*pte = pa | perm | PTE_P`. Panics on remap.
- **`walkpgdir(pgdir, va, alloc)`** — returns pointer to the PTE for `va`. If the PT doesn't exist and `alloc=1`, `kalloc` a new PT, `memset` to zero, install in PD with `PTE_P|PTE_W|PTE_U`. PD-level perms are intentionally permissive — actual restrictions are encoded in the **PTE**.

### Address-space layout (post-boot)
```
 0xFFFFFFFF ┌────────────────┐
            │   free memory  │
            ├────────────────┤  ← end of kernel
            │ kernel text/data│   (CPL=0, kernel-only)
 0x80100000 ├────────────────┤
            │      BIOS      │
 0x80000000 ├────────────────┤  ← KERNBASE
            │      heap      │
            ├────────────────┤
            │     stack      │   (CPL=3, user)
            ├────────────────┤
            │ user text/data │
 0x00000000 └────────────────┘
```
- Above `KERNBASE` = kernel half (DPL_KERN), present in every PD identically.
- Below `KERNBASE` = per-process user half (DPL_USER), differs per address space.
- This layout means that on a syscall the kernel can read user pointers via the *same* page table (no CR3 switch).

### xv6 VM limitations and design implications
| Limitation | Consequence |
|---|---|
| No many-VA → 1-PA mapping | **Copy-on-Write impossible** out of the box (Lab 2 fixes this) |
| No shared mappings | No shared libs, no `mmap` shared regions |
| Phys page state is binary (free / used) | No reference counting → fork must duplicate, not share |
| Kernel maps *all* physical RAM (≤ 2 GB) | `P2V`/`V2P` are simple `+/− KERNBASE` macros → fast but caps RAM |

### "Other OSes" contrast
- Linux/BSD: phys pages are reference-counted (`struct page`); enables CoW, `mmap`, shared libs, page cache.
- Tradeoff: page-info structures consume memory proportional to RAM (e.g. ~1.6% overhead in Linux).

---

## 11. Performance Analysis Hooks

> **Tags:** `vm performance` `tlb hit cdf` `page walk latency` `address space switch cost`

### CDF: time per memory access (with VM enabled)
```
P[t ≤ x]
  1 │            ─────────
      │       ╱           ← outliers: page fault → disk swap (ms!)
      │     ╱
      │   ╱   ← TLB miss + 2-or-4 level walk (~50–500 ns)
   .99│  ╱
      │ ┃  ← TLB hit (~1 cycle ≈ 0.3 ns)
   .9 │┃
      └─────────────────►  latency
        ns        ms
```
- **Knees** map to TLB hit / miss / page-fault tiers.
- More PT levels widen the middle plateau.
- Hugepages compress the middle plateau (fewer walks).

### SLOs (Service Level Objectives)
- **Latency-sensitive workload** (web server, DB lookup): target p99 memory access ≤ X ns → demands high TLB hit rate, often hugepages.
- **Throughput workload** (batch / analytics): can tolerate p99 page faults; cares about *average* memory cost.
- **Heterogeneous SLOs** across designs:
  - 4MB-page kernel: very low translation latency, but coarse protection → poor SLO for *isolation*.
  - 4KB 2-level: best protection SLO, worse latency SLO.
- Heterogeneity implies the same workload may want **different page sizes for different regions** (transparent hugepages).

---

## 12. Quick Reference — Names & Acronyms

> **Tags:** `vm acronyms` `va pa` `cr3 cr0 cr4` `mmu tlb`

| Acronym | Meaning |
|---|---|
| VA / LA | Virtual / Linear address |
| PA | Physical address |
| VPN / PPN | Virtual / Physical Page Number (top 20 bits in 32-bit) |
| PTE / PDE | Page Table Entry / Page Directory Entry |
| PT / PD | Page Table / Page Directory |
| PML4(E), PDPT(E) | 64-bit upper levels |
| MMU | Memory Management Unit (HW translator) |
| TLB | Translation Lookaside Buffer (cache) |
| CR0.PG | Bit that enables paging |
| CR0.WP | Write-Protect — even ring 0 must obey PTE_W |
| CR3 | PA of current PD/PML4 |
| CR4.PSE | Page Size Extensions (enables 4MB pages) |
| KERNBASE | xv6 split between user (low) and kernel (high) VAs (`0x80000000`) |
| PHYSTOP | xv6 max usable phys RAM |
| KERNLINK | VA where kernel was linked (`KERNBASE + EXTMEM`) |

---

## 13. Common Exam Gotchas

> **Tags:** `gotchas` `vm trick questions`

- **CR3 stores a *physical* address**, not virtual. (Common wrong answer: "virtual.")
- **A 2-level page walk = 2 memory operations** (PD lookup + PT lookup), *not* 3 — the final access is the *user's* memory access, not part of the walk.
- **Page Directory size = 4KB** because `1024 entries × 4 B = 4096 B` — and that's exactly **one frame**, no waste.
- **`PTE_PS` on a PDE** ⇒ this PDE is a leaf, the "PT level" is skipped, and the page is 4MB.
- **TLB is *not* coherent with PT writes.** Kernel must `invlpg` or reload CR3 after editing a PTE.
- **Switching processes flushes the TLB** (CR3 reload) → expensive cold start; PCIDs/ASIDs mitigate.
- **In xv6 the kernel half of VA is mapped in *every* PD** → kernel never has to switch CR3 on syscall entry.
- **`walkpgdir` sets `PTE_W|PTE_U` on the PDE** even for kernel mappings — fine because the *PTE* is what hardware ultimately checks (HW ANDs perms across levels: most-restrictive wins, but here PD is most-permissive and PT carries the real perms).
- **Segmentation in xv6 post-boot** is just used for ring switching; bases/limits are flat.

---

## L07 — Virtual Memory II (Lazy / CoW) — xv6

*([→ back to concept](<#L07 — Virtual Memory II (Lazy / CoW)>))*

## 14. xv6 — Detailed Implementation (How Lab 2 Wires This In)

> **Tags:** `xv6 cow lab` `lab2 cow` `xv6 lazy alloc` `xv6 page fault handler`
> `pgrefcnt` `T_PGFLT` `trap 14 xv6` `copyuvm cow` `kfree refcount`

### What's NOT in vanilla xv6
- No reference counts → cannot share frames safely → `fork()` calls **`copyuvm` (vm.c)** which kallocs+memmoves every page eagerly. This is the line you replace.
- Page faults from user mode → `trap.c` falls through to "kill the process" branch and prints `pid X bad: trap 14 err Y on cpu Z eip W addr V`. **The lab tells you to NOT print this** under CoW (autograder hates it).
- `kfree` blindly returns the frame to `kmem.freelist` regardless of whether someone else still references it.

### Lab 2 — typical implementation hooks
1. **Add `pgrefcnt[PHYSTOP/PGSIZE]` array** in `kalloc.c`. Initialize all entries via `kinit2`; protected by `kmem.lock`.
2. **`kalloc`**: set `pgrefcnt[pfn] = 1` on hand-out.
3. **`kfree`**: `if (--pgrefcnt[pfn] > 0) return;` — only actually free when last ref drops.
4. **Add a helper `incref(pa)`** for fork to bump shares.
5. **Replace `copyuvm`** with `cowuvm` (or modify in place):
   - For each present PTE in the parent: clear `PTE_W`, copy PTE bytes into the child's PT, `incref(PTE_ADDR(*pte))`, set a custom `PTE_COW` (one of the AVL bits 9–11).
   - Crucially: also clear `PTE_W` on the **parent's** PTE — both parties must trap on next write (otherwise parent's writes silently corrupt child).
   - `lcr3(V2P(myproc()->pgdir))` to flush stale TLB entries.
6. **`trap.c`** in the `case T_PGFLT:` handler:
   - Read `rcr2()` to get faulting VA, `tf->err` to confirm it was a write (`err & 2`).
   - Walk `myproc()->pgdir` to find the PTE; check `PTE_COW` and `!PTE_W`.
   - If `pgrefcnt == 1`: just set `PTE_W`, clear `PTE_COW`, `lcr3` (or `invlpg`).
   - Else: `kalloc` new frame, `memmove` from old, decref old, install new with `PTE_W|PTE_U|PTE_P`, flush TLB.
   - On any failure (including kalloc returning 0): kill the process **silently** (no print).
7. **Kernel-side writes** (the slide pitfall): `read`/`write`/`pipe`/etc. ultimately call kernel code that writes user pages. Two options:
   - Patch the call sites to manually invoke the CoW path before writing.
   - Or catch the kernel-mode write fault in `trap.c` and re-enter the same handler with `tf->cs == SEG_KCODE<<3`. Most labs prefer the latter — a single hook covers all syscalls.
8. **`exit`**: traverse PT and `kfree` (refcount-aware) every user page so that surviving siblings keep their refs.

### The `n != 2` insight
- Don't try to encode "parent-of" / "child-of" — just use the **per-frame refcount** and let it implicitly capture "however many processes happen to point here."
- `wait()` reaping a zombie still triggers `kfree` on the child's pages → refcount drops by however many of those pages were still uniquely held by the child.
- Reparenting to `init` is a no-op for the refcounts; the fork chain does not need explicit modeling.

### Common Lab-2 bugs (oral tradition)
- Forgetting `lcr3` after `cowuvm` → parent runs with stale RW TLB entries → ghost writes.
- Decrementing the refcount *before* the memcpy in the fault handler → if the memcpy itself page-faults (recursive!) the page may already have been freed.
- Treating `kalloc` as `malloc` (the slide nag): `struct X *p = (struct X*) kalloc()` is fine *only* if you actually wanted a 4KB page. For a small struct, just declare `struct X x;` on the stack.
- Forgetting that `walkpgdir(...,1)` *allocates* a PT page if missing — calling it in your fault handler when you didn't mean to changes process state.
- Stress test (slide list): "Fork hundreds or thousands of times, die, exec, read from/write to memory with wild abandon. Everything should still work." The bugs that hide in n=2 surface immediately under chained forks.

### "kalloc != malloc" — the rant slide
- `kalloc()` returns a **whole 4 KB page**, no smaller granularity.
- It does **not** zero or initialize anything (xv6 actually fills with `0x01` for poisoning).
- Use it for page-aligned, page-sized things (page tables, frames, kernel stacks). For everything else: stack-allocate or use a kernel allocator-of-objects.

### Files & functions you'll touch
| File | What changes |
|---|---|
| `kalloc.c` | Add `pgrefcnt`, modify `kalloc`/`kfree`, add `incref`/`decref` |
| `vm.c` | Replace/augment `copyuvm` → `cowuvm`; possibly tweak `mappages` |
| `trap.c` | New `case T_PGFLT:` arm that checks `PTE_COW` and either fast-path or copy |
| `mmu.h` | Reserve a `PTE_COW` bit in the AVL field (bits 9–11) |
| `proc.c` | `exit()` already calls `freevm` → already invokes ref-count-aware `kfree` |

---

## 15. One-line summary

> **CoW fork = lazy `copyuvm`. Demand paging = lazy `kalloc`. Single zero page = lazy `memset`. Memory-mapped files = lazy `read`. Swapping = lazy "stay-in-RAM." All of them are the same pattern: lie to the MMU about permissions/presence, trap on the access you care about, fix up state in the handler, retry. The whole game is choosing your trigger and your bookkeeping.**

---

## L08 — Virtual Memory III (CoW & Tricks) — xv6

*([→ back to concept](<#L08 — Virtual Memory III (CoW & Tricks)>))*

## 13. xv6 Implementation — Lab 2 CoW

> **Tags:** `xv6 cow` `lab2 cow` `xv6 lab 2` `cowfork` `cow_handler` `xv6 refcount`
> `kalloc cow` `kfree cow` `mappages cow` `walkpgdir cow` `T_PGFLT xv6` `trap.c xv6`

### Baseline xv6 fork (`proc.c:fork()`)
```c
int fork(void) {
  ...
  if((np->pgdir = copyuvm(curproc->pgdir, curproc->sz)) == 0) { ... }
  ...
}
```
- `copyuvm(pgdir, sz)` walks every PTE up to `sz`, **kalloc's a fresh frame**, **memmoves** the page contents, and `mappages` it into the new PD.
- Cost: O(sz) — duplicates **everything** even though most child processes immediately `exec`.

### What Lab 2 changes
1. **Add a per-physical-frame refcount table.**
   - xv6's `kmem` free-list stores nothing per-page-info; you must add a parallel array, e.g. `int kref[PHYSTOP/PGSIZE]` in `kalloc.c`.
   - Initialize to 0 on free, increment on each new mapping, decrement on `kfree`-equivalent path.
   - `kfree(pa)` only **really** frees the page when `kref` reaches 0; otherwise it just decrements.

2. **Replace `copyuvm` with `cowuvm`.**
   ```c
   pde_t* cowuvm(pde_t *pgdir, uint sz) {
     pde_t *d = setupkvm();
     for(uint i = 0; i < sz; i += PGSIZE) {
       pte_t *pte = walkpgdir(pgdir, (void*)i, 0);
       uint pa = PTE_ADDR(*pte);
       uint flags = PTE_FLAGS(*pte);
       // Strip PTE_W from BOTH parent and child.
       *pte &= ~PTE_W;
       *pte |= PTE_COW;            // PTE_COW = a free AVL bit (e.g., 1<<9)
       flags = (flags & ~PTE_W) | PTE_COW;
       mappages(d, (void*)i, PGSIZE, pa, flags);
       incref(pa);                  // bump refcount instead of memmove
     }
     lcr3(V2P(pgdir));               // flush parent's TLB
     return d;
   }
   ```

3. **Handle `T_PGFLT` in `trap.c`.**
   ```c
   case T_PGFLT: {
     uint va = rcr2();
     pte_t *pte = walkpgdir(myproc()->pgdir, (void*)va, 0);
     if(!pte || !(*pte & PTE_P) || !(*pte & PTE_COW)) {
       // genuine fault → kill process
       myproc()->killed = 1; break;
     }
     uint pa = PTE_ADDR(*pte);
     if(getref(pa) == 1) {
       // last owner → just promote in-place
       *pte = (*pte | PTE_W) & ~PTE_COW;
     } else {
       // share-break: kalloc + memmove
       char *mem = kalloc();
       if(!mem) { myproc()->killed = 1; break; }
       memmove(mem, (char*)P2V(pa), PGSIZE);
       *pte = V2P(mem) | PTE_W | PTE_U | PTE_P;
       decref(pa);
     }
     lcr3(V2P(myproc()->pgdir));     // xv6 only does full flush
     break;
   }
   ```

4. **Update `copyout` (kernel-to-user copy used by syscalls like `read`).**
   - `copyout` writes user pages through their kernel-half mapping (`P2V(pa)`); it bypasses the MMU's W-bit check **at the user PTE** but still must trigger CoW logic.
   - Lab 2 fix: in `copyout`, walk the user PTE; if it's CoW, perform the same break-share before writing, otherwise the parent and child silently share the syscall-written buffer.

5. **Update `kfree` to be CoW-aware.**
   ```c
   void kfree(char *v) {
     ...
     if(decref(V2P(v)) > 0) return;  // still other owners
     // genuine free
     memset(v, 1, PGSIZE);
     r = (struct run*)v; r->next = kmem.freelist; kmem.freelist = r;
   }
   ```

### Lab 2 corner cases (slide checklist)
- **Children / grandchildren** — fork-after-fork must keep refcounts coherent (each fork increments by 1, each handler decrement decrements by 1).
- **OOM in handler** — if `kalloc` fails during CoW resolution, the only safe response is to kill the faulting process (cannot undo the trap).
- **Cleanup on `exit`** — must walk PD and `kfree` (which now decrements refcount, not always free) every PTE; pages with multiple owners survive.
- **`exec`** — replaces address space; old PD's pages get refcount-decremented in `freevm`; new pages allocated normally (no CoW until the next fork).
- **Concurrency** — refcount inc/dec must be atomic (xv6 is single-big-lock simple, but multi-CPU-safe needs `xchg` or per-bucket lock).

### What Lab 2 does **not** do
- **No PTP CoW** — page tables themselves are still freshly allocated in `cowuvm` (per slide note).
- **No swap** — xv6 still has no disk-backed paging.
- **No mmap, no shared memory** — those need a many-to-one VA→PA infrastructure that Lab 2 only partially introduces (refcount table is the prerequisite).

### Files you typically touch
- `kalloc.c` — refcount array, `incref`/`decref`/`getref`, modified `kfree`.
- `vm.c` — `copyuvm` → `cowuvm`, modified `copyout`, helper `cowfault(va)`.
- `trap.c` — handle `T_PGFLT`.
- `mmu.h` — define `PTE_COW = 0x800` (one of the AVL bits 9–11).

---

## 14. Common Exam Gotchas

> **Tags:** `cow gotchas` `vm trick gotchas` `exam tricks`

- **CoW writes still cost a page fault** — the kernel "lies" but the lie has a price (TLB miss + handler).
- **Refcount overhead is per-PFN, not per-process** — sized by RAM, not by #processes.
- **CoW does not magically share writes** — once written, the page is **private** to that writer; CoW only delays the copy, doesn't avoid it for written pages.
- **Read-only pages stay shared forever** — refcount stays > 1, no copy ever happens. Code segments after `fork+exec` are a great example.
- **A `PTE_W=0` page is not necessarily CoW** — it could be a genuinely RO mapping (kernel text, mmap'd RO file). Use the AVL `PTE_COW` bit to distinguish.
- **`vfork` is not CoW** — it shares the *entire* address space (no PT copy at all) and assumes the child won't write anything except call `exec`. Faster than CoW, less safe.
- **OOM at write time** is the dark side of CoW — eager copy fails fast, CoW fails late and unpredictably.
- **xv6 only flushes TLB on `cr3` reload** — fine-grained `invlpg` is rare in xv6, so CoW handlers do a full flush.
- **Kernel writes via `copyout`** must respect CoW too — common Lab 2 bug source.
- **xv6 baseline cannot do CoW** because its physical-page state is binary (free/used) with no way to track "shared by N processes". Adding a refcount is the **prerequisite** to all of these tricks.
- **Dirty CoW** is the canonical reminder that CoW is concurrency-sensitive — the RO lie must be lifted atomically with the copy.

---

## 15. Quick Reference

| Term | Meaning |
|---|---|
| CoW | Copy-on-Write |
| ZFOD | Zero-Fill On Demand |
| PTP CoW | Page-Table-Page CoW (sharing the PT structure itself) |
| `PTE_COW` | Software flag in AVL bits marking "this RO is because of CoW" |
| Refcount | Per-PFN integer of how many PTEs map this physical frame |
| `T_PGFLT` | x86 trap vector 14 — page fault |
| `CR2` | Register holding the faulting linear address on `T_PGFLT` |
| Error code (PF) | bit 0=P (1 if perm violation, 0 if not present), bit 1=W (write), bit 2=U (user) |
| `vfork` | fork without CoW, shares entire AS — undefined behavior unless child immediately execs |
| Dirty CoW | CVE-2016-5195 — race in Linux CoW giving root |

---

## L09 — Concurrency I (Interrupts & Traps) — xv6

*([→ back to concept](<#L09 — Concurrency I (Interrupts & Traps)>))*

## 11. xv6-Specific Implementation

> **Tags:** `xv6 traps` `xv6 IDT` `xv6 syscall` `int 0x40` `T_SYSCALL` `vectors.pl` `trap.c xv6`

> Conceptual content above is design-agnostic. This section documents how **xv6 specifically** wires it up.

### Layout
| File | Role |
|---|---|
| `x86.h` | `struct trapframe`, `gatedesc`, `SETGATE` macro, `lidt` inline |
| `mmu.h` | `STS_IG32`, `STS_TG32`, `DPL_USER`, IDT entry layout |
| `traps.h` | Vector numbers (`T_SYSCALL=64`, `T_PGFLT=14`, `IRQ_TIMER=0`, etc.) |
| `vectors.pl` → `vectors.S` | 256 auto-generated stubs, each `pushl trapno; jmp alltraps` |
| `trapasm.S` | `alltraps` (entry) and `trapret` (exit) |
| `trap.c` | `tvinit()`, `idtinit()`, `trap()` C dispatcher |
| `usys.S` | User-side `SYSCALL(name)` stubs that issue `int $T_SYSCALL` |
| `syscall.c` | `syscall()` dispatcher reading `tf->eax`, calling `sys_*` handlers |

### Boot path
- `main()` → `tvinit()` (build IDT once, system-wide) → per-CPU `idtinit()` runs `lidt(idt, sizeof(idt))` to load IDTR.
- The IDT itself is a **single static array** shared across all CPUs.

### Privilege rules in xv6
- Every IDT entry has `DPL=0` **except `T_SYSCALL`**, which has `DPL=DPL_USER` so `int 0x40` is permitted from ring 3.
- All entries are **interrupt gates** (auto-`cli`) **except `T_SYSCALL`** which is a **trap gate** so xv6 can decide IF policy in C.

### What `trap()` does
- For `T_SYSCALL`: calls `syscall()`. If process was `killed`, `exit()` after.
- For `T_IRQ0+IRQ_TIMER`: increments `ticks`, wakes sleepers, calls `yield()` if process is `RUNNING` → drives **preemptive scheduling**.
- For `T_IRQ0+IRQ_IDE/KBD/COM`: calls device-specific ISR.
- For `T_PGFLT` (Lab 2): inspect `cr2`, decide CoW vs lazy alloc vs kill.
- Default: kernel panic if from kernel; otherwise mark process killed.

### What xv6 does **not** do
- No `syscall`/`sysret` fast path — always `int 0x40`.
- No nested interrupts during user-mode interrupt-gate handlers (`IF` cleared).
- No deferred work / softirqs / tasklets — handlers run inline.
- No per-CPU IDT (one IDT, all CPUs).
- No NMI handling beyond crashing.

### `tvinit` quick gotcha (slide "Q?")
- All 256 entries are installed with `DPL=0` first, **then** `T_SYSCALL` is overwritten with `DPL=DPL_USER`. If the order were reversed, the syscall gate would be clobbered. The two-step pattern matters.

---

## 12. Common Exam Gotchas

> **Tags:** `interrupt gotchas` `trap gotchas` `concurrency gotchas` `exam tricks`

- **Vector ≠ IRQ.** IRQ is the PIC line (0–15). Vector is the IDT index (0–255). xv6 maps `IRQ_n → T_IRQ0+n = 32+n`.
- **Vectors 0–31 are CPU-reserved** for exceptions (Intel). HW IRQs must remap above that, hence `T_IRQ0 = 32`.
- **`cli` only masks `INTR`.** NMI and exceptions still fire.
- **Interrupt gate clears IF; trap gate does not.** This is *the* behavioral difference. Know which xv6 uses where.
- **Syscall gate must be DPL=3.** Otherwise `int 0x40` from user mode raises `#GP`.
- **`int N` from user with DPL<3 entry → #GP**, *not* the requested handler.
- **HW pushes an error code only on some exceptions** (PF=14, GP=13, DF=8, …). `vector.S` shoves a dummy 0 for the rest so the trap frame is uniform.
- **`iret` is atomic** — cannot be split into manual pops without a window for an interrupt to derail the restore.
- **Holding a spinlock implies `cli`** on uniprocessor xv6; a handler waiting on the same lock would deadlock otherwise.
- **TSS provides the kernel `SS:ESP`** on ring change — the IDT alone isn't enough.
- **`pushcli`/`popcli` nest** — needed so nested lock acquires don't reenable interrupts at the wrong level.
- **Clock algorithm only approximates LRU** — pathological access patterns make it degenerate to FIFO.
- **`PTE_A` is set by HW automatically** on read/write — no trap needed; kernel just reads/clears it.
- **NMI in xv6 = panic.** Real OSes handle it (e.g., for kernel debuggers).

---

## 13. Quick Reference

| Term | Meaning |
|---|---|
| **IDT** | 256-entry table mapping vector → handler |
| **IDTR** | CPU register holding (base, limit) of IDT |
| **`lidt`** | Instruction to load IDTR |
| **Vector** | 0–255 number selecting handler |
| **IRQ** | PIC input line (0–15 on dual 8259A) |
| **PIC** | 8259A interrupt multiplexer |
| **APIC/IOAPIC/LAPIC** | Modern replacement; per-CPU + many vectors |
| **NMI** | Non-Maskable Interrupt (vector 2) |
| **INTR** | Maskable hardware interrupt pin |
| **INT N** | Software interrupt instruction |
| **INTA** | Interrupt-acknowledge bus signal |
| **EFLAGS.IF** | Interrupt-enable flag (`sti`/`cli`) |
| **DPL** | Descriptor Privilege Level — caller-CPL minimum |
| **CPL** | Current Privilege Level (ring of running code) |
| **Trap gate** | IDT entry that leaves IF unchanged on entry |
| **Interrupt gate** | IDT entry that clears IF on entry |
| **TSS** | Task State Segment — supplies kernel `SS:ESP` on ring change |
| **`T_SYSCALL`** | xv6 syscall vector = 64 = `0x40` |
| **`T_PGFLT`** | Page-fault vector = 14 |
| **`T_IRQ0`** | Base vector for HW IRQs in xv6 = 32 |
| **`PTE_A`** | Accessed bit, set by HW on any read/write |
| **`PTE_D`** | Dirty bit, set by HW on writes |
| **Clock alg.** | Circular-list LRU approximation using `PTE_A` |
| **Belady** | Optimal but unrealizable eviction policy |
| **`alltraps`** | xv6 common interrupt-entry assembly stub |
| **`trapret`** | xv6 common interrupt-exit assembly stub |
| **Trap frame** | Saved register state on kernel stack at trap |

---

## L10 — Concurrency II (Locks & Memory Models) — xv6

*([→ back to concept](<#L10 — Concurrency II (Locks & Memory Models)>))*

## 13. xv6 Concrete Implementation

> **Tags:** `xv6 spinlock` `xv6 acquire` `xv6 release` `pushcli` `popcli` `holding`
> `getcallerpcs` `lk->locked` `lk->cpu` `lk->pcs`

### `struct spinlock` (xv6)
```c
struct spinlock {
    atomic_uint locked;   // 0 = free, 1 = held
    char *name;           // for debug prints
    struct cpu *cpu;      // which CPU holds it
    uint pcs[10];         // call stack at acquire time (debug)
};
```
- `name` / `cpu` / `pcs` exist purely for **debugging** — `panic` on double-acquire prints the holder.

### `acquire(struct spinlock *lk)`
```c
void acquire(struct spinlock *lk) {
    pushcli();                              // disable interrupts (refcounted)
    if (holding(lk)) panic("acquire");      // double-acquire by same CPU == bug
    while (atomic_exchange_explicit(
              &lk->locked, 1, memory_order_acq_rel) != 0)
        ;                                   // spin
    lk->cpu = cpu;
    getcallerpcs(&lk, lk->pcs);             // record call stack
}
```
- `pushcli()` *first*, **then** xchg — order matters: if you xchg first and the interrupt fires after, an int handler trying to acquire on this CPU will deadlock.
- `memory_order_acq_rel` on the xchg is the **acquire fence** — no later loads/stores from the CS can be reordered above it.
- Spin loop is the simplest possible: no backoff, no MCS queueing.

### `release(struct spinlock *lk)`
```c
void release(struct spinlock *lk) {
    if (!holding(lk)) panic("release");
    lk->pcs[0] = 0;
    lk->cpu = 0;
    atomic_store_explicit(&lk->locked, 0,
                          memory_order_release);
    popcli();                               // re-enable interrupts (if depth back to 0)
}
```
- `memory_order_release` on the store: all CS writes are globally visible **before** another CPU sees `locked=0`. Pairs with the `acquire` order on the `xchg`.
- `popcli()` *last* — keep interrupts disabled until the lock is fully released, otherwise an interrupt could see partial state.
- `pushcli`/`popcli` are **nest-counted** — supports nested critical sections in the kernel.

### `holding(lk)` and `pushcli`/`popcli` invariants
- `holding(lk)` returns `lk->locked && lk->cpu == cpu`.
- `pushcli()` saves the **previous interrupt-enabled state** on the first call and disables interrupts; nested calls just increment a counter.
- `popcli()` decrements; only when count hits 0 does it restore the original interrupt state. Panics if called with interrupts already enabled (mismatched pair).

### Why xv6 doesn't do better
- **No higher-level primitives** — kernel coders use raw spinlocks everywhere.
- **No backoff** — heavy contention burns cores.
- **No reader/writer locks** — even read-mostly state takes the full lock.
- **Single big locks** in places (`ptable.lock`, `kmem.lock`) — easy to reason about, terrible scalability past ~4 cores.
- xv6's design priority is **pedagogical clarity**, not concurrency throughput.

### Lab 2 connection
- Lab 2 introduces a **physical-page refcount** (for CoW). Inc/dec must be **atomic** because multiple CPUs fork/exit/fault simultaneously.
- xv6's go-to atomicity: hold the relevant spinlock (`kmem.lock`) around the refcount update — simple, correct, scales poorly. A multicore-optimized kernel would use `atomic_fetch_add`.

### xv6 deadlock-avoidance discipline
- **Max two locks held at once** (slide).
- **Global lock ordering** required when holding two — e.g., `ide` then `ptable`, never the reverse.
- All lock-holders must keep CS short; any sleep/`yield` releases the relevant locks first (`sleep()` has special hand-off semantics — covered in Concurrency I / Ordering & Waiting lectures).

---

## 14. Common Exam Gotchas

> **Tags:** `concurrency gotchas` `exam tricks` `concurrency2 traps`

- **`(eax=0, ebx=0)` is observable on x86** — TSO allows it; SC forbids it. Always check the model the question assumes.
- **Disabling interrupts is enough on uniprocessor, never on SMP** — another CPU is still running freely.
- **Spinlock without `cli` deadlocks with interrupt handlers** on the same CPU.
- **`volatile != atomic`** — never use `volatile` for thread synchronization in C/C++.
- **Peterson is correct under SC, broken under TSO** without explicit fences.
- **Atomic store/load alone are not enough for mutex** — you need an RMW (xchg / CAS / fetch-add).
- **A successful `xchg(&lock, 1)` returning 0 is the moment of acquisition** — returning 1 means "still locked, keep spinning."
- **`memory_order_relaxed` does NOT order anything but the access itself** — fine for counters, deadly for locks.
- **Lock ordering is global** — all code paths must agree, or one renegade path reintroduces the cycle.
- **Holding a lock across a sleep/IO is a usually a bug** — except when the sleep primitive explicitly hands off the lock (xv6 `sleep`).
- **Deadlock differs from livelock differs from starvation** — deadlock = stuck forever, livelock = busy but no progress (Peterson with both yielding), starvation = some thread perpetually loses races.
- **Even atomic counters can be wrong** if the *invariant* you care about needs more than one variable updated together — atomic doesn't compose; locks do.
- **Compiler reordering happens before CPU reordering** — both must be tamed (atomics handle both).
- **xv6 `pushcli` order matters** — disable interrupts *before* taking the lock; restore *after* releasing.

---

## 15. Quick Reference

| Term | Meaning |
|---|---|
| Critical section (CS) | Code that must execute with mutual exclusion |
| Spinlock | Busy-wait lock; spin on `xchg` until acquired |
| Sleep lock | Lock that yields the CPU on contention |
| `xchg` / `atomic_exchange` | Atomic swap — building block of spinlock |
| CAS | Compare-and-swap; conditional atomic update |
| TSO | Total Store Order — x86's memory model; allows W→R reorder |
| SC | Sequential Consistency — idealized; what naive code assumes |
| DRF0 | Data-Race-Free → SC behavior guaranteed |
| Fence / barrier | Instruction enforcing memory ordering |
| `memory_order_acquire` | Loads after this can't move before it |
| `memory_order_release` | Stores before this can't move after it |
| `pushcli`/`popcli` | xv6 nestable interrupt-disable pair |
| `holding(lk)` | xv6 check: this CPU currently holds `lk` |
| Deadlock | Circular wait, no progress |
| Livelock | Active progress but no useful work (e.g., everyone yields) |
| Starvation | Some thread never gets the lock |
| Safety | "Nothing bad" — invariant always holds |
| Liveness | "Something good eventually" — progress |
| Peterson | Software-only 2-thread mutex; needs SC |
| `volatile` | "Don't optimize this access" — NOT a sync primitive |

---

## L11 — Schedulers — xv6

*([→ back to concept](<#L11 — Schedulers>))*

## 13. xv6 Implementation — Specific Realization

> **Tags:** `xv6 scheduler` `xv6 swtch` `xv6 yield` `xv6 sched` `forkret` `ptable.lock` `proc->context`
> `cpu->scheduler` `RUNNABLE` `RUNNING` `SLEEPING` `switchuvm` `switchkvm` `xv6 round robin`

> The conceptual sections above are independent of xv6. Below: **how xv6 specifically implements all that.**

### Policy
- **Round-robin** — that's it. No priority, no nice, no feedback.
- Quantum = whatever interval the timer interrupt fires (set up in `lapic.c`, ~10 ms).
- Picking is cheap: linear scan of `ptable.proc[]`.

### The scheduler loop (`proc.c::scheduler()`)
```c
for (;;) {
    sti();                              // enable interrupts on this CPU
    acquire(&ptable.lock);
    for (p = ptable.proc; p < &ptable.proc[NPROC]; p++) {
        if (p->state != RUNNABLE) continue;
        proc = p;                       // per-CPU current process
        switchuvm(p);                   // load p's user page table + TSS
        p->state = RUNNING;
        swtch(&cpu->scheduler, p->context);   // → into p
        switchkvm();                    // back to kernel page table
        proc = 0;
    }
    release(&ptable.lock);
}
```
- `ptable.lock` is **held across the swtch** — only released by the *next* code that runs in `p` (a deliberate, slightly mind-bending invariant).
- The scheduler thread per CPU has its **own kstack**; `cpu->scheduler` is the saved context to resume after a process gives up.

### Giving up the CPU — invariants
A process must, before calling `sched()`:
1. **Hold `ptable.lock`** (it's the global runqueue lock).
2. **Release any other locks** (avoid deadlock — never sleep with extra locks).
3. **Update its own state** (`RUNNABLE`, `SLEEPING`, `ZOMBIE` — never `RUNNING`).
4. **Call `sched()`**, which calls `swtch(&proc->context, cpu->scheduler)`.

`yield`, `sleep`, and `exit` all follow this protocol.

### `yield` — preemption path
```
timer IRQ → trap → yield() → sched() → swtch() → scheduler thread
```
- At the end of every interrupt, `trap` may call `yield` if `proc->state == RUNNING`.
- `yield()`:
  ```c
  acquire(&ptable.lock);
  proc->state = RUNNABLE;
  sched();
  release(&ptable.lock);
  ```

### `sched` — the choke point
- Asserts: `holding(&ptable.lock)`, `cpu->ncli == 1` (only ptable.lock), `proc->state != RUNNING`, interrupts disabled.
- Calls `swtch(&proc->context, cpu->scheduler)` → returns later when scheduler picks this proc again.
- "Kernel thread always gives up in `sched` and switches to the same location in `scheduler`" — symmetric coroutine pattern.

### `swtch(struct context **old, struct context *new)`
Implemented in **`swtch.S`** (assembly). Steps:
1. **Load args off the stack into `%eax`, `%edx`** *before* `%esp` is changed (args become inaccessible after).
2. Push **callee-save** registers: `%ebp`, `%ebx`, `%esi`, `%edi` (and `%esp` saved as `*old`).
3. `%eip` is *not* explicitly pushed — it was placed there by the **`call` instruction** that invoked `swtch`; it sits **just before the saved `%ebp`** on the stack.
4. **`movl %edx, %esp`** — switch to the new context's stack.
5. Pop callee-save registers in reverse order.
6. `ret` — pops the saved `%eip`, resuming the new thread *exactly where it last called `swtch`*.

> Caller-saved registers are **not** touched — by the C calling convention they were already saved by the caller before the `call swtch`.

### `forkret` — the one exception
- A brand-new process has no prior `sched` call to return from. Its initial `proc->context->eip` is set to **`forkret`**, a tiny stub that:
  - Releases `ptable.lock` (the scheduler held it).
  - Returns into `trapret` → returns to user space at the entry point (set up by `userinit`/`fork`).
- This is the only place the scheduler-↔-process coroutine pattern is asymmetric.

### Per-CPU vs per-process state
- Per-CPU: `cpu->scheduler` (context), `cpu->ts` (TSS), `cpu->ncli`, `cpu->intena`, `cpu->proc` (current running proc).
- Per-process: `proc->context` (saved kstack pointer + callee-save regs), `proc->kstack`, `proc->state`, `proc->pgdir`, etc.
- A kernel thread = (kstack, context). A process = (kernel thread, page table, file table, …).

### `switchuvm` / `switchkvm`
- `switchuvm(p)` — load `p`'s page directory (`lcr3`), point TSS to `p->kstack` so future kernel entries land on the right stack.
- `switchkvm()` — load the kernel-only page directory; used while running scheduler code that has no user mapping.

### Where xv6 is bad and why
- **Single global `ptable.lock`** — every CPU contends on every scheduling decision; doesn't scale past a handful of cores.
- **Linear `O(n)` scan** of NPROC (= 64) — fine for pedagogy, terrible at scale.
- **No priorities, no aging** — a tight CPU loop and `vim` get equal share.
- **Quantum = timer tick (~10 ms)** — fixed, not adaptive.
- **No CPU affinity / no load balancing** — process can bounce, blowing caches.
- **Holds `ptable.lock` across the entire `swtch`** — large lock-hold time. (Necessary for the way state mutation and stack switch are ordered, but bad for scalability.)

### What xv6 does *right* (for a teaching kernel)
- Demonstrates **mechanism vs policy** separation cleanly: `swtch` is policy-free; the scheduler loop *is* the policy.
- Demonstrates the **coroutine** pattern between proc and scheduler.
- Demonstrates the **lock-hand-off invariant** that's required to safely change `state` and switch stacks atomically (the topic of L09 Concurrency I).

---

## 14. SLO / Objective Analysis — Are Goals Homogeneous?

> **Tags:** `slo homogeneous` `slo heterogeneous` `objective analysis` `mixed workload`

| Scheduler | Implicit SLO | Homogeneous across procs? | Implication |
|---|---|---|---|
| FCFS | "throughput-only" | Yes | Long-tail wait acceptable |
| RR (xv6) | "equal CPU share, bounded wait ≈ N·quantum" | Yes (uniform) | All procs treated equal; no class awareness |
| Priority | "high-prio responds fast" | **No** — class-tiered | Need anti-starvation policy (aging) |
| MLFQ / CFS | "interactive ~ms, batch ~s" | **No** — feedback-derived | Inferred per-process; resilient to phase change |
| RT (FIFO/RR) | "deadline D_i for task i" | **No** — explicit per-task | Admission control required |
| Cluster (TetriSched) | "deadline + locality + group" | **No** — declarative per-job | Solver-based scheduler |

**Heterogeneous SLOs** *imply* the scheduler must (a) know or infer the class, (b) preempt to honor priority, (c) defend against starvation. **Homogeneous SLOs** simplify the scheduler to a single discipline (RR, FCFS) but lose the ability to bound tail latency for important work.

---

## 15. Common Exam Gotchas

> **Tags:** `scheduler exam tricks` `scheduler gotchas` `scheduling traps`

- **xv6 is round-robin** — don't say "xv6 uses MLFQ" or "priority" on the exam.
- **Round-robin is starvation-free** but **not deadline-aware**.
- **SJF/SRTF need an oracle** (or estimator) — this is the central reason they're not used in commodity OSes.
- **Priority without aging starves low priority** — aging or boosting is required.
- **CFS is WFQ** — not MLFQ, even though both bias toward interactive.
- **CFS picks smallest vruntime** (not smallest priority number).
- **`nice` lower number = higher priority** (`nice -20` is highest, `nice 19` is lowest).
- **`SCHED_FIFO`/`SCHED_RR` are RT classes** — they preempt all `SCHED_OTHER`. A runaway one hangs the box.
- **Hard real-time + virtual memory don't mix** — page faults break worst-case timing.
- **Soft real-time needs both** priority *and* low dispatch latency — getting only the first is a common mistake.
- **xv6 switches kernel-context → kernel-context only** — never user→user direct, never user→scheduler direct.
- **`swtch` saves only callee-save registers** — caller-saves were saved by the C compiler before the call.
- **`%eip` is not in `struct context`** in the saved-by-`swtch` sense — it lives at the implicit "return address" slot the `call` instruction pushed.
- **`ptable.lock` is held across `swtch`** — the *next* runner releases it (or `forkret` does for a new proc).
- **`forkret` exists because** a new proc has no prior `sched` to return from.
- **Holding an extra lock across `sched` is a deadlock** — `sleep()` is the only sanctioned way (and it carefully releases its lock and reacquires after wakeup).
- **Quantum tradeoff is U-shaped** — too small = CSW dominates, too large = bad latency.
- **Latency CDF "shifted left" = better.** SLO attainment = `CDF(SLO)`.
- **Non-work-preserving** ≠ broken — sometimes optimal (delayed scheduling, reservation systems).
- **Scheduler is the canonical *multiplexing* mechanism** — if a question asks "which key idea does scheduling exemplify?" → **multiplexing** (with isolation/sharing as second-order).

---

## 16. Quick Reference

| Term | Meaning |
|---|---|
| Quantum / timeslice | CPU time given before preemption |
| Preemptive | Scheduler can forcibly take CPU back (timer-driven) |
| Cooperative | Process must voluntarily yield |
| Convoy effect | Long job blocks short jobs behind (FCFS) |
| Aging | Boost waiting low-prio jobs to avoid starvation |
| `nice` | Linux user-visible priority hint, −20 (high) … 19 (low) |
| WFQ | Weighted Fair Queuing — proportional CPU share |
| CFS | Linux Completely Fair Scheduler — vruntime-keyed RB-tree, WFQ |
| MLFQ | Multi-level Feedback Queue — learns class from behavior |
| MinJCT | Minimize job completion time |
| Dispatch latency | Time from "wake task" to "first instruction runs" |
| WCET | Worst-case execution time (RT) |
| EDF / RM | Earliest-Deadline-First / Rate-Monotonic (RT algorithms) |
| TetriSched | Spatio-temporal cluster scheduler (EuroSys'16) |
| Power of two choices | Sample 2 servers, pick less-loaded; near-optimal |
| Delayed scheduling | Wait briefly for locality-friendly slot (EuroSys'10) |
| `swtch` | xv6 assembly: save/restore callee-save regs + esp/eip |
| `sched` | xv6 C: the only sanctioned path to leave the CPU |
| `yield` | xv6: timer-driven preemption (`RUNNING → RUNNABLE`) |
| `forkret` | xv6: first-time entry stub for a freshly-created proc |
| `ptable.lock` | xv6 global runqueue lock; held across `swtch` |
| `cpu->scheduler` | Per-CPU saved scheduler-thread context |
| `proc->context` | Per-proc saved kernel-thread context |
| `RUNNABLE / RUNNING / SLEEPING / ZOMBIE` | xv6 process states |
| Tail latency | Right tail of latency distribution (P99, P99.9) |
| SLO | Service Level Objective — numeric latency target |

---

## L12 — Ordering, Waiting & Context Switch — xv6

*([→ back to concept](<#L12 — Ordering, Waiting & Context Switch>))*

## 16. xv6 Concrete Implementation

> **Tags:** `xv6 swtch` `xv6 sched` `xv6 yield` `xv6 sleep` `xv6 wakeup` `xv6 ptable`
> `xv6 chan` `xv6 forkret` `xv6 sleeplock`

### Per-process state
- `struct proc { ..., enum procstate state; void *chan; struct context *context; char *kstack; ... }` in `proc.h`.
- `state ∈ {UNUSED, EMBRYO, SLEEPING, RUNNABLE, RUNNING, ZOMBIE}`.
- `chan` is the wait-channel pointer (can be **any address**, used as an opaque key — typically the address of the data structure being waited on, e.g., `&pipe->nread`).
- `context` points into the kstack at the saved callee-saved registers and saved `%eip`.

### `swtch` (proc.S)

```asm
.globl swtch
swtch:
    movl 4(%esp), %eax        # old (struct context**)
    movl 8(%esp), %edx        # new
    pushl %ebp ; pushl %ebx ; pushl %esi ; pushl %edi
    movl %esp, (%eax)         # *old = %esp  (creates the context block)
    movl %edx, %esp           # %esp = new context's stack
    popl %edi ; popl %esi ; popl %ebx ; popl %ebp
    ret
```

### `sched()` (proc.c)

```c
void sched(void) {
    struct proc *p = myproc();
    if (!holding(&ptable.lock)) panic("sched ptable.lock");
    if (mycpu()->ncli != 1)     panic("sched locks");      // exactly one cli depth (the ptable.lock's)
    if (p->state == RUNNING)    panic("sched running");    // must have changed state
    if (readeflags() & FL_IF)   panic("sched interruptible");
    int intena = mycpu()->intena;
    swtch(&p->context, mycpu()->scheduler);
    mycpu()->intena = intena;
}
```

The four panics enforce the invariants from §11.

### `yield()` (proc.c)

```c
void yield(void) {
    acquire(&ptable.lock);
    myproc()->state = RUNNABLE;
    sched();
    release(&ptable.lock);
}
```

Called from `trap()` on every timer interrupt that hits a RUNNING user process — that's how xv6 implements **involuntary preemption** by tacking voluntary `swtch` onto the trap return path.

### `scheduler()` (proc.c) — per-CPU

> See [L11 — Schedulers — xv6 §13](<#L11 — Schedulers — xv6>) for the full `scheduler()` per-CPU loop and the `switchuvm`/`switchkvm`/`ptable.lock` hand-off discussion. (Round-robin by ptable scan order; `swtch(&c->scheduler, p->context)` is the entry edge into a proc.)

### `sleep()` and `wakeup1()` (proc.c)

```c
void sleep(void *chan, struct spinlock *lk) {
    struct proc *p = myproc();
    if (lk != &ptable.lock) {
        acquire(&ptable.lock);   // need ptable.lock to change state
        release(lk);             // release caller's lock — atomic w.r.t. wakeup
    }
    p->chan  = chan;
    p->state = SLEEPING;
    sched();                     // ← actual context switch
    p->chan = 0;                 // ← resumes here on wake
    if (lk != &ptable.lock) {
        release(&ptable.lock);
        acquire(lk);             // restore caller's lock
    }
}

static void wakeup1(void *chan) {
    struct proc *p;
    for (p = ptable.proc; p < &ptable.proc[NPROC]; p++)
        if (p->state == SLEEPING && p->chan == chan)
            p->state = RUNNABLE;
}

void wakeup(void *chan) {
    acquire(&ptable.lock);
    wakeup1(chan);
    release(&ptable.lock);
}
```

- **Atomicity trick**: `sleep` acquires `ptable.lock` *before* releasing the caller's lock. `wakeup` must acquire `ptable.lock` to flip state. Therefore: a wakeup that races with sleep either (a) runs before `sleep` releases lk → sees no SLEEPING proc, harmless because the caller will re-check the predicate and not sleep; or (b) runs after sleep has set state=SLEEPING → flips it to RUNNABLE correctly. **No lost wakeups.**
- xv6 uses `chan = (void*)pointer-to-some-shared-data` as the rendezvous key (e.g., `sleep(p, &p->lock)` for `wait()`-ing on a child's exit; `sleep(&pipe->nread, ...)` in pipes).
- `wakeup` does an O(NPROC) scan — fine because NPROC=64 in xv6.

### `sleeplock` (sleeplock.c)
- xv6 *does* implement a sleeplock for long-held resources like inode buffers (`acquiresleep`, `releasesleep`). Same shape as §10: spinlock guards `locked`, `sleep(lk, &lk->lk)` blocks on contention, `wakeup(lk)` on release.

### `forkret` — the only thread that doesn't enter via `sched`
- New proc's context is hand-crafted by `allocproc` to `ret` into `forkret`, which releases `ptable.lock` (because the scheduler acquired it) and falls through to `trapret` to enter user mode for the first time.

### What xv6 lacks (vs real systems)
- **No condition variables proper** — sleep/wakeup with a `chan` *is* the CV primitive, but there is no `cv_t` struct and no broadcast-vs-signal distinction (every `wakeup` is effectively a broadcast on that chan).
- **No priority** — pure round-robin via ptable scan order.
- **No CPU affinity, no load balancing** — each CPU's `scheduler()` independently scans the global `ptable`.
- **No per-CPU run queue** — global `ptable.lock` becomes the contention point under load.
- **No futex / no userspace mutex** — user threads don't really exist in xv6 (one thread per proc).

These are exactly the gaps that motivate the topics in `schedulers.md` (CFS, per-CPU runqueues), `threads.md` (kernel vs user threading), and the security/distributed lectures later in the course.

---

## L13 — User & Kernel Threads — xv6

*([→ back to concept](<#L13 — User & Kernel Threads>))*

## 12. xv6 — Where It Actually Stands

> **Tags:** `xv6 threads` `xv6 kernel stack` `xv6 no user threads` `xv6 no SMP`
> `xv6 single CPU sched` `xv6 process is thread`

> **Conceptual section above is disjoint from this implementation section.**

### xv6 baseline (before lab3)
- **Each process has its own kernel stack** (one stack per process, used during traps/syscalls).
- **No user-level threads** — xv6 has no thread API; one process = one user-side execution flow.
- **Scheduler has no thread awareness** — it schedules processes (`struct proc`), not threads.
- **No SMP support** in the baseline — scheduler runs on a single CPU; no per-CPU run queues.
- A "kernel thread" in xv6 already exists conceptually: every `proc` *is* a kernel thread (it has a kernel stack, a saved `context`, a scheduler entry via `swtch`). User-side, it's only a single execution stream.

### What lab3 adds
- A `clone(void *stack, int size)` syscall that creates a `proc` **sharing the parent's pgdir** (no COW, no copy of address space).
- A `thread_create()` user-space wrapper.
- `thread_wait()` to join.
- Mutex via `park`/`setpark`/`unpark` — kernel-supported sleep/wakeup primitives that user-space mutex code calls into when contended (xv6's small-scale futex analogue).
- Condition variables (`cond_wait`, `cond_signal`) layered on the mutex + park/unpark.

### Concretely: how xv6 ends up at 1:1
- After lab3, xv6's design is **1:1 kernel threading**: every user thread = one `struct proc` sharing pgdir with siblings.
- Kernel scheduler picks `proc`s; threads are first-class to it.
- Memory sharing comes from sharing `pgdir`; the stack is the per-thread private state (caller-allocated, child uses it).
- **No M:N.** No scheduler activations. Matches what modern Linux/BSD do (NPTL-style, minus futex sophistication).

### Per-thread vs per-process state in xv6 after lab3
| State | Per-thread | Per-process (shared) |
|---|---|---|
| `pgdir` | ❌ shared | ✅ |
| User stack | ✅ private (caller-allocated) | — |
| Kernel stack | ✅ (each `proc` has one) | — |
| `context` (saved regs) | ✅ | — |
| `tf` (trapframe) | ✅ | — |
| File table (`ofile[]`) | shared (siblings inherit) | ✅ |
| `cwd` | shared | ✅ |
| PID/TID | ✅ unique | — |

---

## 13. One-Line Summary

> **Threads = mechanism for the abstraction of concurrency, parameterized by where the scheduler lives (user/kernel/both) and how user-flows map to kernel-flows (M:1, 1:1, M:N). Modern systems converged on 1:1 + user-space sync (futex). xv6 lab3 builds exactly this: `clone()` for shared-pgdir tasks, park/unpark for kernel-assisted sleep, mutex + cv on top.**

---

## L14 — Security I (Goals, Threats, Memory Safety) — xv6

*([→ back to concept](<#L14 — Security I (Goals, Threats, Memory Safety)>))*

## 13. xv6 — How These Concepts Map to the Real Implementation

> **Tags:** `xv6 security` `xv6 memory safety` `xv6 password` `xv6 trust boundary` `xv6 syscall validation`
> `argptr` `argstr` `argint` `xv6 C` `xv6 user kernel boundary`

> **Conceptual content above is disjoint from xv6.** This section is the xv6-specific instantiation.

### What xv6 *is*, security-wise
- xv6 is written in **C** — it is **memory-unsafe** in exactly the way the lecture warned about.
- xv6 has **no ASLR, no DEP/NX, no stack canaries, no CFI**. The kernel image is loaded at a fixed
  virtual address (`KERNBASE = 0x80000000`); user binaries load at fixed virtual `0x0`.
- xv6 has **no users, no passwords, no authentication.** Every process is "the user." The only
  privilege boundary is **user vs kernel** (CPL ring 3 vs ring 0).

### Trust boundary: the syscall interface
- The single trust boundary in xv6 is **user → kernel** at `int $T_SYSCALL` (vector 64).
- The kernel must treat **every** user-supplied argument as adversarial (Kerckhoff applied locally).
- Argument-fetch helpers in `syscall.c`:
  - **`argint(n, *ip)`** — fetches the n-th syscall arg as an int (off the user stack).
  - **`argptr(n, *pp, size)`** — fetches a pointer arg **and validates** that
    `[ptr, ptr+size)` lies inside the calling process's address space (`addr < proc->sz`).
  - **`argstr(n, **pp)`** — fetches a NUL-terminated user string, also validating each byte is in range.
  - **`fetchint` / `fetchstr`** — the underlying single-word/string fetches with bounds checks.
- These checks **are the mechanism** that enforces the policy "user cannot trick the kernel into reading/writing
  outside its own address space."
- Forgetting to use these helpers (e.g., `*((int*)user_ptr)` directly in a syscall) is exactly the kind of
  **bad mechanism** the lecture describes — a kernel bug that becomes a privilege-escalation vuln.

### Memory-safety surface in xv6
- **`copyout` / `copyin`** equivalents are open-coded via the `arg*`/`fetch*` helpers.
- **Stack overflows** in kernel mode are bounded only by the kernel stack size (one page per proc).
  Recursion / deep call chains in syscalls would corrupt adjacent kernel data — there is **no guard page**.
- **`exec`** parses an ELF header from a user-supplied file → historical source of OS bugs (header
  field validation, integer overflow on segment sizes). xv6 does basic checks; not a hardened parser.
- **No `strncpy`-style hygiene** — xv6 uses `safestrcpy` (a small bounded copy helper) in places, but
  the codebase relies on small sizes and careful authors, not on systematic bounds checks.

### What xv6 demonstrates *correctly*
- **Policy/mechanism separation** at the syscall layer:
  - Policy = "process can only access its own address space" (declared in design).
  - Mechanism = `argptr`'s `addr + size <= proc->sz` check + the **page table** itself (hardware mechanism).
- **Defense in depth**: even if `argptr` were buggy, the **MMU** still enforces page-level
  isolation between user procs (each proc has its own page directory).
- **Privilege boundary** via x86 rings:
  - User runs at **CPL=3**, kernel at **CPL=0**.
  - Transition is **only** via `int` (trap gate) or `iret`.
  - The IDT and TSS (set up in `tvinit` / `mpenter`) are the *mechanism* for this *policy*.

### Where xv6 is bad (security-wise) and why that's pedagogically OK
- **No ASLR** — kernel & user load at known fixed addresses.
- **No DEP/NX** — pages are R/W/X however the page directory says, but xv6 doesn't bother to
  mark `.text` non-writable or stacks non-executable.
- **No stack canaries / CFI / shadow stack** — vanilla compile.
- **No SMAP/SMEP** equivalents — the kernel can freely read/write user memory by design (it has to,
  for syscalls), and there's no hardware barrier to accidentally jumping into user code.
- **Single global locks** (`ptable.lock`, etc.) — not directly a security concern, but in real kernels
  lock bugs become **race-condition vulns** (TOCTOU around syscall args is a Linux classic).

### xv6 vs the failure-mode taxonomy

| Failure mode | xv6 instance |
|---|---|
| **Bad policy** | "Every process is the user" — fine for a teaching kernel, fatal in production |
| **Bad threat model** | Implicitly assumes user processes are not *malicious*, just buggy — wrong on a real machine |
| **Bad mechanism** | No DEP/ASLR/canary; would fall to a textbook stack-smash if syscalls had OOB writes |

### Take-away for the exam
- xv6 cleanly shows the **user/kernel trust boundary** and the **`arg*` mechanisms** that police it.
- xv6 is **deliberately not** a hardened kernel — its lack of memory-safety mitigations is a feature
  for teaching the *concepts*, but exactly the reason it would be eaten alive in the real world.
- If asked "where does xv6 enforce a security mechanism?": **page tables (MMU) + ring 3/0 split + `argptr`/`argstr` validation in `syscall.c`.**

---

## L15 — Security II (Access Control, Sandboxing) — xv6

*([→ back to concept](<#L15 — Security II (Access Control, Sandboxing)>))*

## 15. xv6 — Real Implementation

> **Tags:** `xv6 security` `xv6 access control` `xv6 setuid` `xv6 capabilities` `xv6 sandbox`

xv6 is a **teaching kernel** — its security story is intentionally minimal. The conceptual L15 ideas above are *not* what xv6 implements, by design.

### What xv6 *does* have
- **DAC, in skeletal form:**
  - Each `proc` has a **PID and parent**, but **no UID/GID** in the base xv6 — there is effectively a single user.
  - Inodes carry `type, major, minor, nlink, size, addrs[]` — **no mode bits, no owner UID/GID** (see `kernel/fs.h`, struct `dinode`).
  - `chmod`, `chown`, `setuid` — **not implemented**.
- **Process isolation via paging** (real mechanism, see VM crib sheets):
  - Each process has its own page table → memory isolation.
  - User mode (CPL=3) cannot touch kernel pages (U/S bit).
  - System call boundary (`int $T_SYSCALL`) is the only way up.
- **Trap-based protection** — every syscall enters `usertrap`/`syscall` and is dispatched through a fixed `syscalls[]` table (`kernel/syscall.c`); no dynamic loading, no `setuid`-style elevation.

### What xv6 does *not* have
- **No SELinux / no MAC** — no labels, no contexts, no policy file.
- **No seccomp / no eBPF** — every running process can call any syscall.
- **No capabilities** — no unforgeable tokens; FDs are just integers, no rights bits beyond `O_*` flags.
- **No sandboxing primitives** — no namespaces, no cgroups, no chroot.
- **No fuzzing infrastructure** — bugs are found by reading code or tests in labs.

### What xv6 *teaches* about L15
- **The trap/syscall boundary** is the *only* protection mechanism — every L15 mechanism above (DAC, MAC, seccomp, caps) is a *layer added on top of this same boundary*.
- xv6's **`exec`** could host a setuid bit (it doesn't). The minimal change to add setuid would be: read inode `mode`, set `proc->uid = inode->uid` on exec.
- **Confused deputy is impossible in xv6** because there are no privileged userspace daemons — the only privileged code is the kernel, accessed via well-defined syscalls.
- Lab-relevant: when you implement features (system calls, FS extensions), you are extending the *one* protection boundary that xv6 has — a setuid-style hole would compromise everything.

### xv6 vs L15 mapping

| L15 concept | xv6 reality |
|---|---|
| DAC (`rwx`) | **Absent** — single user, no mode bits in dinode |
| MAC (SELinux) | **Absent** |
| setuid | **Absent** — `exec` doesn't change identity |
| Confused deputy | **N/A** — no privileged userspace |
| Capabilities | **Absent** — FDs not rights-tagged |
| seccomp / eBPF | **Absent** — all syscalls always available |
| System decomposition | **Absent** — monolithic kernel; no privsep services |
| Fuzzing | **Absent** — manual testing |

> **xv6's protection is purely (1) user/kernel mode separation via x86 CPL+paging, and (2) the syscall trap as a narrow gate.** Everything in L15 is the story of how *real* OSes *layer additional mechanisms* on top of these same two primitives.

---

## L16 — Networking — xv6

*([→ back to concept](<#L16 — Networking>))*

## 18. xv6 — How xv6 Implements (Or Doesn't Implement) Networking

> **Tags:** `xv6 networking` `xv6 nic` `xv6 e1000` `xv6 lab4 network` `xv6 socket` `xv6 net driver`
> `xv6 ip` `xv6 tcp` `xv6 has no networking`

> **Disjoint section:** the conceptual stack above is OS-agnostic. This is what xv6 *actually* does.

### Stock xv6 has *no networking*
- The vanilla xv6 codebase shipped to students has **no NIC driver, no IP stack, no TCP, no sockets, no DNS**.
- The only "I/O abstractions" xv6 ships with are **console** (UART) and **disk** (IDE / virtio-blk).
- This is **deliberate** — networking is a full-class topic; xv6 is meant to teach OS *kernel* fundamentals, not L4 protocols.

### Lab 4 networking option
- **Lab 4** has an optional **networking track**: students implement a **NIC driver** and **network-enabled xv6 apps** (some semesters: ping, simple HTTP).
- The driver is typically for an **emulated E1000 (Intel Pro/1000)** in QEMU.
  - Set up TX/RX **descriptor rings** in DMA-coherent memory.
  - Wire the **PCI** discovery and **MMIO** registers for the E1000.
  - Hook the **interrupt** for RX completion → push frames into a kernel queue.
  - Add a **`net_tx`/`net_rx`** kernel interface and a tiny user-space stack (or just raw frame send/recv) on top.
- **Possibly eBPF** — some semesters extend further to a tiny eBPF-style packet filter.

### What you'd need to add, in order
1. **PCI scan + E1000 init** — find the device, map BARs, set up rings, enable RX/TX.
2. **Trap handler** — register the E1000 IRQ in `trap.c`, dispatch on `T_IRQ0 + IRQ_E1000`.
3. **Driver buffers** — kalloc'd ring of `mbuf`-style frame buffers, head/tail indices.
4. **System calls** — `sys_send(frame, len)` / `sys_recv(buf, len)` (or full sockets for the brave).
5. **(Optional) ARP + IP + UDP** in tiny C — enough for ping or DNS.
6. **(Optional) TCP** — far more involved; usually skipped or simplified to half-duplex.

### How xv6 maps to lecture concepts
| Concept (lecture) | xv6 stock | xv6 + Lab 4 net |
|---|---|---|
| NIC driver | **absent** | E1000 / virtio-net in `e1000.c` |
| Link layer (Ethernet frame) | absent | manual frame construction |
| L3 (IP) | absent | tiny IPv4 header builder |
| L4 (TCP/UDP) | absent | UDP usually; TCP optional |
| Socket interface | absent | typically a flat `send`/`recv` syscall, *not* full BSD sockets |
| Netfilter / firewall | absent | absent |
| eBPF | absent | possibly a toy XDP-like hook in lecture-driven extension |
| Softirq / NAPI / qdisc | absent | absent — xv6 just does it in IRQ ctx or a kernel thread |

### Why the simplification matters pedagogically
- **xv6 ≠ Linux** by design — it strips the stack so the student sees the **bare minimum** to make a NIC talk.
- This mirrors xv6's general pattern: *real* OS = "build all the abstractions on bare metal." Lab 4 networking applies that pattern to networking.
- The **conceptual lecture** describes the **mature** stack (Linux); xv6 is the *minimal viable kernel* — you build up from MAC frames toward whatever abstraction you need, and the gap between the two is the point.

---

## L17 — File Systems I — xv6

*([→ back to concept](<#L17 — File Systems I>))*

## 18. xv6 Implementation Notes (specific impl, disjoint from concept)

> **Tags:** `xv6 fs.h` `xv6 fs.c` `xv6 mkfs.c` `xv6 sysfile.c` `xv6 bio.c` `xv6 ide.c`
> `xv6 dinode struct` `xv6 inode struct` `xv6 superblock struct` `BSIZE 512` `xv6 NDIRECT 12`
> `xv6 NINDIRECT 128` `xv6 70KB max file` `xv6 inum 0 root` `xv6 single sector blocks`

xv6 makes the simplest possible choices for each design knob above:

- **Files:** sources — `fs.h` (constants & on-disk types), `fs.c` (FS logic), `mkfs.c` (build initial image), `sysfile.c` (syscalls), `bio.c` (bcache), `ide.c` (disk driver).
- **Block size:** `BSIZE = 512` (one sector). Real OSes use 4 KB+.
- **Layout (block 0 onward):** `boot | super | log | inodes | bitmap | data ...`.
- **Superblock** — `struct superblock` in `fs.h`: total size, # data blocks, # inodes, log size, log start, inode start, bitmap start (`bmapstart`).
- **`dinode`** (on-disk inode):
  ```c
  struct dinode {
    short type;            // 0 = free
    short major, minor;    // device files
    short nlink;           // # dirents pointing here
    uint  size;            // bytes
    uint  addrs[NDIRECT+1]; // 12 direct + 1 indirect
  };
  ```
  - Size: **64 bytes** → 8 inodes per 512-byte block.
- **Macros:** `NDIRECT = 12`, `NINDIRECT = BSIZE/sizeof(uint) = 128`, `MAXFILE = NDIRECT + NINDIRECT = 140 blocks ≈ 70 KB`.
- **inum 0** is the root directory `/`. Byte address on disk: `2*512 + 64*0 = 1024`.
- **Dirent:** `{ ushort inum; char name[14]; }` — 16 bytes; `inum==0` means free slot.
- **Inode in-memory cache** (`struct inode` in `file.h`): adds `ref` count + `lock` + `valid` flag on top of `dinode`.
- **Buffer cache:** fixed pool (e.g. 30 bufs in v6), doubly-linked LRU, `B_BUSY` / `B_VALID` / `B_DIRTY` flags, single global `bcache.lock` plus per-buffer sleeplock.
- **Disk driver (`ide.c`):**
  - Talks to QEMU's emulated PIIX3 IDE controller.
  - One lock `idelock`, one queue per device.
  - `ioapicenable(IRQ_IDE, ncpu-1)` pins IDE IRQ to last CPU.
- **Logging (`log.c`)** — `log_write` replaces `bwrite`; transactions begin/commit so create/unlink survive crashes (covered in L19/20).
- **Concurrent allocation correctness** — relies on **buffer-cache block locks** (acquired by `bread`) for both `ialloc` and `balloc` mutual exclusion; no separate inode-table or bitmap locks.
- **Lab4-fs typical extensions:**
  - **Large files** — replace `addrs[12+1]` with `[11+1+1]` to add a *doubly indirect* block → increases max file size to ~16 MB.
  - **Symbolic links** — add `T_SYMLINK` type; new syscall `symlink`; modify `namei`/`open` to follow links.
  - These exercises are essentially "edit `fs.h`, `fs.c`, and `sysfile.c` carefully and pass `usertests`/`bigfile`."

### What xv6 deliberately does NOT do
- No multi-level indirection (just 1 level) → small max file.
- No extents.
- No write-back coalescing beyond log batching.
- No fsync (every committed transaction is durable; no per-file flush API).
- No path caching — every `namei` re-walks from `/`.
- No VFS layer — only one FS implementation.
- No quota / ACLs / xattrs.

---

## L18 — File Systems II — xv6

*([→ back to concept](<#L18 — File Systems II>))*

## 10. xv6 Implementation Specifics (disjoint conceptual ↔ xv6)

> **Tags:** `xv6 fs.c` `xv6 namex` `xv6 ilock sleeplock` `xv6 hand over hand`
> `bget mutual exclusion` `inode cache size NINODE` `mkfs layout`

### 10.1 On-disk image (built by `mkfs.c`)

```
[ boot | super | log | inodes | bmap | data ]
```

- Inode region size from `sb.ninodes`; bmap from `sb.bmapstart`; data from `sb.size − sb.nblocks`.
- `mkfs` writes the **superblock**, allocates **root inode (inum=1) of type T_DIR**, links **"."** and **".."** into it, then loops adding user programs (`README`, `_cat`, `_ls`, …).

### 10.2 In-memory inode cache

- File `fs.c`. Fixed array of `NINODE` entries. Lookup is linear (small).
- `iget(dev, inum)`: scans cache; if hit → ++ref; if miss → recycle a `ref==0` slot, set `valid=0`, return.
- ⇒ `iget` performs **no I/O**; deferred to `ilock`.

### 10.3 `ilock(ip)` mechanics

- Acquires per-inode **sleeplock**.
- If `!ip->valid`: `bp = bread(ip->dev, IBLOCK(ip->inum))`; copy 64-byte dinode into struct inode; `brelse(bp)`; `ip->valid = 1`.
- If `ip->type == 0` panic (corrupted free inode).

### 10.4 `namex` ⇒ hand-over-hand in code

```c
ip = iget(ROOTDEV, ROOTINO);  // start at root
while ((path = skipelem(path, name)) != 0) {
    ilock(ip);
    if (ip->type != T_DIR) { iunlockput(ip); return 0; }
    next = dirlookup(ip, name, 0);   // returns iget'ed but UNLOCKED inode
    iunlockput(ip);                  // ★ release prev BEFORE locking next on next iter
    ip = next;
}
```

⚠ Subtle: xv6 actually **iunlockput**s the parent **after** `dirlookup` returns the (already iget'ed) child — so the next iteration's `ilock(ip)` is the "lock the next" half of HoH. Window is sometimes 1 (between `iunlockput` and next `ilock`) — still safe because `iget` pinned the child via refcount before parent was released.

### 10.5 Buffer cache & disk driver — **see file_systems1.md §12 / §11.** Quick recap:
- `bcache` = `NBUF`-entry doubly-linked LRU; flags `B_BUSY | B_VALID | B_DIRTY`; one `bcache.lock` + per-buf sleeplock.
- `bread` returns a locked, valid buffer; `brelse` moves to MRU head.
- **`log_write` replaces `bwrite`** in FS code — actual disk write deferred to `end_op` commit (L19/L20).

### 10.6 Tracing real I/O (`echo > a`, see L17 §13)

- `ialloc` → bread/log_write block 34 (inode block) ×2: once to mark non-free, once to set type/nlink/etc.
- `dirlink` → `writei` to parent dir's data block (e.g. 59) appending the dirent.
- `writei` for file data → `bmap` → `balloc` (mark data bitmap, e.g. block 58) → `log_write` data block (e.g. 613) → `iupdate` (writes inode block 34 with new size/addrs).

### 10.7 Lab4-fs hooks

- **Inode layout:** see §2.4 — fields at `0x0c` owner / `0x0e` perms shrink direct-block array to **11**, max file = 139 blocks ≈ 71 KB book → **8 MB target** in lab.
- **chown / chmod syscalls**: write `owner` / `perms` then `iupdate`.
- **Permission check** lives at `open()` / `namei()`; uses inode's `owner`/`perms` against `proc->uid`.
- **Login (`login_lib.c`)**: privileged code runs as UID 0, drops via `setuid` after authenticating against credential file. Hashing/encryption library provided.
- **Large-file extension**: replace last `addrs[]` entry with **double-indirect** to reach `11 + 128 + 128*128 = 16523 blocks ≈ 8.07 MB`, *without* growing dinode.

---

## 11. Quick Numerics Cheat Card

| Quantity | Book xv6 | Lab4-fs |
|---|---:|---:|
| `BSIZE` | 512 | 512 |
| dinode size | 64 B | 64 B |
| direct ptrs | 12 | **11** |
| indirect ptrs in 1 indirect blk | 128 | 128 |
| max blocks/file | 140 | **139** |
| max bytes/file | 71 680 | 71 168 (need double-indirect for 8 MB) |
| dirent size | 16 B (2+14) | 16 B |
| disk byte addr of inum | `2*512 + 64*inum` | same |
| Inode-block index | `IBLOCK(inum) = inum/IPB + sb.inodestart` | same |
| `IPB` (inodes per block) | `512/64 = 8` | 8 |

---

*End — file_systems2.md*

---

## L19 — FS Atomicity I — xv6

*([→ back to concept](<#L19 — FS Atomicity I>))*

## 9. xv6 Implementation (disjoint conceptual ↔ xv6)

> **Tags:** `xv6 logging` `xv6 log.c` `begin_op` `end_op` `log_write` `commit` `recover_from_log`
> `install_trans` `LOGSIZE` `MAXOPBLOCKS` `outstanding ops` `committing` `ilog.c`

> ⚠ L19 itself only sets up the *concept*. Full xv6 logging mechanics (`begin_op`, `end_op`,
> group-commit, `recover_from_log`) live in **L20 — File System Atomicity II**. This section
> records what's already visible in xv6 from prior labs/lectures so the conceptual section above
> stays disjoint.

### 9.1 xv6's choice — **logging**, **not** shadowing

xv6 implements **redo logging** (write-ahead log of *new* values), no shadowing.
Reasons (already implicit in slides 21–22):

- Disk image is small; can't afford 2× space.
- Multi-block ops (`create` touches inode block + dir block + bitmap + data) are common ⇒ multi-block atomicity is the killer feature.
- No snapshot requirement.

### 9.2 Where logging plugs into xv6 (as visible in L17/L18)

- **Disk image layout** *(`mkfs.c`)*:
  ```
  [ boot | super | log | inodes | bitmap | data ]
  ```
  The **log region** sits right after the superblock — `LOGSIZE` blocks (xv6: `30`).
- `superblock` records: `logstart`, `nlog`, `inodestart`, `bmapstart`, `nblocks`, `ninodes`.
- All FS code calls **`log_write(buf)`** instead of raw `bwrite(buf)` — this *appends* the change to the in-memory log header, deferring actual disk I/O to commit time.
- Every syscall touching the FS is wrapped:
  ```c
  begin_op();           // reserve log space; may sleep if log full
    ... ialloc, dirlink, writei, iupdate ... (each calling log_write)
  end_op();             // possibly triggers commit + install
  ```

### 9.3 What `log_write` *actually* does (preview)

- Locks `log.lock`.
- If block already in log header → no-op (absorption).
- Else add `b->blockno` to in-memory log header and `bpin(b)` so bcache won't evict it.
- ⇒ Real disk writes happen later in `commit()`:
  1. `write_log()` — copy each tracked buffer into log region on disk.
  2. `write_head()` — write log header **with `n` set** = **commit point** (the atomic bit-flip analog).
  3. `install_trans()` — copy log blocks to home locations.
  4. `write_head()` again with `n=0` — frees the log.

(*Step 2 is the analog of the shadow-bit flip from §5.*)

### 9.4 Recovery on boot — `recover_from_log()`

- Read on-disk log header.
- If `header.n > 0` ⇒ a transaction committed but maybe not installed ⇒ **redo install**, then zero the header.
- If `header.n == 0` ⇒ either no in-flight txn, or txn never committed ⇒ **discard** (do nothing — log entries were never authoritative).

This realizes the slide 23 "log supersedes FS" rule on the post-crash boot path.

### 9.5 Lab4-fs implication

- Lab4-fs adds **owner/perms** fields and (for the bonus) **double-indirect** addressing — *both* of these mutate `dinode` and **must go through `log_write`** for crash safety. Forgetting that = orphan inodes after a `make qemu` reboot.
- New syscalls (`chmod`, `chown`) MUST wrap their `iupdate` in `begin_op`/`end_op`.

---

## 10. Quick Recall Cheat Card

| Q | A |
|---|---|
| What does the disk give us? | `read`, `write` (not atomic, may reorder), `flush` (barrier) |
| Only primitive that reduces ordering cardinality? | **happens-before** (via `flush`) |
| Why `(n+k)! ≥ n!·k!`? | Pascal: `C(n+k, k) ∈ ℕ` ⇒ `(n+k)! = n!·k!·integer` |
| Two methods of FS atomicity? | **Shadowing** & **Logging (Journaling)** |
| Atomic point of shadowing? | The **shadow-bit flip** (1 block, 1 bit, atomic) |
| Storage cost of shadowing? | ≥ 2× — separate "current" and "shadow" copy |
| Disk schedule for one shadow update? | `{copy, mutate}  FLUSH  {flip-bit}` — 2 writes + 1 flush |
| Atomic point of logging? | The **commit record** write |
| Read rule under logging? | **Log supersedes FS** for any committed record |
| Why xv6 uses logging not shadowing? | Multi-block atomicity needed, no 2× space, no snapshot requirement |
| xv6's "atomic bit-flip" equivalent? | `write_head()` with `n>0` = commit |
| xv6 log region size? | `LOGSIZE = 30` blocks (book) |
| FS APIs that must wrap with `begin_op`/`end_op`? | Every FS-mutating syscall (create, write, unlink, link, mkdir, chmod-lab4, chown-lab4) |
| Use `bwrite` directly in xv6 FS code? | ❌ NEVER — always `log_write` |

---

*End — fs_atomicity1.md*

---

## L20 — FS Atomicity II — xv6

*([→ back to concept](<#L20 — FS Atomicity II>))*

## 16. xv6 Implementation — Concrete Mapping

> **Tags:** `xv6 logging` `log.c` `begin_op` `end_op` `log_write` `commit phase`
> `install_trans` `recover_from_log` `LOGSIZE` `MAXOPBLOCKS` `transaction` `superblock log header`

### 16.1 Where the log lives

- Disk image layout (from `mkfs.c`): `[boot | super | LOG | inodes | bitmap | data]`.
- **Log region** is a fixed range starting after the superblock (`sb.logstart`, `sb.nlog`).
- **Log header block** (block 0 of log region) records:
  - `n` — number of blocks in current transaction.
  - `block[]` — destination block numbers for each logged block.
- **Commit point = writing the header with `n > 0`.** Crash with header `n == 0` ⇒ nothing to replay.

### 16.2 The xv6 transaction API

| Call | Role |
|---|---|
| `begin_op()` | acquire log; wait if log near full |
| `log_write(b)` | mark buffer `b` for logging — replaces raw `bwrite`; copies into log slot in memory |
| `end_op()` | when last op exits, **commit**: writes log blocks → writes header (commit) → installs blocks → zeros header |

- All FS-mutating syscalls (`sys_unlink`, `sys_create`, `sys_write`, …) are wrapped in `begin_op() / end_op()`.
- This is the textbook **transaction-level + block-level granularity** of §13.

### 16.3 Commit phase order (xv6's `commit()` in `log.c`)

```
write_log()        // copy in-memory log buffers → log region on disk
write_head()       // CRC-less commit: write header with n>0  ← the commit point
install_trans()    // copy each logged block to its real home
write_head()       // header with n=0  ← clear the log
```

- This is **commit mechanism 1** (separate header block as commit). xv6 does **not** use checksum commit (Mech 2) — just relies on **single-block-write atomicity** of the header.
- `write_head()` writing `n=0` is the "**invalidate first entry**" trick of §5.3.

### 16.4 Recovery in xv6

- On boot, `initlog() → recover_from_log()`:
  - `read_head()` reads the log header.
  - If `n > 0` → **install_trans()** replays committed blocks.
  - `write_head()` zeros header → log clear.
- All replay ops are **idempotent** (just `bwrite(disk[block[i]], log[i])`).

### 16.5 What xv6 gives you

| Property | xv6 status |
|---|---|
| Atomicity (multi-block) | ✅ via header commit |
| Ordering | ✅ via in-order block install |
| Crash recovery | ✅ via replay |
| Idempotent replay | ✅ block-level overwrites |
| Checksum commit | ❌ (relies on single-sector atomicity for the header) |
| `fsync` distinction | ❌ — xv6 doesn't expose per-file `fsync` semantics; `end_op` is the only commit point |
| Multiple concurrent transactions | ❌ — global lock on log; `begin_op` may sleep |
| Log merging concurrent w/ writers | ❌ (simpler model — fully serial) |
| OCC-style `osync`/`dsync` | ❌ |

### 16.6 xv6 vs the design space (mapping)

| Concept (§) | xv6 implementation |
|---|---|
| Logging (§3) | `log.c` with header + log blocks |
| Commit Mech 1 (§4.1) | `write_head()` with `n>0` |
| Idempotent replay (§5.2) | `install_trans()` is plain `bwrite` |
| Atomic clear (§5.3) | `write_head()` with `n=0` |
| Recovery (§5.4) | `recover_from_log()` at boot |
| Granularity (§13) | block-level entries, transaction-level commit |
| Modern modes (§7) | xv6 ≈ **full journaling** (data and metadata both go through `log_write`) — but no concurrency, so HOL pain is hidden |
| `fsync` (§8) | **not exposed** — every syscall implicitly commits at `end_op` |
| User-level atomicity (§10) | unnecessary — `end_op` already atomic; but apps still can't get *cross-file* atomicity |
| OCC (§11) | absent — interesting extension exercise |

> **Takeaway:** xv6's design is a clean **Commit-Mechanism-1, full-journaling, block-granularity, single-transaction** point in the design space — perfect for teaching, but pays the HOL cost that real systems escape via *ordered mode* + *checksum commit* + (research) *osync/dsync*.

---

## L21 — Distributed Systems — xv6

*([→ back to concept](<#L21 — Distributed Systems>))*

## 14. xv6 Implementation — How the Course Touches Distributed Systems

> **Tags:** `xv6 distributed` `xv6 networking` `lab4 net` `xv6 paxos` `xv6 single node`
> `lab4 networking option` `xv6 limitations`

xv6 is **explicitly not a distributed OS** — it's a single-node teaching kernel. The course's **only direct contact with distributed-systems mechanics** is through Lab4-net (which lives at the *networking* layer, not the consensus layer). The sections above are conceptual; this section is about what xv6 actually does and doesn't.

### What xv6 has that's distributed-relevant
- **Lab4-net** — implements the **NIC driver + UDP/IP stack** in xv6. This gives xv6 nodes the *medium* over which a distributed protocol could be built (see networking.md for full details).
  - Provides `recv()` / `send()` for raw frames.
  - No retransmission, no congestion control, no consensus — bare hardware-level packet IO.
- **Locking primitives** (`spinlock`, `sleeplock` — see concurrency2.md) — the *single-node analogue* of the synchronization that distributed consensus replaces with messages.
- **fork-style replication** — only spatial (within one machine), not across nodes.

### What xv6 deliberately does NOT have
- No Paxos / Raft / consensus library.
- No leader election.
- No notion of replication, quorum, or partition handling.
- No vector clocks, no Lamport timestamps.
- No RPC framework (you'd have to build it on top of Lab4-net's UDP).
- No CAP-style replication store — the FS is local-disk only.

### How Lab4-net relates conceptually
- Lab4-net builds the **unreliable channel** that the Two Generals problem operates on.
- If you wanted to extend xv6 into a real distributed system, you'd:
  1. Build an RPC layer over Lab4-net's UDP sockets.
  2. Implement a consensus library (Paxos or Raft) on top of that.
  3. Replicate the **filesystem journal** (file_systems2.md, L19/L20 atomicity) across N xv6 instances.
  4. Wire `sys_write` etc. to go through the consensus log before committing.
- This is essentially the **path from xv6 → a distributed FS like GFS/HDFS/Spanner**, sketched in lecture form.

### Why xv6 stops where it does
- The instructional point of xv6 is to expose **single-node OS mechanism** (paging, scheduling, FS, concurrency).
- Distributed mechanism is a **separate course** worth of material (CS6210, CS7210 at GT).
- L21 is a **conceptual capstone** — it shows you that *the same abstractions* (sharing, multiplexing, isolation) recur at the cluster scale, but the **mechanisms** (message passing, quorums, consensus) are fundamentally different from what xv6 implements.

### One-line summary for xv6
> xv6 gives you the **NIC and the spinlock**; distributed systems theory tells you that even with both, **agreement is hard**, and Paxos/Raft/Dynamo are the engineering responses to FLP and CAP.

---

## L22 — Efficient AI Stack — xv6

*([→ back to concept](<#L22 — Efficient AI Stack>))*

## 18. xv6 / Course-Code Connection

> **Tags:** `xv6` `xv6 connection` `not in xv6` `course code` `lab connection`

This lecture is a **research talk** and is **not implemented in xv6**. There is no SuperServe code in the xv6 tree. However, the conceptual machinery generalises to several xv6 mechanisms students have already seen:

- **EDF + slack-based scheduling** generalises the round-robin scheduler in `xv6/kernel/proc.c` (`scheduler()`). xv6 uses *unweighted RR* — no deadlines, no slack. To turn xv6 into a SuperServe-style system you would:
  - Add a `deadline` field to `struct proc`.
  - Replace the RR loop with an EDF priority queue.
  - Compute slack as `deadline − ticks` in `scheduler()` and let the policy pick a "subnet-equivalent" workload variant.

- **Weight sharing / one-blob-many-views** is structurally analogous to **xv6 fork's COW page sharing** (vm3.md, `uvmcopy`/`cowfault`): one physical resource (page / supernet weights) is multiplexed across many logical consumers (processes / subnets) until divergence is needed.

- **Fast switching** is the same idea as **fast context switching** in `swtch.S` — make the act of changing what's running cheap enough that you can do it often. xv6 makes context switching ~µs cheap; SubNetAct makes *model* switching ~µs cheap.

- **Batching vs latency** is the same trade-off as **disk request batching** in `bio.c` and the FS log (fs_atomicity1.md): batch up writes for throughput at the cost of per-request latency. SlackFit just generalises this with deadlines.

- **Profiler-driven decisions** is structurally similar to the FS layer's static block-cache sizing: pre-measure offline, decide online from the table.

In short: SuperServe is what you'd get if you took xv6's **scheduler + COW + buffered I/O** ideas and pointed them at GPU-resident DNNs with deadlines.

---

## 19. Quick-Reference Glossary

| Term | Definition |
|---|---|
| **R1, R2, R3** | Latency-SLO attainment, Accuracy, Resource efficiency |
| **SLO** | Service-Level Objective — deadline a query must meet |
| **CV²ₐ** | Squared coefficient of variation of inter-arrival times; >1 = bursty |
| **λ** | Mean ingest rate (QPS) |
| **MAF** | Microsoft Azure Functions trace — canonical bursty workload |
| **Subnet (φ)** | A specific architectural slice of the supernetwork |
| **Supernetwork** | Single network whose subnets share weights; trained by NAS |
| **SubNetAct** | Mechanism that activates a subnet in-place (<1 ms) |
| **SlackFit** | Online scheduler picking (B, φ) from Pareto-optimal subnets via slack |
| **Slack** | Time remaining for the most urgent queued query (= deadline − now) |
| **EDF** | Earliest-Deadline-First scheduling |
| **Cold start** | Latency penalty when loading a model from CPU/disk to GPU |
| **Pareto-optimal subnet** | Subnet not dominated in (latency, accuracy) by any other |
| **NAS** | Neural Architecture Search — produces the supernetwork |
| **Gen1 / Gen2 / Gen3** | Static-single (Clipper) / Coarse-auto (InFaaS) / Fine-reactive (SuperServe) |

---
