Tomasulo's Algorithm

Since renaming has solved WAW and WAR dependencies, we can start executing out of order and correct for any RAW dependencies.

- **Branch prediction** removes (most of) the control dependences
- **Register renaming** removes WAR/WAW (name) dependences
- → execute out of order to exploit the available **ILP**

**Tomasulo's Algorithm**

- Used in the **IBM 360/91** (1960s)
- Tracks when operands are available → satisfies data (RAW) dependences
- Removes name dependences through register renaming
- Almost all modern high-performance processors use a derivative → much of the terminology survives today

## Hardware

**Instruction Buffers**

- Holds fetched instructions in order within a buffer
- Feeds instructions into reservation stations and specialized buffers
- Act as a queue, oldest dispatch first

**Reservation Station**

- Holds an instruction in a buffer, waiting to receive the operands (from registers or the CDB)
- After getting operands, runs through execution unit (alu, mux, etc.)

**Register Alias Table**

- Holds where the newest value for each register will come from
- Points to either a register in hardware, or an ID to a reservation station

**Register File**

- Where values are actually held

![[Pasted image 20261008200614.png|500]]

- Example setup:
    - **Adder** RSs: A1–A3 (IDs 1–3)
    - **FP-Cmplx** RSs: C1–C2 (IDs 4–5)
    - RAT entry `0` → value is in the register file; nonzero → ID of the RS that will produce it

## Operations

### Issue

- Get next instruction from instruction queue
- Find a free reservation station for it (wait if there are none)
- Read operands that are in the register
    - If the operand is not in the register, find the reservation station that will produce it The reservation station IDs are essentially treated as temporary names

![[Pasted image 20261008200821.png|500]] RAT points to index 4 for F1, meaning it isn't ready yet in register file, but it'll be ready at ID=4 (C1 reservation station)

- Issue to-do list:
    1. Get next inst from IBs
    2. Find free RS
    3. Read operands from RF
    4. Record source (RS ID) of the other operands
    5. Update RAT → dest reg now points to this RS

### Execute

- Monitor results as they're produced
- Put a result into all reservation stations waiting for it
- When all operands are available for an instruction we can execute it
- If there are several ready instructions in one functional unit, pick one (oldest first heuristic); load/store are the exception and must stay in order ![[Pasted image 20261008201249.png|500]]
- Execute to-do list: monitor results from ALUs → capture matching operands → compete for ALUs
- **>1 ready inst for the same unit**
    - Common heuristic: **oldest first**
    - Optimal is impossible: **precedence-constrained scheduling is NP-complete**
        - …and that assumes you have access to the entire dependence graph
    - Choice only affects **performance, not correctness**
- **Load/store** must be done in proper order → avoids hazards through memory (later lecture)

### Write

- Once a result is completed, put it on a common data bus (CDB) where a reservation station can pick it up
- Store writes to memory
- Result stored in register file
- Free the reservation station ![[Pasted image 20261010145638.png|500]]
- Write to-do list: broadcast on CDB → writeback to RF → update mapping → free RS
- Freeing the RS **recycles the temporary name**
    - → future instructions find the value in the actual register again (until it's renamed again)
- **Only update RAT (and RF) if the RAT still contains your mapping!**
    - A newer instruction may have renamed the same reg → RAT holds _its_ RS ID
    - Overwriting would clobber the newer mapping → still broadcast on CDB so waiting RSs capture it

### Load/Store

- RSs take care of dependences **through registers**
- Dependences also possible **through memory**
- Original IBM 360: loads and stores **not reordered**
- Load-store reordering → later lecture

## Detailed Example

|Unit|Latency|
|---|---|
|Load|2|
|Add|2|
|Mult|10|
|Divide|40|

- Initial: `R2 = 100`, `R3 = 200`, `F4 = 2.5`
- RSs: LD1–LD2, AD1–AD3, ML1–ML2

```asm
1. L.D   F6, 34(R2)
2. L.D   F2, 45(R3)
3. MUL.D F0, F2, F4
4. SUB.D F8, F2, F6
5. DIV.D F10, F0, F6
6. ADD.D F6, F8, F2
```

- RS fields: `Busy`, `Op`, `Vj`/`Vk` (operand values), `Qj`/`Qk` (RS that will produce a missing operand), `A` (address info for loads)
- **Register Status** row = the RAT (reg name → value in RF, RS name → pending)

|Cycle|Event|Register Status|
|---|---|---|
|1|Issue L.D F6 → LD1 (offset 34, R2 = 100)|F6 → LD1|
|2|Issue L.D F2 → LD2 (offset 45, R3 = 200); LD1 executes|F2 → LD2|
|3|Issue MUL.D → ML1: F4 = 2.5 read, F2 waits on LD2; LD2 executes|F0 → ML1|
|4|LD1 writes F6 = 10.5 (LD1 freed); issue SUB.D → AD1: captures F6 = 10.5, F2 waits on LD2|F6 → RF, F8 → AD1|

Final:

|Instruction|Is|Ex|Wr|
|---|---|---|---|
|1. L.D F6, 34(R2)|1|2|4|
|2. L.D F2, 45(R3)|2|3|5|
|3. MUL.D F0, F2, F4|3|6|16|
|4. SUB.D F8, F2, F6|4|6|8|
|5. DIV.D F10,F0, F6|5|17|57|
|6. ADD.D F6, F8, F2|6|9|11|

## Timing Example

- Simplified version: track **only timing** → much faster by hand (exams)
- Rules (from the worked numbers):
    - **Is**: in order, 1/cycle — **don't forget to check RS availability!**
    - **Ex**: cycle after issue, or cycle after the last source's `Wr` (whichever is later)
    - **Wr**: `Ex + latency`
- Trap: slides first guess DIV Ex = `6?` and ADD Ex = `7?` → wrong, operands not ready yet

|Instruction|Is|Ex|Wr|Comment|
|---|---|---|---|---|
|1. L.D F6, 34(R2)|1|2|4||
|2. L.D F2, 45(R3)|2|3|5||
|3. MUL.D F0, F2, F4|3|6|16|waits F2 (Wr 5)|
|4. SUB.D F8, F2, F6|4|6|8|waits F2 (Wr 5)|
|5. DIV.D F10,F0, F6|5|17|57|waits F0 (Wr 16)|
|6. ADD.D F6, F8, F2|6|9|11|waits F8 (Wr 8)|

## Conflict Example

- Careful: keep track of **all** the resources

|Unit|Latency|
|---|---|
|Load|2|
|Add|1|
|Mult|4|
|Divide|40|

```asm
1. L.D   F6, 34(R2)
2. ADD.D F2, F0, F10
3. SUB.D F0, F6, F4
4. MUL.D F8, F2, F6
5. L.D   F10, 28(R4)
6. ADD.D F6, F4, F12
```

|Instruction|Is|Ex|Wr|
|---|---|---|---|
|1. L.D F6, 34(R2)|1|2|4?|
|2. ADD.D F2, F0, F10|2|3|4?|
|3. SUB.D F0, F6, F4|3|||

- L.D and ADD.D both want to write in cycle 4 → only one CDB → conflict (`?`), one must wait