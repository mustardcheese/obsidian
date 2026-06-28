Information is processed data, whereas knowledge is information that is modeled to be useful
- ML converts information into knowledge, but we need information first

![[Pasted image 20260601100134.png|600]]
- Data -> Info is difficult, and likely created junk data which causes issues
	- Merging and Data cleaning, 95% your time
- Info -> Knowledge, ML model
- Knowledge -> Action, your choice


## Uncertainty and Information
![[Pasted image 20260601100324.png|400]]
- The right case is more uncertain, 50/50 could go either way whereas 75/25 is likely to go one way
**Uncertainty == Entropy**

Let's say we have this information we are giving to our ML model
$X = [\text{cat, cat, cat}]$
$P(X=\text{cat})=1$ probability function, where we originally only expect cat with probability of 1
$I(x) = log_2 \frac{1}{P(x)}$, our surprise information. In the case when we only have cat, surprise information is 0

$X = [\text{cat, cat, cat, dog}]$
$P(X = \text{cat}) = \frac{3}{4} \rightarrow I(X=\text{cat})=\log_2 \frac{1}{\frac{3}{4}} = \log_2 \frac{4}{3}$
$P(X = \text{dog}) = \frac{1}{4} \rightarrow  I(X=\text{dog})=\log_2 \frac{1}{\frac{1}{4}} = \log_2 4 = 2$

Say we're reading through emails
- Words like "I, the, and" are very high, and surprise information would be low
- A phrase like "Machine Learning" are low, and so surprise information is high

### Entropy
Expected value $E[.]$, $E[g(x)] = \sum g(x)p(x)$

**Entropy** is equal to the expected value of surprised information
$E[I(x)] = \sum_{\text{cat, dog}} P(x) I(x) = (P(x=\text{cat})\cdot I(x=\text{cat}))+(P(x=\text{dog})\cdot I(x=\text{dog})) = H(x)$
- Sometimes written as H(x)


$X = [1,2,3,4,5,6]$
$P(x) = [\frac{1}{6}, \frac{1}{6}, ... \frac{1}{6}]$
$H(x) = \frac{1}{6} \cdot \log_2 6 + \frac{1}{6} \cdot \log_2 6 + \ldots + \frac{1}{6}\log_2 6 = \log_2 6$
- $\log_2 6 > 1$, entropy can be more than one

For an n-sided die, entropy would be $\log_2 n$, therefore it can be any value
	$H(x) \geq 0$

### Information
$I(X) = \log_2(\frac{1}{p(x)})$

![[Pasted image 20260601102059.png|450]]
	H has higher surprised information, since probability is lower
	- H then should be assigned more bits of information

![[Pasted image 20260601102213.png|450]]
	This version uses only 6 bits of information to represent the same thing

Frequently occurring events should have short encodings
 - ex. "a", "the", "and" should have short encodings

### Information Theory
Provides a mathematical framework to address questions about randomness

$P(x,y) = P(x|y)\cdot P(y)$
$H(x,y) = H(x|y)\cdot H(y)$



## Entropy
For a simple case like an unbiased coin, flipping it has a max entropy of 1
- As soon as it become a little more biased, entropy decreases because we will be more certain about an outcome
![[Pasted image 20260601102701.png|500]]
- for ML, $\log 0 = 0$ for simplicity sake


### Properties of Entropy
1. Nonegative: $H(P) > 0$
2. Invariant wrt permutation of its inputs
	$H(p_1, p_2, ... , p_k) = H(p_\tau(1), p_\tau (2), ... p_\tau(k))$
3. For any other probability distribution q, we can get a KL divergence metric
	$H(P) = \sum_i p_i \cdot \log\frac{1}{p_i} < \sum_i p_i \cdot \log\frac{1}{q_i}$
	$p_i$ is the actual pdf value $q_i$ is the predicted value
	
	$\sum p_i \log \frac{p_i}{q_i} \geq 0$
	zero for the case when p = q

4. $H(p) \leq \log_2 k$ with equality iff $p_i = \frac{1}{k} \forall i$
5. The further P is from uniform, the lower the entropy

### Joint Entropy
![[Pasted image 20260601103555.png|400]]
- $P(M = \text{low}) = 0.6$
- $P(M = \text{low}, T = \text{mild}) = 0.4$
- $P(M=\text{low} | T = \text{mild}) = \frac{0.4}{0.5}$
- $P(T = \text{mild} | M=\text{low}) = \frac{0.4}{0.6}$

$H(T) = H(0.3, 0.5, 0.2) = -P(T=c)\log_2 P(T=c) - P(T=m)\log_2 P(T=m) - P(T=h)\log_2 P(T=h)$
$= 1.48548$
$H(M) = \ldots = 0.970951$
$H(T) + H(M) = 2.456431$

**Joint Entropy** $\sum_{t,m} P(T=t, M=m)\cdot \log\frac{1}{P(T=t, M=m)} = 2.32193$
$H(T,M) \leq H(T) + H(M)$

### Conditional Entropy
![[Pasted image 20260601105321.png|600]]
![[Pasted image 20260601105341.png|600]]
![[Pasted image 20260601105353.png|600]]

### Mutual Information
$I(X_i, Y) = H(Y) = H(Y|X_i)$
- Entropy of the system, minus entropy once we see one feature

Mutual Information is the quantity of the reduction in uncertainty in $Y$ after seeing $X_i$
- The question becomes, which feature is the one that allows us to reduce uncertainty by the most?

$I(X,Y) = H(X) - H(X|Y) = \sum_{x,y}P(x,y) \cdot \log \frac{P(x,y)}{P(x)P(y)}$
- Symmetric
- Non-negative
- Zero iff X,Y are independent

![[Pasted image 20260601110008.png|450]]

### Cross Entropy
The expected number of bits when a wrong distribution is Q is assumed while the data actually follows a distribution P
- p -> actual pdf
- q -> predicted pdf

$H(p,q) = -\sum_{x\in X}p(x)\log q(x) = H(P) + KL[P][Q]$
- Entropy of the system is **always** there since there is always noise. Even if we had a perfect prediction q, and the KL value is zero, there is *still going to be entropy* 

![[Pasted image 20260601110504.png|600]]
*genuinely what*