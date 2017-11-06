# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
 1. I conveerted the images to grayscale
 2. I used the gaussian_blur to smooth the image, i use the 5x5 kernel to do it. Next I used the canny to get the edegs for the input image, with the parameters: low_threshold = 50, high_threshold = 150
 3. I defined a polygon to confirm the lane lines in it.
 4. I used hough_lines to find out all lines in polygon.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by change the name to draw_lanes, differentiate the left and right lanes with the slope of the line ((y2 - y1)/(x2 - x1)), when the slop < 0 the line is in the left lane, and clean the lines if the line's slope is less than threshold, i guess it can pop some level line. next i used numpy.ployfit to fit the left line and right line in the function calc_lane_vertices, last i 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
