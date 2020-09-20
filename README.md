[//]: # (Image References)

[image1]: ./images/sample_dog_output.png "Sample Output"
[image2]: ./images/vgg16_model.png "VGG-16 Model Layers"
[image3]: ./images/vgg16_model_draw.png "VGG16 Model Figure"


## OVERVIEW

In this project, I built a pipeline that can be used within a web or mobile app to process real-world, user-supplied images.  Given an image of a dog, the algorithm identifies an estimate of the canine’s breed.  If supplied an image of a human, the code will identify the resembling dog breed.  

![Sample Output][image1]

Along with exploring state-of-the-art CNN models for classification and localization, There are important design decisions about the user experience for your app.  The goal is to understand the challenges involved in piecing together a series of models designed to perform various tasks in a data processing pipeline.  Each model has its strengths and weaknesses, and engineering a real-world application often involves solving many problems without a perfect answer.  This imperfect solution nonetheless creates a fun user experience!

## FILES

- dog_app.ipynb (Notebook containing code)
- report.pdf (Pdf version of notebook)
- images (images for README)
- README.md

## DATASETS

- [dog dataset](https://s3-us-west-1.amazonaws.com/udacity-aind/dog-project/dogImages.zip)
- [human dataset](http://vis-www.cs.umass.edu/lfw/lfw.tgz)

## RESULTS

### Face Detection
OpenCV's implementation of Haar feature-based cascade classifiers to detect human faces in images.

[image]

100%, Total 100 human faces found in 100 human images
This is the accuracy

16%, Total 16 human faces found in 100 dog images
This is the error rate

### Dog Detection

Detect Dogs using VGG-16 model, along with weights that have been trained on ImageNet. Dictionary keys 151-268, inclusive are dog breeds.


100.0%, Total 100 dog faces found in 100 dog images
This is the accuracy

0.0%, Total 0 dog faces found in 100 human images
This is the error rate

### Dog Breed Detection using CNN from Scratch

| CNN Architecture  |
|----------|
| Conv3-64 |
| Conv64-128 |
| Conv128-256 |
| Conv256-512 |
| Conv512-512 |
| Flatten7*7*512 |
| FC25088-512 |
| Dropout |
| FC512-133|

**NOTE**: Each convolution layer has a Relu Activation function followed by Max pooling.

Loss Function: Cross Entropy Loss
Optimizer: Adam Optimizer

**Training Results**

**Test Results**

### Dog Breed Detection using Transfer Learning

To acheive this I chose the VGG16 Model. Used its feature detection layers and pre-trained weights, while attaching my own classifer (Fully-Connected Network) 

Loss Function: Cross Entropy Loss
Optimizer: Adam Optimizer

**Training Results**

**Test Results**


