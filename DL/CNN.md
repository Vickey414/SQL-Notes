CNN在很多任务上的效果很好但是其学到的内容和规则难以被人类理解，俗称“黑盒子”，如果能对CNN进行可视化（包括模型的中间激活结果、filter提取的是什么特征、输出对那些位置的像素敏感），这对我们理解模型、分析模型的问题非常有帮助.  
# 深度学习可解释性领域
## CAM(Class Activation Mapping)  【类别激活映射图、类别热力图、显著性图】
解释： 将一张和原始图片等同大小图，该图片上每个位置的像素取值范围从0到1，一般用0到255的灰度图表示。可以理解为对预测输出的贡献分布，分数越高的地方表示原始图片对应区域对网络的响应越高、贡献越大。
可视化：可视化的时候，利用热力图和原图叠加的形式呈现。如下图，颜色越深红的地方表示值越大。可以认为，网络预测“狗”这个类别时，红色高亮区域是其主要判断依据。
<img width="640" alt="image" src="https://user-images.githubusercontent.com/29950267/218269684-27757b37-51ba-40bd-9acf-b34021ed84c0.png">   
A. 原始图 B为CAM灰度图 C为CAM彩色热图 D为原图+CAM彩色热图  
作用：  
* 有助于理解和分析神经网络的工作原理及决策过程，进而去更好地选择或设计网络。例如对于分类网络，如果参考CAM相当于除了分类accuracy以外，对网络又提出了更高的要求：不但要求预测准确率高，还需要网络提取到我们需要的特征。不同网络对相同的数据的CAM是有较为明显的差异。当然即便是同一个网络，不同训练过程也会导致CAM有很大的差异。  
* 利用可视化的信息引导网络更好的学习，例如可以利用CAM信息通过"擦除"或""裁剪""的方式对数据进行增强；
* 利用CAM作为原始的种子，进行弱监督语义分割或弱监督定位。既然CAM能够cover到目标物体，所以可以仅利用分类标注来完成语义分割或目标检测任务，极大程度上降低了标注的工作量，但这对CAM的要求更高。一般情况下，分类网络只会提取到最具有判别性的特征。所以也有很多做法来提高分类网络的CAM精准度。  





