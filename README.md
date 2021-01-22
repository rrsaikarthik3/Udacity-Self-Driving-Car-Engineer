# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

The aim of this project is to detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

In order to try out this code, please run the 'P1.ipynb' file with the appropriate libraries set up in your machine.

Description
---
This project was first attempted to mark the lanes in an image. This was done in order to calibrate the parameters that were used and then these were trained on multiple video clips. In order to get a detailed description of the method used to achieve this, please read [writeup_Project1.md] (https://github.com/rrsaikarthik3/Udacity-Self-Driving-Car-Engineer_Project_1_FInding_Lane_Lines/writeup_Project_1.md)
1. The pipeline used to achieve this project basically consisted of  : 
Grayscaling -> Guassian Blurring -> Canny Edge Detection -> Cropping the region of Interest -> Marking Lines that could be formed -> Grouping Lines to form single lined lane marking on either side

2. This project has potential shortcomings when the vehicle can encounter a sharp turn or when there is not a distinct contrast between the lanes and the road (i.e. road is not dark enough)

3. Possible solutions is to have a Sobel Operator in order to filter out the unwanted lines as well as to have a continuous learning of the line parameters in order to have a continuous and stable lines.


##The Project
---
The directories that end with 'output' are the place where the project output is written and the directories that do not have the name 'output' are their corresponding input files.

