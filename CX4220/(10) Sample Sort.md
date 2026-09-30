# Sample Sort

## Parallel Sorting Lower Bounds

Before exploring algorithms, establish the baseline that any distributed memory parallel sort must meet.

**Sequential sorting lower bound:** Comparison-based sorting of $n$ elements requires at least $\Omega(n \log n)$ comparisons.

**Distributed memory parallel sorting lower bound:**

Assume $n/p$ elements per processor initially.

- **Computation:** $\Omega\left(\frac{n \log n}{p}\right)$ — just the sequential bound divided by $p$ processors
- **Communication (bandwidth):** $\Omega\left(\mu \frac{n}{p}\right)$

The communication bound comes from a counting argument: in the worst case, all $n/p$ elements on a processor belong to other processors. Even in the average case, $\frac{n}{p}\left(1 - \frac{1}{p}\right) = \Theta\left(\frac{n}{p}\right)$ elements must be sent elsewhere. Every element that moves costs $\mu$ per word, so:

$$\boxed{\text{Computation: } \Omega\left(\frac{n \log n}{p}\right) \qquad \text{Communication: } \Omega\left(\mu \frac{n}{p}\right)}$$

![[SLIDE_PLACEHOLDER_lower_bound_diagram.png|500]]

---

## Why Not Bitonic Sort?

Bitonic sort complexity (from Lecture 9):

$$T_{comp} = O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log^2 p\right) \qquad T_{comm} = O\left(\tau \log^2 p + \mu \frac{n}{p}\log^2 p\right)$$

The problem: the $\log^2 p$ factor on bandwidth. Every element participates in $\log^2 p$ data movement rounds, each moving $n/p$ data. Compared to the lower bound of $\Omega(\mu \cdot n/p)$, bitonic sort has an **extra $\log^2 p$ factor** on communication.

**Key question:** Can we determine which processor each element should go to _before_ the communication, so we only need to move the data **once**?

---

## Parallel Quicksort

**Algorithm:**

1. Pick a pivot and broadcast it — $O(\log p \cdot (\tau + \mu))$
2. Partition locally around pivot — $O(n/p)$
3. Re-arrange partitions (exchange data with partner) — $O(\tau + \mu \cdot n/p)$
4. Split communicator and recurse on each half
5. If $p = 1$, locally sort

![[SLIDE_PLACEHOLDER_quicksort_tree.png|500]]

**Best/expected case (assuming balanced pivots):**

There are $O(\log p)$ iterations before reaching $p = 1$ and doing a local sort.

- **Computation:** $O\left(\frac{n}{p}\log p + \frac{n}{p}\log\frac{n}{p}\right) = O\left(\frac{n \log n}{p}\right)$ — matches the lower bound
- **Communication:** $O\left(\tau \log p + \mu \frac{n}{p} \log p\right)$

**Worst case:** Much worse — a bad pivot can send $\Omega(n)$ elements to one side.

**The two problems with parallel quicksort:**

1. The **extra $\log p$ factor** on bandwidth: the algorithm recurses $\log p$ times, each round potentially moving $O(n/p)$ data, giving $\mu \cdot (n/p) \cdot \log p$ total bandwidth cost
2. **Worst-case load imbalance** from poor pivot selection

**Key insight for sample sort:** If we could pick $p - 1$ good "splitters" (instead of one pivot) and redistribute all data in a **single** all-to-all round, we'd eliminate the $\log p$ bandwidth factor.

---

## Sample Sort — High-Level Framework

**Algorithm (5 steps):**

1. Sort locally
2. Find $p - 1$ "good" splitters
3. Split local sequence into $p$ segments according to splitters
4. Many-to-many communication (all-to-all personalized)
5. Locally merge $p$ received sequences

![[SLIDE_PLACEHOLDER_sample_sort_overview.png|500]]

**What makes splitters "good"?**

