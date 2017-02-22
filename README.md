#**Finding Lane Lines on the Road** 

##Writeup Template


---

**Finding Lane Lines on the Road**

The requirements of the project:
	* Make a pipeline that finds lane lines on the road
	* Identify road images from a video and return video stream as an output
	* The detected line segments should be averaged to map out the full extent of the left and right lane boundaries 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

	1.  The images were converted to grayscale

	2. 	The Gaussian smoothing was used to reduce images noise

	3. 	Apply Canny transform to detect the edges

	4. Apply a mask on the area of interest

	5. The Hough transformer was applied on edge detected image. Then use these lines on a blank image. Then, use the weight function to draw the lines on the real image


####1.1 To get the full length of the visible lane instead of discontinued lines, the following was done (Modification to draw_lines() function) : 

	1. Iterate over the lines and get the dimensions of each line

	2. split the lines into lift and right using slope's line

	3. calculate the average of lines on the left and right

	4. extrapolate the line segments and get finally lift line and right line

	5. draw the line on the original image


Here are the output images after running the code: 

![alt text][solidWhiteCurve.jpg]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a nother lane cross the lane especially on the cross roads 

Another shortcoming could be: I am not sure about the results of the current code if the lines' colors are dim.  

	-Maybe also some printed signed on the road could mislead our lane detection


###3. Suggest possible improvements to your pipeline


More changes should be done to the draw_lines() function to consider the history of changes and smooth the line drawn on the images

Another improvement: the configuration parameters could be automatically tuned based on the image state. Maybe the image is more noisy and we need to change the parameters of the Gaussian smoothing and the thresholds on Canny transform 