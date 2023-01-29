# Decision Tree
 Definition: A decision tree is a binary tree that recursively segment the input space X（also called the feature space）along the coordinate directions 
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
###### Building a regression decision Tree
Given a learning set D ={ ( $x_i$ , $y_i$)_ $1 \leq i \leq n$ ⊂ X×Y and using the empirical quadratic risk function, one should solve:


##### CART  
Definition: CART provides a partition of $R_2$ in classes by horizontal/vertical line segments.  


##### How  much  should  we  let  the  tree  grow?
  * Too big a tree may overﬁt the data
  * Too small a tree risk of not capturing their structure
  * The optimal size is a hyper-parameter to calibrate on the data.  
> 方法： 
>> * The repetition is made until a stopping criterion is met. Examples of stopping criterion:
>>> *  maximum depth
>>> *  maximum number of leaves
>>> *  minimum number of sample per leaf
>> * Pruning: We make the tree grow to the maximum and then we remove the uninteresting nodes.
>>> * Penalized Criterion
>>> $R_α(f_T)$ = $R_n(f_T)$ + α ${|T|} \over n$
>>> $R_α(f_T)$ is the error term linked to the decision subtree fT (ex: Mean Squared error or the rate of misclassiﬁcations)
>>> The complexity parameter α∈[0, 1] penalizes large trees

