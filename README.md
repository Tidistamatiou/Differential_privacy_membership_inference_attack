## Short description
The aim of this thesis is the implementation and evaluation of different membership inference attack strategies. A membership inference attack is a attack that aims to assess whether a given sample was part of the training data of the model that is being attacked. The aim of the implementation is to extend the PySyft framework with the different membership attacks according to the PySyft collaboration rules.

For the evaluation, a distributed learning model will be privately trained, using the PySyft framework, on publicly available data. The different attacks will then be performed on this model and evaluated. This evaluation will include both the performance from the view of the attacker as well as the degree of privacy of the model using established privacy metrics.

The goal of this research is to contribute to the PySyft framework, PySyft is a framework which was created to preserve sensitive datasets whilst making them accessible for researchers. The evaluation will thus show how well PySyft is able to prevent attacks like membership inference. Besides this thesis on membership inference, two other students will be conducting the same research but will be focusing on model inversion and reconstruction attacks. 

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

For a link to these papers please see the links.txt file in the 'papers' folder or see the PDF's that are included in this folder.
## Brief summary of the relevant papers that I have read:
* Demystifying Membership Inference Attacks
  * **Aim:** This paper presents a comprehensive study towards demystifying membership inference attacks from two perspectives; first they talk about the development of a black-box membership inference attack model, secondly they describe the importance of model choice on model vulnerability.
  * **Relevance:**
  This paper presents the first generalized framework for the development of a membership inference attack model. This can be very valuable for me during the implementation of different attack models that I have found as it can help me to get a better understanding on the reason why some attacks work and some may fail.
* LOGAN: Membership Inference Attacks Against Generative Models
  * **Aim:** This is the first paper that presents membership inference attacks against generative models by leveraging generative adverserial networks to detect
  overfitting and identify instances that were part of the training dataset.
  * **Relevance:**
  This paper is very relevant for my thesis as it presents a way of attacking generative models. The paper is relatively new and is cited by other papers that I have found and included in the collection which again shows its relevance in this field of study.
* Monte Carlo and Reconstruction Membership Inference Attacks against Generative Models
  * **Aim:** This paper presents two new ways of membership inference attacks, they call it information leakage attacks, that outperform the previous work in this field.
  * **Relevance:**
  Two other methods of membership inference attacks are presented in this paper which can be helpful in my thesis. It too focusses on attacks on generative models which is what I am interested in, they do evaluate this attack method on a GAN which is not exactly what I think I will be doing but the attack should be working without any assumption on the type of generative model which means I should be able to use it. The second attack they describe is actually aimed at Variational Auto Encoders, I'm not sure whether I will use this as this would mean that I would have to use VAE for the other attacks as well.
* Understanding Membership Inferences On Well-Generalized Learning Models
  * **Aim:** This paper debunks the idea that a model has to be overfitted in order to be vulnerable to a black-box access membership inference attack. They demonstrate that a well-generalized model contains vulnerable instances subject to a new generalized membership inference attack.
  * **Relevance:**
  I think the relevance of this paper is clear, as I assume that the model we will be using to be attacked will not be trained with overfitting in mind, it should
  be well generalized and thus this paper is very relevant as I would still like to be successfull when performing my membership inference attack. If I would choose to implement the shadow models that are described in the paper of Shokri et Al, this paper would be a nice different way of attacking as a method is described that does not use shadow models.
* Membership Inference Attacks Against Machine Learning Models
  * **Aim:** This is the paper that seemed to kick off this field of research as it presented the first quantative analysis of information leakage for machine learning models. They evaluate their techniques on differnt machine learning as a service providers which they train for classification use, then they show that these kinds of models are prone to membership inference attacks by training shadow models.
  * **Relevance:**
  The relevance of this paper can not be understated as it is the most referenced paper in this field of study and describes a membership inference attack very clearly and in detail. It can be used as the base-level membership inference attack as it only requires black-box access to a model of unknown structure.
* Deep Models Under the GAN: Information Leakage from Collaborative Deep Learning
  * **Aim:** This papers shows shows that any privacy-preserving collaborative deep learning is susceptible to privacy issues by training a GAN to generate prototypical samples of the targeted training set.
  * **Relevance:**
  I'm not sure if I can actually use this in my thesis as it does not focus on membership inference in the classical sense, it tries to recreate the whole (private) data set instead of just checking membership for a given sample. However if this method is actually very accurate in recreating the data set I could then easily check if this created dataset contains my sample and therefore this attack could very well be relevant for my research.
