Speculative execution still works with interrupts and exceptions:
- ROB maintains program order
- ROB temporarily stores results
- Register rename recovery makes sure we have correct register mapping

**1. Undo the effects**
**2. Know how to resume**

## Basics
Exceptions are unprogrammed control flow
	The system takes an action to handle the flow

- **Interrupts**
	- Caused by external events
	- ***Asynchronous*** to program execution
	- May be handled in between instructions
	- Suspend and resume user program
- **Exceptions (Traps)**
	- Caused by internal events
	- ***Synchronous*** to program execution
	- Condition must be remedied by the handler
	- Instruction may be retired and program continued or program may be aborted

### Which stages can generate exceptions?
Fetch:
- Page fault on instruction fetch
- Misaligned memory access
- Memory-protection violation
Decode:
- Undefined or illegal opcode
Execution:
- Arithmetic exception
Memory:
- Page fault for data
- Misaligned memory access
- Memory-protection violation
- Memory error

### Precise Exceptions
Exceptions should be **precise**
	***Precise*** = the state of the machine is preserved as if program executed up to the exception causing instruction
- Prior instructions should remain executed
- Subsequent instructions did not modify process state
- Exception causing instruction may or may not have been executing depending on architecture

## Commits and Exceptions
What happens when a speculatively executing instruction faults?
![[Pasted image 20261011174459.png|550]]


We treat the fault like a result:

Regular register results written to the ROB until
- Instruction is oldest for in-order state update
- Instruction is known to be non-speculative

We do the same with faults
- At exec, make note of any faults but don't expose to the outside world
- If the instruction gets to commit, then expose the fault

*tldr, run everything and continue to commit until we reach the failure point*

## Branch Mispredictions
We can fix branch mispredictions the same way we fix exceptions
- Wait for a mispredicted branch (instruction) to commit
- Flush wrong path instructions still in pipeline
- Start fetching instructions from the correct path

However, this wastes time because the branch misprediction is detected far before it's committed, but in the meantime we've already been fetching wrong-path instructions and they getting ready to read and write other wrong path values.

### Checkpointing
At each branch, make a copy of the RAT

On a misprediction:
1. mark wrong path instructions in ROB (so they commit as NOPs)
2. Deallocate wrong path RAT checkpoints
3. Recover RAT from checkpoint
4. Start fetching correct instructions and resume normal renaming
![[Pasted image 20261011175707.png|500]]

## Memory Instructions
How do we handle memory dependencies?
```
SW R1, 0(R2)
LW R1, 0(R3)
```
store writes to memory only at commit to prevent garbling memory if cancelled

If we store before we load all out of order, who's to say where load gets the data?

![[Pasted image 20261011180358.png|500]]

We *could* block loads from executing OoO but that reduces ILP

Other possibilities:
- The value loaded is stale
- The value loaded is the from the wrong store
- After memory data forwarding, the value loaded isn't even the right one

### Memory Disambiguation
This only happens with memory operations because there are not absolutes with memory
- Operand specifiers in non-memory are absolute: "R1" refers to one specific location
- Operand specifiers in memory are ambiguous: "R1" refers to memory location by the value of R1; pointers change and so does the location

Are there any earlier executed stores to the same address as myself?
	yes or no

**Store-to-load Forwarding Problem**
- Load: Which earlier store do I get my value from?
- Store: Which later loads do I give my value to?
Non-binary question, depends on instruction

## Load Store Queue (LSQ)
![[Pasted image 20261011191329.png|550]]
Load and Store operations slowly fill up the queue
- Every time there's a dependent load, it reads stores from queue (**Forwarding**)
- Commits move oldest pointer in the LSQ forward, meaning loads can't execute until stores are finished (**Disambiguation**)

### Issue
- Need to allocate an LSQ entry for each LD/ST
	on top of ROB entry, RS, etc.
### Execute
- Generate address (update/lookup LSQ)
- Produce result (update ROB, mark as done)
### Commit
- If ST, send value to memory
- Move LSQ head
	on top of moving ROB head, etc.

LSQ keeps address but for value
- ST uses value field in LSQ since there is no destination register for a store, only a value to keep track of, used for forwarding and commits
- LD puts loaded value in ROB since there is a destination register



