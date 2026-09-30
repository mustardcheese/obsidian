# Embeddings

**Core idea:** You designed an algorithm for a **source** network topology (ring, mesh, tree), but the machine you have is a **target** network (hypercube). An embedding maps source nodes/edges onto target nodes/edges so you can run the algorithm on the target without redesigning it.

![[SLIDE_PLACEHOLDER_embedding_source_target_diagram.png|400]]

We care about the case where the target supports **(relaxed) hypercubic permutations** — i.e., the target can efficiently route any communication pattern where each processor sends to a partner that differs in at most one bit.

---

## Performance Metrics

Given embedding of source graph $G(V, E)$ into target graph $G'(V', E')$:

**Dilation:** Maximum number of edges in $E'$ that any single edge in $E$ is mapped to. In other words, the worst-case stretch — the farthest apart two source-neighbors end up in the target.

**Congestion:** Maximum number of edges from $E$ that are mapped onto a single edge in $E'$. In other words, the most "traffic" any single target link has to carry.

**Load:** Maximum number of nodes in $V$ that map to a single node in $V'$. If load > 1, multiple source nodes share one physical processor.

**Expansion:** Ratio $|V'| / |V|$. If expansion > 1, we're wasting target processors.

**Impact on runtime:**

- Computation slows down by a factor of **Load**
- Communication slows down by a factor of **Congestion $\times$ Dilation**
- Expansion > 1 means wasted resources

**Ideal embedding (a "mapping"):** Load = Congestion = Dilation = 1. When this holds, the parallel runtime on the target is **identical** to the source — efficiency is perfectly preserved.

**Key insight:** Even with a perfect mapping, there _might_ exist a different algorithm designed directly for the target that is more efficient. But if the source algorithm is already optimally efficient, this concern vanishes.

---

## Gray Codes

Gray codes are the fundamental tool for all the embeddings in this lecture. A $d$-bit Gray code is an ordering of all $2^d$ binary strings such that consecutive entries differ in exactly one bit.

### Binary Reflected Gray Code (BRGC)

Constructed recursively by **reflection**:

- 1-bit: $0, 1$
- 2-bit: prepend $0$ to the 1-bit code, then prepend $1$ to the **reversed** 1-bit code → $00, 01, 11, 10$
- 3-bit: prepend $0$ to the 2-bit code, then prepend $1$ to the **reversed** 2-bit code → $000, 001, 011, 010, 110, 111, 101, 100$

![[Pasted image 20260405232134.png|400]]

### Conversion Functions

**btog (binary to Gray):** Given a binary number $b$, compute its Gray code representation.

$$\text{btog}(b) = b \oplus (b \gg 1)$$

That is, XOR $b$ with itself right-shifted by 1. For example: $b = 5 = 101_2$, so $b \gg 1 = 010_2$, and $101 \oplus 010 = 111_2 = 7$. So btog(5) = 7, i.e., binary 5 maps to Gray code $111$.

**gtob (Gray to binary):** Given a Gray code $g$, recover the binary number. Computed bit-by-bit from MSB to LSB:

$$b_d = g_d, \quad b_i = g_i \oplus b_{i+1} \quad \text{for } i = d-1, d-2, \ldots, 0$$

The MSB stays the same; each subsequent bit is XOR of the Gray bit and the previously recovered binary bit.

### Reference Table (3-bit)

|Decimal|Binary|Gray Code|
|---|---|---|
|0|000|000|
|1|001|001|
|2|010|011|
|3|011|010|
|4|100|110|
|5|101|111|
|6|110|101|
|7|111|100|

### Why Gray codes work for embeddings

Adjacent entries in the Gray code differ in exactly one bit → they are **neighbors** in the hypercube. So if you lay out a ring/linear-array in Gray code order, every ring-neighbor pair maps to a hypercube-neighbor pair. This gives dilation = 1.

---

## Embedding a Linear Array / Ring into a Hypercube

A linear array (or ring) of $2^d$ nodes can be embedded into a $d$-dimensional hypercube using the Gray code mapping.

**Mapping:** Linear array node $i$ → hypercube node $\text{btog}(i)$.

**Recursive definition (from slides):**

$$G(0, 1) = 0, \quad G(1, 1) = 1$$