* Differential Privacy Preservation in Deep Learning: Challenges, Opportunities and Solutions
  * **Aim:** This paper presents the challenges faced by differential privacy in the deep learning model. They present different aspects which I think are also interesting for Serge and Boris. They analyse the existing work, classify them by the layers of the differential privacy mechanism and discuss their advantages and disadvantages.
  * **Relevance:**
  I think this paper can be relevant as they look into the three different aspects of privacy attacks which are the three different subjects that Serge, Boris and me are handling. We could use the framework used in this paper as inspiration for how we want to compare our different attacks and such.
* Membership Inference Attacks against Adversarially Robust Deep Learning Models
  * **Aim:** This paper investigates the security and privacy domain challenges posed by deep learning, their novelty is that they look into the combination of both domains which has not been done before. They do this by implementing membership inference attacks against adversarial training and provable defence.
  * **Relevance:**
  I'm not sure if I will be using this paper as the implemented membership inference attacks are the ones that I already included in other papers I think. However it could be helpful to see how they implemented it and what the results are against these adverserially robust models as I am not sure what kind of model we will have to attack.
* Membership Inference Attack against Differentially Private Deep Learning Model
  * **Aim:** This paper studies the impact of a membership inference attack against a diferentially private deep model.
  * **Relevance:**
  I think the relevancy of this paper is clear, they do exactly what I am going to be doing and are doing this on a diferentially private deep model which is, in my understanding, the same kind of model that I will be using in my research.

## More indepth review of the papers that I'm picking attack methods from
* Membership Inference Attacks Against Machine Learning Models
 * **Requirements:**
    * Black-box access to the target model
    * requires some information about dataset, namely syntactic format of data records used in training in order to generate syntehtic samples for shadow models
    * Access to the same architecture that the target model was trained on (so same MLaaS or algorithm)
    * Trains shadow models on synthesized training data
    * Trains a attack model on the labeled inputs and outputs of these shadow models (so it is known which instances are in the training data and which instances aren't)
    * After training the attack model can be used to classify, based on the prediction vector obtained from the target model, whether a sample was in the training dataset or not.
 * **pro's/con's**
    * Method is trained on publicly availalbe datasets like CIFAR, locations data from Foursquare, MNIST and UCI Adult dataset as well as a puchased datasets from Kaggle
    * A con is that they don't use GAN's whilst they have been very promising and are sought-after to get a publication as indicated by Saba.
    * Another con is the need to have information about syntatic format of the dataset and it rqeuires predictions scores which are not presented by generative models.
* LOGAN: Membership Inference Attacks Against Generative Models
 * **Requirements:**
    * Black box access to the target model, so no information about parameters and hyper-parameters, no information about target model archit
    * Assumes that the attacker knowns the size of the training set, does not know how data-points are split into training and test set
    * The attacker needs to have a set with data points they suspect are in the original training record to measure accuracy
 * **pro's/con's**
    * present a method for a black-box attack that is mounted through GAN's with over 80% of the training set inferred through this method
    * method is trained on LFW, CIFAR-10 and medical images datasets.
    * Requires no predictions scores as opposed to the previous paper
* Monte Carlo and Reconstruction Membership Inference Attacks against Generative Models
 * **Requirements:**
    * Black-box access to the target model
    * Monte carlo attack relies on samples which are close to the training data, so requires good quality of training data
    * Use PCA, HOG and CHIST to calculate distance between samples
 * **pro's/con's**
    * Proposed black-box attacks are evaluted in comparison to the black-box attacks from the LOGAN paper
    * Applicable on all generative models
    * Trained on MNIST, Fashion MNIST and CIFAR-10
    * Especially Monte Carlo attack is promising as in their results it outperforms the LOGAN attack, Reconstruction attack is possible but optimized for VAE's so questionably interesting for my research
    * A con is that I still find it quite difficult to really grasp the foundation of the Monte Carlo attack
* ML-leaks: Model and Data Independent Membership Inference Attacks and Defenses on Machine Learning Models
 * **Requirements:**
    * Black-box access to the target model
    * access to the same kind of model architecture (through same MLaaS provider) to train shadow model for some methods
    * Access to the same dataset that was used for training the target model for one method
 * **pro's/con's**
    * Relaxes the need to have information about the dataset, so in comparison to Shorki et al. they don't neccesarily need to create a synthetic dataset
    * Attack still works even after training shadow model on dataset from different domain
    * Present an attack that works without any shadow model -> does require the posteriors (outcomes)
* Understanding Membership Inferences On Well-Generalized Learning Models
 * **Requirements:**
    * 
 * **pro's/con's**
    * Relaxes the assumption that it is a neccesary condition for the target model to be overfitted but shows it is only a sufficient condition

