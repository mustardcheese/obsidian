Tomasulo's Algorithm

Since renaming has solved WAW and WAR dependencies, we can start executing out of order and correct for any RAW dependencies.
## Hardware

**Instruction Buffers**
- Holds fetched instructions in order within a buffer
- Feeds instructions into reservation stations and specialized buffers
- Act as a queue, oldest dispatch first

**Reservation Station**
- Holds an instruction in a buffer, waiting to receive the operands (from registers)
- After getting operands, runs through execution unit (alu, mux, etc.)

**Register Alias Table**
- Holds where the newest value for each register will come from
- Points to either a register in hardware, or an ID to a reservation station

**Register File**
- Where values are actually held

![[Pasted image 20261008200614.png|500]]

## Operations

### Issue
- Get next instruction from instruction queue
- Find a free reservation station for it (wait if there are none)
- Read operands that are in the register
	- If the operand is not in the register, find the reservation station that will produce it
		The reservation station IDs are essentially treated as temporary names

![[Pasted image 20261008200821.png|500]]
	RAT points to index 4 for F1, meaning it isn't ready yet in register file, but it'll be ready at ID=4 (C1 reservation station)

### Execute
- Monitor results as they're produced
- Put a result into another reservation station as necessary
- When all operands are available for an instruction we can execute it
- If there are several ready instructions in one functional unit, pick one (oldest first heuristic) that isn't load/store
![[Pasted image 20261008201249.png|500]]

### Write
- Once a result is completed, put it on a common data bus (CDB) where a reservation station can pick it up
- Store writes to memory
- Result stored in register file
- Free the reservation station
![[Pasted image 20261010145638.png|500]]

