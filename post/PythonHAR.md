---
date: 2020-11-15T11:00:59-04:00
description: "I used Python to classify different physical activities (e.g., walking, climbing stairs) from tri-axial smartphone accelerometer data as accurately as possible"
featured_image: "/images/HAR.png"
tags: []
title: "Physical activities classification with Python"
---

# Using Python for Research Final Project

## Introduction

The goal of the project is to classify different physical activities (e.g., walking, climbing stairs) from tri-axial smartphone accelerometer data as accurately as possible.

## Input Data

The input data used for training in this project consists of two files. The first file, [train_time_series.csv](https://courses.edx.org/assets/courseware/v1/b98039c3648763aae4f153a6ed32f38b/asset-v1:HarvardX+PH526x+2T2020+type@asset+block/train_time_series.csv), contains the raw accelerometer data, which has been collected using the [Beiwe research platform](https://github.com/onnela-lab/beiwe-backend).
Raw_data timestamp column as the time variable; 
the last three columns, here labeled x, y, and z, correspond to measurements of linear acceleration along each of the three orthogonal axes.

The second file , [train_labels.csv](https://courses.edx.org/assets/courseware/v1/d64e74647423e525bbeb13f2884e9cfa/asset-v1:HarvardX+PH526x+2T2020+type@asset+block/train_labels.csv), contains the activity labels, and I'm going to use these labels to train the model. Different activities have been numbered with integers with the following encoding: 1 = standing, 2 = walking, 3 = stairs down, 4 = stairs up. Because the accelerometers are sampled at high frequency, the labels in train_labels.csv are only provided for every 10th observation in train_time_series.csv.

## Methods
1. I start from importing libraries and reading two files to train the model.
2. I explore two training files to see how x, y, and z measurements of linear acceleration change during the activity time and understand how balanced the training data is.
3. I combine x, y, and z measurements of linear acceleration into 4th component, combined magnitude, by taking a square root of summ of squares of x, y, z linear acceleration.
4. I calculate rolling average and rolling standard deviation for all four components that gives me 8 features to analyze and train the model
5. I check how RandomForest, LogisticRegression, Support Vector Classifier and KNeighborsClassifier perform on train and validation dataset

## Results
The pattern of activity was easy to detect for standing and walking activity, and not so obvious for moving up and down stairs. As for data balance it was obvious that most of the time the person was walking. The imbalanced input data might had led to the results of an accuracy on a test dataset of 63.2%. 
I could significantly improve the model by finding the solution of giving the model the idea that labels shouldn't change every second. Also I could improve the model by finding out extra features to extract to train the model.
Anyway KNN classifier was the best to perform in this case.

## Conclusion
The task to classify the human activity is very interesting to solve. I invested a lot of time thinking about the project. The run time was fast, 3.125 seconds with KNN Classifier and 85.6% of accuracy on validation data set, and 63.2% of accuracy on a test dataset.
It was a great opportunity to practice and think. I see an endless opportunity to gain more knowledge.
{{< figure src="/images/HAR.png" >}}