- Each processor should receive at most $m \leq c \cdot \frac{n}{p}$ elements in step 4, where $c \geq 1$ is a small constant
- Finding the splitters should not be too expensive (shouldn't dominate overall complexity)

**Step costs (assuming good splitters with $c = 2$):**

|Step|Operation|Computation|Communication|
|---|---|---|---|
|1|Local sort|$O\left(\frac{n}{p}\log\frac{n}{p}\right)$|—|
|2|Find splitters|depends on method|depends on method|
|3|Partition locally|$O\left(\frac{n}{p}\right)$ via linear scan|—|
|4|Many-to-many|—|$O\left(\tau p + \mu \frac{n}{p}\right)$|
|5|Merge $p$ sequences|$O\left(\frac{n}{p}\log p\right)$|—|

The entire game is in **Step 2** — how cheaply can we find splitters that guarantee good load balance?

---

## Attempt #1: Evenly Split Local Arrays (No Splitter Selection)

**Idea:** After sorting locally, simply split each local sorted array into $p$ equal segments of size $\frac{n}{p^2}$. Processor $i$ sends its $j$-th segment to processor $j$.

![[SLIDE_PLACEHOLDER_attempt1_diagram.png|500]]

**Complexity:**

- Computation: $O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log p\right) = O\left(\frac{n \log n}{p}\right)$
- Communication: $O\left(\tau p + \mu \frac{n}{p}\right)$

This **matches the lower bounds** on both computation and bandwidth!

**What's wrong:** This assumes data is uniformly distributed. If every element happens to fall in the range that maps to one processor, that processor gets everything. We **cannot assume any particular distribution of data** — the algorithm must work for all inputs.

---

## Attempt #2: Random Splitters (Like Quicksort)

**Idea:** After sorting locally, pick $p - 1$ random samples globally to use as splitters.

**Algorithm:**

1. Sort locally — $O\left(\frac{n}{p}\log\frac{n}{p}\right)$
2. Pick $p - 1$ random samples globally, sort them — $O(p \log p)$
3. Split local sequences into $p$ segments — $O\left(\frac{n}{p}\right)$
4. All-to-all communication — $O\left(\tau p + \mu \frac{n}{p}\right)$
5. Locally merge — $O\left(\frac{n}{p}\log p\right)$

![[SLIDE_PLACEHOLDER_attempt2_diagram.png|500]]

**What's wrong:** Worst-case load imbalance is $\Omega(n)$. A single random sample of $p - 1$ splitters gives **no guarantee** on partition quality. You could end up sending nearly all $n$ elements to one processor.

**The lesson:** We need _more_ samples and a systematic way to choose splitters that provably guarantee bounded load imbalance.

---

## The Actual Sample Sort: Regular Sampling

This is the algorithm. Know it cold.

### Step 1: Local Sort

Each processor sorts its $n/p$ elements.

$$T_{comp}^{(1)} = O\left(\frac{n}{p}\log\frac{n}{p}\right)$$

### Step 2: Find Good Splitters via Regular Sampling

This is the heart of the algorithm. It has **four sub-steps:**

**(2a) Pick local splitters:** Each processor picks $p - 1$ equally spaced elements from its local sorted array. These are the **local splitters**.

With $n/p$ elements per processor, the local splitters are at indices approximately $k \cdot \frac{n}{p^2}$ for $k = 1, 2, \ldots, p-1$. The spacing between consecutive local splitters is $\frac{n}{p^2}$ elements.

This produces $p(p-1)$ local splitters total across all processors.

**(2b) Sort all local splitters using bitonic sort:** We have $p(p-1)$ total local splitters distributed across $p$ processors (each has $p - 1 \approx p$ splitters). This is bitonic sort with problem size $\approx p^2$ on $p$ processors, so each processor has $\approx p$ elements.

Using the bitonic sort formula with $n_{splitters} = p(p-1)$, each processor holding $p - 1$ elements:

$$T_{comp}^{(2b)} = O(p \log^2 p)$$ $$T_{comm}^{(2b)} = O\left((\tau + \mu p)\log^2 p\right)$$

**(2c) Pick global splitters:** From the now-sorted array of $p(p-1)$ local splitters (distributed evenly, $p-1$ per processor after bitonic sort), pick the **last element on each processor**, excluding the last processor. This gives exactly $p - 1$ global splitters.

These global splitters are evenly spaced within the sorted collection of all local splitters — specifically at positions $p-1, 2(p-1), 3(p-1), \ldots, (p-1)(p-1)$ in the sorted splitter array.

**(2d) Allgather the global splitters:** Broadcast the $p-1$ global splitters to all processors.

$$T_{comm}^{(2d)} = O(\tau \log p + \mu p)$$

### Step 3: Partition Locally

Each processor uses binary search (or a linear scan, since both arrays are sorted) to split its local sorted data into $p$ buckets according to the $p - 1$ global splitters.

$$T_{comp}^{(3)} = O\left(\frac{n}{p}\right) \text{ (linear scan) or } O\left(p \log\frac{n}{p}\right) \text{ (binary searches)}$$

### Step 4: Many-to-Many Communication

