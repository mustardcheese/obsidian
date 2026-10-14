## Instruction Level Parallelism (ILP)

**Basic Idea**: Execute several instructions in parallel

We already have pipelining, but only push out at most 1 instruction/cycle We want multiple instructions per cycle

- Gets complicated → more transistors/logic
- That's how we got from the 486 (pipelined) → Pentium and beyond

ISA currently defines instruction execution one at a time

- I1: ADD R1 = R2 + R3
    - Fetch instruction
    - Read R2 and R3
    - Do the addition
    - Write R1
    - Increment PC
- Repeat for I2, etc.

Pipelining _already_ breaks the "rules"

- We fetch I2 before I1 has finished

Parallelism exists in that we perform different operations (fetch, decode, …) on several different instructions in parallel

- Still limited to 1 IPC

Instructions must stay "correct", but what's correct?

- Defined by the ISA
- Same processor state as if they were executed one a t a time
    - State = registers, PC, memory
- Can **squash** instructions that don't correspond to "correct" execution
    - e.g. misfetched instructions after a taken branch, instructions after a page fault

**Toll booth analogy**: caravan of cars (D C B A) must stay in order

- Single lane → in order, but slow (everyone waits on each car)
- Two lanes in parallel → faster, and if they regroup in order after the booth, "you didn't see that"

### Illusion of Sequentiality

So long as everything looks OK from the outside, you can do whatever you want!

- Outside appearance = "Architecture" (ISA)
- Whatever you want = "Microarchitecture"
    - μArch = everything not explicitly defined in the ISA
    - Pipelining, caches, branch prediction, etc.

**Simple ILP**

- Read and decode instructions each cycle
    - Can't execute > 1 IPC if we're not fetching > 1 IPC
- If instructions are independent, do them at the same time
- If not, do them one at a time ![[Pasted image 20260909163141.png|450]]

**Example: Original Pentium**

- Fetch: up to 32 bytes
- Decode1: decode up to 2 instructions
- Decode2 (×2): read operands, check dependencies
- Execute (×2), Writeback (×2)

**Superscalar** "Scalar" CPU executes one instruction at a time

- Includes pipelined processors "Vector" CPU executes one instruction at a time, but on vector data
- X[0:7] + Y[0:7], one instruction with 8x data, would need 8 scalar processors "Superscalar" CPU executes more than one unrelated instruction at a time
- e.g. `ADD X + Y` and `MUL W * Z` together

## Scheduling

The biggest problem is to find where "legal" (independent) parallelism exists

In Pentium, decode stage checks for multiple conditions

- Data dependency
    - Does one instruction generate a value needed by the other?
    - Do both instructions write to the same register?
- Resource conflict
    - Most CPUs only have one divider → two divides can't execute at the same time

How many instructions do we look for?

- 3-6 is typical today
- A cpu that can ideally do N instructions per cycle is "N-issue superscalar", "N-way", "N-issue", "N-wide"
    - N is known as the issue width
    - "Ideally" = **peak** execution bandwidth

### Example: 2-issue single-cycle in-order

- Already fetched + decoded; execute up to 2 at a time, **in program order only**

```
I1: ADD R1, R2, R3
I2: SUB R4, R1, R5
I3: XOR R6, R7, R8
I4: SW  R6, 0(R4)
I5: MUL R6, R5, R9
I6: ADD R7, R1, R6
I7: SLR R6, R1, R4
```

|Inst|Cycle|Why|
|---|---|---|
|I1|1||
|I2|2|RAW on R1 (I1)|
|I3|2||
|I4|3|RAW on R6 (I3), R4 (I2)|
|I5|3||
|I6|4|RAW on R6 (I5)|
|I7|4||

→ 7 insts in 4 cycles (CPI = 0.57)

### Example: 3-issue single-cycle in-order

- Same code, up to 3 at a time, still in order
- I1 = cycle 1; I2, I3 = cycle 2; I4, I5 = cycle 3; I6, I7 = cycle 4
    - I5 can't join I2/I3 in cycle 2: it writes R6, which I3 writes (WAW) and I4 still needs to read (WAR)
