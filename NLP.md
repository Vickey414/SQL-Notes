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

Feature Extraction and Convolution.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224024265-dea27a94-f9cc-41fd-97c4-1b5f16c0107d.png">

By changing the weight of the filter our model is able to learn how to identify different types of feature.eg. edge detection 
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/223849165-413cb043-e0d0-4dfa-92bd-c98c88a2a25b.png">
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224024465-98286f25-32ca-469b-bfa4-1b08d012849a.png">
* Convolutional layers: local connectivity
    ** For a neuron in the hidden layer:
        - take the inputs from patch
        - compute weighted sum
        - apply bias
** Within a single Convolutional layer now we can have multiple filters. So becomes volumn of images
** Layer dimension: h*w*d where h and w are spatial dimensions, d(depth) = number of filyers
** Stride: Filter step size
** Receptive field: Locations in input image that a node is path connect to.  
<img width="590" alt="image" src="https://user-images.githubusercontent.com/29950267/224027375-56bc3d00-aae5-4daf-8c71-12a1396dd45e.png">

* Non-linearity
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/224027533-152a1f06-3965-4195-b9d2-ff79f2e3e4d0.png">
<img width="380" alt="image" src="https://user-images.githubusercontent.com/29950267/224027649-2f94bf5c-fced-428e-b21d-32859a30a197.png">
Relu: serve as a thredhold - when an input image is less than zero, nothing get passed through.  

* Pooling: down scale our features our filters are going to attend to a larger region of the input space.  
    - To reduce the dimensionality and make the model scalable in practice while still preserve spatial invariance and structure.
    - 比如maxpooling：就是取每个filter中最大的数值
<img width="1044" alt="image" src="https://user-images.githubusercontent.com/29950267/224028951-210ea854-0f56-4b72-a04f-597b03190643.png">




### Recurrent neural networks
为什么需要有RNN（循环神经网络）
以前提到的神经网络只能取单个neuron并处理一个个的输入，前一个输入和后一个输入是完全没有关系的。但是，某些任务需要能够更好的处理序列的信息，即前面的输入和后面的输入是有关联的情况。  

<img width="325" alt="image" src="https://user-images.githubusercontent.com/29950267/224029660-839952fa-9b30-4efe-a692-d95baf3e36aa.png">
Data Sequence Model
Sequence model的情况和例子：
第一种，不是sequence
第二种：input is sequential
第三种：Output is sequential

Neurons with recurrence 循环神经网络
At the beginning(就是中间层没有关联的时候)， we treat the individual time steps as isolated time steps. We don’t yet have a notion of the relationship between time step zero to time step1.  
Our output vector at a particular time step is just going to be the input at that time step
We have this transformation yet but this is inherently sequential data and it’s probably for the sequence for some important reason and still no interdependence here.  
So we consider the output of at our last time step is related to the inputs at the previous time step how can we capture this interdependence.
We need to relate the network’s computations at a particular time step to its prior history and its memory of the network of the computations from those prior time step passing information forward and propagating it through time. And specifically the way we do this in neural recurrent models is by having what we call an internal memory or a state(h).
And the output at the particular time of t depends both on the input and the past memory
(past memory is going to capture the prior history of what has occurred previously in the sequence)
<img width="338" alt="image" src="https://user-images.githubusercontent.com/29950267/224029871-ea7178b1-4b11-438d-9090-5e39663793ca.png">
<img width="380" alt="image" src="https://user-images.githubusercontent.com/29950267/224029940-4a82511e-2030-45f6-9c3a-add342e3b286.png">


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