Processor $i$ sends its $j$-th bucket to processor $j$. This is a personalized all-to-all exchange where message sizes vary.

By the Load Balance Theorem (see below), each processor receives at most $2n/p$ elements. So $R, S \leq 2n/p$, and using the many-to-many primitive:

$$T_{comm}^{(4)} = O\left(\tau p + \mu \frac{n}{p}\right)$$

### Step 5: Local Merge

Each processor merges the (up to) $p$ sorted sequences it received. Total received data is at most $2n/p$ elements.

$$T_{comp}^{(5)} = O\left(\frac{n}{p}\log p\right)$$

---

## Worked Example ($p = 3$, $n = 24$)

![[SLIDE_PLACEHOLDER_sample_sort_example.png|600]]

**Initial data distribution (8 elements per processor):**

|$P_0$|$P_1$|$P_2$|
|---|---|---|
|33, 7, 2, 5, 21, 8, 11, 17|3, 1, 30, 9, 27, 15, 22, 13|24, 6, 4, 16, 29, 18, 37, 19|

**Step 1 — Local sort:**

|$P_0$|$P_1$|$P_2$|
|---|---|---|
|2, 5, 7, 8, 11, 17, 21, 33|1, 3, 9, 13, 15, 22, 27, 30|4, 6, 16, 18, 19, 24, 29, 37|

**Step 2a — Pick local splitters ($p - 1 = 2$ per processor):**

Each processor has 8 elements, spacing is $n/p^2 = 24/9 \approx 2.67$, so pick elements at roughly positions 2 and 5 (evenly spaced):

|$P_0$|$P_1$|$P_2$|
|---|---|---|
|**7**, **17**|**9**, **22**|**16**, **24**|

**Step 2b — Sort all 6 local splitters via bitonic sort:**

Input splitters across processors: $P_0$: {7, 17}, $P_1$: {9, 22}, $P_2$: {16, 24}

After bitonic sort: $P_0$: {7, 9}, $P_1$: {16, 17}, $P_2$: {22, 24}

**Step 2c — Pick global splitters (last element on each processor, excl. last):**

- $P_0$'s last: **9**
- $P_1$'s last: **17**
- ($P_2$ excluded)

Global splitters: **9, 17**

**Step 2d — Allgather splitters:** All processors now know splitters are 9 and 17.

**Steps 3–5 — Partition, exchange, merge:**

Each processor splits its data into 3 buckets: $(\leq 9)$, $(10\text{–}17)$, $(> 17)$:

||Bucket 0 ($\leq 9$)|Bucket 1 (10–17)|Bucket 2 ($> 17$)|
|---|---|---|---|
|$P_0$|2, 5, 7, 8|11, 17|21, 33|
|$P_1$|1, 3, 9|13, 15|22, 27, 30|
|$P_2$|4, 6|16|18, 19, 24, 29, 37|

After many-to-many (send bucket $j$ to $P_j$) and local merge:

|$P_0$|$P_1$|$P_2$|
|---|---|---|
|1, 2, 3, 4, 5, 6, 7, 8, 9|11, 13, 15, 16, 17|18, 19, 21, 22, 24, 27, 29, 30, 33, 37|

Final sorted output: $1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 13, 15, 16, 17, 18, 19, 21, 22, 24, 27, 29, 30, 33, 37$

Note: $P_0$ got 9 elements, $P_1$ got 5, $P_2$ got 10. The maximum (10) is less than $2n/p = 16$, as guaranteed.

---

## Load Balance Theorem and Proof

**Theorem:** Each processor receives at most $\frac{2n}{p}$ elements.

This is the most important proof in this lecture. You must be able to reproduce it on an exam.

### Proof

Consider the elements received by any single processor. After the global splitters are determined, each processor receives all elements falling between two consecutive global splitters.

