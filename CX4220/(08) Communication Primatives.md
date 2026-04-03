## Broadcast

Say we want to broadcast a value with root = 0 ![[Pasted image 20260218111036.png|center|500]]

- We can use divide and conquer to distribute
- Takes $\log(p)$ steps

How do we actually choose which to send?

1. We start with 000 and send to 100 — bottom 2 bits remain the same (0)
2. We now use 000 and send to 010, 100 to send to 110 — bottom 1 bit remains the same (0)

```
   _ _ _ x x x
&& 0 0 0 1 1 1
--------------
   0 0 0 x x x
```

Use a bitmask for the bottom d bits

### Pseudocode

```
flip <- 1 << (d-1)   // flip (d-1)th bit
mask <- flip - 1     // subtract by 1 to get d mask

for j = d-1 to 0 do
	if((rank AND mask) == 0)              // are all bottom d bits zero?
		if((rank AND flip) == 0)            // is d-1th bit 0?
			send x to (rank XOR flip)         // send to flipped rank
		else
			receive x from (rank XOR flip)    // if it isn't the one to send, receive
	mask <- mask >> 1                     // shrink active region
	flip <- flip >> 1                     // move to next dimension
```

### Edge Cases

What if p isn't $2^d$?

- We find $p'$ such that it is a power of 2 where $\frac{p'}{2} < p \leq p'$
- We run the code like it has $p'$ processors and ignore communications to/from non-existent processors ($\text{rank} \geq p$)

$$\Theta(\tau \log p + \mu \cdot m \cdot \log p)$$

Despite being parallel, every processor that doesn't have the message still needs a message — minimum $p-1$ messages sent.

### What if root is not processor 0?

- Naive: send root's data to processor 0 first
- One communication in $\Theta(\tau + \mu m)$
- Does not change overall complexity

Better approach: use **virtual ranks** via XOR with root.

![[Pasted image 20260218113014.png|center|400]]

### Pseudocode for Root ≠ 0

```
flip <- 1 << (d-1)
mask <- flip - 1

for j = d-1 to 0 do
	if(((rank XOR root) AND mask) == 0)     // virtual rank check
		if(((rank XOR root) AND flip) == 0)
			send x to (rank XOR flip)            // XOR trick: virtual → real cancels out
		else
			receive x from (rank XOR flip)
	mask <- mask >> 1
	flip <- flip >> 1

// Why (rank XOR flip) and not something more complex?
// (rank XOR root) -- who am I? (virtual)
// XOR flip        -- who do I send to? (virtual)
// XOR root        -- who do I send to? (real)
// The XOR with root cancels: (rank XOR root XOR flip XOR root) = rank XOR flip
```

This saves us the extra initial send to zero, and only works when $p$ is a power of 2.

## Reduce

- Reverse of broadcast
- Second half of processors sends to first half and combines (e.g., sum)
- That half sends to its first half and combines
- Repeat until all data is at root (processor 0)

![[Pasted image 20260401134651.png|500]]

$$\Theta(\tau \log p + \mu \cdot m \cdot \log p)$$

## AllReduce

- Like reduce, but every processor ends up with the result
- Both halves send to each other and perform the operation simultaneously
- In each subhalf, send to the other subhalf and perform the operation again
- Repeat until finished (butterfly pattern)

![[Pasted image 20260401142121.png|500]]

$$\Theta(\tau \log p + \mu \cdot m \cdot \log p)$$

## Scan

(parallel prefix sum == scan)

- Each processor $P_i$ ends up with the reduction of values from $P_0$ through $P_i$

$$\Theta(\tau \log p + \mu \cdot m \cdot \log p)$$

## Gather

![[Pasted image 20260401142146.png|500]]

- Not a reduce — no combining/operation is performed
- **Concatenates** the data into a **larger** message at the root
- At each step of the tree, the message being forwarded **doubles** in size
- Message sizes: $m, 2m, 4m, \ldots, \frac{p}{2}m$

$$\Theta(\tau \log p + \mu \cdot m \cdot p)$$

Bandwidth term is $m(1 + 2 + 4 + \cdots + \frac{p}{2}) = m(p-1) = \Theta(m \cdot p)$.

## AllGather

- Like gather, but every processor ends up with the full concatenated data
- Follow same pattern as AllReduce (both halves exchange with each other)

![[Pasted image 20260401142158.png|500]]

### In-place AllGather

Instead of copying/rearranging arrays at each step, use a distance-doubling scheme:

1. Communicate distance 1 — each processor swaps with its neighbor, now has 2 blocks
2. Communicate distance 2 — swap 2-block chunks, now has 4 blocks
3. Communicate distance 4 — swap 4-block chunks, now has 8 blocks
4. Continue until everyone has all $p$ blocks

![[Pasted image 20260401142218.png|400]]

![[Pasted image 20260401142230.png|400]]

![[Pasted image 20260401142243.png|400]]

![[Pasted image 20260401142255.png|400]]

Appending arrays is straightforward — no complex index rearranging needed.

$$\Theta(\tau \log p + \mu \cdot m \cdot (1 + 2 + \cdots + \frac{p}{2})) = \Theta(\tau \log p + \mu \cdot m \cdot p)$$

## Scatter

Reverse of gather — root has data of size $m \cdot p$ and distributes unique pieces to each processor.

