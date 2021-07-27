---
title: Credit Card Fraud Detection
author: Chenghao Ding
layout: post
comments: true
---

# Credit Card Fraud Detection

* Question: Identify the subject of 60,000 labeled images?

<div class="fig figcenter fighighlight">
  <img src="/assets/images/snapshot.png" width="800" height="800">
  <div class="figcaption"><br> The sample images.<br>
  </div>
</div>

CIFAR-10  is an established computer-vision dataset used for object recognition. It is a subset of the 80 million tiny images dataset and consists of 60,000 32x32 color images containing one of 10 object classes, with 6000 images per class. The whole project can be found in my GitHub: <a href="https://github.com/ChenghaoDing90/CIFAR10">(CIFAR10)</a>.

## Data Description
The CIFAR-10 data consists of 60,000 32x32 color images in 10 classes, with 6000 images per class. There are 50,000 training images and 10,000 test images in the official data. There are 10 different lables in this dataset, such as: airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck. The first 36 images is shown above.

The datasets are separated into train( of size 50000), validation(10000), and test datasets(300000) respectively.

In this project, two commonly used CNN models: VGG and ResNet is implemented.

## VGG
Pre-trained VGG16 and VGG19 are included in Keras, here, I build a VGG-like CNN models for object recognition.

### Visualization of VGG model

Here is the screenshot of the output of model.summary().

<div class="fig figcenter fighighlight">
  <img src="/assets/images/Capturevgg.png" width="800" height="800">
  <div class="figcaption"><br> Summary of VGG Model Building.<br>
  </div>
</div>

### VGG loss and accuracy versus training epochs

<div class="fig figcenter fighighlight">
  <img src="/assets/images/vgg_loss.png" width="800" height="400">
  <div class="figcaption"><br> Results of VGG Model.<br>
  </div>
</div>


## ResNet

The ResNet structure was re-implemented in Python. 
### ResNet loss and accuracy versus training epochs

<div class="fig figcenter fighighlight">
  <img src="/assets/images/resnet_loss.png" width="800" height="400">
  <div class="figcaption"><br> Results of ResNet Model.<br>
  </div>
</div>

The training/validation loss and accuracy versus training epochs are shown below. After 200 epochs, the test accuracy is around 0.90840. But looking carefully, after epoch 75, the training loss is still dropping while testing loss do not get any better since then. So the model seems to overfit.






