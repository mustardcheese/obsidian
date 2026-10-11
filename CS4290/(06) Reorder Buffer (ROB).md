The ROB separates architectural (ISA) registers from physical registers. It also enables in-order completion or "commit"

![[Pasted image 20261010193612.png|600]]


**ROB Fields**
- Type: ALU, op, load, store, branch
- Dest: Which architected register to update
- Value
- Fin: Set when the result has been written back

## Issue
- Read instruction from instruction buffer
- Check if resources are available:
	- RS has open slots
	- ROB has open slots
- Read RAT, read available sources, Update RAT
- Write to RS and ROB

## Execute
- Wait for operands to arrive
- Compete to use functional unit
- Execute

## Write Result
- Broadcast result on CDB (any dependents will take value)
- Write result into ROB entry
	- ARF only holds "official" register state
	- Mark ready/finished bit in ROB once ready
- Reservation station can be freed

## Commit
When an instruction is the oldest in the ROB (head points to it):
- Write result (if ready/finished bit is set)
	- to ARF if register
	- to mem if store
- Advance ROB to next instruction

![[Pasted image 20261010212350.png|500]]