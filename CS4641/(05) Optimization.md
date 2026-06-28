We can swap the minimization/maximization of our objective function by multiplying by -1

If our objective function has a constant it's okay, because we still optimize for the same value

Log Likelihood $l(\theta |x) = \sum_{i=1}^N \log f(x^{\{i\}}|\theta)$
- maximization problem

multiply by -1 to turn into minimization problem
$l(\theta |x) = -\sum_{i=1}^N \log f(x^{\{i\}}|\theta)$

multiply everything by constant $\frac{1}{N}$
min avg = $l(\theta | x) = \frac{1}{N}\sum^N_{i=1}-\log f(x^{\{i\}}|\theta) = \text{avg} = E[...]$
*fill in what i missed*

Negative Average Log Likelihood = Cross Entropy
*insert work to get there above ^^*

Since we want to minimize cross entropy, we also want to minimize negative average log likelihood



---
The function we use to compare y actual and y predicted is the loss function

$\text{cat} = [1 0 0]$ $\text{dog} = [0 1 0]$ $\text{fish} = [0 0 1]$

One Hot Encoding, discrete values, and similar to a pmf
*insert picture of  new y actual and y predicted after one hot encoding*

We also need to pass it through a softmax normalization function to allow it to be pmf
*insert picture of normalized y predicted*

We could use an l2 norm to compare the distance between actual and predicted data point as our loss function to minimize
- Lower distance == closer prediction, minimize towards zero
- This can be dangerous because squaring and subtracting numbers creates even smaller numbers

We could use a dot product between actual and predicted data as our loss function to maximize
- Closer to 1 == closer prediction, maximize towards N
- Same issue of multiplying small numbers creating even smaller numbers

### Why Cross Entropy over Dot Product
$CE = -\sum p(x) \log q(x) = -\sum^N_{i=1}y^{\{i\}}_a \log \hat y^{\{i\}T}_p$
- Nearly the same as a dot product except we take the log of the predicted value instead of just multiplying

$y_a = \begin{bmatrix} 1 & 0 & 0 \\ \ & \ & \ \\ \ & \ & \ \end{bmatrix}$
$\hat y_p = \begin{bmatrix} 0.7 & 0.2 & 0.1 \\ \ & \ & \ \\ \ & \ & \ \end{bmatrix}$ 

$CE = -(\begin{pmatrix} 1 & 0 & 0 \end{pmatrix} \begin{pmatrix} \log 0.7 \\ \log 0.2 \\ \log 0.1 \end{pmatrix} +\ \ldots\ )$

Log works better than a linear form and functions as an alarm system
- If our optimization is just slightly off, it will be closer to 1 and the value is small
- If we make a little mistake the log increases dramatically, signaling an error much quicker than a linear function could

By introducing the log, it greatly increases the speed of optimization

## KL Divergence
$KL[P][Q] \geq 0$ and is zero when $Q == P$

Any time we need to determine whether we optimize for min or max, we need to take the second derivative to determine concavity
- **Strictly** Concave == maximize, **one** global optimal solution
- Concave == maximize, multiple possible global optimal solutions
- **Strictly** Convex == minimize, **one** global optimal solution
- Convex == minimize, multiple possible global optimal solutions

### Jensen's Inequality
Take two points on our function, say $f(x) = -x^2$

$E[f(x)] \leq f(E[x])$ **concave**
- The two points will always be less than or equal to the actual function

$x = [-2, 2]$
$f(x) = [-4, -4]$
$P(x) = [0.5, 0.5]$
$E[f(x)] = \sum P(x)f(x) = P(x=-2)f(x=-2) + P(x=2)f(x=2) = 0.5(-4) + 0.5(-4) = -4$
$f(E[x]) \rightarrow E[x] = \sum P(x)x = 0.5\cdot -2 + 0.5\cdot -2 = 0 \rightarrow f(0) = 0$

*insert drawing of the chart and the dots*
- This is the case where the two points are 50/50, meaning the middle point is exactly in the middle
- $E[f(x)]$ will always just reside on the line between the two points
- $f(E[x])$ will always just trace along that middle point on the main function

$E[f(x)] \geq f(E[x])$ **convex**

For functions that are neither concave or convex and fluctuate, then we can put constraints on the function, splitting it into concave and convex sections which can be optimized

**Log** then, is a **concave** function
$E[g(x)] \leq g(E[x]) \rightarrow E[\log(x)] \leq \log(E[x])$

---
$KL[P][Q] = \sum P(x) \log \frac{P(x)}{Q(x)} \rightarrow -KL[P][Q] = \sum P(x) \log \frac{q(x)}{p(x)}$
say $\frac{q(x)}{p(x)} = g(x)$ for simplicity
$-KL[P][Q] = \sum p(x) \log g(x) = E[\log g(x)] \leq log E[g(x)]$
							      	$\leq \log\sum q(x)$
								$\ \ \ \ \leq \log 1 = 0$

$\therefore KL[P][Q] \geq 0$


## Optimization
Three ways to perform optimization:
- No constraint $f(x,y) = x^2 + y^2$
- Equality constraints $f(x,y) = x^2 + y^2$, s.t $x + y = 10$
	- Lagrange function
- Inequality constraints $f(x,y) = x^2 + y^2$, s.t $x-y \geq 10$, $x+y = 20$
	- Lagrange function but also need to satisfy KKT conditions

s.t means "subject to"

