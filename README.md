# **Term 3 Project 2: Semantic Segmentation Project [Elective]**
Self-Driving Car Engineer Nanodegree Program

The goals of this project are the following:

* Use a Fully Convolutional Network (FCN) to label the pixels of a road in images
* Using the VGG-16 model as the encoder, built an decoder using convolutional transpose layers
* Build an optimizer to minimize cross entropy lost and train the FCN

[//]: # (Image References)

[image1]: ./images/.png "P1"
[image2]: ./images/.png "P2"
[image3]: ./images/.png "P3"
[image4]: ./images/.png "P4"
[image5]: ./images/.png "P5"
[image6]: ./images/.png "P6"
[image7]: ./images/.png "P7"
[image8]: ./images/.png "P8"
[image9]: ./images/.png "P9"

The Rubric Points are listed in this following [link](https://review.udacity.com/#!/rubrics/989/view)

### Fully Convolutional Network Implementation
Using a pre-trained VGG-16 model, the output from layer 3, 4, and 7 were extracted to create the deconvolutional layers in order to build the decoder section of the FCN.  After the FCN architecture is defined, an optimizer was implemented in order to minimize the loss function, and the Adam Optimizer was used.  


### Loading VGG-16


### Decoder Implementation


### Optimization and Training Neural Network
