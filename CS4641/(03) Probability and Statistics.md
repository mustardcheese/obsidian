 ## Probability Distributions

A **Sample Space** $S$ is the set of all possible outcomes
	$(1\ 2\ 3\ 4\ 5\ 6)$, $S$ is the set of all possible outcomes of a dice roll
An **Event** $A$ is a subset of $S$
	Seeing "1" or "6" in a dice roll
	$P(X=x) = \frac{1}{6}$
Probability function:
	$p(x) = P(X=x)$
- Probability cannot be negative
- Probability cannot be greater than 1
- $0 \leq p(x) \leq 1$

### Variables
A **continuous variable** is a continuous probability distribution, represented by a probability density function (PDF)
-  Density or likelihood value
- Temperature (real number)
- Gaussian Distribution
- $\int_x p(x)\,dx = 1$

A **discrete variable** is a discrete probability distribution, represented by a probability mass function (PMF)
- Probability Value
- Coin flip (integer)
- Bernoulli Distribution
- $\sum_{x\in A}p(x)=1$

## Continuous Probability Functions

In this course, $\theta$ means parameters and is what we optimize for.

Uniform Density Function:
$f_x(x) = \begin{cases} \frac{1}{b-a} & a \leq x \leq b \\ 0 & ow \end{cases}$
- This *is* a CDF, summing over $\frac{1}{b-a}$ is 1
- $\{b,a\} \in \theta$


Exponential Density Function
$f_x(x)=\frac{1}{\mu}e^{-\frac{x}{\mu}}$ for $x \geq 0$
$F_x(x) = 1-e^{\frac{-x}{\mu}}$ for $x \geq 0$
- $\{\mu\}\in \theta$

Gaussian (Normal) Density Function
$\frac{1}{\sqrt{2\pi}}e^{-\frac{(x-a)^2}{2\rho^2}}$

## Discrete Probability Functions
Examples:
- Bernoulli Distribution
	- $\begin{cases}1 - p & \text{for } x = 0 \\ p &\text{for } x = 1\end{cases}$
- Binomial Distribution
	- $P(X=k)=\binom{n}{k}p^k(1-p)^{n-k}$

## Statistical Rules
Say X = to throw a dice
Say Y = to flip a coin
- These are **statistically independent**, different from linear independence and a much stronger assumption
![[Pasted image 20260527094127.png]]
$P(Y=t, X=4) = \frac{5}{35}$, N=35   $\frac{n_{ij}}{N}$
$P(Y=t) = \frac{20}{35} = \frac{C_j}{N}$
$P(X=4) = \frac{7}{35} = {C_i}{N}$
$P(Y=t\ |\ X=4)=\frac{5}{7} = \frac{n_{ij}}{C_i}$
- When we shrink the sample size, it improves the prediction ability of an ML algorithm
$P(X=4\ |\ Y=t)=\frac{5}{20}=\frac{n_{ij}}{C_j}$
$P(Y=y,X=x)=\frac{n_{ij}}{N} = \frac{n_{ij}}{C_i}\frac{C_i}{N}=P(Y=y\ |\ X=x)P(X=x)$
    $= \frac{n_{ij}}{C_j}\frac{C_j}{N} = P(X=x\ |\ Y=y)P(Y=y)$
- **Product Rule**
- $P(Y,X)=P(Y\ |\ X)P(X) = P(X\ |\ Y)P(Y)$

**Sum Rule**
$p(X=x_i)=\sum^L_{j=1}p(X=x_i, Y=y_i) \rightarrow p(X)=\sum_Y P(X,Y)$

**Joint Probability** is difficult to solve and is bad for machine learning. We try to use the different statistical rules to avoid joint probabilities.
	$P(a,b,c) = P(a,b\ |\ c)P(c) = P(b\ |\ a,c)P(a,c)$

## Conditional Independence
P(Virus | DrinkBeer) = P(Virus)
	iff Virus is independent of Drink Beer

P(Flu | Virus, DrinkBeer) = P(Flu | Virus)

P(Headache | Flu, Virus, DrinkBeer)
- Joint probability, do not like
$P(H,F,V,D) = P(H|F, V, D)\cdot P(F,V,D) = P(H|F,D)\cdot P(F,V,D) = P(H|F,D)\cdot P(F|V,D)\cdot P(V,D)$
$P(H|F,D)\cdot P(F|V) \cdot P(V|D) \cdot P(D)$

## Bayes' Rule
- $P(Y,X) = P(Y|X)\cdot P(X) \rightarrow P(Y|X)=\frac{P(X,Y)}{P(X)}$
- **Bayes' Rule General Form**
- 'Given' part just goes to denominator

