# Decision Tree
#### Definition
* A decision tree is a binary tree that recursively segment the input space X（also called the feature space）along the coordinate directions 
to create a set of K hyper-rectangles $R_k$ , k∈{1,...,K } as basic prediction units for ﬁtting constant values $\gamma_k$  within each of them.   
                  $f(x)$ = $\displaystyle\sum_{k=1}^k$ $\gamma_k$ $1_{x∈R_k}$.  
$\gamma_k$ is the corresponding predicted value or class for the dependent variable (called also output variable and denoted Y). And $\gamma_k$ is the decision tree parameter.  
  
 #### 决策树的性质
  * The set of K hyper-rectangles $R_k$ is determined by a set of K−1 chosen splits and their order during the recursive binary segmentation.  
  * Each split is determined by a greedy strategy to best discriminate the observations in its two branches respectively.  
  * The ﬁtted value $\gamma_k$ assigned to each terminal node Rk is usually decided by the majority vote (classiﬁcation task) or the average (regression task).  
  * Non-parameter model: It’s not because it does not have any but because the number of parameters is not determined prior to training.  
  * Decision Tree are intuitive and easy to interpret. Such models are often called white box models.
  * In contrast, Random Forests are generally considered black box models. Black box make great predictions but it is usually hard to explain.  

#### How to evaluate DT
  * By minimizing a given risk function or impurity measure.
      R(f):= P(y $\neq$ f(x))  
      
#### Building a regression decision Tree
Given a learning set D ={ ( $x_i$ , $y_i$)_ $1 \leq i \leq n$ } ⊂ X×Y and using the empirical quadratic risk function, one should solve:
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215343140-a98d0a2b-e116-4110-b1fa-268f7b4114da.png">
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215343164-1729bf4d-42d8-445e-b292-6a0d1508eb44.png">
* Conclusion
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215343197-21ab7906-f9d8-4ae6-8088-248d02075ad1.png">

#### CART  
Definition: CART provides a partition of $R_2$ in classes by horizontal/vertical line segments.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215343244-e1559df3-33f5-48a9-9bbe-61528eddd0d3.png">


##### How  much  should  we  let  the  tree  grow?
  * Too big a tree may overﬁt the data
  * Too small a tree risk of not capturing their structure
  * The optimal size is a hyper-parameter to calibrate on the data.  
> Methods： 
>> * The repetition is made until a stopping criterion is met. Examples of stopping criterion:
>>> *  maximum depth
>>> *  maximum number of leaves
>>> *  minimum number of sample per leaf
>> * Pruning: We make the tree grow to the maximum and then we remove the uninteresting nodes.
>>> * Penalized Criterion
>>> $R_α(f_T)$ = $R_n(f_T)$ + α ${|T|} \over n$
>>> $R_α(f_T)$ is the error term linked to the decision subtree fT (ex: Mean Squared error or the rate of misclassiﬁcations)
>>> The complexity parameter α∈[0, 1] penalizes large trees

##### Building a classiﬁcation DT:Formalization
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215356136-b14bf21c-b80f-4000-b0c1-9fd1110f70b4.png">
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/215356153-6eaba252-886a-44d1-84e2-2992a3fb5350.png">

To split nodes, we want to choose a split yielding a maximal impurity reduction to solve the optimization problem 
 * Misclassiﬁcation error: Q($D_k$) = ${1} \over {n_k}$ $\displaystyle\sum_{x_i \in R_k}$ $I_{{y_i \neq c(k)}}$ = 1- $P_{k,c(k)}$


