ML is broken into two categories:
- Unsupervised Learning
	No labels $y$, need to explore $x$, via clustering, then EDA, and a pretext for SL
- Supervised Learning
	With labels $x,y$ , by regression

Occam's razor when it comes to ML, start with the simplest baby model possible, on a toy dataset. If it works, the we can consider making it more advanced.

Clustering is difficult, for almost everything we can divide clusters everywhere arbitrarily, dependent of shape, color, culture, politics, etc.
- Clustering is **subjective** and is context dependent

---

## Distance Function

### Euclidean Distance
Properties of dissimilarity function
- $d(x,y) = d(y,x)$
- $d(x,y) = 0$ iff $x=y$
- triangle inequality

Suppose two datapoints both in $R^d$, $x = (x_1, x_2, ..., x_d)$$ $y = (y_1, y_2, ..., y_d)$

We like the euclidean distance $d(x,y) = \sqrt{\sum^d_{i=1} (x_i-y_i)^2}$ ($l_2$ norm) because it's easy to optimize and therefore easier to train

Other options are:
- Manhattan distance ($l_1$ norm)
- Minkowski distance ($l_p$ norm)
- Inf distance ($l_\infty$ norm)
These aren't necessarily always bad and they do have applications, but in general euclidian is more useful

Traversing a map from point A to point B, you can't just draw a straight line to calculate distance, you'll need to go road by road, block by block
	**Manhattan Distance**

As we continually increase the distance between data points and features, then at a certain point distance functions become useless because when everything is too far away, relative distance is zero.
	**Inf Distance**

The ML model demands for datapoints to features at an exponential rate. For every new feature we add, we need exponentially more datapoints. In general then we want to minimize features used.

### Edit Distance
Transform one object to another and measure how much effort it takes

![[Pasted image 20260608100853.png|550]]
- Deletion has higher cost because sometimes deletions are on purpose
- This doesn't satisfy symmetry, if we were to swap x and y deletion becomes insertion which has different costs

---

## K-Means Algorithm

Review on GD
$x^{\{t+1\}} \leftarrow x^{\{t\}} - \alpha \frac{\delta f(x)}{\delta x}$
- $-$ means gradient **de**scent
- $+$ means gradient **as**cent
- $\alpha$ is the learning step -> we need hyperparameters

For K-Means we need $K$, the hyperparameter

![[Pasted image 20260608101503.png|500]]
![[Pasted image 20260608101552.png|500]]
- $K=11$ makes more groups and is pretty solid, but how do we choose a good value for our hyperparameters? (research topic)


Iterative Process
1. Choose centroid
2. Calculate distance and cluster based on clustering
3. Move centroid to be the center of the cluster regious
4. Recalculate distance and recluster based on distance
5. Repeat until convergence

We then finally determine the cluster when we sum all the distances per cluster to their centroid
- We want distances to be as little as possible because that means a tight clustering, so our objective function becomes minimizing the distances to the centroid


### Hard Clustering
Initialize $k$ cluster centers $c_1, c_2, ..., c_k$ randomly

Then:
- Decide cluster membership of each datapoint $x_i$ by assigning it to the nearest cluster center **(cluster assignment)** $\pi(i) = argmin_{j=1,...k} ||x^{\{i\}}-c^{\{i\}}||^2$
- Adjust the cluster centers **(cluster adjustment)** $c_j = \frac{1}{|i:\pi(i)=j|}\sum_{i:\pi(i)}x_i$
Repeat until the objective function is converged


This is called **hard clustering** because once the cluster has been determined, it is solid and is not possible to change clustering

This is also used in EM, Expectation Maximization because we want to maximize where we expect it to be

K-Clustering is non-deterministic and depends on where the initial points are
K-Clustering does however always stop at some point (local minima)

### Formal Statement
- Given $n$ data points $\{x_1,x_2,...,x_n\}$ $x \in R^d$
- Find $k$ cluster centers $\{c_1, c_2, ..., c_k\}$ $c \in R^d$
- And assign each data point $i$ to one cluster, $\pi(i)\in \{1,...,k\}$
- Such that the average square distances from each data point to respective cluster center is small
**Objective Function: Distortion**
$min_{c,j} \sum^n_{i=1} ||x_i - c_{\pi(i)}||^2$


*insert slide of how minimizing the formula means c needs to be the avg of data points*

Clustering is an NP-Hard problem and for k clusters and n points, there are $n^k$ possibilites

### Choosing a good K
![[Pasted image 20260608110949.png|550]]



K-Means works good for euclidian distances in data, so circular things
Distance function can work as a hyperparameter, something we can choose, for K-Means
- If we use Manhattan Distance instead of euclidian distance it becomes K-Medians
- K-Means works well for circular sets, K-Medians for diamond, squareish sets