OS have a three stage boot procedure **BIOS/UEFI → Bootloader/Bootblock → Kernel**

- If it weren't for the bootloader, ever kernel would have to find a way to boot onto every type of hardware
- The bootloader acts as a common middleman to interact with hardware (BIOS) and software (kernel)

# Handover Protocols

## BIOS

### Reset Vector

![[Pasted image 20260309140116.png|200]] The Reset Vector is a **hardwired CPU behavior** (baked into silicon, not software-configurable) that sets the **instruction pointer (IP) to a specific address** pointing to the top 16 bytes of the address space.

- Hardcoded entry point into the code
- I386: IP → (4GB - 16B) = (0xFFFFFFF0)
- I286: IP -> (1MB - 16B) = (0xFFFF0)

**Note**: The top of the address space is 0xFFFFFFFF, leaving just 16 bytes worth of executable address space. Every architecture will _always_ have these 16 bytes available. This is solely used to perform the jump/longjump to execute code in BIOS/UEFI ROM. The ROM chip's last 16 bytes are physically mapped to this address — this is a hardware contract between the CPU and motherboard designer.

```nasm
0xfffffff0: ljmp $0xf000,$0xe05b
```

_the longjump instruction that fits in that 16 byte space_

### 16-Bit Real Mode

For compatability reasons, every x86 processor will boot in a 16-bit 'real' mode

- 16 bit processor w/ 16 bit registers
- When in 16-bit mode, it has access to a 20-bit address space

The physical address for a ljump is calculated as CS << 4 + IP

- CS, _the code segment_, 16 bits, bitshifted by 4 allows 20 bits to be used
- 0xF000 << 4 == 0xF0000
- 20-bit usable address space in 16-bit mode
- $2^{20}$ = 1MB addressable physical address space

```nasm
0xfffffff0: ljmp $0xf000,$0xe05b
```

CS = 0xF000 IP = 0xE05B

CS << 4 = 0xF0000 (CS << 4) + IP = 0xFE05B IP <- 0xFE05B ![[Pasted image 20260309145732.png|500]]

IVT: interrupt handling is done directly via the IVT (later it will be the IDT interrupt descriptor table)

#### Address Line Trick (active only from power-on until first ljmp)

The top 12 bits (0xFFF) are set high upon power on by **hardware** (not the CPU itself).

- Power On
- 16-bit CPU computes address 0xFFFF0, but hardware forces top 12 address bus lines high → physical bus sees 0xFFFFFFF0
- Ljump held at 0xFFFFFFF0 (in high ROM mapping) executes
- **Address line forcing permanently stops** after this first ljmp
- CPU is now in true real mode, jumps to 0x000FE05B (in low ROM mirror)

#### Why Two ROM Mappings?

The same physical ROM chip is mapped at two address ranges by the chipset:

- **High mapping** (0xFFFE0000–0xFFFFFFFF): 128KB ROM at top of 4GB. Used solely for the reset vector fetch at power-on.
- **Low mapping/mirror** (0xF0000–0xFFFFF): 64KB alias in the 1MB real-mode space. Needed because after the ljmp, the CPU can only address 1MB and must continue executing BIOS code.

Both mappings are necessary — high for reset vector, low for continued BIOS execution. Neither is redundant. The high mapping keeps the ROM out of valuable low memory for when the OS later takes over in protected mode.

### 32-bit Mode

BIOS actually starts at a high memory location 0xFFFFFFFF - 0xFFFE0000, 128kb ROM

- Because of real mode we only execute in the 20-bit mode, but the rest still exists unused ![[Pasted image 20260309152101.png|600]]

---

## Bootblock/Bootloader

### BIOS-to-Bootloader Handover

The handover is simple compared to the reset vector — no hardware tricks:

1. BIOS reads first 512 bytes from boot device (disk sector 0)
2. BIOS verifies boot signature (last two bytes must be 0x55AA)
3. BIOS copies those 512 bytes into RAM at 0x7C00
4. BIOS jumps to 0x7C00:

```
jmp 0x7c00
```

The address 0x7C00 is a **convention** — chosen decades ago to leave room for the stack and stay clear of the IVT and BIOS data area.

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

**Bring the CPU state into a sane state, and disable interrupts so bootloader isn't hindered by interrupts from BIOS.**

We switch from real mode to protected mode. **Move from only physical memory addresses to virtual address mapping.**

### Registers

![[Pasted image 20260309152612.png|500]]

a — accumulator b — base c — count d — data si — source index di — destination index bp — base pointer sp — stack pointer ip — instruction pointer E prefix for 32-bit R prefix for 64-bit