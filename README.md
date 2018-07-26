# **Term 3 Project 2: Semantic Segmentation Project [Elective]**
Self-Driving Car Engineer Nanodegree Program

The goals of this project are the following:

* Use a Fully Convolutional Network (FCN) to label the pixels of a road in images
* Using the VGG-16 model as the encoder, built an decoder using convolutional transpose layers
* Build an optimizer to minimize cross entropy lost and train the FCN

[//]: # (Image References)

[image1]: ./images/um_000021.png "P1"
[image2]: ./images/.png "P2"
[image3]: ./images/.png "P3"
[image4]: ./images/.png "P4"
[image5]: ./images/.png "P5"
[image6]: ./images/.png "P6"
[image7]: ./images/.png "P7"
[image8]: ./images/.png "P8"
[image9]: ./images/.png "P9"

The Rubric Points are listed in this following [link](https://review.udacity.com/#!/rubrics/989/view)

## Fully Convolutional Network Implementation
Using a pre-trained VGG-16 model, the output from layer 3, 4, and 7 were extracted to create the deconvolutional layers in order to build the decoder section of the FCN.  After the FCN architecture is defined, an optimizer was implemented in order to minimize the loss function, and the Adam Optimizer was used.  Finally, the FCN was trained and the loss of the network was printed while the network was training.  AWS was used to train the FCN since I want to gain more experience using AWS EC2 to run deep learning solutions.  The udacity-carnd-advanced-deep-learning community AMI was used and a spot instance was created using the instance type of g3.4xlarge.  Jupyter Notebook was used to develop the code for this project.  The helper.py and project_tests.py code provided were implemented into a single Jupyter Notebook in this project.  An 48 epoches were used to create results similar to the picture shown below:

![alt text][image1]

## Loading VGG-16
VGG-16 was trained using the ImageNet and this creates the starting point of constructing the FCN.  Loading of VGG-16 model was implemented in Cell #5, using the function definition of "load_vgg".  Cell #1 consist of loading the dependencies and libraries for the code as well as testing if GPU is present.  Cell #2 and #3 are the provided functions used to support the development of the code and initial test of the model.  Cell #4 was not necessary but I would like to make sure that the pre-trained VGG was downloaded and put into the correct folder.  Beside the output from layer 3, 4, and 7, the image input and the keep probability was also extracted from the VGG-16 model.  Initial test for the VGG load process was passed, which means that the load_vgg function was implemented correctly.

## Decoder Implementation
The transpose layers were implemented in the "layer" function definition in Cell #5. From the output of VGG-16 layer 7, I applied a 1 by 1 convolution in order to preserve the spatial information of the input image.  The next step is to up-sample layer 7 output, which has now went through a 1 by 1 convolution, using a transpose layer.  In order to preserve some spatial information about the image in earlier encoder layers, skip connection technique was used.  By getting the output from the pooling layers #3 and #4 from the VGG-16 model, the FCN can use information from multiple resolution to better understand the scene.  Both layer 3 and 4 went through a 1 by 1 convolution and then they went through a skip connection operation.  Layer 4 and the deconvoluted layer 7 were combined together using the element-wise addition operation, and the result of that goes into a transpose layer operation and then it is combined with layer 3, after it has been processed by a 1 by 1 convolution.  The final output is a skip connection of layer 3, as it was just described, followed by a deconvolution.  The test for these deconvolutional layers were passed and thus the requirements were satisfied.



## Optimization and Training Neural Network
