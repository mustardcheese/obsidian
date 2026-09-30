# Bitonic Sort

## Why Not Parallel Merge Sort?

Sequential merge sort: divide list in half, sort each, merge.

$$T(n) = 2T\left(\frac{n}{2}\right) + O(n) = O(n \log n)$$

Parallelize by assigning each half to half the processors:

$$T(n, p) = T\left(\frac{n}{2}, \frac{p}{2}\right) + O(n)$$

The merge step is **sequential** $O(n)$ — you have to scan both sorted lists together. Unrolling:

$$T(n, p) = T\left(\frac{n}{p}, 1\right) + O\left(n + \frac{n}{2} + \frac{n}{4} + \cdots + \frac{n}{p/2}\right) = O\left(\frac{n}{p}\log\frac{n}{p} + n\right)$$

The $O(n)$ term dominates. Can't effectively use more than $\log n$ processors — the merge is the bottleneck.

![[SLIDE_PLACEHOLDER_parallel_merge_sort_recurrence.png|500]]

### The Key Insight

Given two sorted lists $l_1$ (ascending) and $l_2$ (ascending), the concatenation $l_1 \| \text{rev}(l_2)$ is a **bitonic sequence**. This structure lets us split into two halves where every element in one half $\leq$ every element in the other — and this operation is **fully parallel** (each pair of elements can be compared independently).

![[SLIDE_PLACEHOLDER_l1_rev_l2_example.png|500]]

Example: $l_1 = 2, 6, 8, 11, 14, 19, 26, 28$ and $l_2 = 1, 4, 5, 7, 9, 10, 16, 23$.

$l_1 \| \text{rev}(l_2) = 2, 6, 8, 11, 14, 19, 26, 28, 23, 16, 10, 9, 7, 5, 4, 1$ — goes up then down, bitonic!

Taking element-wise min and max of the first half and second half:
- $l_{min} = 2, 6, 8, 9, 7, 5, 4, 1$ — all elements of $l_{min}$ are smaller
- $l_{max} = 23, 16, 10, 11, 14, 19, 26, 28$ — all elements of $l_{max}$ are larger

---

## Bitonic Sequence

**Definition:** $x_0, x_1, \ldots, x_{n-1}$ is bitonic if $\exists k$ $(n > k \geq 0)$ such that:
- **(T1)** $x_0, \ldots, x_k$ is non-decreasing and $x_{k+1}, \ldots, x_{n-1}$ is non-increasing, OR
- **(T2)** $x_0, \ldots, x_k$ is non-increasing and $x_{k+1}, \ldots, x_{n-1}$ is non-decreasing, OR
- **(T3)** There is a **cyclic shift** of the sequence that makes (T1) or (T2) true.

Intuitively: the sequence goes up then down (or down then up), possibly with a cyclic wrap.

Examples (all bitonic):
- $3, 5, 7, 10, 15, 14, 12, 9, 8, 4, 1$ — clearly T1 (up then down)
- $14, 12, 9, 8, 4, 1, 3, 5, 7, 10, 15$ — cyclic shift of the above (T3)
- $8, 4, 1, 3, 5, 7, 10, 15, 14, 12, 9$ — another cyclic shift (T3)

Note: any sorted sequence is trivially bitonic (T1 with the non-increasing part empty, or T2 with the non-decreasing part empty). Any sequence of length 1 or 2 is bitonic.

---

## Bitonic Split

**Definition:** Given a bitonic sequence $l = x_0, x_1, \ldots, x_{n-1}$ (even length $n$), decompose it into:

$$l_{min} = \min(x_0, x_{n/2}),\ \min(x_1, x_{n/2+1}),\ \ldots,\ \min(x_{n/2 - 1}, x_{n-1})$$

$$l_{max} = \max(x_0, x_{n/2}),\ \max(x_1, x_{n/2+1}),\ \ldots,\ \max(x_{n/2 - 1}, x_{n-1})$$

Each element at position $i$ in the first half is compared with the element at position $i + n/2$ in the second half. The smaller goes to $l_{min}$, the larger goes to $l_{max}$.

