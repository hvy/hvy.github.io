---
layout: post
title: Convolutional Neural Networks, CNN - Preparation
tags: [Convolutional Neural Networks, CNN]
---

## Preparation

### Datasets
There are many tutorials out there but most of them only uses the [MNIST](http://yann.lecun.com/exdb/mnist/) dataset available at the homepage of Yann LeCun. Let's try to be different, and down the rabbit-hole we go.

### 1-channel grayscale, MNIST
MNIST is a dataset based on [National Institute of Standards and Technology, NIST](http://srdata.nist.gov/gateway/gateway?keyword=handwriting+recognition) containing a set of handwritten single-digits digits, 60000 for training and another 10000 for testing (testing the trained network model).

The MNIST dataset is well suited for explaining CNNs since it only contains a single channel, i.e. a grayscale where a regular image usually contains three channels defined by the RGB model. We proceed mainly with the RGB model.

### 3-channel RGB

as an example and/or uses a library to explain the network model. After reading this article you will hopefully be able to implement a simple CNN. It assumes that you have a basic knowledge of simple multilayered perceptrons and that you're familiar with forward and backward propagation.
