# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

In this project a lane lines detection pipeline is implemented. For this purpose, several computer vision techniques such as gaussian blur, canny edge detection, hugh transform and more will be used. The code will be implemented in Python using at the same time OpenCV library. This project is part of the Self-driving car nanodegree (Udacity). The code was written into a jupyter notebook (P1.ipynb) and is fully documentated. 

### Reflection

### 1. Pipeline description

My pipeline consists in x steps: convert input image to gryscale, remove noise with gaussian blur, detect edges with canny detector, create a mask in order to perform a proper segmentation only of the road, detect straight lines with hugh transform, compute the line segments and finally combine the original image with the line segments. 

For computing the line segments (line_segments function) we firstly detect right and left-sided lines by computing the slope of detected lines (slopes of right-sided lines are positive, meanwhile left-sided are negative). Then, we filter the lines by using median value of the slopes and a threshold value. If the difference between current lines slope and median value is below the threshold, the line will be considered. Finally, we compute the one-dimensional polinominal class of the least squares polynominal fit and drawing the resulting lines of each side.

The results of each step are included into the notebook. 
Video results are in test_videos_output folder.



### 2. Identify potential shortcomings with your current pipeline

My pipeline doesn't work with the optional video because of the curved lines which are not extrapolated properly. At the same time, the filtering process by using median value may be slow. Maybe this step can be improved in performance and results. 

### 3. Possible improvements to your pipeline

Use RANSAC in order to improve line fitting. In this way maybe we can avoid better the impact of outliers. We also can improve Hough transform in order to deal with curved lines.
