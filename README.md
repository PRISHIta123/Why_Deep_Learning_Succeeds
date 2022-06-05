# Reviewing Performance of Deep Neural Networks with Overparameterization and Backward Feature Correction  


This project has been completed as part of the Mathematical Foundations of Machine Learning (CS5783) at Cornell University in Spring 2022 and is not for reproduction.  

Neural Networks of varying architectures are able to perform relatively well on benchmark classification datasets such as CIFAR-10, MNIST, etc. However, an exact understanding of how the increase in number of hyperparameters in these networks affects the SGD optimization process as well as final accuracy and generalization still poses a challenge. A kernel-based method, called Neural Tangent Kernel (NTK) is able to capture the behaviour of fully-connected deep nets in the infinite width limit trained by gradient descent. Therefore, combining Convolutional Neural Network architectures (CNNs) with NTK, as performed in [1] can be used to explore these questions and gain an intuition about the correlation of the network complexity with the classification accuracy. 

As neural networks are by-far the most successful in comparison to other existing algorithms, despite having high complexity, when theoretically this should not be possible can also be understood through hierarchical learning. In such a setting, a learner learns to represent a complicated target function by decomposing it into a sequence of simpler functions to reduce sample and time complexity. Deep neural networks can optimize well on such tasks using SGD. The training of higher-level layers in the networks can actually improve the features of lower-level ones. This is the concept of backward feature correction as explained in [2]. 

In this project:
* Implementation of a vanilla CNN along with its infinite width neural tangent kernel(CNTK) is done over benchmark datasets such as CIFAR-10, MNIST etc. to analyse the effect of their architecture, in terms of extent of overparameterization, on empirical performance on the classification tasks. 
* Additionally, naive finite-width NTK versions of the (ReLU) WRN-L-10 architecture are trained on these datasets to draw a conclusion about how the algorithm used 
by neural networks can explain their ability to perform backward feature correction and hence perform so efficiently.

The final report and colab notebooks can be accessed at Report.pdf, MFM1.ipynb and MFM2.ipynb

Link for the code implementation for Paper 1:
https://colab.research.google.com/drive/1dwG_pEBjeS35gTUGkr6TQBnSK65haps3?usp=sharing

Link for the code implementation for Paper 2: 
https://colab.research.google.com/drive/1SRVAIAwFKBCq89zP4GGTColutB0HCQKO?usp=sharing


**Note:**
i. To run the code for paper 1 (MFM1.ipynb), please change the runtime device in the Colab notebook by going to the top menu, select Runtime->Change Runtime Type-> From None, to GPU. This should be followed for both the CNNs and the infinite width CNTKs. 
ii. To run the code for paper 2 (MFM2.ipynb), please change the runtime device in the Colab notebook by going to the top menu, select Runtime->Change Runtime Type-> From None, to GPU for the networks and to TPU for the NTKs. 
iii. Please check comments asking to modify input features based on dataset used, or parameters to vary depth and width in the experiments.

### Results:

Experiments were performed on subsets of the MNIST, Fashion MNIST and CIFAR 10 datasets due to resource constraints. 

<p align="center">
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Tables/table1.JPG?raw=true" width="800" height="175"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Tables/table2.JPG?raw=true" width="500" height="150"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Figures/fig1.JPG?raw=true"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Tables/table3.JPG?raw=true"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Figures/fig2.JPG?raw=true"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Figures/fig3.JPG?raw=true"/>
  <img src="https://github.com/PRISHIta123/Why_Deep_Learning_Succeeds/blob/main/Figures/fig4.JPG?raw=true"/>
</p>

From the results, neither overparameterization, nor the backward feature correction algorithm can properly explain the success of deep learning. The actual superiority in the performance can be attributed to the overall network architecture of neural networks, designed to obtain more abstract representations from the input data with each successive layer or block, via subsampling (pruning ofquality inputs to each layer). However, the innermost abstraction should be just sufficient to capture the larger patterns and should not be too simple so as to hurt the basic discrimination ability. Therefore, the actual depth and width suitable for different applications requires experimentation and thus leads to development of new models. 

#### References:

[1] Arora, Sanjeev, et al. "On exact computation with an infinitely wide neural net." Advances in Neural Information Processing Systems 32 (2019).  
[2] Allen-Zhu, Zeyuan, and Yuanzhi Li. "Backward feature correction: How deep learning performs deep learning." arXiv preprint arXiv:2001.04413 (2020).


