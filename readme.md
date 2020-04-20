## Relevant papers that I have read:
- [x] Demystifying Membership Inference Attacks
- [x] LOGAN: Membership Inference Attacks Against Generative Models
- [x] Monte Carlo and Reconstruction Membership Inference Attacks against Generative Models
- [x] Understanding Membership Inferences On Well-Generalized Learning Models
- [x] Membership Inference Attacks Against Machine Learning Models
- [x] Deep Models Under the GAN: Information Leakage from Collaborative Deep Learning
- [x] Differential Privacy Preservation in Deep Learning: Challenges, Opportunities and Solutions
- [x] Membership Inference Attacks against Adversarially Robust Deep Learning Models
- [x] Membership Inference Attack against Differentially Private Deep Learning Model
12:51
## Brief summary of the relevant papers that I have read:
* Towards Reverse-Engineering Black-box Neural Networks
  * **Aim:** This paper focuses on predicting three attributes, namely the architecture (hyperparameters), optimisation function, and the training data of a neural network.
  * **Requirements:** You need to submit query inputs (eg. digit pictures) to a black-box model and then receive the outputs of the model (eg. class prediction). Furthermore, they assume that the attacker has a basic understanding of what the model does so that he can create similar white-box models. These similar models are needed to train a _meta model_.
  * Their work is done on the MNIST-dataset (digit classification taks).
  * It accomplishes this goal by first collecting a range of different white-box models, named a _meta-training set_. It then trains a _meta model_ that takes a model as input and returns the corresponding model attributes as output. Therefore, the metamodel is a classifier of classifiers.