![[SLIDE_PLACEHOLDER_bitonic_split_diagram.png|500]]

### Bitonic Split Lemma

**Lemma:** Let $l$ be a bitonic sequence, and $l_{min}$, $l_{max}$ result from its bitonic split. Then:
1. $l_{min}$ and $l_{max}$ are each **bitonic**
2. $\max(l_{min}) \leq \min(l_{max})$

This is the key property — one split cleanly separates all small elements from all large elements, *and* each half retains the bitonic structure so we can recurse.

### Proof Sketch (T1 case, $x_0 > x_{n/2}$, $k < n/2$)

![[SLIDE_PLACEHOLDER_proof_diagram.png|500]]

Consider the transition point $k$ where $l_1$ peaks. The critical comparison pairs straddle this point.

We need to show $\max(l_{min}) \leq \min(l_{max})$.

- $\max(l_{min}) = \max(x_k, y_{n-k-2})$ — these are at the boundary where min/max assignments change
- $\min(l_{max}) = \min(x_{k+1}, y_{n-k-1})$

Four inequalities establish the result:
1. $x_k \leq x_{k+1}$ — because $l_1$ is sorted (non-decreasing part)
2. $x_k \leq y_{n-k-1}$ — transition after $k$ means $x_k$ is still in the ascending part, $y_{n-k-1}$ is in the portion that maps to $l_{max}$
3. $y_{n-k-2} \leq x_{k+1}$ — transition after $k$ means elements crossing the boundary swap roles
4. $y_{n-k-2} \leq y_{n-k-1}$ — because $l_2$ is sorted

Together: $\max(x_k, y_{n-k-2}) \leq \min(x_{k+1}, y_{n-k-1})$ $\implies$ $\max(l_{min}) \leq \min(l_{max})$. $\square$

### Sub-Lemma (Cyclic Shifts)

**Sub-Lemma:** Let $l$ be bitonic and $l'$ be a cyclic shift of $l$. If we bitonic-split $l$ into $l_{min}, l_{max}$ and $l'$ into $l'_{min}, l'_{max}$, then $l'_{min}$ is a cyclic shift of $l_{min}$ and $l'_{max}$ is a cyclic shift of $l_{max}$.

This handles **T3 sequences**: cyclic shifting doesn't change the bitonic nature, and the split result is just a shifted version. So the lemma holds for all three types.

![[SLIDE_PLACEHOLDER_sublemma_cyclic_shift.png|500]]

### Odd-Length Extension (HW3)

Standard split assumes even length. For **odd-length** bitonic sequences:
1. **Duplicate** the last element and append it (sequence is still bitonic)
2. Perform the split normally on the now-even-length sequence
3. **Remove** the marked duplicate from whichever half it ends up in

Important: you **cannot** pad with $\pm\infty$ or INT_MAX/INT_MIN because that would break the bitonic property.

---

## Bitonic Merge

**Bitonic merge** = turning a bitonic sequence into a sorted sequence by **repeated bitonic splits**.

Algorithm:
1. Bitonic split the sequence → $l_{min}$ (all small) and $l_{max}$ (all large), each of size $n/2$, each bitonic
2. Recursively bitonic-merge $l_{min}$ and $l_{max}$ independently
3. Concatenate: sorted $l_{min}$ followed by sorted $l_{max}$

Depth of recursion: $\log n$ (halving the size each time).

![[SLIDE_PLACEHOLDER_bitonic_merge_recursive.png|500]]

In the parallel setting (one element per processor on a hypercube):

$$BM(p, p) = O(\log p)$$

Each level of the recursion is one communication round — processors that differ in one bit exchange values and keep min or max. That's $\log p$ rounds total.

---

## Bitonic Sort Algorithm

### High-Level Idea

Bitonic sort builds a sorted sequence **bottom-up** from pairs:
1. Start: each processor holds one element (trivially sorted)
2. **Stage $i$** ($i = 0, 1, \ldots, \log p - 1$): merge pairs of sorted subsequences of size $2^i$ into sorted subsequences of size $2^{i+1}$
   - Within each pair, one subsequence is sorted ascending and the other descending — their concatenation is **bitonic**
   - Apply bitonic merge to sort the bitonic sequence