- → **Still** 7 insts in 4 cycles; wider issue alone didn't help

From here, we can reorder instructions based on data dependencies ![[Pasted image 20260914153336.png|500]]

- I3 can move up to cycle 1
- I5 _could_ go in cycle 1 based on its inputs, but must wait until cycle 3 (would overwrite R6 before I4 uses it)

Seems good, but still stuck at 7 instructions in 4 cycles. **Can we go faster?**

## Dependencies

Data Dependencies

- RAW: Read-After-Write (True Dependence) need to wait for value to update
- WAR: Anti-Dependence need to consume value before writing
- WAW: Output Dependence instructions cannot be reordered since order needs to stay consistent

Control Dependence

- When instructions depend on outcome of a previous jump
- We already know how to solve: prediction and predication

### Data Dependencies

**Register Dependencies

- RAW, WAR, WAW based on register *number
- Register names known at **decode**

**Memory Dependencies**

- Based on _address_
- Harder, since memory address not known until execute

![[Pasted image 20260914155536.png|550]]

### Types of Data Dependencies

(A comes before B in program order)

**RAW** (true dependency): A writes a location, B reads it

```
A: R1 = R2 + R3
B: R4 = R1 * R4
```

**WAR** (anti-dependence): A reads a location, B writes it

- If B executes before A reads → A's operand is lost

```
A: R1 = R3 / R4
B: R3 = R2 * R4
```

**WAW** (output dependence): A and B write the same location

- If B writes first, then A → location ends with the wrong value

```
A: R1 = R2 + R3
B: R1 = R3 * R4
```

### Impact of Ignoring Dependencies

Start: R1 = 5, R2 = -2, R3 = 9, R4 = 3

|Dep|A → B (correct)|B → A (reordered)|
|---|---|---|
|RAW|R1 = 7, R4 = 21|R4 = 15 ✗, R1 = 7|
|WAR|R1 = 3, R3 = -6|R3 = -6, R1 = -2 ✗|
|WAW|R1 = 27|R1 = 7 ✗|

## Hazards

Hazards are when dependent instructions occur close enough that it changes the outcome of the program (for a given microarchitecture). Not all dependencies lead to hazards, however

Dependencies are a property of the program Hazards are when dependencies cause issues during execution

- Hazards = code **AND** hardware

Data Dependency -> Data Hazard, but it depends on the processor

Some processors cannot have hazards (the dependencies still exist in the code), like a one-at-a-time processor. Nearly every processor will have some kind of dependency that doesn't necessarily manifest into a hazard. In practice the hazards don't happen.

### False Dependencies

A dependency that we can do something about.

They happen because: **there's a finite number of registers**

- At some point, you're forced to overwrite some value somewhere
    - Most RISC: 32 registers, x86: only 8, x86-64: 16
- WAR and WAW are also "name dependencies" because the data is still _somewhere_ but under different names
- Thought exercise: what if you had infinite registers?

Why not add more registers?

- We'd still run out anyways, and while it helps, it will never resolve fully the problem
- Not a scalable solution
- All code needs to be recompiled
- Changing ISA can break lots of compatability
    - x86-64 _did_ add registers, but in a mostly backwards-compatible way

![[Pasted image 20260914160826.png|500]]![[Pasted image 20260914160842.png|500]]

- **Eliminating WAR**: write B's result to a different register
    - `B: R3 = R2 * R4` → `B: R5 = R2 * R4` → reordering B before A still gives correct R1 = 3
- **Eliminating WAW**: same fix
    - `A: R1 = R2 + R3` → `A: R5 = R2 + R3` → either order gives R1 = 27

**Reuse is Inevitable**

- Loops, functions, etc all have to reuse registers
- Loops: writing R1 in a loop body → R1 reused every iteration → many false deps
    - **Loop unrolling** helps a little, but you still run out of registers; trade-off with code bloat
- Function calls: if `printf` writes R1, every call reuses R1
    - **Inlining** helps a little for short functions (same caveats)

**Solution: HW Register Renaming**