**Key observation:** Between any two consecutive global splitters (i.e., in any single processor's bucket), there are exactly $p - 1$ local splitters.

_Why?_ We had $p(p-1)$ local splitters total. After sorting them, the $p - 1$ global splitters were chosen at evenly spaced positions (every $(p-1)$-th element). So between consecutive global splitters there are exactly $p - 1$ local splitters.

**Setup:** Let $s_i$ denote the number of these $p - 1$ local splitters that originally came from processor $P_i$.

$$\sum_{i=0}^{p-1} s_i = p - 1$$

**Bounding the contribution from each processor:** On processor $P_i$, the $p - 1$ local splitters divide the local sorted array into $p$ segments, each of size at most $\frac{n}{p^2}$.

![[SLIDE_PLACEHOLDER_proof_segments.png|400]]

If $s_i$ of $P_i$'s local splitters fall in this bucket, then at most $s_i + 1$ of $P_i$'s segments can overlap with this bucket (the $s_i$ segments between consecutive local splitters, plus one on either side). Therefore:

$$\text{Max elements from } P_i < (s_i + 1) \cdot \frac{n}{p^2}$$

(Strict inequality because the boundary elements are local splitters themselves, and the segments between them have size $< n/p^2$ in the worst case.)

**Summing over all processors:**

$$\text{Total elements received} < \sum_{i=0}^{p-1}(s_i + 1)\frac{n}{p^2}$$

$$= \frac{n}{p^2}\sum_{i=0}^{p-1} s_i + \frac{n}{p^2}\sum_{i=0}^{p-1} 1$$

$$= \frac{n}{p^2}(p-1) + \frac{n}{p^2} \cdot p$$

$$= \frac{n(p-1)}{p^2} + \frac{n}{p}$$

$$= \frac{n(2p - 1)}{p^2} < \frac{2n}{p}$$

$$\boxed{\text{Each processor receives} < \frac{2n}{p} \text{ elements.} \quad \square}$$

---

## Total Complexity

### Computation

$$T_{comp} = \underbrace{O\left(\frac{n}{p}\log\frac{n}{p}\right)}_{\text{Step 1: local sort}} + \underbrace{O(p\log^2 p)}_{\text{Step 2b: bitonic sort of splitters}} + \underbrace{O\left(\frac{n}{p}\log p\right)}_{\text{Step 5: local merge}}$$

$$= O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log p + p\log^2 p\right)$$

Since $\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log p = \frac{n}{p}\left(\log\frac{n}{p} + \log p\right) = \frac{n}{p}\log n = \frac{n \log n}{p}$:

$$\boxed{T_{comp} = O\left(\frac{n \log n}{p} + p\log^2 p\right)}$$

### Communication

$$T_{comm} = \underbrace{O\left((\tau + \mu p)\log^2 p\right)}_{\text{Step 2b: bitonic sort of splitters}} + \underbrace{O(\tau \log p + \mu p)}_{\text{Step 2d: allgather}} + \underbrace{O\left(\tau p + \mu \frac{n}{p}\right)}_{\text{Step 4: many-to-many}}$$

The dominant terms:

- Latency: $\tau p$ from many-to-many dominates $\tau \log^2 p$ and $\tau \log p$
- Bandwidth: $\mu \frac{n}{p}$ from many-to-many plus $\mu p \log^2 p$ from bitonic sort of splitters

$$\boxed{T_{comm} = O\left(\tau p + \mu\left(\frac{n}{p} + p\log^2 p\right)\right)}$$

---

## Optimality Condition

The algorithm is **optimal** when the splitter-finding overhead is absorbed by the main sorting work. The overhead terms are $p \log^2 p$ in computation and $\mu p \log^2 p$ in communication.

**For computation optimality:** Need $p \log^2 p = O\left(\frac{n \log n}{p}\right)$, which holds when $n > p^2 \log^2 p$ (since $\log n > \log p$ in that regime).

**For communication optimality:** Need $\mu p \log^2 p = O\left(\mu \frac{n}{p}\right)$, i.e., $p^2 \log^2 p = O(n)$.

Both are satisfied when:

$$\boxed{n > p^2 \log^2 p}$$

Under this condition, sample sort achieves:

$$T_{comp} = O\left(\frac{n \log n}{p}\right) \qquad T_{comm} = O\left(\tau p + \mu \frac{n}{p}\right)$$

This matches the computation and bandwidth lower bounds. The $\tau p$ latency term is inherent to any algorithm that does a personalized all-to-all exchange.

---

## Why Regular Sampling Works (Intuition)

The key idea: by taking $p - 1$ **evenly spaced** samples from each of $p$ processors (not just a random handful), we get $p(p-1)$ samples that are guaranteed to be "representative" of the global data distribution — regardless of the input.

Each processor's local splitters divide its sorted data into $p$ equal-sized chunks of $n/p^2$. When we sort all these local splitters globally and pick every $(p-1)$-th one, we're essentially partitioning the union of all these fine-grained chunks into $p$ roughly equal groups.

The proof shows that no bucket can "grab" more than about 2 chunks from any single processor, leading to the $2n/p$ bound.

**Contrast with random sampling:** Random samples might cluster in one region of the data, leaving huge gaps elsewhere. Regular (evenly spaced) sampling from **already sorted** local arrays avoids this by construction.

