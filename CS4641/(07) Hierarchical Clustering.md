## Overview
Hierarchical Clustering
- Tree structure
	- Agglomerative -- bottom up
	- Divisive -- top down

![[Pasted image 20260608111302.png|250]]
Partitional Clustering
- K-Means
![[Pasted image 20260608111327.png|250]]

## Hierarchical Clustering
We organize objects into a tree-based hierarchical taxonomy (dendrogram)
![[Pasted image 20260608111409.png|500]]
- If we draw a partition somewhere in the tree (horizontal, between levels) we separate the trees into clusters (3,7, ...)




![[Pasted image 20260608111534.png|550]]
- We start with seven different clusters and gradually build up an entire tree
- ((((Brown + Polar) + Black) + Speculated) + ... )
- This is chain merging


![[Pasted image 20260608112355.png|550]]

## Bottom-Up Agglomerative Clustering

1. Say each point is its own cluster
2. Find most similar pair of clusters
3. Merge it into a parent cluster
4. Repeat

How do we compare clusters if one has multiple points?
	We could compare based on the centers of clusters, called **centroid linkage**
	We could calculate all distances and take the average, **average linkage**
	We could compare based on the closest points in each clusters, **single linkage**
	We could compare based on the furthest points in each cluster, **complete linkage**
There are many ways to compare clusters to each other with tradeoffs
- Complete == balance
- Single == chaining
- Average == in-between Complete/Chain
- Centroid == also in-between


If we start with a distance matrix, $n\times n$
- This euclidean distance matrix is symmetric, dist(a,b) == dist(b,a) and dist(x,x) == 0 so it's a symmetric matrix with zero along the diagonal
After determining the new cluster, we can merge them into the new euclidean distance matrix, sized $n-1 \times n-1$
- We continually repeat this until we only have just one cluster

Once we have the complete cluster, we then can partition to have separate clusters

This is a **very** computationally expensive algorithm because pairwise linkage is expensive. This should only be used for **toy datasets**.


## Beta-CV Measure
Let W be the pair-wise distance matrix for all points. For data points S,R we define:
$W(S,R) = \sum_{x_i \in S} \sum_{x_k \in R} W_{ij}$

![[Pasted image 20260610102123.png|560]]
![[Pasted image 20260610101504.png|550]]
We calculate every possible point to every possible point, and divide by two to account for double counting. This is $\bf{W_{in}}$ the cohesion value and we want it to be a smaller value.

We also calculate every possible point to other points, outside of clusters. This is $\bf{W_{out}}$ the separation value and we want it to be a smaller value.

The issue is that strict sums bias clusters with large amounts of data points. If you sum more points, you will end up with a higher value. That's why we also need to also divide by number of points in cluster.
![[Pasted image 20260610102054.png|550]]

**BetaCV**, like elbow is a way to measure how good your clustering is

## Normalized Cut
![[Pasted image 20260610102424.png|550]]
Another metric to determine how good our clustering is.