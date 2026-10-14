## Computer Architecture

- **Architecture**: put parts together to achieve some overall goal
    - e.g. the architecture of a chip, the Internet, a database system, an email system
- Why it matters: exploit advances in technology → faster, smaller, cheaper → enables new applications
    - advancement of comp arch is vital for the advancement of all other areas of computing

### Moore's Law (1965)

- **Transistors per inch²** → 2× after ~1.5–2 years
- Related trends
    - Processor performance → 2× after ~18 months
    - Memory capacity → 2× in <2 years
- Not a law of nature, but fairly accurate for >45 years
    - "No exponential is forever, but we can delay forever" (Moore, 2003) → we're now somewhere near the end

### How to use 10B+ transistors?

- **ISA**: interface between HW and SW
    - different ISAs can be more/less effective for different application areas
- **Microarchitecture**: techniques below the ISA level (transparent to SW)
    - pipelining, caching, branch prediction, superscalar, dynamic scheduling, clock-gating, …

### Purpose → design priorities

|Purpose|Examples|Priorities|
|---|---|---|
|General-purpose|Office, internet, multimedia, games, AI training|Performance, price/performance, power (→ cost, noise, size)|
|Server|File/web servers, databases|Throughput (transactions/s), availability; chip cost not a major issue|
|Embedded|Phones, cars, fridges, watches|Cost, power, size, predictable performance|

### Fabrication Costs

- **Die** size greatly affects cost of all systems
    - Current CPUs 1–2 cm² (Apple M4 = 1.66 cm²); embedded much smaller
    - Cost/footprint really matters in a thermostat or keyfob
- **Yield**: fraction of dies on a wafer that work → manufacturing defects kill dies
    - Bigger die → fewer dies per wafer AND a larger share of them hit by a defect

![[Pasted image 20261012121337.png|450]]

|Die size|Dies/wafer|Yield|Working/wafer|Cost/die ($250 wafer)|
|---|---|---|---|---|
|Small|52|81.25% (13/16)|42.25|$5.92|
|Large|17|25.0% (1/4)|4.25|$58.82|

### Interaction of Price and Performance

- Add a new feature (more perf, less power, …) → **die size ↑**
    - Fewer dies per wafer + more defective dies
- Die testing more expensive → must test that the feature works
- Package more expensive → larger, maybe more pins; more power → better heat sink

### Goal of Processor Design

- **Maximize performance** within constraints:
    - Peak/avg power, thermals, reliability, manufacturing cost, implementation + verification complexity, time-to-market, cost to manufacturer/OEM/customer
- → Huge multi-variable optimization problem; variables not independent

## Performance

- **Latency**: how long to do X (a.k.a. response time, execution time)
- **Throughput**: how often it can do X
- Car assembly line: 6 h to make a car (latency), a car leaves every 5 min (throughput = 12 cars/h)
    - Overlap → `Throughput > 1/Latency`

### Measuring Performance

- **Peak** (MIPS, MFLOPS) → often not useful
![[Pasted image 20261012121420.png|450]]
- **Benchmarks**
    - **Real applications / suites**: SPEC CPU2000, SPEC 2006, TPC-C, TPC-H, EEMBC, MediaBench
    - **Kernels**: "representative" parts of real apps
        - Easier/quicker to set up and run
        - Often not really representative of the entire app
    - **Toy programs, synthetic benchmarks**: not very useful for reporting
        - Sometimes used to test/stress specific features
![[Pasted image 20261012121440.png|450]]

### "Iron Law" of performance

$$CPU\ Time = Instruction\ Count \times Cycles\ Per\ Instruction \times Clock\ Cycle\ Time$$ $$CPU\ Time = \frac{seconds}{program} = \frac{instructions}{program} \times \frac{cycles}{instruction}\times \frac{seconds}{cycle}$$

- instructions/program is isa/compiler dependent
- cycles/instruction is isa/organization dependent
- seconds/cycle are hardware/organization dependent


- **Example**: 33B instructions, CPI = 2, clock = 3 GHz

$$CPU\ Time = 33 \times 10^9 \times 2 \times \frac{1}{3 \times 10^9} = 22\ s$$

- Sometimes clock cycle time is given instead (3 GHz → cycle = 333 ps)
- IPC sometimes given instead of CPI

$$CPU\ Time = CPU\ Clock\ Cycles \times Clock\ Cycle\ Time$$ $$CPU\ Time = \sum_{i=1}^n IC_i \times CPI_i \times Clock\ Cycle\ Time$$

- `i` = each kind of instruction; `IC_i` = how many of that kind in the program; `CPI_i` = cycles to execute one of that kind

Different architectures have varying frequencies and amount of time for instructions

- Integer, Branch, Load, Store
- Integer operations might happen much more frequently than Store operations
- Branch operations might take more cycles than Integer operations

- **Example**: Total insts = 50B, clock = 2 GHz

|Type|% of insts|CPI|
|---|---|---|
|Integer|40%|1.0|
|Branch|20%|4.0|
|Load|20%|2.0|
|Store|10%|3.0|

