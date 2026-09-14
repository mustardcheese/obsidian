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