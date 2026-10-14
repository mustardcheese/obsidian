Dependence chains limit ILP in general, so we should try to either shorten or move dependence chains further apart

- HW only looks at so many instructions at once (**ROB**, **RS** limits) → compiler has to expose the ILP

# Methods

### Tree Height Reduction

Shorten the critical path using associativity ![[Pasted image 20261011203314.png|500]]

- `R8=((R2+R3)+R4)+R5` (3-deep chain) → `R8=(R2+R3)+(R4+R5)` (I1, I2 independent, 2-deep)
- **Not all math ops are associative!** (e.g. FP)
- C defines **left-to-right** semantics for most arithmetic → compiler can't always regroup

### Instruction Scheduling

Moves independent instruction into stall slots caused by operations ![[Pasted image 20261012010537.png|500]]

#### Simple loop example

```c
for (i=1000; i>0; i--)
    x[i] = x[i] + s;
```

- Assume single-issue, latencies:

|Producer → Consumer|Extra cycles|
|---|---|
|FP ALU → Store|+2|
|Load DW → FP ALU|+1|
|Branch|+1|

|Unscheduled (9 cycles)|Scheduled (7 cycles)|
|---|---|
|`L.D F0,0(R1)`|`L.D F0,0(R1)`|
|stall|`ADDUI R1,R1,#-8`|
|`ADD.D F0,F0,F2`|`ADD.D F0,F0,F2`|
|stall|stall|
|stall|stall|
|`S.D F0,0(R1)`|`S.D F0,8(R1)`|
|`ADDUI R1,R1,#-8`|`BNE R1,R2,Loop`|
|stall||
|`BNE R1,R2,Loop`||

- Hoist the `ADDUI` into the load stall slot
    - **Store offset changes** `0(R1)` → `8(R1)` since R1 was already decremented
- **Problem:** can only do this **within one iteration** → still 2 stalls left (Slide 9)

#### Scheduling for multiple-issue

```
A: R1 = R2 + R3        A: R1 = R2 + R3
B: R4 = R1 – R5        C': R8 = LOAD 0[R7]
C: R1 = LOAD 0[R7]     B: R4 = R1 – R5
D: R2 = R1 + R6        E': R9 = R3 + R5
E: R6 = R3 + R5        D': R2 = R8 + R6
F: R5 = R6 – R4        F': R5 = R9 – R4
```

- Reordering alone is blocked by **name dependences** (C reuses R1, E writes R6)
- Rename C → `R8`, E → `R9` → same functionality, **no stalls**

#### Scheduling, RegAlloc, and Branches
- Largely limited by **architected registers**
    - Weird interactions w/ register allocation → could cause more **spills/fills**
- Code motion limited by branches:
    - Hoisting `R1 = LOAD 0[R6]` above `BEQZ R1` → must allocate a different reg (`R8`) since R1 is still used on the other path
    - LOAD now runs even when branch goes the other way → **Dynamic Dead Code**

![[Pasted image 20261012141934.png|500]]


#### Scheduling and Predication
- Branches make scheduling harder → **predication** may help
- 50-50 branch = no "common case" to schedule for
- **If-conversion** → single large block for scheduling
- Can't if-convert a loop though → need unrolling / SW pipelining to schedule across iterations
![[Pasted image 20261012141951.png|500]]
### Loop Unrolling

- M-iteration loop → loop with M/N iterations = **unrolled N times**

```c
for(i=1000;i>0;i--)          for(i=1000;i>0;i-=4){
    x[i]=x[i]+s;                 x[i]=x[i]+s;
                                 x[i+1]=x[i+1]+s;
                                 x[i+2]=x[i+2]+s;
                                 x[i+3]=x[i+3]+s;
                             }
```

- Compiler can do it (`gcc -funroll-loops`) or do it manually

#### Why unroll?

1. **Less loop overhead** → 1000 branches → 250
2. **Better scheduling** → independent copies fill each other's stall slots
    - Unroll + rename regs (F0, F4, F6, F8) + single pointer update:

```
L.D    F0,0(R1)
L.D    F4,-8(R1)
L.D    F6,-16(R1)
L.D    F8,-24(R1)
ADD.D  F0,F0,F2
ADD.D  F4,F4,F2
ADD.D  F6,F6,F2
ADD.D  F8,F8,F2
DADDUI R1,R1,#-32
S.D    F0,32(R1)
S.D    F4,24(R1)
S.D    F6,16(R1)
S.D    F8,8(R1)
BNE    R1,R2,Loop
```

- ↑ No stalls, 14 instrs for 4 elements; offsets adjusted after `DADDUI`

3. **Get rid of small loops**
    - `for(i=0;i<4;i++) a[i]*=2;` → `a[0]*=2; a[1]*=2; a[2]*=2; a[3]*=2;`
    - Hard to hoist insts from bottom block to top block w/ branches in the way → no branches = easier

