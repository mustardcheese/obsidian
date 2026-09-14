Control Dependency is knowing the next instruction to fetch based on the current instruction

We want the pipeline ot be full of useful instructions, but branches are very frequent
- Instructions are ~20% composed of branches
We can't wait until we know where the branch goes because:
- Long pipeline == Long stalls
- Parallel pipelines == Parallel stalls

We can try to predict the next instruction through speculation:
- If we assume we always take the branch, we don't have to wait for the branch to resolve, saving us a few cycles but leads to the possibility of incorrect branches


We need to recover from mispredictions when we take the wrong path. Following the three crucial rules:
1. Do not write to registers
2. Do not write to memory
3. Do not trigger a branch misprediction if you aren't a branch

## Branch Types
To correctly do branch prediction we need to know two things:
- Whether or not the branch is taken (direction, binary decision)
- The target address if taken (target)


**Direct Jumps**, Function Calls
	Direction known (always taken), target easy to compute
	We know where to go, PC-relative offset and we know if we are going somewhere for certain
	
**Conditional Branches**
	Direction difficult to predict, target easy to compute
	We know where to go, PC-relative offset but to predict if we are going we might need to read registers and run comparisons
	
**Indirect Jumps**, Function Returns
	Direction known (always taken), target difficult to compute
	We might not know where to go, without a stack or return saved somewhere it might be difficult to find where to return, but we know if we are going somewhere for certain

Direction for conditional branches are the hardest and is the biggest issue to solve
Target prediction is also required, but it's relatively simple compared to Direction predictor

## Branch Prediction Direction
Needed for conditional branches, which most branches are

Many kinds of predictors, main two are:
### Static Branch Prediction
Prediction follows a rule (never/always/etc.)
- Reasonable performance for such cheap implementation
- Still guesswork, just very simple guesswork
- Compiller (software) annotations can aid with this, "BEQL" flag to say "branch equal likely"
- We still need a target predictor because if we follow a heuristic for direction, we sometimes still get it wrong and do actually need to know the target
	- We still need *some* kind of target predictor, which is cheap but not that cheap if we try to save on the static predictor

**Examples**
- Always predict NT
	- 30-40% accuracy (because of loops)
	- Completely free to use
- Always predict T
	- 60-70% accuracy (because of loops)
- BTFNT (Backwards T, Forward NT)
	- Loops have a number of iterations so always predict the loop is taken

We don't know target until decode
- Before then we don't even know if it's a branch or not
- Can try predecoding to see if it's a branch early

## Dynamic Branch Prediction
Hardware predicts
- Ex. predicted direction is the same as the last time this branch was executed, store in a hardware table, **BTB**
	- The nice thing about this is we *only* need the PC, and when we start the very beginning of the branch we *only* know the PC as well, therefore we don't even need to calculate anything since predictions will *likely* resolve itself in the table already

### One-Bit Branch Predictor
![[Pasted image 20260831163105.png|450]]
A very long 1-bit lookup table


We take the LSB of the addresses that vary since branches that live close together tend to have the same upper bits anyways.
![[Pasted image 20260831163659.png|450]]
- For % 10, 9 out of 10 times we can correctly predict no
- For & 1, it's a 50/50 if we correctly predict. The worst-case scneario is we keep flip flopping T and NT, causing a 100% prediction miss rate.
- The toggling branches are luckily not very common
Every single predictor has a worst-case scenario where it guesses wrong forever

Another example of a toggling branch could be picking a node from random out of a tree. Approximately half the tree are leaves so if(leaf) could be a degenerate 100% misprediction


### Two-Bit Predictor
![[Pasted image 20260902153831.png|450]]

By having two bits instead of one, it takes "more effort" to "change your mind"
- Multiple consistent NT or T outcomes to force a change, majority prediction

Works well for many things like short loops, aids with misprediction but doesn't remove it entierly

![[Pasted image 20260902154128.png|450]]
	1 bit predictor, takes 1 round warmup but upon getting it wrong messes it up for two

![[Pasted image 20260902154221.png|450]]
	2 bit predictor, takes 2 round warmup but upon getting it wrong doesn't continue to mispredict and adjusts itself


