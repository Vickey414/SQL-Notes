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
Assumption: Once you heal, you can never get infected again
• Assuming perfect mixing (the network is a complete graph) the  model dynamics is:
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461193-d5324eb5-cf1a-4e89-9537-8cc9a6fe69ef.png">

##### SIS Model (Susceptible-Infected-Susceptible)
• Assumption: Cured nodes immediately become susceptible
• Important factor: Virus “strength”: s = β / δ
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461503-2b7d016e-84ca-4a99-bda0-ae99aecbcdc3.png">

• epidemic thredhold: 在这个thredhold以上或者以下去定义infection的情况
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227461907-99a5ca50-d312-462b-a1bb-746733270a35.png">
Find a condition that connects the properties of the virus and the structure of the graph, under which
– s = β / δ < τ : virus will die out exponentially quickly 
– s = β / δ > τ : the infection survives and  becomes an epidemic
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227462561-a0126150-c42a-4c6a-aaa3-a171b831d173.png">
Similarity to this Connection: centrality matrix [也是用到了largest eign-vector，但是是用到transition matrix]
With higer eign-value, the better connectivity.
怎么看图
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227463857-4d882808-5f40-4f49-be50-acd992d4fe23.png">

##### IC model(Independent Cascade)
• Assumption: Initially some nodes S are active
• Each edge (u,v) has probability (weight) $p_uv$, when node u becomes active/infected, It activates each out-neighbor v with prob $p_uv$
• Activations spread through the network
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227464375-3d558625-ec2f-42f0-b3b8-78103dc8838a.png">





