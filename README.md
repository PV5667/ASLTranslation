# ASLTranslation


### This repository contains: 

#### The code that I used for training the model for Few Shot Learning and Supervised Learning (based in Kaggle)

#### The weights for the few-shot based model and the code to load the weights


My project lies at the corssroads between research project and an engineering project. 

While the WLASL Dataset (https://arxiv.org/pdf/1910.11006.pdf) is one of the largest Word Level American Sign Language Datasets in existence, its use is limited for supervided learning because of the low number of samples per class. 

As seen in the figure below, the majority of the dataset is composed of ~ {num} samples

This problem is extended by the fact that around 1/2 of the dataset is unusable; the dataset video samples are loaded in via downloading through link, and some of these links do not exist anymore.

With these "missing" videos, we get this figure to show the distribution of samples in the dataset.

{Image}


As seen by the figure, the top 100 classes contain the most samples, so I chose to train my models on this subset of data.


Here are the sample distributions for the training and testing datasets for the 100 class subset specifically: 
{2 Images}


As one can see, at certain points the test dataset contains 0 samples, so I could not reliably use the test split to validate my data.
{Image}


Using supervised learning, my results were lackluster and my model stopped improving after ~40% training accuracy on the dataset.

Several problems were present here. 

First, the number of samples per class in this dataset were just too small for supervised learning
Second, and partially connected to the first problem, I did not have a reliable way to validate the accuracy of my model. 

For this problem, I am currently planning to create a validation dataset of my own, at times pooling instances of the same class in a different dataset (e.g. using "book" instances from another dataset) or possibly scraping some video samples off the web on my own.

I had actually noted the first problem, the one where each class did not have enough instances, as I was originally reading through the WLASL paper. 
The authors proposed the idea of few-shot learning as a possible forward direction for this research; I planned to train a model with supervised learning as a control to allow me to observe the effects of training a model with few-shot learning. 

Few-shot learning is specifically geared to datasets with small numbers of instances per class; its aim is to teach the model how to learn rather than teaching the model with specific labels.

It would essentially be teaching the model, "this is an object that is of a different type than this object and here's how to differentiate them" instead of "this is a pen and this is a marker"

Using few-shot learning, I was able to obtain a training accuracy of about 80%, a marked imporvement over the supervised learning based approach's accuracy of around 40%.

This success on the 100-class subset inspired me to train a few-shot model on the 300-class subset of WLASL.


With this project, I was able to 1) use few-shot learning techniques to train a model to about 80% accuracy on the WLASL-100 dataset and 2) show the promise that few-shot learning holds for this topic of sign language translation through machine learning.

In terms of aspects that I want to improve and keep working on, I want to create a test dataset to validate the accuracy of my models, and then based on this, scale up to bigger subsets of WLASL including those with 1000 and 2000 words.



