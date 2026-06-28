## Norms
Norm informally is a measure of the "length" of a vector, $|| x ||$
- $x \in \mathbb{R}^d$, vector of size $1 \times d$

Formally, norm is any function that maps $f: \mathbb{R}^d \rightarrow \mathbb{R}$
	Norms must be:
- Nonnegative $f(x) \geq 0$
- Definite $f(x) = 0 \iff x= 0$
- Homogenous
- Satisfy Triangle Inequality

Norms are used for optimization == training. Commonly used norms are
	$l_2 \text{ norm}$
	$||x||_2 = \sqrt{\sum_{i=1}^d}x_i^2$
	This is **differentiable** which makes it good

$l_1$ norm
$||x||_1 = \sum_{i=1}^d |x_i|$
- This is not always differentiable

$l_\infty$ norm
$||x||_\infty = \sum_{i=1}^d \ max_i |x_i|$
- This only chooses the max

$l_p$ norm
$||x||_p = (\sum_{i=1}^d |x|^p)^{\frac{1}{p}}$
- This, like $l_2$ is differentiable but the function is more 'complicated'
- $\frac{d}{dx} f(x) = x^4 = 4x^3\ \ \ \ \text{vs}\ \ \ \ \ \frac{d}{dx} f(x)=x^2 = 2x$

![[Pasted image 20260520095323.png|450]]

## Special Matrices

Identity matrix is where diagonals are ones and everything else zeroes

Diagonal matrix is where all non-diagonal elements are zero
$A = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 3 \end{bmatrix}$
$A^{-1} = \begin{bmatrix} \frac{1}{1} & 0 & 0 \\ 0 & \frac{1}{2} & 0 \\ 0 & 0 & \frac{1}{3} \end{bmatrix} = \frac{1}{A}$

Two vectors $x,y \in \mathbb{R}^d$ are orthogonal if $x \cdot y = 0$
A square matrix is **orthonormal** if columns are orthogonal to each other and normalized.
- $U U^T = I = U^T U$
- $||Ux||_2 = ||x||_2$


## Linear Independence and Matrix Rank
For dot products, we can say if $x \cdot y = 0$ they are orthogonal, and **linearly** independent. Independence is too strong of an assumption to say

Linear Dependency means no vector can be represented as a linear combination of the other vectors. 
	For data point matrices, this means features compared to each other. We want linearly independent data point matrices if features are can be formed from each other, it would be pointless.

We have Tall (more rows than cols) and Wide (more cols than rows) matrices. In ML, we use tall matrices

**Column Rank** is the size of the largest subset of cols that form a linearly independent set
**Row Rank** is the size of the largest subset of rows that form a linearly independent set
**Full Rank** is if the rank is $min\{n,d\}$ and it is the maximum possible rank
- This can turn rows/cols in a matrix to be redundant, can be used to perform dimensionality reduction
- Matrices with full rank means they are also invertable

## Matrix Inverse
In ML, the matrix inverse is in the "do not look list"

Inverse matrices are those where for a matrix $A$, there exists an inverse $A^{-1}$ such that $AA^{-1} = I$ and $A^{-1}A = I$ . In order for A to have an inverse it must be full rank.

For non-square matrices denoted by $A^+$ is given by $A^+ = (A^TA)^{-1}A^T$ is the **pseudo inverse**

Since for this course n >> d, when we multiply $A_{n \times d} \cdot A^{-1}_{n \times d}$ it doesn't equal $I_{d \times d}$
- We would need $A^T_{d \times n} \cdot A^{-1}_{n \times d} = I_{d \times d}$

## Matrix Determinant
$det(A)=\sum_{j=1}^d = (-1)^{i+j} a_{ij}M{ij}$
For a $2 \times 2$ matrix:
	$det(A) = ad-bc$
![[Pasted image 20260520102815.png|450]]

## Eigenvalue and Eigenvector
When we perform matrix by vector multiplication, the matrix has the ability to both scale and rotate the vector to some other new vector. However, if it is the eigenvalue $\lambda$, then there will be no rotation component, only scaling.
	$Ax = \lambda x, x\neq 0$

This means, if we multiply the matrix A with a vector x and get the same vector scaled, then we know what eigenvalue $\lambda$ is

$Ax = \lambda x$
$Ax - \lambda x = 0$
$(A-\lambda I)x = 0$
This only works when $|A-\lambda I| = 0$, so $A-\lambda I$ cannot be full rank

**Matrix Trace** is the sum of the diagonal elements in the array

## SVD
n: instances
d: dimensions
X is a centered matrix
	$\bar X_{n \times d}$

$U_{n\times n}$ unitary matrix $U \times U^T = I$, $U^T = U^{-1}$
$\Sigma_{n\times d}$ diagonal matrix
$V_{d \times d}$ unitary matrix $V \times V^T = I$, $V^T = V^{-1}$

This splits a massive matrix into three smaller matrix representations. We lose some data in exchange for speed. This is still okay though since lots of data has noise.

### Covariance Matrix
$C_{d \times d} = \frac{\bar X^T \bar X}{n}$
where $\bar X = U\Sigma V^T$
- Calculating the covariance matrix is extremely time consuming
- The direct calculation is long and difficult
$C = \frac{V\Sigma^T U^T \Sigma V^T}{n} = \frac{V\Sigma^2 V^T}{n}$
$CV = \frac{V\Sigma^2V^TV}{n} = \frac{V\Sigma^2}{n} = V\frac{\Sigma^2}{n}$
$CX = X\Lambda$ where V is our $X$ matrix, and $\frac{\Sigma^2}{n}$ is our eigenvalue


`np.svd(x)` calculates it for us

