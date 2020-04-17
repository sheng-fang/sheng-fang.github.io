---
layout: post
title: "Overview of optimizers for DNN: when and how to choose which optimizer"
# subtitle: 
# image: /img/avatar-icon.jpg
tag: [ml, ml_optimization, pinned]
# bigimg:
---

In this post, I would like to review the development of optimization methods for deep neural network (DNN) and share suggestions to use optimizers.

### What you can find:
1. A brief review of the popular optimizers from the an intuitive perspective.
2. The disadavantage of the popular adaptive optimizer, Adam.
3. Suggestions on jointly using different optimizers to achieve better performance.

### Who may be interested:
1. Want a brief overview of optimizers from SGD to Nadam.
2. Want practices on how to use them.


# 1. Intuitive perspective of optimization
The goal of the optimization of *DNN* is to find the best parameters w to minimize the loss function $$f(w, x, y)$$, using $$f(w)$$ bellow for simplification, subject to x, y, where x are the data and y are the labels. The gradient descent (*GD*) is the most frequently used optimization method for machine learning. In this method, we need another parameter called learning rate, $$\alpha$$.