## Neuron deletion for sentence classification

There is a paper by Deepmind [1] about the stability of a trained large ConvNet when removing some of its neurons (Fig. 1). 
They also showed that there is a correlation between generalization and robustness (Fig. 3b).

* Choose a sentence classification task, train a few (different) types of networks. Could be one academic task + one task from industry
* Generate Figure 1 for these networks (without label noise) 
* Generate Figure 3b for these networks, look for clusters
* Investigate if robustness can be used as an early stopping signal (Figure 4)
* Investigate the role of dropout / recurrent dropout, compare with ConvNet results (Figure 5a)
* (harder) Investigate the role of recurrent batch-norm (Figure 5b)
* (harder) Generate Figure 1 _with_ label noise. Requires proof that the network will still be able to overfit (see the task _"Overfitting ability of recurrent networks"_)

[1] Ari S. Morcos, David G.T. Barrett, Neil C. Rabinowitz, Matthew Botvinick, _On the importance of single directions for generalization_,
[https://arxiv.org/abs/1803.06959]


## Overfitting ability of recurrent networks

Attempt to confirm the results of the famous paper on "rethinking generalization" [1] for recurrent networks

* Choose the tasks. Could be something from NLP or EHR (MIMIC-III)
* Think about the equivalents of _random pixels_ and _shuffled pixels_ for the selected tasks
* Generate Figure 1 from the paper
* Think about the effect of regularization (augmentation, dropout, etc.)

[1] Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, Oriol Vinyals, _Understanding deep learning requires rethinking generalization_, [https://arxiv.org/abs/1611.03530]


## Test the quality of multilingual embeddings

There are two recent pretrained multilingual embeddings:
* Unsupervised, based on Facebook's [MUSE](https://github.com/facebookresearch/MUSE)
* Supervised using Google Translate API by [BabylonPartners](https://github.com/Babylonpartners/fastText_multilingual/blob/master/README.md)
* There is an old blogpost about (possibly) more techniques by [Sebastian Ruder](http://ruder.io/cross-lingual-embeddings/).

The task is to validate the quality of these embeddings for transfer learning. 
* Take a famous academic dataset in English. Could be Amazon's reviews. Find a related dataset (with the same labels) in a different language
* Train models on the English dataset using pure English vectors and different types of multilingual embeddings. See if multilingual embeddings are performing worse
* Train and evaluate similar models on the (smaller) dataset in another language 
* Evaluate English models with multilingual embeddings on the smaller dataset
* Train on a combination of English dataset and the other one. Plot a chart of accuracy depending on the size of the second dataset.




# Tasks related to MIMIC-III benchmarks
The main repo of the benchmark: https://github.com/YerevaNN/mimic3-benchmarks


## Implement more neural architectures for the benchmark
* GRU-D, published in [Nature Scientific Reports](https://www.nature.com/articles/s41598-018-24271-9)
* The network from Google's EHR paper from [Nature Digital Medicine](https://www.nature.com/articles/s41746-018-0029-1)
  * It is not yet clear that this network is fully applicable to the benchmark, so some modifications might be required.
* TODO: are there more good architectures?

## Adversarial training on the benchmark data
* Understand adversarial training for images. [Cleverhans](https://github.com/tensorflow/cleverhans) is a good starting point
* Investigate adversarial training for RNNs, look for a reasonable codebase
  * Great starting point by Berkeley researchers published in [EMNLP 2017](http://aclweb.org/anthology/D17-1187). Code is on [Github](https://github.com/jxwuyi/AtNRE)
* Implement adversarial training on the benchmarks
* Train multiple models with different hyperparameters for adversarial training (noise levels etc.). Plot charts

## Adversarial reprogramming for the benchmark tasks
There is an interesting [paper by Google Brain](https://arxiv.org/abs/1806.11146) team on adversarially reprogramming pretrained neural networks to perform a new task. The idea is demonstrated to reprogram ImageNet network to perform MNIST classification. So far, there is no evidence that it might work on recurrent networks. This fact makes this task a risky one :)

* Attempt to repeat the experiment on ImageNet to MNIST to understand the difficulty of the work
* Attempt to reprogram phenotyping network for in-hospital mortality prediction
* Discuss different methods of modifying the input
  * Add the "program" before/after the input (the results should be similar)
  * Add the "program" between the existing timesteps
* (harder) attempt to do the same without fixing the input size!

## Visualizing the neural models
There are lots of papers on "visualizing and understanding" convolutional networks, mostly starting from [1]. In recent years a few similar papers appeared for RNNs, especially about sentiment analysis [2,3].
* Read the papers, understand different methods
  * Looks like that the methods used in [2] and [3] are different
  * This can result in a great reading group meetup
* Apply some of these techniques on the pretrained models

[1] Karen Simonyan, Andrea Vedaldi, Andrew Zisserman, *Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps*, https://arxiv.org/abs/1312.6034

[2] Jiwei Li, Xinlei Chen, Eduard Hovy and Dan Jurafsky, *Visualizing and Understanding Neural Models in NLP*, NAACL-HLT 2016, http://www.aclweb.org/anthology/N16-1082

[3] Leila Arras, Gregoire Montavon, Klaus-Robert Muller, and Wojciech Samek, *Explaining Recurrent Neural Network Predictions in Sentiment Analysis*, 8th Workshop on Computational Approaches to Subjectivity, Sentiment and Social Media Analysis, 2017, http://www.aclweb.org/anthology/W17-5221


## Improve multitask learning
It is generally a hard problem to determine weights for the tasks in the multitask training setting (TODO: any reference?). The experiments on MIMIC benchmarks showed that the networks overfit on some tasks earlier than on others.

Is it possible to create an architecture that will automatically modify the weights during the training? Something similar to [1]... 

[1] Marcin Andrychowicz, Misha Denil, Sergio Gomez, Matthew W. Hoffman, David Pfau, Tom Schaul, Brendan Shillingford, Nando de Freitas, *Learning to learn by gradient descent by gradient descent*, 2016, https://arxiv.org/abs/1606.04474
