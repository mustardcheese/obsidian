## Performance
### "Iron Law" of performance
$CPU\ Time = Instruction\ Count \times Cycles\ Per\ Instruction \times Clock\ Cycle\ Time$
$CPU\ Time = \frac{seconds}{program} = \frac{instructions}{program} \times \frac{cycles}{instruction}\times \frac{seconds}{cycle}$
- instructions/program is isa/compiler dependent
- cycles/instruction is isa/organization dependent
- seconds/cycle are hardware/organization dependent

$CPU\ Time = CPU\ Clock\ Cycles \times Clock\ Cycle\ Time$
$CPU\ Time = \sum_{i=1}^n IC_i \times CPI_i \times Clock\ Cycle\ Time$

Different architectures have varying frequencies and amount of time for instructions
- Integer, Branch, Load, Store
- Integer operations might happen much more frequently than Store operations
- Branch operations might take more instructions than Integer operations



### Comparing Performance
"X is n times faster than Y"
$\frac{\text{Execution time}_Y}{\text{Execution time}_X} = n$
Execution Time -> higher is worse

"Throughput of X is n times that of Y"
$\frac{\text{Tasks per unit time}_X}{\text{Tasks per unit time}_Y} = n$
Tasks per unit time -> higher is better

If you're making a comparison they need to be on the exact same thing. Otherwise apples and oranges.


### Summarizing Performance
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

### CPI/IPC

When making comparison,
- The program is the same for CPUs and the clock speedWhen making comparison, is the same for two CPUs, therefore instread of computing CPI we can just do IPC.
- Modern processors are so fast that when calculating, it's <1 CPI which doesn't make sense, so IPC makes more sense

IPC -> CPI before using it in the Iron Law

Average CPI = $\frac{\sum CPI_i}{N}$
Average CPI = $\frac{\sum IPC_i}{N} \neq \frac{1}{CPI}$

### Amdahl's Law
Speedup = $\frac{\text{Execution Time without Enhancement t}}{\text{Execution Time with Enhancement t}} = \frac{ \text{Execution Time}_{old} }{ \text{Execution Time}_{new} }$

Execution Time without using enhancement time t at all
over
Execution time using ehnacement t when possible

$\text{Execution Time}_{new} = \text{Execution time}_{old} \times (1-\text{Fraction}_{enhanced} + \frac{\text{Fraction}_{enhanced}}{\text{Speedup}_{enhanced}})$

