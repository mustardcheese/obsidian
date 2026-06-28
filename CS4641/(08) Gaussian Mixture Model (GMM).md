Univariate Gaussian: $N(\mu, \sigma) = \frac{1}{\sqrt{2\pi \sigma ^2}}e^{-\frac{x^{\{i\}}-\mu)^2}{2\sigma^2}}$
Covariant Gaussian: $N(\mu, \Sigma)$
- $\Sigma$ is the covariance matrix, square of size of features $d\times d$

For **d** dimensions, the Gaussian distribution of a vector $\bf{x} = (x_1, x_2, ..., x_d)^T$
- Needs to be transposed to be able to multiply everything out
![[Pasted image 20260610103436.png|400]]
* $\mu$ acts as a datapoint and is $1\times d$ 
* N is a scalar, $1 \times 1$

![[Pasted image 20260610103755.png|500]]
* $\sigma^2_h = 0.25$
* $\sigma^2_w = 1$
* $\sigma^2_hw = 0.3 = \sigma^2_wh$

Weight has higher variance, and when we plot it in 2D as a contour map, w (the y-axis) is stretched further because there is more variance in weight than height.

Since our covariance (0.3) is positive, that means the relation between the two are positive, so when any of w or h increases, then so will the graph.

$\begin{bmatrix}0.25 & 0.30 \\ 0.30 & 1.00\end{bmatrix}$
- 0.25, 1.00 control the scale
- 0.30 control the rotation
$\begin{bmatrix}scale & rotation \\ rotation & scale \end{bmatrix}$


*insert pictures from contour drawings*


For a covariance like
$\begin{bmatrix} 625 & 25 \\ 25 & 1\end{bmatrix}$
- Determinant is 0 -> non-invertable -> rank deficiency
- This is a linearly dependent system ($h = \alpha w$)
- Contour for this is just a line

### Is Gaussian Concave?
For a standard gaussian, $\mu \pm \sigma$ are the inflection points
- This means between $(\mu - \sigma, \mu + \sigma)$ it is concave
- $(-\infty, \mu - \sigma) \cup (\mu + \sigma, \infty)$ it is convex
Neither


 $f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{\frac{1}{2\sigma^2}-(x-\mu)^2}$   ->   $c_1 \cdot exp(c_2 \cdot -1 \cdot (x-\mu)^2)$
 $\log f(x) = \log(c_1 exp(-c_2(x-\mu)^2)) = \log(c_1 exp(u))$
	$= \log c_1 + \log exp(u) = \log c_1 - c_2(x-\mu)^2$
	$f(x) = -(x-\mu)^2$


**Log of a Gaussian is concave**
Summation of concave functions will also be concave

Say we have two gaussians:
$f_1(x) = N(x | \mu_0, \sigma_0)$
$f_2(x) = N(x|\mu_1 \sigma_1)$
...
$f_1(x|\theta) = f_1(x|\mu,\sigma) = f_1(x)$


$f(x) = f_1(x) + f_2(x) + f_3(x)$
- When we sum three Gaussian we get this new function that is not concave and is no longer Gaussian
Optimizing the $\log f(x)$ will be *very* hard since it is not guaranteed to be concave, and the function is crazy.


However, if we compute the logs beforehand,
$f'(x) = \log f_1(x) + \log f_2(x) + \log f_3(x)$
- We know for certain that the result of this will be concave, meaning it is possible to optimize

## GMM

### Clustering
K-means is **hard assignment** where each object only belongs to one cluster
Mixture modeling is **soft assignment**, considering the probability that an object belongs to another cluster.

This clustering probability matrix is the **Responsibility Matrix**
- Size $n \times k$ where $k$ is number of clusters
- $\upsilon_{nk} = \Gamma_{nk}$
In the end, once we have the responsibility matrix, we can just take the max() of each point to determine its hard assignment.
![[Pasted image 20260610111532.png|500]]
This can be used for EDA before hard clustering. Say
$x^{\{i\}} = \begin{bmatrix} 0.33 & 0.33 & 0.33 \end{bmatrix}$
- Lots of entropy, hard clustering would be random
- Soft clustering would allow for analysis before making a decision


Say we have a dataset like this.
![[Pasted image 20260610112001.png|400]]

For circularly distributed data, K-means works well here (euclidian distance)
![[Pasted image 20260610112026.png|400]]
	By only needing to find the centroid, we just have one parameter to optimize for
	($\mu$)
for k-means we want to minimize distance

We could try to use GMM on this dataset
![[Pasted image 20260610112149.png|400]]
	It works but for the covariance matrix there's now two parameters to optimize for
	($\mu, \Sigma$)
for gmm, we want to maximize probability density (contour stuff)
we recalculate by recalculating $\mu$ and $\Sigma$, get likelihood, recalculate them again


What about this dataset?
![[Pasted image 20260610112038.png|400]]
K-means doesn't work as well anymore

But GMM works well because of the scaling and rotation capabilities
![[Pasted image 20260610112858.png|400]]

new parameter for GMM,  $\Pi$ the mixing coefficient
ex. green = 1000, red = 20, yellow = 20, blue = 30
$\Pi_{\text{green}} = \frac{1000}{N}$ -> prior

