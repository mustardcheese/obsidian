## Instruction Level Parallelism (ILP)

**Basic Idea**: Execute several instructions in parallel

We already have pipelining, but only push out at most 1 instruction/cycle
We want multiple instructions per cycle


ISA currently defines instruction execution one at a time
- I1: ADD R1 = R2 + R3
	- Fetch instruction
	- Read R2 and R3
	- Do the addition
	- Write R1
	- Increment PC
- Repeat for I2, etc.


Parallelism exists in that we perform different operations (fetch, decode, …) on several different instructions in parallel

Instructions must stay "correct", but what's correct?
- Defined by the ISA
- Same processor state as if they were executed one a t a time


### Illusion of Sequentiality
So long as everything looks OK from the outside, you can do whatever you want!
- Outside appearance = "Architecture" (ISA)
- Whatever you want = "Microarchitecture"

**Simple ILP**
- Read and decode instructions each cycle
- If instructions are independent, do them at the same time
- If not, do them one at a time
![[Pasted image 20260909163141.png|450]]




**Superscalar**
"Scalar" CPU executes one instruction at a time
"Vector" CPU executes one instruction at a time, but on vector data
- X[0:7] + Y[0:7], one instruction with 8x data, would need 8 scalar processors
"Superscalar" CPU executes more than one unrelated instruction at a time


## Scheduling
The biggest problem is to find where "legal" (independent) parallelism exists

In Pentium, decode stage checks for multiple conditions
- Data dependency
- Resource conflict

How many instructions do we look for?
- 3-6 is typical today
- A cpu that can ideally do N instructions per cycle is 
  "N-issue superscalar", "N-way", "N-issue", "N-wide"
	- N is known as the issue width


From here, we can reorder instructions based on data dependencies
![[Pasted image 20260914153336.png|500]]

Seems good, but still stuck at 7 instructions in 4 cycles. **Can we go faster?**

## Dependencies

Data Dependencies
- RAW: Read-After-Write (True Dependence)
	need to wait for value to update
- WAR: Anti-Dependence
	need to consume value before writing
- WAW: Output Dependence
	instructions cannot be reordered since order needs to stay consistent

Control Dependence
- When instructions depend on outcome of a previous jump
- We already know how to solve: prediction and predication

### Data Dependencies
**Register Dependencies
- RAW, WAR, WAW based on register *number

**Memory Dependencies**
- Based on *address*
- Harder, since memory address not known until execute

![[Pasted image 20260914155536.png|550]]


## Hazards

Hazards are when dependencies in a program changes the outcome of an unresolved dependency.
	Not all dependencies lead to hazards, however

Dependencies are a property of the program
Hazards are when dependencies cause issues during execution

Data Dependency -> Data Hazard, but it depends on the processor

Some processors cannot have dependencies or hazards, like a one-at-a-time processor. Nearly every processor will have some kind of dependency that doesn't necessarily manifest into a hazard. In practice the hazards don't happen.

### False Dependencies
A dependency that we can do something about.

They happen because: **there's a finite number of registers**
- At some point, you're forced to overwrite some value somewhere
- WAR and WAW are also "name dependencies" because the data is still *somewhere* but under different names

Why not add more registers?
- We'd still run out anyways, and while it helps, it will never resolve fully the problem
- Not a scalable solution
- All code needs to be recompiled
- Changing ISA can break lots of compatability

![[Pasted image 20260914160826.png|500]]![[Pasted image 20260914160842.png|500]]


**Reuse is Inevitable**
- Loops, functions, etc all have to reuse registers

**Solution: HW Register Renaming**
- Have temporarily more registers than specified by the ISA
- Temporarily map ISA registers to physical registers to avoid overwrites
Components:
- Mapping Mechanism
- Physical Registers

## Register Renaming
![[Pasted image 20260914161404.png|500]]
 We can give I3 a temporary name/location *S* for the value it produces
 - I4 also uses that temporary value
 - Subsequent uses and writes are changed
WAW can be removed by changing R2 in I5 to *T*

![[Pasted image 20260914161647.png|250]]

How can we implement register renaming?

The simple solution is to do renaming for every instruction. We can change the name of a register each time we decode an instruction that will write to it and remember the name we gave to it.

## Dynamic (out of order) Scheduling
