{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# **Finding Lane Lines on the Road** \n",
    "\n",
    "\n",
    "---\n",
    "\n",
    "**Finding Lane Lines on the Road**\n",
    "\n",
    "The goals / steps of this project are the following:\n",
    "* Make a pipeline that finds lane lines on the road\n",
    "* Reflect on your work in a written report\n",
    "\n",
    "\n",
    "[//]: # (Image References)\n",
    "\n",
    "[image1]: ./test_images_output/gray.jpg \"Grayscale\"\n",
    "[image2]: ./test_images_output/blur_gray.jpg \"Blur Gray\"\n",
    "[image3]: ./test_images_output/edges.jpg \"Edges\"\n",
    "[image4]: ./test_images_output/masked_edges.jpg \"Masked Edges\"\n",
    "[image5]: ./test_images_output/weight_image.jpg \"Weighted Image\"\n",
    "\n",
    "\n",
    "---\n",
    "\n",
    "### Reflection\n",
    "\n",
    "### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.\n",
    "\n",
    "My pipeline consisted of 5 steps. \n",
    "#### I). I conveerted the images to grayscale\n",
    " ![alt_text][image1]\n",
    "#### II). I used the gaussian_blur to smooth the image, i use the 5x5 kernel to do it. \n",
    " ![alt_text][image2]\n",
    "#### III). Next I used the canny to get the edegs for the input image, with the parameters: low_threshold = 50, high_threshold = 150\n",
    " ![alt_text][image3]\n",
    "#### IV). I defined a polygon to confirm the lane lines in it.\n",
    " ![alt_text][image4]\n",
    "#### V). I used hough_lines to find out all lines in polygon.\n",
    "##### In order to draw a single line on the left and right lanes, I modified the draw_lines() function by change the name to draw_lanes, differentiate the left and right lanes with the slope of the line ((y2 - y1)/(x2 - x1)), when the slop < 0 the line is in the left lane, and clean the lines if the line's slope is less than threshold, i guess it can pop some level line. next i used numpy.ployfit to fit the left line and right line in the function calc_lane_vertices, last i draw the line in image.\n",
    " ![alt_text][image5]\n",
    "\n",
    "\n",
    "### 2. Identify potential shortcomings with your current pipeline\n",
    "\n",
    "\n",
    "One potential shortcoming would be what would happen when the contrast is not obvious, like the color of road is colse the lane line, upside can't confirm the lines. \n",
    "\n",
    "Another shortcoming could be the shadow, when shadow on the road, upside can catche the the shadwo's line, this is the noise, but clean it is difficult， and not robust.\n",
    "\n",
    "Another shortcoming could be the arc line, when car is turnning left or turnning right, the lane line is a arc line, not straight line，fit it will be a big worker.\n",
    "\n",
    "\n",
    "### 3. Suggest possible improvements to your pipeline\n",
    "\n",
    "A possible improvement would be to use the DeepLearn, let the machine know this is the lane line. \n",
    "\n",
    "Another potential improvement could be to use the Dynamic tracing to get the change in the specified polygon, let the machine know in this scope the changed thing must attention。\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {
    "collapsed": true
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.5.2"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
