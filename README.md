# Human and dog identification & Breed Classificatin
Udacity Data Scientist project

In this project different models are used:
1) to detect human faces
2) to detect dogs
3) to classify dog brees

First of all a CNN from scratch is used to classify dog breeds, then using Transfer Learning I did the same using Inception model

## Detect human faces
With implementation of [Haar feature-based cascade classifiers](http://docs.opencv.org/trunk/d7/d8b/tutorial_py_face_detection.html) using OpenCV:
99.0 % of the first 100 images in human_files had a human face detected in them.
12.0 % of the first 100 images in dog_files had a human face detected in them.

## Predictions with pre-trained model
Making Predictions with pre-trained ResNet-50 model:
0.0 % of the first 100 images in human_files had a dog detected in them.
100.0 % of the first 100 images in dog_files had a dog detected in them.

## CNN from scratch
With CNN it is much faster to train and avoid overfitting, it also doesn't need alot of training data, so I created a used the following CNN model which gave me a test accuracy of 0.7177% in predition dog breeds

Model: "sequential"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 conv2d (Conv2D)             (None, 224, 224, 16)      208       
                                                                 
 max_pooling2d (MaxPooling2D  (None, 112, 112, 16)     0         
 )                                                               
                                                                 
 dropout (Dropout)           (None, 112, 112, 16)      0         
                                                                 
 conv2d_1 (Conv2D)           (None, 112, 112, 32)      2080      
                                                                 
 max_pooling2d_1 (MaxPooling  (None, 56, 56, 32)       0         
 2D)                                                             
                                                                 
 dropout_1 (Dropout)         (None, 56, 56, 32)        0         
                                                                 
 conv2d_2 (Conv2D)           (None, 56, 56, 64)        8256      
                                                                 
 max_pooling2d_2 (MaxPooling  (None, 28, 28, 64)       0         
 2D)                                                             
                                                                 
 dropout_2 (Dropout)         (None, 28, 28, 64)        0         
                                                                 
 global_average_pooling2d (G  (None, 64)               0         
 lobalAveragePooling2D)                                          
                                                                 
 dense (Dense)               (None, 133)               8645      
                                                                 
=================================================================
Total params: 19,189
Trainable params: 19,189
Non-trainable params: 0

## Transfer Learning
And to reduce training time Transfer Learning is used to classify dog breeds using [Inception](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/DogInceptionV3Data.npz) bottleneck features and achieved a test accuracy of 79% and this can be improved by using augmentation and adding more layers and nodes, and just enough training epochs


## Acknowledgement:
This is one of the capstone projects for Data Scientist nanodegree at Udacity. Sponsored by Misk and Udacity in Saudi Arabia.
Part of code is provided by Udacity