#### Problems

- **Code bloat**
- Trip count not a multiple of N? Not known at compile time? `while` loop?
    - Fix: unrolled main loop + **cleanup loop** for leftovers

```c
j1=j-j%4;
for(i=0;i<j1;i+=4){
    a[i]*=2;
    a[i+1]*=2;
    a[i+2]*=2;
    a[i+3]*=2;
}
for(i=j1;i<j;i++)
    a[i]*=2;
```

### Function Inlining

- Sort of like "unrolling" a function → replace call w/ function body

```c
c=max(a,b);   →   if (a>=b) c=a;
                  else c=b;
```

- **Benefits** (similar to unrolling):
    - Remove call overhead: `CALL`/`RETN` (+ possible branch mispreds), arg/ret-val passing, stack allocation, spills/fills of caller/callee-save regs
    - Larger block of instructions for scheduling
- **Problems:**
    - ↑ register pressure
    - Primarily code bloat
    - Recursive functions?

### Unrolling Often Not Enough

- Need a lot of unrolling to hide load latency
- MULs also slow and on the **critical path**

```c
for(i=0;i<100;i+=2){
    prod*=a[i];
    prod*=a[i+1];
}
```

```
Loop: LD  F0,0(R1)
      LD  F1,8(R1)
      MUL F7,F7,F0
      MUL F7,F7,F1
      ADD R1,R1,16
      BNE R1,R2,Loop
```

- Both MULs still chained through `F7`

### Software Pipelining

- **Instruction pipelining:** each stage does a different op on a different instruction (WB i, MEM i+1, EX i+2, ID i+3, IF i+4)
- **Software pipelining:** each instruction in the loop body does ops from **different logical iterations**

#### Example

```c
for(i=0;i<100;i++)
    sum+=a[i]*b[i];
```

- Latencies: LOAD 3, MUL 3, ADD 1
- SW pipeline stages:
    - **Stage 1:** loads `a[i]`, `b[i]`
    - **Stage 2:** multiply
    - **Stage 3:** add to sum

```c
p2=a[0]*b[0];              // start-up: stages 1-2 for iter 0
a1=a[1];b1=b[1];           //           stage 1 for iter 1
for(i=2;i<100;i++){
    sum+=p2;               // stage 3, iter i-2
    p2=a1*b1;              // stage 2, iter i-1
    a1=a[i];b1=b[i];       // stage 1, iter i
}
sum+=p2;                   // finish-up: stage 3 for iter 98
sum+=a1*b1;                //            stages 2-3 for iter 99
```

#### Problems

- **Code gets bigger** → start-up + finish-up code, slightly larger body
- **Eats up registers** → regs hold temps, act as the **pipeline latches**
- Need to know **exit condition early** → right after stage 1 of the last iteration
- Only works for loops

#### SW Pipelining vs. Loop Unrolling

- SW pipelining → overlap ramps up once (start-up) and down once (wind-down), full overlap in between
- Unrolling → ramp up/down every unrolled iteration; only overlap within/between adjacent unrolled bodies
![[Pasted image 20261012142046.png|500]]
### Data Speculation

- **Why:** schedule loads early → load starts early → value arrives in time to be used
- **Problem:** possibly conflicting stores

```
ST  F2,100(R3)          LD  F1,0(R1)     ; moved above store
LD  F1,0(R1)      →     ST  F2,100(R3)   ; same address?
ADD F2,F1,F3            ADD F2,F1,F3
```

- **Solution:** tell HW what we're doing

#### Exceptions and Speculation

- Advanced load may trigger exceptions that **never happen** in original code
- Speculative load doesn't raise the exception → **poisons** its destination reg
- **Check** placed where the original load was
    - Reg poisoned → check triggers a **re-load**
    - If exception should really happen → non-speculative re-load raises it

### Vectors

- Used in scientific & engineering apps; short vectors in multimedia
- **Idea:** treat entire vector as one data item

```c
for(i=0;i<64;i++)
    a[i]=b[i]*c[i];      →   mulv a,b,c
```

- **Why:**
    - Vector ops can be **deeply pipelined**
    - Fetch/decode/issue only **one** op → no loop overhead, no branch prediction needed
    - Access pattern exposed to HW

#### Problems

- Compiler must be pretty good
    - e.g. `a[i]=b[i]*c[i]+d[i]` → `mulv t,b,c` + `addv a,t,d`
- Less benefit for **short vectors** → high start-up cost w/ deep pipelines
- **"Irregular" apps** (control-intensive, pointer-intensive) → very hard to vectorize, even by hand

### ISA Media Extensions

- **Short vector regs** for "media" data (pixels, sound samples) → typically small values (e.g. 16-bit sound)
- Use "normal" execution units → 64-bit adder can easily do four 16-bit adds
- Media-specific arithmetic → **saturation** instead of overflow