Since green dominates by so much and the mixing coefficient $\Pi$ is so large, we have a prior disposition to put more datapoints into green, since *most* points are in green anyways.

*insert drawing of multiple gaussians on one feature, 1D lines slide 23*

![[Pasted image 20260621215608.png]]
$\mu = \frac{1}{N}\sum^N_{i=1}x^{\{i\}}$

Remember, the log of a Gaussian turns it concave
$\log f(x^{\{i\}}|\theta) + \log f(x^{\{2\}}|\theta) + \cdots \log f(x^{\{n\}}|\theta)$
summing multiple log Gaussian (concave) makes another concave function


### Soft-Clustering
The idea is to create a single pdf that combines all (three) Gaussian.
$\Pi_0$ the mixing coefficient is the chance a data point comes from a specific Gaussian
- When we sum the Gaussian values across all points, we end up with some new function, but not necessarily a Gaussian
- This new function is a pdf, so the area under the curve should be one

$f(x)=f(x|\theta)=f(x|\mu, \sigma) = N_0(x | \mu_0 \sigma_0) + N_1(x|\mu_1 \sigma_1) = f(x|\theta) + f_1(x|\theta) = N_0 + N_1$
integrate everything
$\int N_0 dx + \int N_1 dx = 2$
- integrating over each gaussian would result in 1, meaning our new pdf won't have an area of 1 but N.

Now, we integrate our mixing coefficient $\Pi$ to help determine the chance of a data point coming from a certain gaussian.
$f(x) = \Pi_0 N_0 + \Pi_1 N_1$
integrate everything
$\int \Pi_0 N_0 dx + \int \Pi_1 N_1 dx = \Pi_0 + \Pi_1 = 1$
- $\Pi_0 N_0$ is component 0

We can form a joint probability table from density values against component values
![[Pasted image 20260621221117.png|400]]
and by sum rule, we can sum over the density values, to achieve the joint probability values for each component (gaussian)
![[Pasted image 20260621221142.png|600]]

Now to make this pdf work we'll need a new third parameter, $\Pi$ for our function

$f(x) = f(x|\theta) = f(x|\mu, \sigma, \Pi) = \Pi_0 N_0 + \Pi_1 N_1 = \Pi_0 N_0(x|\mu_0 \sigma_0) + \Pi_1 N_1(x|\mu_1 \sigma_1)$
$\Pi_0 = P(z_0)$ 
- The chance that a datapoint comes from component ($z$) zero.

$N_0(x|\mu_0,\sigma_0)=P(x|z_0)$
- "given a component, the datapoint comes from a gaussian" 

$f(x) = P(z_0)P(x|z_0) + P(z_1)P(x|z_1) = P(x,z_0) + P(x,z_1) = \sum P(x,z_k) = P(x)$

$P(z_0|x^{\{1\}})$ $P(z_1|x^{\{1\}})$ => $P(z_0|x^{\{1\}}) = \frac{P(x^{\{1\}}|z_0)P(z_0)}{P(x^{\{1\}})}$
$P(x^{\{1\}}) = \Pi_0 N_0(x^{\{1\}}|\mu_0, \sigma_0) + \Pi_1 N_1(x^{\{1\}}|\mu_1 \sigma_1)$
$P(x) = \Pi_0 N_0 + \Pi_1 N_1$

Responsibility Matrix
$\tau = P(z|x)$
![[Pasted image 20260621225023.png|500]]

What needs to be known to calculate the responsibility matrix?
- $\Pi_0, \Pi_1, N_0, N_1$
- $N_0 = \frac{1}{\sqrt{2\pi \sigma_0^2}} exp(-\frac{1}{2\sigma_0}(x^{\{i\}}-\mu_0^2))$
- $\Pi_0, \Pi_1, \rho_0, \rho_1, \sigma_0, \sigma_1$
These six values are what we need to optimize for

$P(x) = P(x|\theta) = P(x|\mu, \rho, \pi) = \Pi_0 N_0 + \Pi_1 N_1 = P(z_0)P(x | z_0) + P(z_1) P(x | z_1)$
to optimize this pdf, we need to construct a likelyhood function, maximized for every single data point

$max\ \Pi^N_{i=1}P(x^{\{i\}}|\theta)$ ->$max \log L(\theta | x) = \mathcal{l}(\theta | x) = \log \sum^N_{i=1} p(x^{\{i\}}|\theta)$
- s.t $\sum_{i=0}^N \Pi_i = 1$

Sum of Gaussian is neither concave nor convex. log of that sum becomes even harder to optimize. Currently not friendly to maximization.

max $\log(\Pi_0 N_0 (x | \mu_0 \sigma_0) + \Pi_1 N_1 (x | \mu_1 \sigma_1))$
- in order to optimize we'd need to take the gradient of all six of these variables
$\frac{\partial l}{\partial \mu_0} = 0$ -> $\frac{\Pi_0}{\Pi_0 N_0 + \Pi_1 N_1} \frac{\partial N_0}{\partial \mu_0}$

*some stuff about being unable to solve it directly, so we solve using older responsibility matrix entries*
## Expectation Maximization

![[Pasted image 20260624000731.png|550]]
Recalculate everything at every step until we reach convergence
- At every step we still need to calculate the objective function (log likelyhood)
- Once the objective function stops moving, it means we're reaching convergence.