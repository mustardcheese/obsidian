We put bounds onto our regression model to reduce the error
- Remember the bias variance tradeoff: L = $\text{bias}^2 + \text{variance}$ 
- We need to adjust our bias and variance just a little bit to achieve a good balance
![[Pasted image 20260629094707.png|500]]

When we adjust the $x^d$ terms they can fluctuate a lot
When we adjust the $\theta_d$ terms they can fluctuate a lot
- We can't bound the features of data, it is what is is, but we can bound the weights
s.t $|\theta_0 + \theta_1 + \cdots + \theta_d| \leq 100$
- by bounding the weights we are more likely to not get an overfitted line
- it's the **weights** that end up causing overfitting, and what we need to target to stop overfitting

The weights $\theta$ are what affect our regression curve the most, so if we bound $\theta$ with a constraint, then we can hopefully reduce loss
- This means, however, our constraint is a new hyperparameter

With hard constraints:
$y = \theta_0 + \theta_1z1 + \theta_2z_2 + \cdots + \theta_d z_d$
	s.t $\theta_d = 0$ for $d > 2$
$y = \theta_0 + \theta_1z_1 + \theta_2z_2 + 0 + 0 + \cdots + 0$

by doing this though, we end up losing data and losing valuable info, like $\theta_5$

The MLE of the error function of $\theta$ it happens to be a convex function, meaning we can find the global solution (minima)

$E(\theta) = \frac{1}{N} \sum^n_{i=1}(y^{\{i\}}-z^{\{i\}}\theta)^2$
We can graph it onto a contour graph:

![[Pasted image 20260629095212.png|450]]
- At the absolute minima, error = zero, meaning overfitting is likely to be happening (since this would mean every point was perfectly hit which is nearly impossible)

![[Pasted image 20260629095419.png|450]]
- This contour for example is a good solution. In terms of error it's high, but in terms of bias and variance, it's low.
- If we were to just follow the gradient we would fall into the overfitted final answer, so we need to set constraints "higher" in the curve to find a good answer but not overfit

For:
$g(\theta) = |\theta_0| + |\theta_1| + \cdots + |\theta_d| \leq C$
- this isn't differentiable and therefore cannot be optimized, abs isn't differentiable
$g(\theta) = ||\theta_0||^2 + ||\theta_1||^2 + \cdots + ||\theta_d||^2 \leq C$
- take the euclidian distance instead, and now it can be optimized

Now let's define a Lagrangian based on the error and weight functions
![[Pasted image 20260629100508.png|450]]


![[Pasted image 20260629100300.png|450]]

By using a Lagrangian we can "trick" the gradient to have the gradient equal to zero at the minima of the active solution by altering our $\lambda$ which is the true best answer.

**Low Lambda:**
![[Pasted image 20260629100620.png|400]]

**High Lambda:**
![[Pasted image 20260629100634.png|400]]


Minimize $E(\theta)$ -> MSE = $\frac{1}{N} \sum^N_{i=1} (y_a^{\{i\}}-x^{\{i\}}\theta)^2$
	s.t $||\theta^2|| \leq C$ -> $\theta^T \theta = C$ -> $g(\theta) = \theta^T \theta - C$
Lagrangian:
$L(\theta, \lambda) = E(\theta) + \lambda(\theta^T \theta -C)$
	$\frac{\partial L}{\partial \theta} = 0$
	$\frac{\partial L}{\partial \lambda} = 0$
This is unsolvable, there is no closed form solution since the two are interconnected: if we set one to zero then another vanishes and vice versa


If we introduce $\lambda$ to be a hyperparameter, then we can treat it as a constant and rewrite the Lagrangian
$L(\theta) = E(\theta) + \lambda \theta^T \theta - \cancel{\lambda C} = E(\theta) + \lambda \theta^T \theta$

$\lambda$ and $C$ have opposite directions: when $C$ grows $\lambda$ shrinks, when $C$ shrinks $\lambda$ grows.
- For high values of $\lambda$ we have high error, so we want to keep $C$ small
- When we have $\lambda$ to be very small, then it's like the $\theta^T \theta$ term doesn't exist, so when we optimize given a very small $\lambda$ hyperparameter, it essentially just turns into optimizing the MLE of error

![[Pasted image 20260629101530.png|500]]
- We use our own model's parameters to regularize the model

## Ridge Regression

![[Pasted image 20260629101742.png|450]]
![[Pasted image 20260629101809.png|450]]
- This is a closed form solution (for when we know $\lambda$)
- By introducing our $\lambda I$ term it reduces all the pains of overfitting
- Same problems as before:
	If $\lambda$ is too large, then we get too much error
	If $\lambda$ is too small, then we get overfitting ($\theta_{overfit} = (z^Tz)^{-1}z^Ty$)

Our bias term $\theta_0$ is being optimized too, so we can create this $D$ matrix, that modifies this:
$\lambda ||\theta||^2$ = $\lambda \theta^T I \theta$ = $\lambda \theta^T D \theta$
	s.t $D = \begin{bmatrix}0 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \cdots & \cdots & 1 & \cdots \\ 0 & 0 & 0 & 1\end{bmatrix}$
We can actually customize this $D$ matrix by introducing a hyperparameter to choose how many of the parameters we want to keep and ignore. In this case D ignores $\theta_0$ the bias term, but we could ignore $\theta_1, \theta_2, \cdots, \theta_n$

Our hyperparameters:
- $\lambda$ allows us to maximize a solution
- D allows us to reduce overfitting

![[Pasted image 20260629102836.png|600]]
- Which $\lambda$ is the best for this data?
- Finding this $\lambda$ is **hyperparameter fine tuning**

ridge regression just means $l_2$ norm. $l_1$ norm is still usable though:
## Lasso Regression
![[Pasted image 20260629103145.png|500]]
![[Pasted image 20260629103134.png|500]]
![[Pasted image 20260629103632.png|450]]
![[Pasted image 20260629103647.png|450]]
![[Pasted image 20260629103739.png|500]]

## Hyperparameter Tuning

### Leave-One-Out Cross Validation
For every $i=1, \cdots, n$:
- train the model on every point except $i$
- compute the test error on the held out point
![[Pasted image 20260629105723.png|400]]
- Train on 2-n, run on 1
- Train on 1, 3-n, run on 2
- Repeat this n times for all datapoints and average the test errors
This will have to run $n$ times, just for one $\lambda$ value
- Repeat the entire process again for a different $\lambda$ value
**this is not efficient.**

### K-Fold Cross Validation
For every $i = 1, \cdots, n$
- train the model on every fold except the $i$ fold
- compute the test error on the $ith$ fold
![[Pasted image 20260629110134.png|400]]
- faster than k-fold because it does less
- 10% validation -> 10-fold cross validation -> folds of size 10%

Typically it's 70% training 10% validation, 20% testing