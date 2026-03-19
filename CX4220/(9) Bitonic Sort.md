We can start with a few decent sequential sorting algorithms
- Mergesort T(n,p) = ... (fill in) = $O(\frac{n}{p}logp ... (fill in))$

Take one list and reverse the other, put the min of both lists into a min list, and the max of both lists into a max list

??? (fill in previous)

**Bitonic Sequence** $x_0, x_1, ... , x_{n-1}$ is bitonic if $\exists k (n > k \geq 0)$
- (T1) x_0 is non-decreasing, $x_{k+1}$ is non increasing
- (T2) x_0 is non increasing and x_k is non-decreasing
- (T3) there is a cyclic shift in the sequence that makes T1 or T2 true

### Bitonic Split
$l_{min} = min(x_0, x_{\frac{n}{2}}), min(x_1, x_{\frac{n}{2}+1})$
