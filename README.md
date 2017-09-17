# Autoencoders

In this project I explore an unsupervised deep learning model, belonging to the neural network family, called as Autoencoder. The aim of an autoencoder is to learn a representation (encoding) for a set of data, typically for the purpose of dimensionality reduction. 

## Introduction

Autoencoders are closely related to PCA (principal components analysis), but are much more flexible. Recall that with neural networks we have an activation function – this can be a “ReLU” (aka. rectifier), “tanh” (hyperbolic tangent), or sigmoid.

This introduces nonlinearities in our encoding, whereas PCA can only represent linear transformations.

The network representation also means you can stack autoencoders to form a deep network, also called as Stacked Autoencoders.

Some facts about the autoencoder:

  1. It is an unsupervised learning algorithm (like PCA)

  2. It minimizes the same objective function as PCA

  3. It is a neural network

  4. The neural network’s target output is its input

## Theory

![Autoencoder_Architecture](https://github.com/darshanbagul/Autoencoders/blob/master/images/Autoencoder_structure.png)

The simplest form of an autoencoder is a feedforward, non-recurrent neural network very similar to the multilayer perceptron (MLP) – having an input layer, an output layer and one or more hidden layers connecting them –, but with the output layer having the same number of nodes as the input layer, and with the purpose of reconstructing its own inputs (instead of predicting the target value Y given inputs X). Therefore, autoencoders are unsupervised learning models.

An autoencoder always consists of two parts, the encoder network and the decoder network. The task of the encoder is to generate a lower dimensional embedding Z, which is referred to code, latent variables, or latent representation. After that, the decoder stage of the autoencoder maps Z  to the reconstruction X' of the same shape as X. 

The training objective is to reduce the error between X and X'.

Different variants of Autoencoders:

  1. Denoising Autoencoder - takes a partially corrupted input whilst training to recover the original undistorted input
  
  2. Sparse autoencoder - learns sparse representations of inputs which can be used for classification tasks)
  
  3. Variational autoencoder (VAE)
  
  4. Contractive autoencoder (CAE) - adds an explicit regularizer in their objective function that forces the model to learn a function that is robust to slight variations of input values

Autoencoders are lossy, which means that the decompressed outputs will be degraded compared to the original inputs (similar to MP3 or JPEG compression). This differs from lossless arithmetic compression.

## Why use Autoencoders?

Similar to PCA – autoencoders can be used for finding a low-dimensional representation of your input data. Why is this useful?

Some of your features may be redundant or correlated, resulting in wasted processing time and overfitting in your model (too many parameters). It is thus ideal to only include the features we need.

If the “reconstruction (X')” of X is very accurate, that implies our low-dimensional representation is good. This transformed low-dimensional data can be used as input into another model.

## Dataset

We will use images of Pokemons as input and try to train a simple Autoencoder and a Convolutional autoencoder, with an aim to generate low-dimensional representations of the images using encoder network. The decoder network shall try to use this latent representation for reconstructing our original input.

# Results

The results of both the approaches are as shown below:

1. MLP Autoencoder

![Simple-Autoencoder](https://github.com/darshanbagul/Autoencoders/blob/master/images/Autoencoder_result.png)

2. Convolutional Autoencoder

![Convolutional-Autoencoder](https://github.com/darshanbagul/Autoencoders/blob/master/images/conv_autoencoder_result.png)

## Conclusion

Since our inputs are images, it makes sense to use convolutional neural networks (convnets) as encoders and decoders. However, the convolutional autoencoders generate a very lossy version of the original image.

As expected the quality is not very high, but the “semantics” of each image is almost preserved.Hence, these autoencoders cannot be used for replacing traditional image compression algorithms such as JPEG, but can certainly be used for training an image classifier, because the spatial representations and semantics are important rather than data quality. 
