When we start with lots of data, some needs to be used for training, and some for other purposes.

We can split into:
- Training + Testing
- Training + Validation (of hyperparameters) + Testing
Generally the split is:
- 80%  + 20%
- 70% + 10% + 20%
We need to test how well it works with "outside" data, or data just set aside for later use.


There are two types of supervised learning:
Regression, working on a continuous real number
- One axis spent on data, second on value
- Prediction curve fitting as the answer
- Objective Function: Minimize the difference between predicted and actual
ex. curve fitting

Classification, working on a discrete value/number/label
- Two axes spent on data, color used for label, '2.5D'
- Decision line as the answer
ex. class estimations

$\hat y_p = mx + b$
predicted = shape + slope

$\hat y_p = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \cdots$
- $\theta_0$ bias term
- $\theta_1$ feature one parameter
- $\theta_2$ feature two parameter

for the entire training set we can represent everything as **LCF**, linear combination of features
$\hat y_p = \theta_0 + \theta_1x_1 + \theta_2 x_2 + \cdots$
$\hat y_p = x^{\{1\}}\cdot \theta = \theta_0 + x_1^{\{1\}}\theta_1 + \cdots + x_d^{\{1\}}\theta_d$
	if the label is linearly independent of the features, then you have bad data

We don't want to make parameters non-linear because it would just be harder to optimize.

## Optimization

### Least Mean Square Method
Given $n$ data points, find $\theta$ that minimizes the mean square error

$\hat \theta = argmin_\theta L(\theta) = \frac{1}{N} \sum^N_{i=1}(y^{\{i\}}-x^{\{i\}}\theta)^2$
	$y_a - y_p$
- loss function $L(\theta)$
- error function $E(\theta)$

$x^{\{i\}}$ is $1\times d+1$
$\theta$     is $d+1 \times 1$

We use square form because it can deal with negative values while still being differentiable. Also since it's a square, it 'highlights' a bad prediction heavier.

As always we set the gradient to solve for the parameters
![[Pasted image 20260624094936.png|450]]

But of course, we don't like summations because it's computationally slow so we opt for matrix multiplication instead.
![[Pasted image 20260624095107.png|450]]
![[Pasted image 20260624095144.png|450]]

To optimize this, we set the gradient to zero
$\frac{\partial L(\theta)}{\partial \theta} = -\frac{2}{n}X^T y + \frac{2}{n} X^T X \theta = 0$
=> $\theta = (X^TX)^{-1} X^T y = X^+ y$
- Pseudo-Inverse $X^T X X^+ = X^T$ for rectangular matrices
- Multiplies everything out to be $d+1 \times 1$, which makes sense for $\theta$
- This a **closed form solution**, very good! No other steps necessary

The chance that $X^TX$ being invertable is very high, and only increases the larger the matrix is. In general n>>d so almost all the time $X^TX$ will be invertible.
- But because the data is so large, we don't use the closed form solution because it's too computationally expensive to calculate the inverse

### Gradient Descent
We start from any random point and move towards gradient (direction of minimal point) to ideally get a minimal solution.
![[Pasted image 20260624100118.png|400]]
	back to summation version of MSE

![[Pasted image 20260624100141.png|450]]
Initialize theta to any random number and put it in. Continually calculate until convergence happens. And the best way to calculate convergence is to calculate our objective function, MSE.
- $\alpha$ is our learning step and hyperparameter, and it determines our step size
*insert drawing of loss per iteration chart*

It may be inefficient to go over all datapoints at every step of GD. Another option is Stochastic Gradient Descent, SGD which does one point at a time.
![[Pasted image 20260624100621.png|400]]
- In every iteration we switch datapoints
*insert drawing of loss per iteration chart*

It oscillates and is less certain but is much cheaper to run than full gradient descent (FGD).


FGD and SGD are extremes. We either use all datapoints or one datapoint.
BGD, batch gradient descent uses a subset of all datapoints, not all, not one.

For 1000 datapoints, and a batch size of 100 we'd need 10 iterations to cover them all.
- Every time we cover all datapoints it is 1 epoch. 10 iteration == 1 epoch (for this example)
- The size of the batch becomes a hyperparameter
- More often than not, people use the power of their hardware to determine the hyperparameter (batch size) beforehand

*insert drawing of loss per iteration chart*
- oscillates much less

### Linear Regression for Classification
don't use it for classification, we have other algorithms for that. but we can try

Let's say we have a picture, $16\times16$ pixels so a total of 256 parameters.
- this is waaaay to many, so we can do feature engineering to extract valuable info

Reduce the features down to 2: intensity and symmetry
	$x = (1, x_1, x_2)$
The sum of all pixels = intensity
Symmetry = -(difference between flip version)

Two good features beats out 256 useless features.

Linear Regression: $x^{\{i\}}\theta = y^{\{i\}} = \pm 1$ 
Sign Function: $\begin{cases}-1 & x^{\{i\}}\theta < 0\\ 0 & x^{\{i\}}\theta = 0 \\ 1 & x^{\{i\}}\theta > 0\end{cases}$
	collapses values into 1, -1, 0

![[Pasted image 20260624102109.png|500]]
- The parameters act as gates, and let data in given a certain value
- Sign function is our activation function which introduced non-linearity
This ends up being SGD, as we process one datapoint at a time.

![[Pasted image 20260624102557.png|400]]
Linear regression works by minimizing difference to draw a good separation line
This only works because we have great features, but sometimes it might not be possible to get such good features

## Higher Order Regression
Say we want to fit a polynomial regression model
$y = \theta_0 + \theta_1 x + \theta_2x^2 + \cdots + \theta_d x^d + \epsilon$

Say we just have one feature, height
$x = \begin{bmatrix} h \\ \cdots \\ \cdots \\ \end{bmatrix}$
we create a new z matrix with the higher order features
$z = \begin{bmatrix} h & h^2 & h^3 & \ & h^d\\ \cdots & \cdots & \cdots & \cdots & \cdots\\ \cdots & \cdots & \cdots & \cdots & \cdots  \end{bmatrix}$
![[Pasted image 20260624105233.png|400]]
By adding more features we are making the model more flexible and more degrees of freedom to adjust itself to different shapes
- This is still an LCF, even if the features have different powers

Nothing has changed except we use z instead of x.
![[Pasted image 20260624105441.png|500]]
![[Pasted image 20260624105511.png|500]]

Running a prediction on real number:
![[Pasted image 20260624105536.png|500]]
- This is a perfect model, the MSE is zero

Try using different degrees of freedom to our regression model, compared to the green ground truth.
![[Pasted image 20260624105722.png|500]]
- D=0 has high bias and is underfitted -- bad for training and real data
	- Low variance high bias
- D=9 has zero bias but is overfitted -- theoretically perfect on training, bad on real data
	- High variance low bias

Suppose we have 1000 data points and 10 features $1000\times 10$
- We can split them into smaller matrices of 100 data points, 10 $100\times 10$ matrices
- We get 10 linear regression lines as a result of this
If we had perfect data, the 10 regression lines would be directly on top of each other
*insert drawing of variance charts*

### Bias-Variance Trade Off
![[Pasted image 20260624111047.png|500]]
