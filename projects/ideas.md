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

