Dynamic Programming 

Dynamic Programming is a very general solution method for problems which have two properties
* Optimal substructure：最优子结构：利用动态规划算法求解问题的第一步就是需要刻画问题最优解的结构，并且如果一个问题的最优解包含其子问题的最优解，则此问题具备最优子结构的性质。
因此，判断某个问题是否适合用动态规划算法，需要判断该问题是否具有最优子结构。
* Overlapping subproblems：
重叠子问题： 适合用动态规划算法去求解的最优化问题应该具备的第二个性质是问题的子问题空间必须足够” 小 “，也就是说原问题递归求解时会重复相同的子问题，而不是一直生成新的子问题。
如果原问题的递归算法反复求解相同的子问题，我们就称该最优化问题具有重叠子问题。

Markov decision analysis process satisfy both properties because (1)Bellman equation gives recursive decomposition. (2) Value function stores and reuses solutions 

Interative Policy Function 
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222728769-e32b98c0-f4a8-40f3-af3c-5b0f2046a9f1.png">
We have the current state, given a policy we want to calculate the value function
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222730507-3eda479c-3c82-485a-afdb-810c51dc1779.png">
最后左上角和右下角是目的地，每个格子行动方向为上下左右，每走一步reward-1，求一个在每个状态都能以最少步数到达目的地的最优行动策略。我们给出的策略是一个uniform random policy，
最后能达到这个目标对应的grid每个的value得到的value function.  
When k become infinite, the grids value function will converge to some point and the come to a static stage.

Policy Iteration
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/222733076-3ce5b7c8-44ff-4b03-b940-dce0dee993ba.png">


Value Iteration: To find the optimal policy
Deterministic Value Iteration
假设我知道了达到下个阶段最佳状态的最大价值方程

Formula：v*(s) <- max
If we know the solution of the subproblems v*(s')
Intuition: start with final rewards and work backwards



Asynchronous updates





Policy Evaluation
