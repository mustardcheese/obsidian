## Problems with Tomasulo

### (1) RS does two jobs

- RS used for both:
    - **Scheduling** instructions (operands ready)
    - **Name** for register renaming (remove false deps)
- Scheduling makes RS expensive
    - Associative logic for CDB updates, opcode, operands, etc.
    - All of this only needed _before_ the inst begins executing
- But RS can't be freed when the inst starts executing → only when it **completes**
    - Still need the temporary name to broadcast the result
- Fix → **separate register renaming from RS**

### (2) Out-of-order completion

- Instructions complete out of order → exceptions and branch mispredictions hard to recover from
- Reorder only if results are the same → must **finish instructions in program order**

|Instruction|Is|Ex|Wr|
|---|---|---|---|
|`DIV.D F10, F0, F6`|1|2|42|
|`L.D F2, 45(R3)`|2|3|5|
|`MUL.D F0, F2, F4`|3|6|16|
|`SUB.D F8, F2, F6`|4|6|8|

- Divide-by-zero detected in cycle 41 → later insts have already written F2, F0, F8

The ROB separates architectural (ISA) registers from physical registers. It also enables in-order completion or "commit"

Circular Queue of updated values

![[Pasted image 20261010193612.png|600]]

### ROB Fields

- Type: ALU, op, load, store, branch
- Dest: Which architected register to update
- Value
- Fin: Set when the result has been written back
- Head pointer

## "Stages"

### Issue

- Read instruction from instruction buffer
- Check if resources are available:
    - RS has open slots
    - ROB has open slots
    - **Stall issue** if any needed resource isn't available
- Read RAT, read available sources, Update RAT
- Write to RS and ROB

### Execute

- Wait for operands to arrive
- Compete to use functional unit
- Execute
- (Same as before in Tomasulo)

### Write Result

- Broadcast result on CDB (any dependents will take value)
- Write result into ROB entry
    - ARF only holds "official" register state
        - Only updated **in program order**
    - Mark ready/finished bit in ROB once ready
- Reservation station can be freed

### Commit

When an instruction is the oldest in the ROB (head points to it):

- Write result (if ready/finished bit is set)
    - to ARF if register
    - to mem if store
    - Q (from slides): what about loads?
- Advance ROB to next instruction
- Commit is what the outside world sees → and it's all **in-order**
    - Insts execute out of program order, but the outside world still "believes" it's in-order

![[Pasted image 20261010212350.png|500]]

## Register Renaming

Now, the ROB serves as the temporary name instead of reservation station

- Freed at commit, so no issue
- Reservation stations get freed faster ![[Pasted image 20261010212602.png|500]]

### RAT Update

- Update ARF as usual
- Move ROB head pointer
- Check if the RAT is pointing to the current ROB entry
    - If not, continue as normal, **don't touch the RAT**
    - If yes, update the RAT

![[Pasted image 20261011141725.png|500]] At ROB17, we shouldn't update the RAT to ARF yet, because another write needs to happen (ROB42) before we can update. After ROB42 finishes, then RAT can be set to ARF.

### Timing

|Instruction|Is|Exec|Wr|Commit|
|---|---|---|---|---|
|`DIV R2, R3, R4`|1|2|42|43|
|`MUL R1, R5, R6`|2|3|13|44|
|`ADD R3, R7, R8`|3|4|5|45|
|`MUL R1, R1, R3`|14|15|25|46|
|`SUB R4, R1, R5`|15|26|27|47|
|`ADD R1, R4, R2`|16|43|44|48|

- Write-backs are out of order, commits are in order (one per cycle)
    - Everything waits behind the DIV → nothing commits until 43

## Unified Reservation Stations

- Problem with separate RSs: if MULT RSs are full → must stall, even if ADD RSs are free
    - RS count per ALU would need to match the program's inst distribution
    - Different programs have different distributions
- Unified RS (e.g. 5 entries) → can hold 5 adds, 5 muls, or any combination

We can unify the reservation station, and allow the execution units to simply choose which RS entry to pick from

- Arbiters decide which instructions get executed by which type of unit

Ready ADDs would fight for the same execution unit and same with MULs Arbiter logic picks instructions to execute

- Arbitration and execution paths a little more complex (not too bad)
- For **N functional units** → RS needs **N read ports**
![[Pasted image 20261012142209.png|500]]
## Superscalar

Tomasulo + ROB can only execute OoO but not superscalar

- Sustained throughput of only 1 IPC
- Need superscalar fetch, decode, etc
- Only one CDB so only one instruction per cycle can write-back result to ROB
- Commits are only 1 IPC

**To Reach Superscalar:**

- Must be able to issue >1 IPC to RS/ROB
- Must be able to send > 1 IPC to functional units
    - Original Tomasulo can already do this (inst ready + FU available → execute)
- Must be able to write back >1 IPC to ROB and RS
- Must be able to commit >1 IPC

### Dual Issue

Check resource ability for two instructions at once (RS/ROB Entries) may issue 0,1, or 2 based on resources Read RAT/ARF/ROB for operands Update RS/ROB

![[Pasted image 20261011165908.png|500]]

#### Dual-Rename

- Read current RAT mappings for all operands
- New destinations = next two ROB entries → `ROB_tail`, `ROB_tail + 1`
- Must check for **RAW dependencies within the issue group**
    - Compare inst 2's sources against inst 1's dest (`src == dst1?`)
    - Match → use inst 1's new ROB entry instead of the RAT mapping

|`R1 = R2 + R3`<br>`R4 = R2 - R4`|`R1 = R2 + R3`<br>`R4 = R1 - R4`|
|---|---|---|
|Inst 1 →|ROB21, srcs `ROB17, ARF3`|ROB21, srcs `ROB17, ARF3`|
|Inst 2 →|ROB22, srcs `ROB17, ROB6`|ROB22, srcs ~~`ARF1`~~ → `ROB21, ROB6`|
![[Pasted image 20261012142147.png|500]]
### Multiple CDB

My implementing more CDBs we increase parallelism but at a cost.

- each RS entry must compare each source with each CDB
- more area, logic, power (\$\$\$)
- Works → done in CPUs today
![[Pasted image 20261011170439.png|350]]

### Committing

Check multiple commits at once

- Head not done -> nothing
- Head done, next isn't -> only head commits
- Head done, next done -> both commit

Then we write-back multiple results from ROB-ARF

- (or memory for stores)
- ROB needs extra read ports
- ARF needs extra write ports

## Terminology

- Issue, Dispatch, Commit, etc. are inconsistent / overloaded
    - Textbook uses terms w.r.t. Tomasulo's algorithm
    - Intel vs. many academics use different conventions
        - e.g. Issue/Alloc/Dispatch, Exec/Issue/Dispatch, Complete/Retire/Graduate

![[Pasted image 20261012142522.png]]

## ROB, PRF, ARF

Three ways to organize where values live:

- **Case 1:** RAT → ROB entry or ARF (ROB holds values)
- **Case 2 (Pentium III)**
- **Case 3 (NetBurst / P4):** separate **PRF**; front-end RAT and retirement RAT map to physical registers; ROB entry just records its PR (e.g. `ROB10: PR10`)

## In-order vs. OoO

- `fetch → decode → issue` : **in-order**
- `exec → write` : **out-of-order**
- `commit` : **in-order**