3. The direction alternates: even-indexed groups sort ascending ($\uparrow$), odd-indexed groups sort descending ($\downarrow$). This ensures that when adjacent groups are concatenated in the *next* stage, the result is bitonic.

### Pseudocode (n = p, one element per processor)

```
for i = 0 to (log p) - 1 do          // stage i: merge groups of size 2^(i+1)
  for j = i downto 0 do              // inner loop: bitonic merge rounds
    if (i+1)-st bit of rank is 0 then
      Compare_Exchange↑ with (Rank XOR 2^j)
    else
      Compare_Exchange↓ with (Rank XOR 2^j)
  endfor
endfor
```

![[SLIDE_PLACEHOLDER_bitonic_sort_pseudocode_and_network.png|500]]

**How to read the pseudocode:**
- **Outer loop** ($i$): which stage we're in — we're building sorted groups of size $2^{i+1}$
- **Inner loop** ($j = i$ downto $0$): the $\log$-depth bitonic merge for that stage. In round $j$, processor communicates with partner at distance $2^j$ (via XOR)
- **Direction bit**: the $(i+1)$-st bit of the processor's rank determines ascending ($\uparrow$) vs descending ($\downarrow$)
- **Compare_Exchange$\uparrow$**: two processors exchange values; the lower-ranked one keeps the min, the higher-ranked one keeps the max
- **Compare_Exchange$\downarrow$**: opposite — lower-ranked keeps the max, higher-ranked keeps the min

### Worked Example (p = 8)

![[SLIDE_PLACEHOLDER_bitonic_sort_8proc_example.png|600]]

With $p = 8$ processors (ranks 000 through 111):
- $BM(2,2)$: pairs exchange across bit 0. Groups of 2 become sorted (alternating $\uparrow\downarrow$)
- $BM(4,4)$: groups of 4 become sorted — first exchange across bit 1, then bit 0. Alternating $\uparrow\downarrow$
- $BM(8,8)$: all 8 become globally sorted — exchange across bit 2, then bit 1, then bit 0

Total rounds: $1 + 2 + 3 = 6 = \frac{3 \times 4}{2} = \frac{\log p (\log p + 1)}{2}$

---

## Complexity Analysis: n = p Case

### Counting Rounds

$$BS(p, p) = BM(2,2) + BM(4,4) + \cdots + BM(p,p)$$

$BM(2^{i+1}, 2^{i+1})$ takes $i + 1$ rounds (inner loop from $j = i$ down to $0$).

$$BS(p, p) = \sum_{i=0}^{\log p - 1} (i + 1) = 1 + 2 + 3 + \cdots + \log p = \frac{\log p (\log p + 1)}{2} = O(\log^2 p)$$

### Computation

Each round is a single compare-exchange (one comparison): $O(1)$ per round, $O(\log^2 p)$ total.

$$T_{comp}(p, p) = O(\log^2 p)$$

### Communication

Each round: one message of size 1 (one element exchanged), with latency $\tau$ and per-word cost $\mu$.

$$T_{comm}(p, p) = O(\tau \log^2 p + \mu \log^2 p)$$

---

## The n > p Case

When $n > p$, each processor holds $n/p$ elements. We can't do single-element compare-exchanges anymore.

### Algorithm

**Step 1:** Each processor **locally sorts** its $n/p$ elements.

$$T_{local\ sort} = O\left(\frac{n}{p} \log \frac{n}{p}\right)$$

**Step 2:** Run the same bitonic sort network ($\log^2 p$ rounds), but replace **Compare_Exchange** with **Merge_Split**.

### What is Merge_Split?

When two processors (each holding $n/p$ sorted elements) need to do a compare-exchange:

1. They **exchange** their full arrays with each other (each sends $n/p$ elements)
2. Each processor now has $2 \cdot n/p$ elements
3. They **merge** the two sorted arrays (since both were already sorted, this is a linear merge)
4. The lower-ranked processor keeps the **bottom** $n/p$ elements, the higher-ranked keeps the **top** $n/p$ elements

