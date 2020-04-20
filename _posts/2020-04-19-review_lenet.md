---
layout: post
title: "Review of LeNet-5"
# subtitle: 
# image: /img/avatar-icon.jpg
tag: [review, classification, pinned]
# bigimg:
---

This post is a review of an old, difficult, and inspiring paper: **Gradient-Based Learning Applied to Document Recognition**"[[1]](#1) by Yann LeCun as the first author. You can find many reviews of this paper. Most of them only focus on the architecture of the Convolution Neural Network (*CNN*) LeNet-5. However, I'd like to talk about some other interesting points:
1. The proposition of the concept of end-to-end solution from the perspective of back-propagation
2. How to incorporate knowledge during the design of a neural network

In fact, there are 2 networks mentioned in this paper. The first one is CNN, named LeNet-5 and the second one is called Graph Transformer Network (*GTN*). I talk only about the LeNet-5 in this post.

## 1. End-to-end solution
### What's end-to-end solution? 
Let me give an example: How can we mark the gender of all the faces in one image? First solution is to detect the positions of all the faces and then classify the gender with sub-images. Second solution is create a model with the image as input and with the gender and the localization of faces as the output. The latter solution is called end-to-end solution.
### What's the advantage of end-to-end solution? 


## 2. Design of CNN with knowledge






## Reference
<a id="1">[1]</a> 
LeCun, Yann and Bottou, Léon and Bengio, Yoshua and Haffner, Patrick &nbsp;
*Gradient-Based Learning Applied to Document Recognition* &nbsp;
IEEE, 1998

