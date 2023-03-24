#  Network Cascades

Definition: Contagion that spreads over the edges of the network
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227458423-5bc9649c-0ee6-4c0a-b225-82e9b855aff9.png">


### How to we model influnce/Diffusion

* Decision based model
- A node observes decisions of its neighbors and makes its own decision.  


* Probabilistic models
- An infected node tries to “push” the contagion to an uninfected node


### Spreading Models of Viruses
2 param:
- Birth Rate($\beta$): Probability than an infected neighbor attacks and infects a healthy neighbor
- Death Rate($\delta$): Probability that an infected node heals

#### SEIR Model
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227459897-fa145573-9567-422d-b111-6b6b35121711.png">

#### SIR Model  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461072-c3f59d4b-f4b9-4f82-b6f3-2fe7c0b66200.png">   
Assumption: Once you heal, you can never get infected again.  
• Assuming perfect mixing (the network is a complete graph) the  model dynamics is:  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461193-d5324eb5-cf1a-4e89-9537-8cc9a6fe69ef.png">

##### SIS Model (Susceptible-Infected-Susceptible)
• Assumption: Cured nodes immediately become susceptible
• Important factor: Virus “strength”: s = β / δ
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461503-2b7d016e-84ca-4a99-bda0-ae99aecbcdc3.png">

• epidemic thredhold: 在这个thredhold以上或者以下去定义infection的情况
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461907-99a5ca50-d312-462b-a1bb-746733270a35.png">
Find a condition that connects the properties of the virus and the structure of the graph, under which.  
– s = β / δ < τ : virus will die out exponentially quickly    
– s = β / δ > τ : the infection survives and  becomes an epidemic.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227462561-a0126150-c42a-4c6a-aaa3-a171b831d173.png">
Similarity to this Connection: centrality matrix [也是用到了largest eign-vector，但是是用到transition matrix]   
With higer eign-value, the better connectivity.   
怎么看图.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227463857-4d882808-5f40-4f49-be50-acd992d4fe23.png">

##### IC model(Independent Cascade)
• Assumption: Initially some nodes S are active
• Each edge (u,v) has probability (weight) $p_uv$, when node u becomes active/infected, It activates each out-neighbor v with prob $p_uv$
• Activations spread through the network.  
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227464375-3d558625-ec2f-42f0-b3b8-78103dc8838a.png">

#### LT model(Linear threshold)
* 公式  
• A node v has a random threshold θv  ~ U[0,1]
• A node v is influenced by each neighbor w according to a weight $b_vw$ such that 
<img width="200" alt="image" src="https://user-images.githubusercontent.com/29950267/227465626-38f1873a-392d-48b6-b552-a62c108c397f.png">
• A node v becomes active when at least θv fraction of its neighbors are active
<img width="200" alt="image" src="https://user-images.githubusercontent.com/29950267/227465696-52956fbf-126b-490d-85d3-7134b64f1f8c.png">
X(v): set of active neighbors of v: 表示V的邻近被active的nodes

### Identification of Influential Spreaders
• Application in epidemic control: detect and vaccinate infected individuals with good spreading properties
• Application in viral marketing: word-of-mouth effect; target a few  initial individuals that can spread the idea/product to a large fraction of the population

• Straightforward approach: consider degree centrality 
– High degree nodes are expected to be good spreaders 
– Hub nodes can trigger big cascades

我们可以用centrality来衡量nodes是否是Influential Spreaders， 但这不是绝对的，because degree is a local criterion局部指标，maybe the high degree nodes are connected to very low degree node

Core-periphery structure of real-world networks

##### Way to calculate Core-periphery
* Degeneracy and k-Core Decomposition   
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227468141-e933c117-c2cc-4076-83b2-2c6afe7e383f.png">
就是一层层的，先从degree = 1的地方删除nodes，然后计算下一层的degree，删除degree = 2的层，比如在这个例子中，已经找不到degree = 4的点的，因为最后remove degree = 3的层，the graph will finally vanish.  

Basic conclusion:
• Strategically placed nodes, as detected by the k-core decomposition are able to spread information to a larger portion of the graph
• The core number is a better spreading predictor compared to the degree 

Heuristic Methods.  
Why no gurantee? 一般是使用与比较not aprroprite distributed的graph


### Influence maximization
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227471601-5bf0bf6f-9296-46e3-90b3-30428f4d3889.png">
Most influential set of size k: set  S of k nodes producing the largest expected cascade size f(S) if activated: maxf(S)

