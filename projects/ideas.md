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

