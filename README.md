
# Real time face mask detection in Android 

![demo 1](demo/demo1.mp4) ![demo 2](demo/demo2.mp4) 


### Overview
The recent coronavirus pandemic has pushed people around the world to new challenges. In this context of uncertainty, we can all play our role by contributing to the fight against this disease. This is an excellent opportunity to put technology at the service of humanity. From my place I could try to contribute with the tools that I can work on. So here I've developed an application to detect face masks in the smartphone. This application works in real time.

### Motivation
Although it is not entirely clear how much the use of the face mask can protect us from the virus, it is chilling to see how far a simple sneeze can drop breath droplets, potentially carrying with them the virus. If the use of the face mask could reduce at least a bit the propagation I think it is worth it to enforce its use.

A solution that is within everyone's reach could help to control the use of the face mask. And today everyone has a smartphone, so perhaps a mobile application could help. This post solves this problem using an Android mobile application that recognizes face masks. I hope this small contribution is useful.


## A good face mask detector for mobile
The great Adrian Rosebrock, has recently published  [a great article](https://www.pyimagesearch.com/2020/05/04/covid-19-face-mask-detector-with-opencv-keras-tensorflow-and-deep-learning/) about how to train a deep learning model to achieve this task. In his post he used [this](https://github.com/prajnasb/observations) dataset provided by [Prajna Bhandary](https://www.linkedin.com/feed/update/urn:li:activity:6655711815361761280/), which was very cleverly generated (by artificially drawing face masks over the positions of detected face landmarks).
The approach proposed by Adrian is to utilize a two-stages detector, first a face detector is applied, to retrieve the faces positions. Then each face is cropped and prepossessed to be feed into the second model which does a binary classification detecting between **"mask"** or **"no-mask"**.

![enter image description here](https://miro.medium.com/max/1400/1*9zeIJ3ySJfLnCV6T0DhnUg.png)

The model was converted from Keras to TensorFlow Lite using the **TocoConverter** python class to migrate from the Keras '*.h5'* format to the TensorFlow Lite *'.tflite'* format.


## Based on TensorFlow Lite Object Recognition Example
This code modified from the TensorFlow's object detection canonical example, to be used with the face mask model described above. In that repository we can find the source code for Android, iOS and Raspberry Pi. Here we will focus on making it work on Android, but doing it on the other platforms would simply consist of doing the analogous procedure.