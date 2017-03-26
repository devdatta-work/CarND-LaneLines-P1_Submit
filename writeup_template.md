#**Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps
* First, I converted the images to grayscale
* Second, I applied Gaussian Blurring
* Third, I used Canny algorithm to draw the edges
* Fourth, I created an image only with the trapezoid in question
* Fifth, I run the Hough lines on this image. This algorithm calls the function draw lines which I modified (more on this below)
* Sixth, I combined the images

I modified the draw_lines()_ function as follows
* I find the slope of the line.  If it is negative, it is the left lane, if positive it is the right lane
* I start with some dead weight on the averages for the slope and intercept, and keep adding lines to the average
* I weight every single data point by the square of the length of the segment.  This gives more weight to the longer segments


###2. Identify potential shortcomings with your current pipeline

* The masking of the image to the trapezoid in front is hard-coded. It will fail when the car is taking a sharp turn.  
* Also the lanes drawn are straight, while lanes in real world are curved.  Depending on how we plan to use the lane information, it will be useful to draw lanes differently (maybe using polynomials instead of straight line)
* Given how we build the average, lines with higher slope will have unfair weight compared to flatter lines.  A work around would be to use the rho and theta paramterization format instead. 

###3. Suggest possible improvements to your pipeline

Included above