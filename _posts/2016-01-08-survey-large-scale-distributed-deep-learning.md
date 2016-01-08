---
layout: post
title: Paper Survey - Large Scale Distributed Deep Learning
tags: [Neural Network, Deep Learning, Large-Scale, Distributed Computing]
---

## Survey
As a part of a network class in my university, I had the opportunety to hold a presentation about a survey of the paper [Large Scale Distributed Deep Learning](http://research.google.com/archive/large_deep_networks_nips2012.html) by Jeff Dean et al., researchers at Google.

I will in this post try to summarize the learnings from the survey. The presentation slides are included below.

<iframe src="//www.slideshare.net/slideshow/embed_code/key/xlMp5vEU13CMNQ" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"></div>

## Motivation

#### Limitations of the current GPU approach

Training neural networks using GPUs has significantly improved the training speed. There are however limitations to this approach. The biggest concern is the **CPU-GPU data transfer overhead** that slows down the whole training process. What you usually do to get around this issue is to design the model allowing it to fit in the GPU memory so that it can carry out the training without the need of transferring data. Obviously, this limits the capacity of the network.

#### What can we do instead?
We could develop efficient algorithms for designing compact but still accurate networks, or design hardware that is dedicated specifically for training neural networks such as the [Big Sur from Facebook](https://code.facebook.com/posts/1687861518126048/facebook-to-open-source-ai-hardware-design/).

*The surveyed paper proposes a new approach based on **distributed computing***.

## The Paper
The paper Large Scale Distributed Deep Learning was published in NIPS in 2012 and introduces a framework called **DistBelief** for training large neural networks with hundreds of millions of parameters in a distributed manner.

### DistBelief
I will not get into the details of the DistBelief framework since you can read about it in the [paper](http://research.google.com/archive/large_deep_networks_nips2012.html), but please continue reading for a short summary.

The framework consists of two parts

#### 1. Parallelization

Dividing the units in the network into multiple subsets, both horizontally and vertically. Assigning a machine to each subset of units.

#### 2. Model Replication

Asynchronousness is guaranteed by creating multiple instances of the parallelized model and allowing them to run independently. They communicate with a single server that stores the parameters of the network. Two alternatives are introduced to achieve this asynchronousness

**Downpour SGD** *Online Asynchronous Stochastic Gradient Descent* - The training data is split into smaller data shards and a model replica is created for each shard. All model replicas process the data independently and communicate with a sharded central parameter server.

**Sandblaster L-BFGS** *Batch Distributed Parameter Storage and Manipulation* - Gets rid of the central parameter server by having a distributed system that is coordinated by a separate process. For each batch, the the tasks are split up into smaller sub tasks and are dynamically assigned by the coordinator to an appropriate model replica to balance the work load and maintain a high hardware utilization.

### Thoughts

The framework presented in the paper improves the training time for deep neural networks and allows the training to scale with the number of parameter. It manages to do this despite the stochasticity that it introduces because of the asynchronousness in the weight updates. The drawback of this approach is that it **limits the unit connectivity** since too many cross machine connections will add an significant overhead to the training, leaving room for further improvements.

As stated by Jeff Dean in the [GitHub issue discussion board for TensorFlow](https://github.com/tensorflow/tensorflow/issues/23), they are highly prioritizing the task of open sourcing the distributed version of it meaning that we might see light being shed on this topic in the near future.