Linear Programming (approach) $f(x,y) = x + y$ s.t $x + y \leq 10$
- Linear function, and linear constraints

Quadratic Programming (approach) $f(x,y) = x^2 + y$ s.t $x + y \leq 10$
- Quadratic function, and **linear** constraints

Non-linear Programming (approach) $f(x,y) = x^2 + e^y$ s.t $x^3 + \sqrt y \leq 10$
- Everything else

Linear, Quadratic are used for ML and both also provide strong duality
- They provide finite optimal results

For multivariabled functions we'd still need to take the second derivative to determine concave/convex, so we take the hessian matrix
$H = \begin{bmatrix}\frac{\delta f}{\delta x^2} && \frac{\delta f}{\delta x y} \\ \frac{\delta f}{\delta y x} && \frac{\delta f}{\delta y^2}\end{bmatrix}$
- We typically don't need to determine the hessian because we'll already know whether or not we want to minimize or maximize

$f(s,m) = 2s^2 + 3m^2$
- s is hours of sleep in a day
- m is hours of studying ML
This function is convex, so without constraints we'd be optimizing for a minimal value

We try to solve this without constraints as we just get 0 for both. This does not help, we need constraints.

$s + m = 24$ -> construct a constraint function -> $g(m,s) = s + m - 24$, but $g(m,s) = 0$ always

$L(s,m,\lambda) = f(s,m) \pm \lambda g(m,s) = 3s^2 + 2m^2 - \lambda(s+m-24)$
- $\lambda$ is the Lagrange multiplier
- For equality constraints it doesn't matter if it's plus or minus

$\frac{\delta L}{\delta \lambda} = 0 \rightarrow 0 + 0 - (s+m-24) = 0$ | $s + m = 24$
$\frac{\delta L}{\delta s} = 0 \rightarrow 6s + 0 - \lambda = 0$                 | $s = \frac{\lambda}{6}$         | s = 9.6
$\frac{\delta L}{\delta m} = 0 \rightarrow 0 + 4m - \lambda = 0$               | $m = \frac{\lambda}{4}$        | m = 14.4

$L(m,s,\lambda) = f(m,s) - \lambda g(m,s)$
$\nabla L = \nabla f - \nabla(\lambda g) \rightarrow \nabla L = \nabla f - \lambda \nabla g = 0$
*insert chart about customized solution*


How do we solve the Lagrangian with multiple constraints?
min $f(m,s)$ | s.t m + s = 24 | s.t $m - s = 24$
- $g(m,s) = m + s - 24$
- $h(m,s) = m - s -24$
$L(m,s,\lambda_1,\lambda_2)$

How do we solve the Lagrangian with inequality constraints?
$f(m,s) = 3s^2 + 2m^2$ | s.t $m + s \leq 24$

To solve the inequality, we'll need:
- Active solution $m + s = 24$
- Inactive solution $m + s < 24$

$g(m,s) = m + s - 24$

Must satisfy **KKT conditions**
1. Stationary conditions -> $L(m,s,\lambda) = f(m,s) + \lambda g(m,s) \rightarrow \nabla L = 0$
2. Primal feasibility -> $g(m,s) \leq 0$
3. Dual feasibility -> $\lambda \geq 0$
4. Complementary Slackness -> $\lambda \cdot g(m,s) = 0$
	If $g(m,s) = 0 \rightarrow \lambda > 0$
	If $g(m,s) \neq 0 \rightarrow \lambda = 0$

When optimization is going wrong, $\lambda$ will grow very large, acting as an alarm for the model

Based on the constraints it determine if we need to use the active or inactive solution

$f(m,s)= \frac{1}{2}m^2 + \frac{1}{2}s^2$
s.t $m + s = 24$ -> $g(m,s) = m + s -24$
- Function quadratic, linear constraint -> Quadratic Programming

$L(m,s,\lambda) = \frac{1}{2}m^2 + \frac{1}{2}s^2 - \lambda g(m,s)$
- $\frac{\delta L}{\delta s} = 0 \rightarrow s = \lambda$
- $\frac{\delta L}{\delta m} = 0$ -> $m = \lambda$
- This is called primal form
We convert it then to just be a function of lambda
$L(\lambda) = \frac{1}{2}\lambda^2 + \frac{1}{2}\lambda^2 -\lambda(2\lambda^2 - 24) =\ ...\ = -\lambda^2 + 24$
- This now becomes a maximization problem
- This is dual form, in the objective function it's a minimization problem but in lambda Lagrangian function its a maximization problem
$\nabla L(\lambda) = 0$ -> $-2\lambda = -24$ -> $\lambda = 12$

*insert picture of weak duality*
- Sometimes, just because we have the min/max solution, it doesn't necessarily mean its the solution of the other

*insert picture of strong duality*
- However, for things like quadratics one solution will work for both

The big question then is "does strong duality hold" so we can solve a simplified equation?

$f(x) = x^2 + exp(x)$
$f'(x) = 2x + exp(x)$
There is no way to solve $f'(x) = 0$ to give us a closed form solution

### Gradient Descent
$x^{\{t+1\}} \leftarrow x^{\{t\}} - \alpha \frac{\delta f(x)}{\delta x} = x^{\{t\}} - \alpha (2x+exp(x))$
- $\alpha$ is also called the learning step or hyper parameter, and is typically a very small value 

We gradually shift $t$ until we get a good answer I guess?