In general, we should prefer $P(X|Y)$ over $P(Y|X)$ depending on which is easiest is easier to calculate. Sometimes $P(Y|X)$ can be very hard to calculate.
- $P(Y|X) = \frac{P(X|Y)\cdot P(Y)}{P(Y)}$

*fill in the rest of the notes*

## Mean and Variance
### Mean
Expectation: The mean value, center of mass, the first moment
	$E_x[g(X)]=\int_{-\infty}^{\infty}{g(X)p_x(x)dx=\mu}$
	$E[g(X)] = \sum_x g(X)p(x)$
- $E[.]$ = mean
- $E(.)$ = function

If multiplied by a scalar, you can factor it out into the mean
- $E[aX] = aE[X]$
If summed with a vector, you can extract it out
- $E[a+X] = a + E[X]$

Expected Value of a Scalar -> Scalar
Expected Value of a Vector -> Scalar

### Variance
$Var(x)= E_x[(X-E_X[X]^2)]=E_X[X^2]-E_X[X]]^2$
***fill in notes after class***

### Example 1
$X = [1, 2, 3]$
$g(X) = x$
$P(X) = [\frac{1}{6}, \frac{3}{6}, \frac{2}{6}]$
$E[g(X)] = \sum_{i=1}^N g(x_i)P(x_i)$
$E[g(X)]= 1 \cdot \frac{1}{6} + 2\cdot \frac{3}{6} + 3\cdot \frac{2}{6} = \frac{13}{6}$

Arithmetic Avg = $\frac{1+2+3}{3}=2$
Expected Value = $\frac{13}{6}$
$Avg(x) \neq E[g(X)]$
- This happens because the arithmetic average assumes a uniform density while the expected value function accounts for it
- In ML, with **more data points** the data gets closer and closer to the correct value

### Example 2
X=$\begin{bmatrix}1\\ 2\\ 3 \end{bmatrix}$ h = height
$\mu_h = \frac{1+2+3}{3}=2$ 
$Var(h) = \mu_h^2 = \frac{1}{N}\sum_{i=1}^N (x^{\{i\}}-\mu_h)^2$
- In general with enough data points arithmetic avg and expected value are the same
- $\frac{1}{N}\sum^N_{i=1}[...] = avg(...) = E[...]$
***fill this in***

In ML for loops are bad, we'd rather just perform matrix multiplication instead of for loops
- Packages like numpy have made matrix multiplication very efficient and therefore better for ML

## Covariance

$X=\begin{bmatrix}1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}$ col1 = h col2 = w
$\mu_h = 3 \rightarrow \rho_h^2\ ,\ \mu_w = 5 \rightarrow \rho_w^2$
- We **can't** get mu this way, we need to do it via covariance

$X \rightarrow \bar X \rightarrow \bar X = \begin{bmatrix}1-\mu_h & 4-\mu_w \\2-\mu_h & 5-\mu_w \\3-\mu_h & 6-\mu_w \\\end{bmatrix}$
$COV = \frac{1}{N}\bar X^T \bar X = \begin{bmatrix}\sigma_h ^2 && \sigma_{hw} \\ \sigma_{wh} && \sigma_w ^2 \end{bmatrix}$
$\sigma_{hw} = \sigma{wh}$ therefore the covariance matrix is symmetric
if $\sigma_{hw} = 0 = \sigma_{wh}$, then they are uncorrelated therefore orthogonal -> linear independence
- However linear independence $\nrightarrow$ uncorrelated
- This is why we can say statistical independence is not as strong as linear independence

## Correlation
Standardization Process -> Derived from standard deviation
$X \rightarrow \bar X \rightarrow \bar X^* = \begin{bmatrix}\frac{h-mu_h}{\sigma_h} && \frac{w-mu_w}{\sigma_w} \\ ... && ...\end{bmatrix}$
$COR = \frac{1}{N} \bar X^{*T} \bar X^* = \begin{bmatrix}\frac{\sigma_h^2}{\sigma_h^2} = 1 && -1 \leq \sigma_{hw} \leq 1 \\ -1 \leq \sigma_{wh} \leq 1 && \frac{\sigma_w^2}{\sigma_w^2}=1\end{bmatrix}$
$h = 2w + CE$
- CE = noise

The correlation matrix is used for EDA (exploratory data analysis)
- Now that we know the upper and lower bound for data, we can explore the features and their relations with each other

