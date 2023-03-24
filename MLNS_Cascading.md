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
- Birth Rate($\belta$): Probability than an infected neighbor attacks and infects a healthy neighbor
- Death Rate($\sigma$): Probability that an infected node heals

#### SEIR Model
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/227459897-fa145573-9567-422d-b111-6b6b35121711.png">

