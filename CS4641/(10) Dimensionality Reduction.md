## PCA (Principal Component Analysis)
is an unsupervised dimensionality reduction method

for each feature, we'll need 15-20 data points as well

![[Pasted image 20260622093738.png]]
Increasing the number of dimensions increases freedoms, allowing for a more accurate decision line that seperates the two features
- This can cause overfitting, so we need to allow some freedom but not too much

![[Pasted image 20260622094530.png|400]]
- These new z axes measure variance between datapoints
- We generally want more variance between data, because that would signify a difference
- However, too much variance can be bad because if cats are as different from each other as they are from dogs, then it wouldn't work.

With a data point we need to project it onto the z dimensions via dot product
*insert slide about dot product onto z space*

When we go from x-space to z-space we will have exactly the same amount of dimensions in both. We go from one space to another by doing a dot product against w, unit vectors.

$x^{\{1\}} \cdot \frac{z_1}{||z_1||} = x^{\{1\}} \cdot w_1$

$x^{\{1\}} \rightarrow z^{\{1\}} \Rightarrow [h^{\{1\}},e^{\{1\}}] \rightarrow [z_1^{\{1\}}, z_2^{\{1\}}]$

$z_1^{\{1\}} = x^{\{1\}} \cdot w_1 = [h^{\{1\}}, e^{\{1\}}] \begin{bmatrix} w_{11} \\ w_{21} \end{bmatrix}  = w_{11} h^{\{1\}} + w_{21} e^{\{1\}}$

$[h^{\{1\}},e^{\{1\}}] \rightarrow [w_{11}h^{\{1\}}+w_{21}e^{\{1\}},w_{12}h^{\{1\}}+w_{22}e^{\{1\}}]$


x-space variance: $Var(x) = \frac{1}{N}\sum^N_{i=1}(x^{\{i\}}-\mu)^2$
z-space variance: $Var(z) = \frac{1}{N}\sum^N_{i=1}(x^{\{i\}}\cdot w - \mu \cdot w)^2$
- s.t $||w|| = 1$
- maximize

By dot producing everything by w, data point and mean, we cast it to z-space and get the equivalent (and w must be a unit vector or it changes things)
- This algorithm is very sensitive to scale, if we alter the scale of height/weight by any amount, then the variance will as well
- So we want everything to stay on the same scale, so $||w|| = 1$

We can make sure scale stays even more constant by standardization
$X\rightarrow \bar X \rightarrow \bar X^*$
data -> centralized -> standardized

*insert formula for standardization from slides*

## Optimization
PCA:
- maximizes variance between the new points
- minimizes square distance to the original points


insert entire slide of calculating pca
- We calculate var(x) and covariance matrix C
- var(z) is just the eigenvector of the covariance matrix

To optimize z-space, we need to maximize variance
$Var(z) = w^TCw$
$cw = \lambda w = w \lambda = w^Tw\lambda = (1)\lambda$
- $\lambda$ is a scalar so we can move it around however we'd like
- finding $\lambda$ IS the optimization

in numpy, the eigenvectors are calculated s.t $\lambda_1 \geq \lambda_2 \geq \cdots \lambda_n$ meaning variance decreases from 1, 2, ...


Since C is a diagonal matrix, then it guarantees all eigenvectors are orthogonal to each other.

We implement a hyper parameter to decide to keep the top n% of data
- Sum the top lambdas and divide by total lambdas to see if it reaches that n%

In real life, the covariance matrix itself is difficult and computationally expensive, even if it is already simplified. Instead we use SVD decomposition.

## Supervised Dimensionality Reduction
Previously we only needed the data to compute the covariance matrix to run PCA.
- Went from x-space to z-space, but the model is trained on z-space
- We need to convert test data from x-space to z-space -- this is one drawback of PCA

What if we just want to run dimensionality reduction on x-space?
Suppose we have a ton of features (h,w,a, etc..) and the associated y vector of tags
- Next we go from x-space to z-space for just one feature, say h along with y and put it into any supervised learning algorithm (NB, SVM, NN, etc.)
- For each feature we also keep track of its accuracy
- Whichever model outputs the best accuracy is what we use
- Hyper parameter of total accuracy


We could then start stacking features on top of each other. We could combine (h,w) to see the accuracy, or (h,a,etc). We run it on the combinations to see if it is above the total accuracy threshold -- then we know which features we need to keep.

This is **forward feature selection**.


Alternatively we could start with every feature and remove them one by one to determine which has the most accuracy change. Whichever has the most is removed and process is continued until we hit our total accuracy.

This is **backwards feature selection**.

This can be very slow. If we had 20 features, we'd have to train every model (all algorithms) twenty times on the different features. Very slow and time consuming.