- Have temporarily more registers than specified by the ISA
- Temporarily map ISA registers to physical registers to avoid overwrites
    - ISA registers = **"logical"** or **"architected"** registers Components:
- Mapping Mechanism
- Physical Registers
    - Allocated vs. free registers
    - Allocation/deallocation mechanism

## Register Renaming

![[Pasted image 20260914161404.png|500]]

```
I1: ADD R1, R2, R3
I2: SUB R2, R1, R5     ; RAW on R1 (I1)
I3: AND R5, R11, R7    ; WAR on R5 (I2)
I4: OR  R8, R5, R2
I5: XOR R2, R4, R11    ; WAW on R2 (I2)
```

- I3 can't exec before I2 → I3 would overwrite R5 before I2 reads it
- I5 can't go before I2 → I2 would later overwrite R2 with a stale value

We can give I3 a temporary name/location _S_ for the value it produces

- I4 also uses that temporary value
- Subsequent uses and writes are changed
    - All uses of R5 from I3 until the next write to R5 → S WAW can be removed by changing R2 in I5 to _T_
- (and in subsequent instructions)

![[Pasted image 20260914161647.png|250]]

How can we implement register renaming?

- Need space for S, T, etc.
- How do we know when to rename a register?

The simple solution is to do renaming for every instruction. We can change the name of a register each time we decode an instruction that will write to it and remember the name we gave to it.

## ILP

- Arrange instructions based on dependencies (dataflow graph)
- **ILP = # instructions / longest path**

```
I1: R2 = 17
I2: R1 = 49
I3: R3 = -8
I4: R5 = LOAD 0[R3]
I5: R4 = R1 + R2
I6: R7 = R4 - R3
I7: R6 = R4 * R5
```

- Longest path = 3 (e.g. I3 → I4 → I7) → ILP = 7/3 ≈ 2.33

### Dynamic (Out-of-Order) Scheduling

```
I1: ADD R1, R2, R3
I2: SUB R4, R1, R5
I3: AND R6, R1, R7
I4: OR  R8, R2, R6
I5: XOR R10, R2, R11
```

- Cycle 1: operands ready? I1, I5 → start I1, I5
- Cycle 2: operands ready? I2, I3 → start I2, I3
- **Window size (W)**: how many instructions ahead we look
    - Don't confuse with **issue width (N)**
    - e.g. 4-issue OOO processor can have a 128-entry window (looks at up to 128 insts at a time)

### ILP in a Loop

```c
p = list_head;
double sum = 0.0;
while(p)
{
    double val = p->f;
    val = val * val;
    sum += val;
    p = p->next;
}
sum = sqrt(sum);
```

```
        ; Loop Prologue
(P1)    LUI  R1, R0, 0xC738
(P2)    ORI  R1, R1, 0x4200   // p = list_head
(P3)    SUB  F2, F2, F2       // sum = 0.0
(P4)    BEQZ R1, bottom       // while(p)
top:    ; Loop Body
(1)     LOAD F3, 0[R1]        // val = p->f
(2)     FMUL F3, F3, F3       // val*val
(3)     FADD F2, F2, F3       // sum += val
(4)     LOAD R1, 8[R1]        // p->next
(5)     BNEZ R1, top          // while(p)
bottom: ; Loop Epilogue
(E1)    SQRT F2, F2           // sqrt(sum)
```

### Ordering?

- In the OOO example, I5 executed before I2, I3, and I4!
- How to maintain the **illusion of sequentiality**?

Toll booth: 4 cars take 5s, 5s, 30s, 5s (3rd car pays with a $100 bill)

|Booth|Total time|
|---|---|
|One-at-a-time|45s|
|"4-issue" toll booth (OOO)|30s|

### ILP != IPC

- **ILP** = attribute of the program
    - Also depends on ISA and compiler
    - e.g. SIMD, FMAC can change instruction count and shape of the dataflow graph
- **IPC** = depends on the actual machine implementation
    - ILP is an **upper bound** on IPC
    - Achievable IPC depends on instruction latencies, cache hit rates, branch prediction rates, structural conflicts, window size, etc.
- Next several lectures → how to build a processor to exploit ILP