## Joint Distribution
Standard Gaussian: $\mu = 0, \sigma = 1$
$x = z$, x is a standard gaussian
*insert drawing*

$y = z^2$
y would be dependent with x, so what's a gaussian squared? **Chi Squiared**
*insert drawing*

$g = z^3$
*fill in drawing*

$COV(x,y) = E[XY] - E[X]E[Y] = E[Z^3]-E[Z]E[Z^2]$
*insert portion*
- Since everything is zero, X and Y are uncorrelated
- However, they are still statistically related

Being linearly independent means you cannot write one feature as a combination of other features.
Being uncorrelated means it is both linearly independent as well as orthogonal.
Being statistically independent means you cannot write one feature as any function of another feature.
LI -> UC -> SI

## Probability vs. Likelyhood
$H,T \rightarrow P(H) = \frac{1}{2};\ H,H,H,T \rightarrow P(H)= \frac{3}{4}$
We move from probabilistic (no data) to statistical (data) world.

$f(x) = f(x|\theta) = f(x|a,b) =  \frac{1}{\sqrt{2\pi a^2}}e^{-\frac{(x-b)^2}{2a^2}}$ where $a = \sigma, b = \mu$
lazy      okay      long

$f(x)$ objective function
*insert image from slides*

The vertical axis of a pdf is the density or likelyhood and it needs to be a good representation of *all* data points

*insert image from slides for likelyhood*
$L(a,b|X)\rightarrow a=1,b=1; a=1,b=2; ...$


Naturally, data points are statistically independent, so we can rewrite the likelyhood, and separate everything out.
- In ML we don't want to be multiplying everything together, because multiplying many small or large numbers will shrink or grow the gradient to 0 or infinity

We want to maximize likelyhood and maximize the objective function.

$L(a,b|x) = \prod_{i=1}^N f(x^{\{i\}}|a,b)$ -> Likelyhood function
- Multiplying across all data points, because we care about all data points

$l(a,b|x) = \log L(a,b|x) = \sum_{i=1}^N \log f(x^{\{i\}} |a,b)$
- **Log Likelyhood** after logging, it turns into a summation, and much better to compute across
- Despite the shape of the function changing our value will remain the same

This only works under the assumption that data points are lineally independent.
- Naturally, with enough data points, they will end up being linearly independent anyways, so it's not a bad assumption


$\Sigma_{d \times d}$ is the covariance matrix, used when we have more than one feature

$COV = \frac{1}{N} \bar X^T \bar X$
- The $n \times d$ matrix X needs to first be centered to $\bar X$ before we compute covariance
Covariant $\mu$ becomes the $\mu$ of each feature
- $\mu$ in multi dimensions is a vector of $1 \times d$ , containing the average of each feature

## Gaussian Distribution
*insert from slides*

the sum of two **independent** Gaussian is also a Gaussian
$Y = X_1 + X_2, X_1 \perp X_2 \rightarrow \mu_y = \mu_1 + \mu_2, \Sigma_y = \Sigma_1 + \Sigma_2$

The multiplication of two Gaussian functions is also a Gaussian, although no longer normalized

## Central Limit Theorem
If a Gaussian is uncorrelated, this means that it is also statistically independent

![[Pasted image 20260601094502.png|400]]
This is a PMF of a biased dice
- PMF because it's discrete
- Biased because it should all be $\frac{1}{6}$ ideally

We could continuously take samples from the pmf, and choose an $n$, say $n=4$
![[Pasted image 20260601094644.png|300]]

Plot them all, and we still end up with a bell curve Gaussian, despite being uncorrelated
![[Pasted image 20260601094703.png|300]]

## Maximum Likelihood Estimation
For Bernoulli Distributions, we need to first create an objective function
$P(x^{\{i\}}|\theta) = \theta^{x^{\{i\}}}(1-\theta)^{1-x^{\{i\}}}$ 

We need to optimize this across ALL data points, but doing so is a joint probability which comes with the caveat that we assume all data points are independent from each other
$P(x^{\{1\}}, x^{\{2\}}, x^{\{3\}}, ..., x^{\{n\}} | \theta) = \Pi^N_{i=1} P(x^{\{i\}}|\theta)$

Products of probabilities are bad, so convert to log likelihood
![[Pasted image 20260601095725.png|550]]

So no we have the objective function, to optimize it we solve with derivative to be zero
![[Pasted image 20260601095750.png|400]]

We KNOW this will give us the maximal value, since it is a concave function

Say a coin flip
H, H, H, T, T
- H = 1, T = 0
- $\frac{1}{5}(1+1+1+0+0)=\frac{3}{5}$
