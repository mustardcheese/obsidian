## Bitonic Sort Practice Problems

---

**Q1 — Algorithm design (medium)**

You are given two bitonic sequences S1 and S2 of length n/2 each, distributed
across p processors (n/p elements per processor). S1 lives on P0...P(p/2-1)
and S2 on P(p/2)...P(p-1). Design a parallel algorithm to produce a single
globally sorted sequence of length n, and give its computation and
communication runtimes.

**Answer:**
Since S1 and S2 are both bitonic sequences, we can perform a bitonic merge across all processors. This merge takes in two bitonic sequences and outputs one fully sorted sequence. This is equivalent to the final merge step in a bitonic sort and will require logp communications, sending block sizes of n/p. No local comp needed as S1 and S2 are already bitonic. T_comm = (taulogp + mu(n/p)logp) = T_total.

---

**Q2 — Runtime analysis (medium)**

Suppose n = p^2 (many more elements than processors). Simplify the total
runtime of bitonic sort as much as possible. Which term dominates — the local
sort or the merge network? What does this tell you about where time is spent
when data is large relative to p?

**Answer:**


---

**Q3 — Optimality reasoning (hard)**

The communication lower bound for parallel sorting is Ω(μ · n/p). Bitonic sort
achieves O(μ · n/p · log²p). By what factor is bitonic sort suboptimal in
communication, and where exactly does that factor come from structurally in the
algorithm? Can it be eliminated while keeping the bitonic approach?

**Answer:**

---

**Q4 — Modified input (hard)**

You are given n elements already sorted in ascending order, distributed across p
processors in block decomposition. You want to reverse the entire sequence (i.e.,
produce a globally descending sorted order). Can you do better than running full
bitonic sort? If so, give the algorithm and its runtime.

**Answer:**

---

**Q5 — Constraint reasoning (medium)**

Bitonic sort requires p to be a power of 2. A colleague proposes rounding p up
to the next power of 2 and filling the extra virtual processors with +infinity.
What is the cost of this approach in the worst case? Is there a scenario where
this padding strategy is particularly wasteful?

**Answer:**
```
