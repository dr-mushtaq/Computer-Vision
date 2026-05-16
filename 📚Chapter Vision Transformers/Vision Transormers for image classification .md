#Introduction

As the Transformers architecture scaled well in Natural Language Processing, the same architecture was applied to images by creating small patches of the image and treating them as tokens. The result was a Vision Transformer (ViT). Before we get started with transfer learning / fine-tuning concepts, let’s compare Convolutional Neural Networks (CNNs) with Vision Transformers.
# Vision Transformer (VT) a Summary

To summarize, in Vision transformer, images are reorganized as 2D grids of patches. The models are trained on those patches.

The main idea can be found at the picture below:\
![](https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%20Vision%20Transformers/Screenshot202024-12-27%252014-25-49.png)

But there is a catch! The Convolutional Neural Networks (CNN) are designed with an assumption missing in the VT. This assumption is based on how we perceive the objects in the images as humans. It is described in the following section.

# What are the differences between CNNs and Vision Transformers?

## Inductive Bias
Inductive bias is a term used in machine learning to describe the set of assumptions that a learning algorithm uses to make predictions. In simpler terms, inductive bias is like a shortcut that helps a machine learning model make educated guesses based on the information it has seen so far.

Here’s a couple of inductive biases we observe in CNNs:

- **Translational Equivariance:** an object can appear anywhere in the image, and CNNs can detect its features.
- **Locality:** pixels in an image interact mainly with its surrounding pixels to form features.
CNN models are very good at these two biases. ViT do not have this assumption. That is why for a dataset size up to a certain threshold actually CNNs are better than ViT. But ViT has another power! The transformer architecture being (mostly) different types of linear functions allows ViT to become highly scalable. And that in turn allows ViT to overcome the problem of not having the above two inductive biases with massive ammount of data!
