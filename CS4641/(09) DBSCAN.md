Density-Based Clustering

The basic idea is to cluster dense regions in data seperated by regions of lower density.
- This is a hard-clustering algorithm
- Cluster is defined as the maximal set of density connected points
- Good for detecting arbitrarily shaped clustering

DBSCAN (Density Based Spatial Clustering of Applications with Noise)

## Overall
Unlike GMM or K-means we don't need to know the number of clusters in advance.

We do have two hyperparameters:
- Epsilon $\epsilon$, the maximum radius of the neighborhood
- MinPts, minimum number of points in the $\epsilon$-neighborhood of a point

High density: $\epsilon$-neighborhood of an object contains at least MinPts of objects
- if it doesn't satisfy the condition, it is considered a low density region

We do this by preforming a radial search: if the euclidian distance between two points is less than the radius.
- One problem with radial search is that it can be very computationally expensive
- Also the center of the point must be in the radius to be considered

**Core points** are those whos $\epsilon$-neighborhood contains MinPts points
**Border points** are those whos $\epsilon$-neighborhood doesn't fufill the MinPts, but were still previously considered to be within the radius of another point, so is considered for the cluster.
**Outliers** don't belong to any cluster

1. We start from any point and begin counting the $\epsilon$ neighborhood (including itself)
2. The inital point is visited, and if its a core point (satisfies MinPts) we add all the points within the $\epsilon$-neighborhood into a queue
3. We continue down the queue:
	1. If the point is a core point, we continue to add all neighbors to the queue
	2. If the point is a border point, we don't add any neighbor points to the queue
4. Repeat until queue is empty, then repeat with new random point
Point statuses can be changed as well. It could start as an outlier, but then checked by another point and change it's status to border point.
- Outlier -> Border is okay
- Outlier -> Core and Border -> Core is not possible

DBSCAN is "almost deterministic"
- It only has issues with bridging points, points that have the possibility to belong to either cluster

## Directly Density Reachable
Points within $\epsilon$-neighborhoods of other core points
- This is one-directional, border points are ddr to it's core point neighbor, but not the other way around
- This means direct density reachability is not symmetric

Density reachable means reachable through a chain of ddr points.

![[Pasted image 20260624212217.png|400]]
- H->Q **directly** density reachable
- Q->H **not directly** density reachable
- Q <-> H density reachable
Notice how we can also reach Z from H and vice versa
- H, Z are related via **density connectivity**
Density connection are points

## Analysis
DB Scan is very sensitive to $\epsilon$, not as sensitive to Minpts
- A high value of eps means cluster will merge and majority of datapoints will be in the same cluster, overclustering
- A low value of eps means large parts of data will be outliers, underclustering

We don't need to define the number of clusters though.

Generally MinPts should be at least 3
- Rule of thumb MinPts >= d+1
- For noisy data MinPts >=q 2*d