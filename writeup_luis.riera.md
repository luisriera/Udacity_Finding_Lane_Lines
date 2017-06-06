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

To achive the objective of this project, a pipline of <<n>> steps was used.  The steps were implemented in the following sequence:
- 1.- All images were converted to grayscale color
- 2.- A Canny Edges funtion was used to detect the gradient lines in the images
- 3.- Hough Transform was applyed to find the Lane Lines from from previous Canny Edges output
- 4.- A Region Masking technique was used pull the Lane Lines from optained in step 3
- .- Lane lines were pulled by combining the mas regiona and thegrayscale images
- .- 



My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