1. Root sends half the data to a partner processor
2. Both halve again and send to partners
3. Continue via hypercubic splitting until everyone has their piece
4. Message sizes shrink: $\frac{mp}{2}, \frac{mp}{4}, \ldots, m$

![[Pasted image 20260401142324.png|500]]

$$\Theta(\tau \log p + \mu \cdot m \cdot p)$$

## All-to-All

Every processor sends a unique message of size $m$ to every other processor. Think of it as transposing a matrix of messages: $m_{ij}$ is the message from $P_i$ to $P_j$.

### Arbitrary Permutation

**Naive approach (bad):**

```
for j = 0 to (p-1) do
	P_i sends m_{i,j} to P_j
```

This serializes communication — everyone tries to send at the same time in each round.

$$O(\tau \cdot p^2 + \mu \cdot m \cdot p^2)$$

**Shift-based approach (good):**

```
for k = 1 to (p-1) do
	P_i sends m_{i, (i+k) mod p} to P_{(i+k) mod p}
```

Each round is a cumulative right-shift — every processor sends exactly one message and receives exactly one message per round, so no conflicts.

$$O(\tau \cdot p + \mu \cdot m \cdot p)$$

$p-1$ communication rounds, each with a single message of size $m$. Total data sent per processor: $m \cdot (p-1) \approx m \cdot p$.

### Hypercubic Permutation

1. Each round corresponds to one hypercube dimension ($\log p$ rounds total)
2. In each round, a processor exchanges **half** of its current data with its partner across that dimension
3. Each processor acts as a **relay** for other processors' data — it holds and forwards messages on behalf of others

![[Pasted image 20260401142634.png|500]]

Example on P0 with $p = 8$:

1. Start: P0 holds all 8 of its outgoing messages (total size $mp$)
2. Step 1 → exchange half with processor 4: sends $\frac{mp}{2}$, receives $\frac{mp}{2}$ (still holds $mp$ total)
3. Step 2 → exchange half with processor 2: sends $\frac{mp}{2}$, receives $\frac{mp}{2}$
4. Step 3 → exchange half with processor 1: sends $\frac{mp}{2}$, receives $\frac{mp}{2}$

Each of $\log p$ steps sends $\frac{mp}{2}$ data.

$$O(\tau \cdot \log p + \mu \cdot m \cdot p \cdot \log p)$$

### Which one should you pick?

**It depends on the message size.**

- **Large messages / small p** → arbitrary wins: $O(\tau \cdot p + \mu \cdot m \cdot p)$ — better bandwidth (no $\log p$ penalty)
- **Small messages / large p** → hypercubic wins: $O(\tau \cdot \log p + \mu \cdot m \cdot p \cdot \log p)$ — better latency ($\log p$ vs $p$ rounds)

## Many-to-Many

Variable message sizes between arbitrary pairs.

- $m_{ij}$: message from $P_i$ to $P_j$, with $|m_{ij}|$ possibly 0
- $S = \max_i \sum_j |m_{ij}|$ — max total send volume from any processor
- $R = \max_j \sum_i |m_{ij}|$ — max total receive volume at any processor

### Stage 1: Distribute message fragments to intermediaries

- Each processor splits its outgoing messages into $p$ pieces (one per intermediate processor)
- All-to-All with max message size $\leq \frac{S}{p}$

### Stage 2: Route message fragments to final destinations and assemble

- Each intermediate processor forwards fragments to actual destinations
- All-to-All with max message size $\leq \frac{R}{p}$

**Stage 1:** $\Theta(\tau \cdot p + \mu \cdot \frac{S}{p} \cdot p) = \Theta(\tau \cdot p + \mu \cdot S)$

**Stage 2:** $\Theta(\tau \cdot p + \mu \cdot \frac{R}{p} \cdot p) = \Theta(\tau \cdot p + \mu \cdot R)$

$$\text{Total: } \Theta(\tau \cdot p + \mu \cdot (R + S))$$

### How does each processor know which fragments go where?

We need to attach metadata (destination info) to each fragment, increasing each message size by a small amount (~$p$ words of overhead).

This modifies the runtime to:

- Stage 1: $\Theta(\tau \cdot p + \mu \cdot (\frac{S}{p} + p) \cdot p)$
- Stage 2: $\Theta(\tau \cdot p + \mu \cdot (\frac{R}{p} + p) \cdot p)$

$$\text{Total: } \Theta(\tau \cdot p + \mu \cdot (R + S + p^2))$$

Which simplifies to $\Theta(\tau \cdot p + \mu \cdot (R + S))$ provided $p^2 = O(S + R)$.

## Summary

|Primitive|Runtime|
|---|---|
|Broadcast, Reduce, AllReduce, Scan|$\Theta(\tau \log p + \mu \cdot m \cdot \log p)$|
|Gather, AllGather, Scatter|$\Theta(\tau \log p + \mu \cdot m \cdot p)$|
|All-to-All (Arbitrary)|$O(\tau \cdot p + \mu \cdot m \cdot p)$|
|All-to-All (Hypercubic)|$O(\tau \cdot \log p + \mu \cdot m \cdot p \cdot \log p)$|
|Many-to-Many|$\Theta(\tau \cdot p + \mu \cdot (R + S))$ when $p^2 = O(S + R)$|