Each Merge_Split:
- **Computation:** $O(n/p)$ — merging two sorted arrays of size $n/p$
- **Communication:** one message of size $n/p$ sent and one received

### Total Complexity Derivation

There are $\log^2 p$ rounds of Merge_Split (same network structure as $n = p$).

**Computation:**

$$T_{comp} = \underbrace{O\left(\frac{n}{p} \log \frac{n}{p}\right)}_{\text{Step 1: local sort}} + \underbrace{O\left(\frac{n}{p} \cdot \log^2 p\right)}_{\text{Step 2: } \log^2 p \text{ merge-splits, each } O(n/p)}$$

$$\boxed{T_{comp}(n, p) = O\left(\frac{n}{p} \log \frac{n}{p} + \frac{n}{p} \log^2 p\right)}$$

**Communication:**

Each of $\log^2 p$ rounds: one message of size $n/p$, incurring latency $\tau$ and bandwidth cost $\mu \cdot n/p$.

$$\boxed{T_{comm}(n, p) = O\left(\tau \log^2 p + \mu \frac{n}{p} \log^2 p\right)}$$

---

## Comparison to Lower Bounds

Lower bounds for distributed memory parallel sort:

$$\text{Computation: } \Omega\left(\frac{n \log n}{p}\right) \qquad \text{Communication: } \Omega\left(\mu \frac{n}{p}\right)$$

Bitonic sort vs. these bounds:

| | Bitonic Sort | Lower Bound | Gap |
|---|---|---|---|
| Computation | $O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log^2 p\right)$ | $\Omega\left(\frac{n \log n}{p}\right)$ | Extra $\log^2 p$ vs $\log n$ factor |
| Communication (bandwidth) | $O\left(\mu \frac{n}{p} \log^2 p\right)$ | $\Omega\left(\mu \frac{n}{p}\right)$ | Extra $\log^2 p$ factor |
| Communication (latency) | $O(\tau \log^2 p)$ | — | — |

The $\log^2 p$ factor in the bandwidth term is the main weakness — every element moves $\log^2 p$ times. This motivates **Sample Sort** (Lecture 10), which achieves optimal $O(\mu \cdot n/p)$ communication for $n > p^2 \log^2 p$.

---

## HW3 Problem: Sorting Two Bitonic Sequences (Exam Pattern)

**Problem:** Given two bitonic sequences $S_1$ and $S_2$ of length $n/2$ each, distributed across $p$ processors ($S_1$ on first $p/2$, $S_2$ on last $p/2$). Sort them into a single sorted sequence $S$.

**Algorithm:**
1. Bitonic Merge $S_1$ ascending on the first $p/2$ processors → sorted $S_3$. Concurrently, Bitonic Merge $S_2$ descending on the last $p/2$ processors → sorted $S_4$.
2. Now $S_3 \| S_4$ is bitonic (ascending then descending). Bitonic Merge the whole thing on all $p$ processors.

**Runtime:**
- Computation: $O\left(\frac{n}{p} \log p\right)$
- Communication: $O\left(\tau \log p + \mu \frac{n}{p} \log p\right)$

Note: this is a **single** bitonic merge (not a full sort), so it's $O(\log p)$ not $O(\log^2 p)$.

---

## Quick Reference: Formulas to Memorize

| Quantity | n = p | n > p |
|---|---|---|
| Bitonic Merge rounds | $\log p$ | $\log p$ |
| Bitonic Sort rounds | $\frac{\log p(\log p + 1)}{2} = O(\log^2 p)$ | $O(\log^2 p)$ |
| $T_{comp}$ | $O(\log^2 p)$ | $O\left(\frac{n}{p}\log\frac{n}{p} + \frac{n}{p}\log^2 p\right)$ |
| $T_{comm}$ | $O(\tau \log^2 p + \mu \log^2 p)$ | $O\left(\tau \log^2 p + \mu \frac{n}{p}\log^2 p\right)$ |
| Per round cost | $O(1)$ comp, size-1 message | $O(n/p)$ comp, size-$n/p$ message |