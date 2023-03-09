### Convolutional neural networks 
Fully connected Neural Network:  
<img width="660" alt="image" src="https://user-images.githubusercontent.com/29950267/223809542-76b20c42-74f2-42bb-ae48-a5a067733070.png">

Implication in Image:  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/223810136-c3f9cfbd-2a87-4498-bd58-311ea9f29876.png">  
We flattern our 2D image, the spatial structure in our image previously pixels that were too closer to each other in the two-dimensional image now may be far from each other in the one-dimensional flattern vector.  

How to no ruin the spatial structure?  
To feed our input and connect it to patches of some weights so instead of feeding it to a fully connected layer of weights, just feed it to a patch of weight. Which also mean that, each neuron in our hidden layer is going to see a small patch of pixels at any given time.  
作用：1. reduce the num of params that our next layer is going to learn from   
    2. pixels that are close to each other share a lot of info(correlation).  
The patchy operation is called "convolution".  

Feature Extraction and Convolution
By changing the weight of the filter our model is able to learn how to identify different types of feature.  
<img width="867" alt="image" src="https://user-images.githubusercontent.com/29950267/223849165-413cb043-e0d0-4dfa-92bd-c98c88a2a25b.png">




### Recurrent neural networks
* Not all problems have fixed-length input and output   
* Problems with sequences of variable length.  
  ** Speech recognition, machine translation, etc.  
* RNNs can store information about past inputs for a time that is not fixed a priori.  

### Features(representations)
* Manual Feature Extraction: Domain knowledge -> Define Feature -> Detect Features to verify.   
  Not robust because of diff types of variations: viewpoint variations, scale variations, deformation, occlusion(闭塞), illumination condition, Intra-class variation, background cluster
* So we use Hierarchical representation learning
** Feature extraction (engineered) : SIFT, MFCC
** Feature aggregation (unsupervised): bag-of-words, Fisher vec
** Recognition model (supervised): linear/kernel classifier


# Tasks solved in NLP
##### Discriminative tasks:判别式任务
   * Classiﬁcation:
    - Sentiment analysis
    - Categorisation into topics
    - Spam detection
    - Intent recognition
    - Fake news detection
  * Question answering
  * Information extraction
  * Grammar correction

##### Generative tasks and seq2seq
* Machine translation
* Text summarisation
* Text simpliﬁcation and style transfer
* Text generation(auto-complete) e.g.assistance in writing e-mails, reports, articles…
* Dialog

+ speech:
  * Speech recognition
  * Text-to-speech generation
  * Speech-to-text translation
+ code
  * Automatic code commenting and documentation
  * Code generation
  * Automatic bug ﬁxing

# Bag-of-words and linear models

# word2vec