$$G(i, x+1) = \begin{cases} G(i, x) & \text{if } i < 2^x \ 2^x + G(2^{x+1} - 1 - i, x) & \text{if } i \geq 2^x \end{cases}$$

This is exactly the reflected Gray code — the first half maps normally, the second half reflects and prepends a 1 bit.

**Properties:** Congestion = 1, Dilation = 1, Expansion = 1. Consecutive array entries differ in exactly one bit, so they are hypercube neighbors.

![[Pasted image 20260405233001.png|900]]

### Ring neighbor formulas (on a hypercube)

Given a processor with hypercube rank $r$ (a $d$-bit Gray code):

- **Ring rank** of this processor: $\text{gtob}(r)$
- **Right neighbor** (hypercube rank): $\text{btog}[(\text{gtob}(r) + 1) \bmod p]$
- **Left neighbor** (hypercube rank): $\text{btog}[(\text{gtob}(r) - 1 + p) \bmod p]$

The pattern: convert to binary (ring-world) → increment/decrement in ring-world → convert back to Gray (hypercube-world).

![[SLIDE_PLACEHOLDER_ring_to_hypercube_btog_gtob.png|500]]

### Worked Example: Hypercube rank $r = 3$ ($= 011$ in binary), $p = 8$

1. Ring rank = $\text{gtob}(011) = 2$
2. Right neighbor's ring rank = $(2 + 1) \bmod 8 = 3$, so hypercube rank = $\text{btog}(3) = 010 = 2$
3. Left neighbor's ring rank = $(2 - 1 + 8) \bmod 8 = 1$, so hypercube rank = $\text{btog}(1) = 001 = 1$

**Important:** This embedding is a **relaxed hypercubic permutation** — ring communication maps to communication between processors differing in one bit, but not always the _same_ bit dimension across all processors.

---

## Embedding a Mesh into a Hypercube

A $2^r \times 2^c$ wraparound mesh (torus) can be mapped to a $2^{r+c}$-node hypercube.

### The Mapping

Mesh node $(i, j)$ → hypercube node $\text{btog}(i) | \text{btog}(j)$

where $|$ denotes bit string concatenation. The row coordinate is Gray-coded into the first $r$ bits, and the column coordinate into the last $c$ bits.

**Properties:** Congestion = 1, Dilation = 1, Expansion = 1.

### Neighbor Formulas

Given a hypercube rank $r$ as a $(r_{\text{bits}} + c_{\text{bits}})$-bit string, split as $r = y | x$ where $y$ is the first $r_{\text{bits}}$ bits and $x$ is the last $c_{\text{bits}}$ bits:

- **Mesh rank:** $(\text{gtob}(y), \text{gtob}(x))$
- **East:** $y | \text{btog}[(\text{gtob}(x) + 1) \bmod 2^c]$
- **West:** $y | \text{btog}[(\text{gtob}(x) - 1 + 2^c) \bmod 2^c]$
- **South:** $\text{btog}[(\text{gtob}(y) + 1) \bmod 2^r] | x$
- **North:** $\text{btog}[(\text{gtob}(y) - 1 + 2^r) \bmod 2^r] | x$

Each neighbor computation works the same way as the ring: decode the relevant coordinate to binary, increment/decrement, re-encode to Gray, and splice back into the full rank.

![[SLIDE_PLACEHOLDER_2x4_mesh_into_3d_hypercube.png|500]]

### Worked Example: $8 \times 8$ torus in a 64-processor hypercube

Hypercube rank 52 = $110100_2$. Split into $y = 110$ (first 3 bits) and $x = 100$ (last 3 bits).

Mesh rank: $(\text{gtob}(110), \text{gtob}(100)) = (4, 7)$

Neighbors:

- West: $(3, 7)$ → $\text{btog}(3) | \text{btog}(7) = 010 | 100 = 010100 = 20$
- East: $(5, 7)$ → $\text{btog}(5) | \text{btog}(7) = 111 | 100 = 111100 = 60$
- North: $(4, 6)$ → $\text{btog}(4) | \text{btog}(6) = 110 | 101 = 110101 = 53$
- South: $(4, 0)$ → $\text{btog}(4) | \text{btog}(0) = 110 | 000 = 110000 = 48$

### Higher-Dimensional Meshes

Generalizes naturally. For a $d_1 \times d_2 \times \cdots \times d_k$ mesh where each $d_i = 2^{b_i}$:

