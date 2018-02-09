# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

My pipeline consisted of 6 steps. The steps was tested with all images provided. 
First I converted each image to be a gray scale image.

[image1]: ./examples/grayscale.jpg "Grayscale"

Second I created a Gaussian Blur filter with a Kernel = 9.

The third step consisted in apply a Canny Algorith on the Gray image created. The algorithm take in care two important parameters. The low_threshold = 60 and high_threshold = 180 in a ratio 1:3. These values allow algorithm find better when occurred a change. The values set were the best fit for all images. 
The purpose of the Canny algorithm is to find the Edges of the image. It also take in care the filter passed by Gaussian Blur to drop strugles, noise, etc. 

The next step was to make a poligon with 4 vertices. This poligon was used to find lane lines just into the region of interest. 

The fifth step is transform the edges found by Canny from cartesian space to Hough Space. Hough is able to represent lines as a point in its space. Hough space uses polar coordinate so that represent its data. So, It also has some parameters to be adjusted. They are: theta = 1 degree, rho = 2, threshold = 20, min_line_lengh = 10, max_line_gap = 150. These values were fittable for the goal of the project. 

The Seventh step was to combine the lines found by Hough algorithm onto the original image. The final results is a original image overlaped by the lane lines detected with a transparency. 


My pipeline consisted of 5 steps. First, I converted the images to grayscale.

then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
