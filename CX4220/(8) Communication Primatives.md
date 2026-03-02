## Broadcast

Say we want to broadcast a value with root = 0
![[Pasted image 20260218111036.png|center|500]]
- We can use divide and conquer to distribute
- Takes log(p) steps

How do we actually choose which to send?

1. We start with 000 and send to 100 — bottom 2 bits remain the same (0)
2. We now use 000 and send to 010, 100 to send to 110 — bottom 1 bits remain the same (0)
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
mask <- flip - 1     // subract by 1 to get d mask

for j = d-1 to 0 do
	if((rank AND mask) == 0)              // are all bottom d bits zero?
		if((rank AND flip) == 0)            // is d-1th bit 0?
			send x to (rank XOR flip)         // send to flipped rank
		else
			recieve x from (rank XOR flip)    // if it isn't the one to send recieve
	mask <- mask << 1                     // change bits
	flip <- flip >> 1
```

### Edge Cases
What if p isn’t $2^d$ ?

- We find p’ such that it is a power of t where $\frac{p’}{2} < p < p’$
- We run the code like it has p’ processors and ignore for non-existent processors

Runtime

- $\Theta(\tau logp + \mu m logp)$

Despite being parallel, every processor that doesn’t have a message still needs a message, minimum p-1 messages sent

What if root is not processor 0?

- Naive: send root to processor 0
- One communication in $\Theta(\tau + \mu m)$

Runtime of the algorithm does not change

![[Pasted image 20260218113014.png|center|400]]
### Pseudocode for Root ≠ 0

```
flip <- 1 << (d-1)   // same as regular pseudocode
mask <- flip - 1

for j = d-1 to 0 do
	if((rank AND mask) == 0)
		if((rank AND flip) == 0)
			send x to (rank XOR flip) // send is special
		else
			recieve x from (rank XOR flip)
			
	mask <- mask << 1
	flip <- flip >> 1

// (rank XOR root) -- who am I? (virtual)
// XOR flip        -- who do I send to? (virtual)
// XOR root        -- who do I send to? (real)
// the xors happen to cancel to rank XOR flip
```

This will save us the 1 operation in the beginning sending to zero

- This only works when p is a power of 2

## Reduce

1. Second half of processors sends to first half
2. That half sends to half
3. Repeat until all at zero

![image.png](attachment:e74dcd13-f2c9-4a3d-9ffb-37f60152177f:image.png)

$\Theta(\tau logp + \mu m logp)$ runtime

## AllReduce

1. Each half sends to each other and performs action
2. In each subhalf sends to other half again and performs action
3. Repeat until finished

![image.png](attachment:4a0c7858-c8f9-4bfb-90f1-4d3f79c1ac81:image.png)

$\Theta(\tau logp + \mu m logp)$ runtime

## Scan

$\Theta(\tau logp + \mu m logp)$

## Gather

![image.png](attachment:af0d6f3c-3713-442a-b316-55e92061b23b:image.png)

- Not a reduce, a gathering
- **Combines** the data into **larger** data

## AllGather

- follow same pattern as allreduce

![image.png](attachment:59af88b3-d93a-4775-bd91-13964c821d07:image.png)

When you gather, the extra cost comes in the copying oepration done by the processors. Instread we use

### In-place AllGather

1. Communicate distance 1
2. Communicate distance 2

![image.png](attachment:018c6994-321e-4808-8d04-e4efa45978a6:image.png)

![image.png](attachment:9fda8597-a190-4aed-b51c-99154df1b5d4:image.png)

![image.png](attachment:066aea64-388b-4da3-a04f-9a74e8e702b9:image.png)

![image.png](attachment:27d70848-f3c6-4a53-af9d-baabb566cab7:image.png)

Appending arrays are relatively staightforward, unlike straight up copying and figuring out arrays

Runtime: $\Theta(\tau logp + \mu \cdot m \cdot (1 + 2 + … + \frac{p}{2}))$ = $\Theta(\tau logp + \mu \cdot m \cdot p)$

## Scatter

Reverse of gather, like a broadcast but not the same data every time

1. Send to one processor, update the data
2. Hypercubic send until everyone has the data

![image.png](attachment:4ac05f9b-34dc-4e69-a502-360c1283d620:image.png)

## All-to-All

Essentially just a matrix transpose

![image.png](attachment:77f8fb2e-345e-45f3-a484-53269316c171:image.png)

![image.png](attachment:64fa466c-8939-47ca-851f-755d16bde2a2:image.png)

### Arbitrary Permutation

```
for j = 0 to (p-1) do 
	P_i sends to m_i,j to P_j
```

This is not efficient, causes a serialization issue

$O(\tau \cdot p^2 + \mu \cdot m \cdot p^2)$

```
for j = 1 to (p-1) do
	P_1 sends m_(i, (i+k)modp) to P(i + j modp) 
```

This is pretty much just a rightshift, cumulatively

$O(\tau \cdot p + \mu \cdot m \cdot p)$

### Hypercubic Permutation

1. half of the processors each send half of their message to the other half of processors
2. Compute until everything is distributed

![image.png](attachment:0545ba48-2c05-4253-addb-67978ebd29c0:image.png)

![image.png](attachment:42ff4e2f-1258-4fba-ad06-02bc360eb622:image.png)

1. Regular data goes out → processor 4
2. Interleave data after recieving from processor 4, data goes out → processor 2
3. Interleave data after recieving from processor 2, data goes out → processor 1
4. Interleave data after recieving from processor 1

$O(\tau \cdot logp + \mu \cdot m \cdot p \cdot logp)$

_Which one should you pick?_

**It depends on the message size.**

- Extremely large numbers or small message p, arbitrary will outperform
    
    $O(\tau \cdot p + \mu \cdot m \cdot p)$
    
- Smaller numbers or lots more processors, hypercubic will outperform
    
    $O(\tau \cdot logp + \mu \cdot m \cdot p \cdot logp)$
    

## Many-to-Many

Variable message sizes

**For 4 processors:**

**Stage 1:**

Break down message and send

![image.png](attachment:6f5e3a28-3ec3-4df3-814d-b2aa58b76513:image.png)

1. Cut each message into blocks (4) to be given to a single processor
2. Concatenate each processor-indended block together, into a block of size $\frac{m}{4}$

**Stage 2:**

Route message fragments to destinations and assemble

Max message size $\leq \frac{R}{p}$

Runtime **(1)**: $\Theta(\tau \cdot p + \mu \cdot m \cdot p)$

Runtime **(2)**: $\Theta(\tau \cdot p + \mu \cdot \frac{R}{p} \cdot p)$ = $\Theta(\tau \cdot p + \mu \cdot (R + S))$

This is slower than all-to-all. Truly only good for variable sized massages

### How does each processor know which fragments go where?

We need to attach some information to the message to identify

- Increases each message size with a tiny bit of data

$\Theta(\tau \cdot p + \mu \cdot (\frac{R}{p} + p) \cdot p)$ = $\Theta(\tau \cdot p + \mu \cdot (R + p^2))$
