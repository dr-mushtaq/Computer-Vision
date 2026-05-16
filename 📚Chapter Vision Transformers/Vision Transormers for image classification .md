## Introduction

As the Transformers architecture scaled well in Natural Language Processing, the same architecture was applied to images by creating small patches of the image and treating them as tokens. The result was a Vision Transformer (ViT). Before we get started with transfer learning / fine-tuning concepts, let’s compare Convolutional Neural Networks (CNNs) with Vision Transformers.
# Vision Transformer (VT) a Summary

To summarize, in Vision transformer, images are reorganized as 2D grids of patches. The models are trained on those patches.

The main idea can be found at the picture below:\
![](https://github.com/dr-mushtaq/Computer-Vision/blob/main/%F0%9F%93%9AChapter%20Vision%20Transformers/Screenshot202024-12-27%252014-25-49.png)

But there is a catch! The Convolutional Neural Networks (CNN) are designed with an assumption missing in the VT. This assumption is based on how we perceive the objects in the images as humans. It is described in the following section.
