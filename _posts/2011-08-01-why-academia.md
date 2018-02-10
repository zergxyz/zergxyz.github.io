---
title: Why Academia?
author: Daniel Seita
layout: post
permalink: /2018/02/09/Intro to Image Classification/
geo_public:
  - 0
categories:
  - Computer Science
---

Image Classification problem, which is the task of assigning an input image one label from a fixed set of categories. This is one of the core problems in Computer Vision that, despite its simplicity, has a large variety of practical applications. 

Example--Cat in pixels. in the image below an image classification model takes a single image and assigns probabilities to 4 labels, {cat, dog, hat, mug}. As shown in the image, keep in mind that to a computer an image is represented as one large 3-dimensional array of numbers. In this example, the cat image is 248 pixels wide, 400 pixels tall, and has three color channels Red,Green,Blue (or RGB for short). Therefore, the image consists of 248 x 400 x 3 numbers, or a total of 297,600 numbers. Each number is an integer that ranges from 0 (black) to 255 (white). Our task is to turn this quarter of a million numbers into a single label, such as “cat”.
![](http://cs231n.github.io/assets/classify.png)

Challenges for image classifcation: 
* Viewpoint variation. A single instance of an object can be oriented in many ways with respect to the camera.
* Scale variation. Visual classes often exhibit variation in their size (size in the real world, not only in terms of their extent in the image).
* Deformation. Many objects of interest are not rigid bodies and can be deformed in extreme ways.
* Occlusion. The objects of interest can be occluded. Sometimes only a small portion of an object (as little as few pixels) could be visible.
* Illumination conditions. The effects of illumination are drastic on the pixel level.
* Background clutter. The objects of interest may blend into their environment, making them hard to identify.
* Intra-class variation. The classes of interest can often be relatively broad, such as chair. There are many different types of these objects, each with their own appearance.

**Data Driven approach**:  instead of trying to specify what every one of the categories of interest look like directly in code, the approach that we will take is not unlike one you would take with a child: we’re going to provide the computer with many examples of each class and then develop learning algorithms that look at these examples and learn about the visual appearance of each class. 


**The image classification pipeline.** We’ve seen that the task in Image Classification is to take an array of pixels that represents a single image and assign a label to it. Our complete pipeline can be formalized as follows:

* Input: Our input consists of a set of N images, each labeled with one of K different classes. We refer to this data as the training set.
* Learning: Our task is to use the training set to learn what every one of the classes looks like. We refer to this step as training a classifier, or learning a model.
* Evaluation: In the end, we evaluate the quality of the classifier by asking it to predict labels for a new set of images that it has never seen before. We will then compare the true labels of these images to the ones predicted by the classifier. Intuitively, we’re hoping that a lot of the predictions match up with the true answers (which we call the ground truth).