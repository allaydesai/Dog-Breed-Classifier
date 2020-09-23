[//]: # (Image References)

[image1]: ./images/sample_dog_output.png "Sample Output"
[image2]: ./images/vgg16_model.png "VGG-16 Model Layers"
[image3]: ./images/vgg16_model_draw.png "VGG16 Model Figure"
[image4]: ./images/img1.png "Result Image 1"
[image5]: ./images/img2.png "Result Image 2"
[image6]: ./images/img3.png "Result Image 3"
[image7]: ./images/img4.png "Result Image 4"
[image8]: ./images/img5.png "Result Image 5"
[image9]: ./images/img6.png "Result Image 6"


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

**CNN Architecture**

| Layer Name | Description |
|-----|----------:|
| Conv1 | Conv_3-64 |
| Conv2 | Conv_64-128 |
| Conv3 | Conv_128-256 |
| Conv4 | Conv_256-512 |
| Conv5 | Conv_512-512 |
| Flatten | Flatten_7*7*512 |
| FC1 | FC_25088-512 |
| Dropout | Dropout |
| FC2 | FC_512-133|

**NOTE**: Each convolution layer has a Relu Activation function followed by Max pooling.

Loss Function: Cross Entropy Loss
Optimizer: Adam Optimizer

**Training Results**

Training Loss: 2.827422 	

Validation Loss: 3.564928

**Test Results**

Test Loss: 3.561034

Test Accuracy: 18% (154/836)


### Dog Breed Detection using Transfer Learning

To acheive this I chose the ResNet50 Model. Used its feature detection layers and pre-trained weights, while attaching my own classifer (Fully-Connected Network) 

FC_2048-133

Loss Function: Cross Entropy Loss
Optimizer: SGD Optimizer

**Training Results**

Training Loss: 0.757137 	

Validation Loss: 0.721440

**Test Results**

Test Loss: 0.715865

Test Accuracy: 86% (720/836)

### Results

![image4]

Hello, Human!
You look like a Dogue de bordeaux

--

![image5]

Hello, Human!
You look like a Dogue de bordeaux

--

![image6]

Hello, Human!
You look like a Dachshund

--

![image7]

Dog Detected!
Detected Dog is a Brittany

--

![image8]

Dog Detected!
Detected Dog is a Brittany

--

![image9]

Hello, Human!
You look like a English springer spaniel