- Weighted CPI = 0.4(1) + 0.2(4) + 0.2(2) + 0.1(3) = 1.9 → 50B × 1.9 / 2 GHz = **47.5 s**
    - Note: slide's table only covers 90% of instructions, so this counts the listed types only

## Comparing Performance

"X is n times faster than Y" $$\frac{\text{Execution time}_Y}{\text{Execution time}_X} = n$$ Execution Time -> higher is worse

"Throughput of X is n times that of Y" $$\frac{\text{Tasks per unit time}_X}{\text{Tasks per unit time}_Y} = n$$ Tasks per unit time -> higher is better

If you're making a comparison they need to be on the exact same thing. Otherwise apples and oranges.

- **But on which application?** "X is n times faster than Y" only holds _on app A_
    - X 10× faster on A, 1.5× on B, but Y 2× faster on C, 3× on D → which is better? → need a way to summarize

## Summarizing Performance

- Arithmetic Mean
    - Average execution time
    - Default weight of 1
    - Gives more weight to longer-running programs
- Weighted Arithmetic Mean
    - More important programs can be emphasized
    - Weights are determined beforehand, taken from surveys on what people use the most, so what they can weigh the most/least
    - Different weights will make different machines look better

Speedups computed with arithmetic means are not always the same as the arithmetic mean of speedups.

- Geometric Mean
    - Takes individual speedups and converts them into another calculation
    - Multiplies all speedups (factors) then takes the nth root
    - $\sqrt[n]{\prod_{i=1}^n Speedup_i}$
    - **Consistent whatever the reference machine** → result doesn't depend on which baseline you normalize to
- In general, **don't use the arithmetic mean for normalized execution times**
    - **Normalized** = expressed relative to some baseline (really 1/speedup over that baseline)

## CPI/IPC

When making comparison,

- The program is the same for CPUs and the clock speedWhen making comparison, is the same for two CPUs, therefore instread of computing CPI we can just do IPC.
- Modern processors are so fast that when calculating, it's <1 CPI which doesn't make sense, so IPC makes more sense

IPC -> CPI before using it in the Iron Law $$Average\ CPI = \frac{\sum CPI_i}{N}$$ $$Average\ IPC = \frac{\sum IPC_i}{N} \neq \frac{1}{CPI}$$

- Must use the **Harmonic Mean** of IPCs to stay ≈ to runtime
    - Essentially convert to CPI, average, then invert

$$\text{Harmonic Mean IPC} = \frac{N}{\sum \frac{1}{IPC_i}} = \frac{1}{Average\ CPI}$$

## Amdahl's Law

- What if an enhancement doesn't enhance everything?

$$Speedup = \frac{\text{Execution Time without Enhancement t}}{\text{Execution Time with Enhancement t}} = \frac{ \text{Execution Time}_{old} }{ \text{Execution Time}_{new} }$$

Execution Time without using enhancement time t at all over Execution time using ehnacement t when possible

$$\text{Execution Time}_{new} = \text{Execution time}_{old} \times (1-\text{Fraction}_{enhanced} + \frac{\text{Fraction}_{enhanced}}{\text{Speedup}_{enhanced}})$$

$$\text{Overall Speedup} = \frac{1}{(1-\text{Fraction}_{enhanced}) + \frac{\text{Fraction}_{enhanced}}{\text{Speedup}_{enhanced}}}$$

- **Caution: fraction of what?** → fraction of the _old_ (unenhanced) execution time

make the common case fast

|Speedup_enhanced|Fraction_enhanced|Overall speedup|
|---|---|---|
|20|0.1|1.105|
|1.2|0.9|1.176|

- Small speedup on the common case beats a huge speedup on a rare case

Principle of Locality: 90% of the time is spent in 10% of the code

### Car Analogy (Turbo)

- Turbo → no benefit when stuck in traffic

|Segment|Plain|Turbo|Turbo++|
|---|---|---|---|
|Highway, 10 mi|50 mph → 0.2 h|100 mph → 0.1 h|200 mph → 0.05 h|
|Campus, 2 mi|10 mph → 0.2 h|0.2 h|0.2 h|
|**Total**|0.4 h|0.3 h|0.25 h|

- Turbo over Plain: 0.4 / 0.3 = **1.33** (fraction 0.5, speedup 2)
- Turbo++ over Turbo: 0.3 / 0.25 = **1.2** (still 2× on highway, but fraction is now 1/3)
    - Not the same as Turbo over Plain → the **"fraction improved" changed**

### Price-Performance

- Turbo is still a net win on speed, but consider cost:

|Cost|Price|Profit/car|Cars sold|Total profit|
|---|---|---|---|---|---|
|Plain|$8,000|$12,000|$4K|10,000|$40M|
|Turbo|$11,000|$16,000|$5K|400 (only gear heads)|$2M|

### Diminishing Returns
![[Pasted image 20261012121547.png|450]]
- Gen 1: green phase = 1/2 of time, sped up 2× → overall **1.33**
- Gen 2 over Gen 1: green now only 1/3 of time, sped up 2× again → overall **1.2**
- Each improvement shrinks the enhanced fraction → same enhancement buys less next time