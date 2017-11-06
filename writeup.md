
# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/gray.jpg "Grayscale"
[image2]: ./test_images_output/blur_gray.jpg "Blur Gray"
[image3]: ./test_images_output/edges.jpg "Edges"
[image4]: ./test_images_output/masked_edges.jpg "Masked Edges"
[image5]: ./test_images_output/weight_image.jpg "Weighted Image"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
#### I). I conveerted the images to grayscale
 ![alt_text][image1]
#### II). I used the gaussian_blur to smooth the image, i use the 5x5 kernel to do it. 
 ![alt_text][image2]
#### III). Next I used the canny to get the edegs for the input image, with the parameters: low_threshold = 50, high_threshold = 150
 ![alt_text][image3]
#### IV). I defined a polygon to confirm the lane lines in it.
 ![alt_text][image4]
#### V). I used hough_lines to find out all lines in polygon.
##### In order to draw a single line on the left and right lanes, I modified the draw_lines() function by change the name to draw_lanes, differentiate the left and right lanes with the slope of the line ((y2 - y1)/(x2 - x1)), when the slop < 0 the line is in the left lane, and clean the lines if the line's slope is less than threshold, i guess it can pop some level line. next i used numpy.ployfit to fit the left line and right line in the function calc_lane_vertices, last i draw the line in image.
 ![alt_text][image5]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the contrast is not obvious, like the color of road is colse the lane line, upside can't confirm the lines. 

Another shortcoming could be the shadow, when shadow on the road, upside can catche the the shadwo's line, this is the noise, but clean it is difficult， and not robust.

Another shortcoming could be the arc line, when car is turnning left or turnning right, the lane line is a arc line, not straight line，fit it will be a big worker.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use the DeepLearn, let the machine know this is the lane line. 

Another potential improvement could be to use the Dynamic tracing to get the change in the specified polygon, let the machine know in this scope the changed thing must attention。



```python

```