Mesh node $(x_1, x_2, \ldots, x_k)$ → hypercube node $\text{btog}(x_1) | \text{btog}(x_2) | \cdots | \text{btog}(x_k)$

Total hypercube dimension = $b_1 + b_2 + \cdots + b_k$.

**Example:** $8 \times 4 \times 16 \times 2 \times 8$ mesh → $2^3 \times 2^2 \times 2^4 \times 2^1 \times 2^3 = 2^{13} = 8192$ node hypercube.

Mesh node $(5, 2, 3, 1, 7)$ → $\text{btog}(5) | \text{btog}(2) | \text{btog}(3) | \text{btog}(1) | \text{btog}(7)$ = $111 | 11 | 0010 | 1 | 100$

---

## Embedding a (Non-Complete) Binary Tree into a Hypercube

This embedding handles a $p$-processor binary tree (with $\log p + 1$ levels) where **only one level is active at a time**. It is NOT a complete binary tree — it has $p$ leaves and we reuse processors across levels.

### Setup

- $p$ processors (power of 2), tree has $\log p + 1$ levels
- Root at level 0, leaves at level $\log p$
- Level $i$ has $2^i$ nodes, numbered $0, 1, \ldots, 2^i - 1$

### The Mapping

Tree node $(i, j)$ (level $i$, rank $j$ within level) is mapped to hypercube processor:

$$\text{rank} = \underbrace{j}_{i \text{ bits}} | \underbrace{00\ldots0}_{\log p - i \text{ bits}}$$

The rank $j$ occupies the leftmost $i$ bits, and the remaining bits are zeros.

![[Pasted image 20260406000631.png]]

### Which levels does a processor participate in?
A processor with hypercube rank $r$ participates in levels $(\log p)$ down to $(\log p - j)$, where $j$ = number of trailing zeros in $r$.

- **Every** processor participates at the leaf level ($\log p$)
- Only processors with at least 1 trailing zero participate at level $\log p - 1$
- Only processors with at least $k$ trailing zeros participate at level $\log p - k$
- Processor $0$ (all zeros) participates at every level, including the root

### Navigation at level $k$

Given a processor with rank $r$ participating at level $k$:

- **Parent:** flip bit $(\log p - k)$ to 0 (i.e., the bit at position $\log p - k$ from the right, 0-indexed)
- **Left child:** itself (rank $r$)
- **Right child:** flip bit $(\log p - k - 1)$ to 1

### Worked Example: $p = 32$ (5-bit ranks), level 3

Processor 28 = $11100_2$. It has 2 trailing zeros, so it participates in levels 5, 4, 3 (i.e., levels $\log 32 = 5$ down to $5 - 2 = 3$). At level 3:

- Tree rank: $(3, 111_2) = (3, 7)$
- Parent: flip bit $(5 - 3) = 2$ to 0 → $11\mathbf{0}00 = 24$
- Left child: itself = 28
- Right child: flip bit $(5 - 3 - 1) = 1$ to 1 → $111\mathbf{1}0 = 30$

Processor 18 = $10010_2$. It has 1 trailing zero, so it participates in levels 5 and 4 only — it does **not** participate at level 3.

---

## Complete Binary Tree Impossibility

**Claim:** A $p$-leaf complete binary tree ($2p - 1$ nodes) **cannot** be embedded into a $2p$-node hypercube with dilation 1 (i.e., as a mapping with congestion = dilation = 1).

### The Proof (by counting / parity argument)

**Key concept — parity of a hypercube node:** A node's parity is the number of 1-bits in its binary representation (even or odd). In a hypercube, every edge connects a node of even parity to a node of odd parity (since flipping one bit changes the parity). So the hypercube is **bipartite**: exactly $p$ nodes have even parity and $p$ nodes have odd parity.

**Argument:**

1. WLOG, assume the root is mapped to a node with an even number of zeros (equivalently, some fixed parity class).
2. In a tree, every edge connects a parent to a child. If dilation = 1, then each tree edge maps to a single hypercube edge, which means parent and child must have **opposite parity**.
3. Therefore, every _alternating_ level of the tree is mapped to the **same** parity class. The root (level 0) is in one class; levels 0, 2, 4, ... are in that class; levels 1, 3, 5, ... are in the other.
4. The entire leaf level (all $p$ leaves) is in one parity class.
5. The same parity class also contains every other internal level (the levels with the same parity as the leaf level).
6. Count the nodes in this one parity class: $p + \frac{p}{4} + \frac{p}{16} + \cdots > p$.
7. But the hypercube only has $p$ nodes of each parity. Contradiction.

