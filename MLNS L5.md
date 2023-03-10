# GNN
shallow encoder: DeepWalk and node2vec, line algorithm
### Limitations of “Shallow Encoders”
* Shallow Encoders do not scale, as each node has a unique embedding.
Shallow Encoders are inherently transductive. It can only generate embeddings for a single fixed graph.
Node Features are not taken into consideration.
Shallow Encoders cannot be generalized to train with different loss functions.
Fortunately, graph neural networks can solve the above limitations.
