Floyd transformation

<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222664691-07b7d754-5001-4760-889a-1cd568c19bb8.png">


* Feature Extraction From Graphs

ML tasks will need to extract different graph features


* Graph Representation Learning (GRL)
1. How to learn the function $\phi$: The function $\phi$ is to map from nodes to embeddings
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222667103-1dd54b18-8d2a-476a-a034-b56111490dc5.png">

2. How to Define Node Similarity?
* Matrix Factorization Method


* Random walk-based models
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222669172-68875e1d-df9e-47b1-9e02-a3ba69013e74.png">
$\Z_{u}Z_{v}$ = probability that v and u co-occur on a random-walk over the network Pr(u|v).
  To take the transition matrix



* DeepWalk and node2vec algorithms
- SkipGram for Graphs?
Use the SkipGram to learn the nodes

The normalization step over all nodes from the softmax function impacts complexity. Can we approximate it?
Here we use negative sampling -  To solve the computational issue
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222674615-6dc11a73-cc85-4c67-a015-b0ee7effc368.png">

- How should we perform random walk
node2vec: Biased Random Walks
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222675804-a20bbffd-28ec-4a60-a0a3-704f8cd1ae61.png">
BFS view: Local community
DFS view: Global neighborhood
Those searching strategies can capture two properties of social networks that lead to different concepts of similarity Homophily(BFS) and structural equivalence(DFS)
u and $S_6$: the same degree, identify as the same role

Biased Random Walk
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222677228-0ccabcf1-07e4-48ff-83ac-1b16484d8805.png">







  
  