---

## Application: Permutation Routing via Sorting (HW4 Q1)

**Problem:** Each processor $P_i$ has a message $m_{ij}$ destined for processor $P_j$ (a permutation — no two sources share a destination, no two destinations share a source).

**Algorithm:** Create tuples $(j, m_{ij})$. Sort the $p$ tuples by the first element using parallel sort. The tuple $(j, m_{ij})$ ends up on processor $P_j$.

**Runtime:** $T_{comp}(p, p) + T_{comm}(mp, p)$ where $m$ is the message size.

This shows that **sorting is a general-purpose communication primitive** — any permutation routing can be solved by sorting.

---

## Special Case: Reverse-Sorted Input (HW4 Q2)

**Problem:** All elements unique, globally in decreasing order, $n/p$ per processor. After sample sort in ascending order, how many elements does each processor have?

**Answer:**

$$f(i) = \begin{cases} \frac{n}{p} - \frac{n}{p^2} & \text{if } i = 0 \[6pt] \frac{n}{p} & \text{if } 0 < i < p - 1 \[6pt] \frac{n}{p} + \frac{n}{p^2} & \text{if } i = p - 1 \end{cases}$$

**Why:** Since the input is globally decreasing, sorting locally is equivalent to reversing each local array. The local splitters, when sorted globally via bitonic sort, get reversed across processors. The global splitter selection ends up slightly asymmetric — processor 0 loses $n/p^2$ elements (its bucket boundary is shifted inward) and processor $p - 1$ gains $n/p^2$ (its bucket extends further). Middle processors are unaffected because the splitter spacing is uniform for them.

This illustrates that while the $2n/p$ bound is worst-case, the actual imbalance is often much smaller — here it's only $\pm n/p^2$.

---

## Comparison of Parallel Sorting Algorithms

|Algorithm|$T_{comp}$|$T_{comm}$|Optimal?|
|---|---|---|---|
|Lower Bound|$\Omega\left(\frac{n \log n}{p}\right)$|$\Omega\left(\mu \frac{n}{p}\right)$|—|
|Bitonic Sort|$O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log^2 p\right)$|$O\left(\tau \log^2 p + \mu \frac{n}{p}\log^2 p\right)$|No ($\log^2 p$ bandwidth factor)|
|Parallel Quicksort (best)|$O\left(\frac{n \log n}{p}\right)$|$O\left(\tau \log p + \mu \frac{n}{p}\log p\right)$|No ($\log p$ bandwidth, bad worst case)|
|Sample Sort|$O\left(\frac{n \log n}{p} + p\log^2 p\right)$|$O\left(\tau p + \mu\left(\frac{n}{p} + p\log^2 p\right)\right)$|Yes, when $n > p^2\log^2 p$|

---

## Quick Reference: Formulas to Memorize

|Quantity|Formula|
|---|---|
|Sorting lower bound (comp)|$\Omega\left(\frac{n \log n}{p}\right)$|
|Sorting lower bound (comm)|$\Omega\left(\mu \frac{n}{p}\right)$|
|Sample Sort $T_{comp}$|$O\left(\frac{n \log n}{p} + p\log^2 p\right)$|
|Sample Sort $T_{comm}$|$O\left(\tau p + \mu\left(\frac{n}{p} + p\log^2 p\right)\right)$|
|Max elements per processor|$< \frac{2n}{p}$|
|Number of local splitters|$p(p-1)$ total, $p-1$ per processor|
|Bitonic sort of splitters (comp)|$O(p\log^2 p)$|
|Bitonic sort of splitters (comm)|$O((\tau + \mu p)\log^2 p)$|
|Allgather of global splitters|$O(\tau \log p + \mu p)$|
|Optimality condition|$n > p^2 \log^2 p$|

---

## Exam Checklist

- [ ] Derive both lower bounds from scratch (especially the communication bound argument)
- [ ] Explain why bitonic sort and parallel quicksort fall short of optimal
- [ ] State all 5 steps of sample sort with sub-steps for splitter selection
- [ ] Trace through a concrete example ($p = 3$, $n = 18$ or $n = 24$)
- [ ] Reproduce the $2n/p$ load balance proof (the $s_i$ argument)
- [ ] Derive total computation and communication complexity by summing step costs
- [ ] State and justify the optimality condition $n > p^2\log^2 p$
- [ ] Explain why regular sampling beats random sampling
- [ ] Solve HW4-style problems: permutation routing via sorting, reverse-sorted input analysis