Therefore, dilation-1 embedding is **impossible**.

### What CAN be done?

The **inorder traversal embedding** achieves dilation = 2. Number the nodes of a $p$-leaf complete binary tree by inorder traversal (left subtree → root → right subtree), starting from 0. This maps $2p - 1$ nodes into a $2p$-node hypercube with dilation 2.

**Proof sketch (induction):** Base case: 2-leaf tree (3 nodes) into 4-processor hypercube. Root gets rank 01, left child 00, right child 10. Dilation between root and right child is 2 (differ in 2 bits). Inductive step: the left subtree occupies subhypercube $0**\ldots*$, right subtree occupies $1**\ldots*$. By induction each subtree has dilation 2. The root is at position $p-1$, its left child at $\frac{p}{2}-1$, right child at $p + \frac{p}{2} - 1$. Left child differs in 1 bit (direct link). Right child differs in 2 bits (dilation 2).

---

## Binomial Tree Embedding (from HW4)

A binomial tree $B(d)$ of height $d$ is defined recursively: $B(0)$ is a single node; $B(d)$ is two copies of $B(d-1)$ where the root of one becomes a child of the root of the other.

**Claim:** $B(d)$ can be embedded into a $2^d$-node hypercube using hypercubic permutations (dilation = 1).

**Proof by induction:**

- Base: $B(1)$ → map root to 0, child to 1. They differ in one bit. ✓
- Inductive step: embed $B(d-1)$ onto subhypercube $0***\ldots*$ (root at $000\ldots0$) and another $B(d-1)$ onto $1***\ldots*$ (root at $100\ldots0$). These two roots differ in exactly one bit (the MSB). Make $000\ldots0$ the root of $B(d)$ by making $100\ldots0$ its child. ✓

---

## Ring to Array Embedding (from HW4)

**Claim:** A $p$-processor ring can be embedded into a $p$-processor array with dilation 2.

**Mapping:** Let $i$ be a ring processor rank and $f(i)$ its array position:

$$f(i) = \begin{cases} 2i & \text{if } i < \lceil p/2 \rceil \ 2p - 2i - 1 & \text{otherwise} \end{cases}$$

Map the first half of the ring to even positions $0, 2, 4, \ldots$ and the second half (in reverse) to odd positions $1, 3, 5, \ldots$ Neighboring ring processors end up at most 2 links apart in the array.

---

## Summary of Key Results

|Source → Target|Mapping|Dilation|Congestion|Expansion|
|---|---|---|---|---|
|Linear Array / Ring → Hypercube|Gray code: btog($i$)|1|1|1|
|$2^r \times 2^c$ Mesh → Hypercube|btog($i$) $\|$ btog($j$)|1|1|1|
|Binary Tree (shared procs) → Hypercube|$j \| 00\ldots0$|1|1|1|
|Complete Binary Tree → Hypercube|**Impossible** at dilation 1|≥ 2|—|—|
|Complete Binary Tree (inorder) → Hypercube|Inorder numbering|2|—|$> 1$ ($2p$ nodes for $2p-1$ tree)|
|Binomial Tree → Hypercube|Recursive subhypercube|1|1|1|
|Ring → Array|Evens-then-odds|2|1|1|

---

## Exam Checklist

**Must be able to:**

1. **Compute btog and gtob** by hand for any bit width (know the XOR formulas)
2. **Map a mesh/torus coordinate to a hypercube rank** and vice versa (split bits, apply gtob/btog per dimension)
3. **Find all 4 neighbors** of a mesh node on the hypercube (the East/West/North/South formulas)
4. **Determine which tree levels** a given hypercube processor participates in (count trailing zeros)
5. **Find parent/children** of a tree node at a given level on the hypercube
6. **Reproduce the complete binary tree impossibility proof** (parity / bipartite argument + counting)
7. **Prove inorder traversal gives dilation 2** (induction structure)
8. **Prove binomial tree embedding** (induction on subhypercubes)
9. **State and explain** all four performance metrics and their impact on runtime