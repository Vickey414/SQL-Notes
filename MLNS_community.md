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




