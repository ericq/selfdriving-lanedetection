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

My pipeline consisted of 5 major steps. First, I converted the images to grayscale, then I used Gaussian smoothing to get a blurred image before found the edges using Canny algorithm. After that, I created a zone of interest and then applied Hough transformation to find all lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by averaging and extrapolating the lines. First, I specified a acceptable zone of the slope for both left line and right line in order to filter out noise. After that, I calcualted the average value for the model y=mx+b for both left and right lines. After found the model, I draw the new lines in the interest zone.



![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be the Hough transformation parameters may need further tuning so it can be more robut in all kinds of instances.  

Another shortcoming could be the allowed scope range need further twist to find different cases during turning etc.

Interest zone today is a static polygon defined and is right in the center front. This zone actually will shift during turns. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to train the Hough transformation parameters in more scenarios.

Another potential improvement could be to find allowed slope range in different cases.

A smarter interest zone definition can be used based on the slope of the lines identified. 

I also noticed that the video takes more time to process after the line averaging function is added. We should consider further optimizaiton to improve performance.
