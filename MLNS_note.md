## Preface
### Ways to analyze network data
* Identify important/influential nodes
  * Centrality criteria
  * Example: viral marketing
* Predict the type/class of a given node
  * Node classification
  * Example: classify online users / products
* Predict whether two nodes are linked
  * Link prediction
  * Example: friend recommendation, knowledge graph completion  
* Measure similarity of two graphs  
  * Graph similarity and graph classification  
  * Example: molecule property prediction
  *why shall we measure the similarity of two graphs?

* Identify densely connected clusters of nodes  
  * Clustering and community detection  
  * Identify user with the same interest.  
  * Example: Social circle detection in social media
*  graph generation (drug discovery/generate graph with the same character).
*  graph evolution (simulations)


### Examples of network graph
*  Traffic Prediction
*  Recommender Systems
*  The Protein Folding Problem
*  Social Circal Detection
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215038994-2cb4acaa-1a89-4548-a377-5540cacf72e9.png">
*  Predicting Epidemics
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215038819-b77a78ca-bedf-4d75-adc1-c86e1ee4e11c.png">


## Concepts of Graph

<img width="420" alt="image" src="https://user-images.githubusercontent.com/29950267/215040372-21e2b669-3505-4bad-ae37-447b94c636a3.png">
G = （V,E） n =|V| # of nodes/vertices, m = |E| # of edges

<img width="420" alt="image" src="https://user-images.githubusercontent.com/29950267/215040863-190d3987-5771-4c74-a598-eaf5673c9739.png">
Undirect graph: The Adjacncy Matrix is symmetric.
Directed graph: The Adjacncy Matrix is nonsymmetric.


Complete graph: A graph G = (V, E) is called complete Kn if every pair of nodes is connected by an edge

### Graph traversal algorithms

#### Breadth-first search (BFS)

#### Depth-First Search (DFS)

#### Connected Components
Definition: A connected component is a maximal connected subgraph of a graph G (there is a path between any pair of nodes)



#### Key Network Properties
Degree distribution: P(k)
Path length: h
Clustering coefficient: C


Number of Paths
使用Adjacncy Matrix to compute


Network Diameter measure how spread of the network



<img width="420" alt="image" src="https://user-images.githubusercontent.com/29950267/215052148-845071b9-8df0-4745-88e4-41b1b0d2029a.png">
We use the log-log to 
<img width="420" alt="image" src="https://user-images.githubusercontent.com/29950267/215052364-5f0f2b8d-369a-4583-9ffb-b852a7d7d454.png">
看上去就是一个抛物线
Let p(k) = fraction of nodes with degree k
p(k) / ck�↵
with α > 1 and c a constant
• How to recognize a power-law distribution?
logp(k) = logc 
转换之后是一个类抛物线的结构


#### Are these values “expected”? Are they “surprising”?
Model we use to answer this model: The Erdős–Rényi random graph model
##### The Erdős–Rényi random graph model
<img width="881" alt="image" src="https://user-images.githubusercontent.com/29950267/215054506-38155f75-d930-4b23-8d23-ad25a162e9da.png">
We use statiscal model to generate the model, and use the graph to compare with real-life model.
Gn,p: undirected graph on n nodes and each edge (u, v) appears i.i.d. with probability p
Gn,m : undirected  graph with n nodes, and m uniformly at random picked edges(m个服从正态分布的nodes)





