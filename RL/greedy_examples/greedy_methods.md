### Greedy Algorithm
* That the greedy policy has linear regret means that an expectation the regret grows as a function that is linear to the number of steps you have take.
* Compare:
  * The greedy policy can lock into a suboptimal action forever.  
  * The $\varepsilon$-greedy policy continue to explore forever.  
* The $\varepsilon$-greedy algorithm
* 例子： 在一家餐厅里面，客人来了不用点单，用算法决定给客人选哪道菜,菜做得好吃的概率为p，不好吃为1-p,菜做的好吃时，客人留下奖励 = 1，菜不好吃时奖励为0
###### 解决思路  
* 探索阶段 (Exploration)：通过多次观测推断出一道菜做的好吃的概率－如果一道菜已经推荐了k遍（获取了k次反馈），我们就可以算出菜做的好吃的概率：  
p = $\displaystyle\sum_{reward_i} \over k $.  
  * 如果推荐的次数足够多，k足够大，那么p(heart)会趋近于真实的菜做的好吃的概率p.  

* 利用阶段 (Exploitation)：已知所有的菜做的好吃的概率，该如何推荐？－ 如果每道菜都推荐了多遍，我们就可以计算出N道菜做的好吃的概率{ $p_1$, $p_2$, $p_3$ ..., $p_N$ }，那么我们就可以推荐p(heart)最大的那道菜.
  * Exploration的代价是要不停的拿用户去试菜，影响客户的体验，但有助于更加准确的估计每道菜好吃的概率.  
  * Exploitation会基于目前的估计拿出“最好的”菜来服务客户，但目前的估计可能是不准的（因为试吃的人还不够多）.  

* With the probability of 1- $\varepsilon$ select the greedy action. [Exploration].  
* With the probability of $\varepsilon$ select the random action. [Exploitation].  
