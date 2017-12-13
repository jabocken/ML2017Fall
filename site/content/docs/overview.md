+++
title = "Project Overview"
description = "Goals and Details"
weight = 1
draft = false
bref = ""
toc = false
+++

## Objective

The objective of the project is to build an image classifier for the cdiscount.com's dataset. 

## Introduction

For this project, we took up a Kaggle competition to build a product classifier for cdiscount.com, an online non-food shopping website based in France. cdiscount.com has provided a dataset containing images for over 7M products and their categories. The challenge is to build a machine learning-based solution that learns from the dataset and makes predictions on test images. 

## Problem Reduction

Each product image belongs to a tuple of three categories, representing an categorial hierarchy. However, we had significant limitations in [hardware resources]({{< ref "docs/system.md" >}}). Therefore, we categorized the images only among the top-level category. 

## Process

### Convolutional Neural Networks

Convolutional Newral Networks (CNN) were the best fit for our problem, since CNNs have the ability to automatically learn features from the dataset. More details on CNNs are in the presentation video. However, CNN models can become unusually complex and can take weeks to train. However, we used the transfer learning approach to minimze our training time.

### Transfer Learning

We used Keras and its built-in models with pre-trained weights to effectively train our new model. We freezed the convolutional and pooling layers using the existing weights provided by Keras and trained only the fully connected blocks. The training was conducted in two phases. The first phase composed of training the fully connected blocks with Adam optimizer and the second phase composed of training with stochastic gradient descent with an adaptive slow learning rate. More details are presented in the video.

More information on the models are available in the [Models page]({{< ref "docs/models.md" >}}).

## Training

We initially experimented with different [datasets]({{< ref "docs/dataset.md" >}}) before arriving to our final choice. We named our datasets DS<sub>A</sub>, DS<sub>B</sub>, and DS<sub>C</sub> as explained [here]({{< ref "docs/dataset.md" >}}). 

We achieved very high training as well as validation accuracy of 85.8 and 64.73, respectively, with the DS<sub>A</sub> dataset, when we used the InceptionV3 model to train on our dataset. However, the dataset only represented a tiny fraction of the data, and our hardware resources were still not saturated.

Next, we produced the DS<sub>B</sub> dataset and trained our models. However, the results we obtained felt like we were underfitting the model.  We quickly realized that the lack of data could be the reason for such low accuracies. Therefore, we produced similar dataset with more images (DS<sub>C</sub>). This dataset by far yielded the best results for InceptionV3. Therefore, we used the same dataset for two other models as well. The results are avaialble in the [tensorboard]({{< ref "docs/tensorboard.md" >}}) page.

