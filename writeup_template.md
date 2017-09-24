# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight.jpg "result"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

I think, in order to solve this big problem, I have to divide it into servial basic part, so I made a analysis at first, the Lane Lines has a few features ,it only appear in the bottom part of the image(position), the lane lines can only be white(colour) and then it's straight(geometry).Thus, My pipeline consisted of 3 steps.:
First find the potential white pixil in the image , I implenment it according to the code in the course. Then I try the geometry feature , use a triangle mask to mask the interest area.
finally,I use Canny edge detection and Hough transform to find out the edge line of lane lines.
the demo result is here:

![alt text][image1]



### 2. Identify potential shortcomings with your current pipeline

colour or geometry feature can be very unstable, since the light can change sharply during the day ,
and the line in the bend truns into a curve and the interest position will change a little bit. 

Then my pipeline identify the lane line by these feature, all above can make great influence on the result. This is really my pipeline's great shortcoming.

### 3. Suggest possible improvements to your pipeline

1. for colour
	I think a great idea is to use a adaptive grey scale threshold method, I even had a try 
	I used OTSU threshold method to process the image, then the pip line do adaptive to the light, but there a few point after canny and cannot be use to find lines. Maybe I can have a few more try.

2. geometry
	I think we don't have to find the straight line at last, in my experiment, after thresh_OTSU and position mask , the lane lines area is very clear (although some noise or other obj come into the image either and i did not find out a good method to identify these area now) , if we remove the straight line detection procedure, the pipeline may adaptive to the bend road. 