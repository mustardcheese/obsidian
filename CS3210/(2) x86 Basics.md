OS have a three stage boot procedure
**BIOS/UEFI → Bootloader/Bootblock → Kernel**

- If it weren’t for the bootloader, ever kernel would have to find a way to boot onto every type of hardware
- The bootloader acts as a common middleman to interact with hardware (BIOS) and software (kernel)

# Handover Protocols

## BIOS
### Reset Vector
![[Pasted image 20260309140116.png|200]]
The Reset Vector sets the **instruction pointer (IP) to a specific address** pointing to the top 16 bytes of the address space.
- Hardcoded entry point into the code
- I386: IP → (4GB - 16B) = (0xFFFFFFF0)
- I286: IP -> (1MB - 16B) = (0xFFFF0)

**Note**: The top of the address space is 0xFFFFFFFF, leaving just 16 bytes worth of executable address space. Every architecture will *always* have these 16 bytes available. This is solely used to perform the jump/longjump to execute code in BIOS/UEFI ROM. 

```nasm
0xfffffff0: ljmp $0xf000,$0xe05b
```
*the longjump instruction that fits in that 16 byte space*

### 16-Bit Real Mode
For compatability reasons, every x86 processor will boot in a 16-bit 'real' mode
- 16 bit processor w/ 16 bit registers
- When in 16-bit mode, it has access to a 20-bit address space

The physical address for a ljump is calculated as CS << 4 + IP
- CS, *the code segment*, 16 bits, bitshifted by 4 allows 20 bits to be used
- 0xF000 << 4 == 0xF0000
- 20-bit usable address space in 16-bit mode
- $2^{20}$ = 1MB addressable physical address space

```nasm
0xfffffff0: ljmp $0xf000,$0xe05b
```
CS = 0xF000
IP = 0xE05B

CS << 4 = 0xF0000
(CS << 4) + IP = 0xFE05B
IP <- 0xFE05B
![[Pasted image 20260309145732.png|500]]

IVT: interrupt handling is done directly via the IVT (later it will be the IDT interrupt descriptor table)

The top 12 bits (0xFFF) are set high upon power on due to the CPU being in 16-bit mode.
- Power On
- 16-bit CPU fetches 0xFFFF0, but in a 32-bit system the top 12 are set high without the CPU 'knowing' -- 0x(FFF)FFFF0
- Ljump held at 0xFFFFFFF0 executes
- CPU *actually* jumps to 0x000FE05B via CS + IP calculation
### 32-bit Mode

BIOS actually starts at a high memory location 0xFFFFFFFF - 0xFFFE0000, 128kb ROM
- Because of real mode we only execute in the 20-bit mode, but the rest still exists unused
![[Pasted image 20260309152101.png|600]]
---

## Bootblock/Bootloader
Handed off from BIOS by jumping to memory location:
```
jmp 0x7c00
```

What does the Bootblock do?
- The CPU is in a state of 16-bit real mode after BIOS
- The memory subsystem is at a very barebones state
    - Only physical addressing memory
    - No virtual memory usage yet

**Bootblock Setup**
- x86 registers (states)
- Memory referencing model
- Switch processor to 32 bit protected mode
- BIOS features (memory aliasing)

**Bring the CPU state into a sane state, and disable interrupts so bootloader isn’t hindered by interrupts from BIOS.**

We switch from real mode to protected mode. **Move from only physical memory addresses to virtual address mapping.**

### Registers

![[Pasted image 20260309152612.png|500]]

a — accumulator
b — base
c — count
d — data
si — source index
di — destination index
bp — base pointer
sp — stack pointer
ip — instruction pointer
E prefix for 32-bit
R prefix for 64-bit