# **Finding Lane Lines on the Road** 

## Writeup Template

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "White"
[image2]: ./test_images_output/solidYellowCurve.jpg "Yellow"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps.
1. Convert the image into a grayscale image
2. Smoothing the image using the Gaussian function
3. Computing the gradient of the image using Canny edge detection algorithm
4. Applying region mask on the gradient image using polygon defined by vertices
5. Finding lane lines on the masked gradient image using hough transform and drawing the lines on the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating the left lines and right lines by calculating the slope of the lines slope_filter(). A simple linear regression was performed on both right and left lines to get the average line slopes and intercepts. Using these paremeters the bottom most and top most line points were calculated which were then used to draw the final lines on the original image. 

Below are the some of the images after complete processing:

![white][image1]
![yellow][image2]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when if the line lines went missing for some of the time in the test videos.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to improve the region_of_interest() function by changing the vertices of the polygon so as to decrease the area of the polygon for the challenge.mp4 to work.
