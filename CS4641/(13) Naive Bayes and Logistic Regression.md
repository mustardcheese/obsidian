![[Pasted image 20260629111411.png|500]]
![[Pasted image 20260629111420.png|500]]
![[Pasted image 20260629111430.png|400]]

$x^{\{i\}}$
$y = +1$ (cat)
$y = -1$ (dog)

$P(y = +1 | x^{\{i\}}) + P(y = -1|x^{\{u\}}) = 1$
$P(y = +1 | x^{\{i\}}) = \frac{P(x^{\{i\}}|y=+1)P(y=+1)}{P(x^{\{i\}})}$
- $P(x^{\{i\}}|y=+1)$ is the likelihood
- $P(y=+1)$ is the prior

Currently the likelihood is not solvable, but we can introduce a hyperparameter
- If we know cats are in a Gaussian distribution, we can substitute in a Gaussian just for the cat datapoints
- We need to calculate all the necessary parts of a Gaussian,
	$\Sigma = \frac{1}{N}\bar X^T \bar X$
	$\mu_x$ is the avg of all features for that cat

Gaussian Definition:
$P(x^{\{i\}}|y=+1) = \frac{1}{\sqrt{2\pi |\Sigma|^2}}exp(-(x^{\{i\}}-\mu)\Sigma^{-1}(x^{\{i\}}-\mu)^T)$
$\begin{align}P(x^{\{i\}}) &= \sum_{y=+1, y=-1}P(x^{\{i\}}, Y=y)\\ &= P(x^{\{i\}},y=+1) + P(x^{\{i\}},y=-1)\\ &= P(x^{\{i\}}|y=+1)P(y=+1) + P(x^{\{i\}}|y=-1)P(y=-1)\end{align}$
Do not like list: inverse of (covariance) matrix


$P(x | y=+1)$
Given the cat datapoints, we assume that all the features $f$ of the cat datapoint are conditionally independent of each other

$\sigma_{cat}^{-1} = \begin{bmatrix} \sigma^2_h & \sigma_{wh} \\ \sigma_{hw} & \sigma^2_w\end{bmatrix}^{-1} = \begin{bmatrix} \frac{1}{\sigma_h^2} & 0 \\ 0 & \frac{1}{\sigma^2_w}\end{bmatrix}$

$P(x_i^{\{i\}},x_2^{\{i\}}|y=+1) = P(x_1^{\{i\}}|y=+1)P(x_2^{\{i\}}|y=+1)$
$P(y=+1|x^{\{i\}}) = \frac{P(x^{\{i\}}|y=+1)P(y=+1)}{P(x^{\{i\}})} = \frac{P(x_1^{\{i\}}|y=+1)P(x_2^{\{i\}}|y=+1)P(y=+1)}{P(x^{\{i\}})}$
### In Practice:
idk fill this in i forget


Given a data point, we want to find the probability it's in one category or another
$P(y=+1 |x^{\{i\}}) = \frac{P(x^{\{i\}},y=+1)}{P(x^{\{i\}})} = \frac{P(x^{\{i\}}|y=+1)P(y=+1)}{P(x^{\{i\}})}$
	likelihood $\times$ prior
- Let's assume the likelihood is a Gaussian distribution, multivariate, $N(x|\mu, \Sigma)$

And the datapoints have multiple statistically independent features
$x^{\{i\}} = \begin{bmatrix}x_1^{\{i\}}, & x_2^{\{i\}}\end{bmatrix}$
$P(x_1^{\{i\}})$...
- Since statistical independence, then we can go from multivariate to univariate
- It's a generative model since it generates values
- It's naive because it assumes features are statistically independent from each other to work

## Gaussian Naive Bayes
GNB, say each distribution ends up following a gaussian
![[Pasted image 20260701094320.png|450]]
Let's call the prior $P(y=1) = \pi_1$

To find the full probability we'd use sum rule to sum ober all labels
$P(x) = \sum_{y=labels} P(x|y=y)P(y=y)$

End result of transformation:
![[Pasted image 20260701094805.png|450]]
- summation of datapoint dependent values plus some constant (bias term $\theta_0$)
- $\theta = \frac{1}{\sigma_i}(\mu_{1i}-\mu_{2i})$, $d+1 \times 1$

$= \frac{1}{1 + exp(-(\sum_i \theta_i x_i + \theta_0))} = \frac{1}{1+exp(-s)}$
- summation == linear combination of datapoints by values
- we go from 2d+1 -> d+1 parameters (d+1 entries in theta)

In regression $\theta$ meant angle and power degree
In GNB, $\theta$ represents a combination between $\sigma, \mu$

$\frac{1}{1+exp(-s)}$ is the **sigmoid** and is a value between $[0,1]$

In a binary case:
$\frac{P(y=1|x)}{1-P(y=1|x)}$ -> $\frac{P(y=cat|x)}{P(y=dog|x)}$ are the odds
- cat=0.5, dog=0.5, odds = 1 (you are just as likely to see dog as cat)
- cat=0.75, dog=0.25, odds = 3 (you are three times more likely to see cat than dog)

$odds$ range is $[0,\infty)$
$\log(odds)$ range is any real number, $\in \mathcal{R}$, $(-\infty, \infty)$

$x\theta$ is $\in \mathcal{R}$ = $\theta_0 + \theta_1 x_1 + \cdots + \theta_d x_d$

$logit(p) = log(odds) = log(\frac{p}{1-p}) = \frac{1}{1+e^{-x\theta}}$

![[Pasted image 20260701100736.png|450]]
Say the result of g(s) = 0.6
- We could name a threshold 0.5 to be the dog/cat line
- This is a hyperparameter, what determines a good threshold?
- It depends on the problem you're trying to solve

![[Pasted image 20260701101608.png|450]]
- sum is the LCF
- activation function is now the sigmoid
The output is a discrete value from $[0,1)$ but we still set a threshold do determine which classification

![[Pasted image 20260701101811.png|550]]

*fill in all the notes about taking gradient descent*

## Multiclass Logistic Regression

Softmax
*fill in screenshots*
*watch lecture video for this one*

