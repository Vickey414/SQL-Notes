## Community


## Community Detection
K-means is not a good way to identify community. 
K-means requires that the graph should be convex/bold/Gaussian Distribution

Steps:
1. Construct a similarity graph based on the topological(拓扑) relationships and distances between data points
2. Then, the problem of clustering the set of data points is transformed to a graph clustering problem

## Graph cuts and graph partitioning


How to solve:
#### Ratio Cut
Normalize cut by the size of the groups
ratio-cut(A,B) = cut(A,B)/|A| + cut(A,B)/|B|
|A||B|表示the size of A and B


#### Normalized Cut
– Connectivity between groups relative to the density of each 
group
normalized-cut(A,B) = cut(A,B)/vol (A) + cut(A,B)/vol (B)
– Vol(A): total weighted degree of the nodes in A, i.e., Σi∈Aki

• Why use this criterion?
– It produces more balanced partitions
• How do we efficiently find a good partition? 
– Computing the optimal cut is NP-hard

Ratio Cut and Normal Cut may obtain better results than the minimum cut, and the normal cut will gain better results
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225849017-743e189a-f761-4d1d-9282-9561d2e92d2e.png">


## Spectral clustering for graph partitioning 
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225849793-223bce29-b290-4174-8bf0-653df44fc394.png">
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225850202-a83737d5-3654-4bc7-8123-6ab6164a45ef.png">
As we have constraints on the s, we can view it as an optimization problem.

– Idea: relax the binary constraints to real ones  $s_2$ = $R^|V|$, $|k|^2$ = 1
变成一个等式而不是binary问题，使得optimization更容易解决
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225851468-5ada3530-2ae7-4d03-80dd-3bdf8a39af26.png">

Spectrum and connectivity
– The smallest eigenvalue λ1 of L is zero
– If the second smallest eigenvalue λ2 ≠ 0, then G is connected 
– If L has n zero eigenvalues, G has n connected components

### k-Way Spectral Clustering
Step:
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225855663-61ebb368-2de3-45ae-a4b3-8f950cc4ae49.png">

How to select k
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225855544-5827e5e4-0fdf-4834-8eee-ac46c2f958a9.png">

## Girvan-Newman’s Method
1. 首先先知道怎么计算importance of the node
* Divisive hierarchical clustering based on the notion of edge betweenness centrality
– Number of shortest paths passing through the edge
* Algorithm
1.  Calculate the betweenness centrality of all edges in the graph
2.  Remove the edge with the highest betweenness score
3.  Recalculate betweenness for all edges affected by the removal
4.  Repeat step 2 until no edges remain
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/225856568-d03ecfc0-b5b4-452b-bfa6-bf4d94e31412.png">

这是一个切分comminity中不同clusters的方法