### Importance of Branches
98% -> 99% branch prediction
- Seemingly not a big deal, but the big gains are in the mispredictions!
- 2% -> 1% mispredictions cut in half

Say we have a misprediction rate of 50%, and 1 in 5 instructions is a branch. The number of useful instructions is then:
	5*(1 + 0.5 + (0.5)^2 + (0.5)^3 + ...) = 10
If we're able to halve the misprediction rate to 25%, then:
	5*(1 + 0.75 + (0.75)^2 + (0.75)^3 + ...) = 20
Halving the miss rate effectively doubles the amount of useful instructions we're able to run



What about a repeating pattern?
(NT)*
(TTNTN)*
1bc and 2bc don't do too well here but it's obviously predictable

## Branch Correlation
The idea is to track the history of a branch. Track the:
- Previous outcome
- Counter if prev=0
- Counter if prev=1

The largest issue is that it's too expensive. For n branch history we need to track both the n branch history as well as 2^n to keep track of all possibilites

![[Pasted image 20260902160629.png|450]]

### Global vs Local

Local behavior
- What is the predicted direction of Branch A given the outcomes of previous instances of Branch A
Global Behavior
- What is the prediction direction of branch Z iven the outcome of *all* previous branches A, B, ..., X and Y?


**fill this in i blanked out during lecture**

## Tournament Predictor
No predictor is clearly the best since different branches exhibit different behaviors
- Constant, global, local, etc. behavior

The idea is to have a predictor to predict which predictor whill predict better

![[Pasted image 20260902161716.png]]
Meta-Predictor is a small predictor just to select which predictor to actually use
- Pred0 and Pred1 might be complex global/local predictor
- Meta predictor will be a simple predictor

| Pred0 | Pred1 | Meta Update |
| ----- | ----- | ----------- |
| miss  | miss  | ---         |
| miss  | hit   | inc         |
| hit   | miss  | dec         |
| hit   | hit   | ---         |
We train the predictors as if they were alone, but the metapredictor is trained on which one is better


**Common Combinations**
- Global + Local history
- "easy" branches + global history
- short history + long history

![[Pasted image 20260902162903.png|450]]

## Target Address Prediction

The BTB is used to predict the address of the branch
- IF stage: need to know fetch addr every cycle
- Need target address one cycle after fetching a branch
- For some branches, target known only after EX stage which is too late




**return address stack notes**


Some branches will be very hard to predict no matter what
```
if(random() & 1){
	a++;
} else{
	b++;
}
```
We can try to make a good predictor for this but it won't really be possible

The idea is then instead of trying to predict **where** the branch goes, we predict instead **whether or not** the condition will actually happen.
- Both paths of the if-else will be executed but once we figure out whether or not it fires, we just go to the correct path

### Conditional Instructions
Write result only if instruction if is true

CMOV -- Conditional Move

```
CMOV R1, R2, R3
```
- R1 = R3 ? R2 : R1
- If R3, then R2 -> R1, else R1 -> R1 (NOP)


For the previous random example, we can read both a,b and increment it, but until we determine which path we take *then* we update the value

```
if (cond)
	a++
else
	b++
```


```
BEQZ R1, else
ADDI R2, R2, 1
B end

else:
ADDI R3, R3, 1

end:
```
branching hard to predict here


```
ADDI R4, R2, 1
ADDI R5, R3, 1
CMOV R2, R4, R1
CMOVN R3, R5, R1
```
- R4, R5 temporary a++ and b++
- Conditionally move into a, b based on condition R1

Problem: Uses more registers, need a CMOV for each value

## "Full" Predication

Every instruction can be predicated, so every instruction will have a condition to whether it writes or not
- Often with separate predicate registers
- Separate instructions to set predicates

**Problem:** Every instruction needs extra bits
- Must use bits to specify predicate
- Four-operand instructions, (2 src 1 pred 1 dst)
**Problem:** Must change the ISA
- Intel Itanium

![[Pasted image 20260909155025.png|500]]
- While predication is not the end all be all of branches, it does reduce the amount needed


