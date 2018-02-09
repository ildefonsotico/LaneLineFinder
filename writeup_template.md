# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of 6 steps. The steps were tested with all images provided. 
First I converted each image to be a gray scale image.

[image2]: ./project_output/images/solidWhiteCurve_grayscale.jpeg "SolidWhiteCurve"
![alt text][image2]

Second I created a Gaussian Blur filter with a Kernel = 9.

The third step consisted in apply a Canny Algorith on the Gray image created. The algorithm take in care with two important parameters. The low_threshold = 60 and high_threshold = 180 in a ratio 1:3. These values allow algorithm find better when occurred a change throught road and lane lines. The values set were the best fit for all images. 
The purpose of the Canny algorithm is to find the Edges of the image. It also take in care the filter passed by Gaussian Blur to drop grubbiness, noise, etc. 

[image3]: ./project_output/images/solidWhiteCurve_canny.jpeg "Canny"
![alt text][image3]

The next step was to make a poligon with 4 vertices. This poligon was used to find lane lines just into this region of interest. 

The fifth step is transform the edges found by Canny from cartesian space to Hough space. Hough is able to represent lines as a point in its space. Hough space uses polar coordinate so that represent its data. So, It also has some parameters to be adjusted. They are: theta = 1 degree, rho = 2, threshold = 20, min_line_lengh = 10, max_line_gap = 150. These values were fittable for the goal of the project. 

The Seventh step was to combine the lines found by Hough algorithm onto the original image. The final results is a original image overlaped by the lane lines detected with a transparency. 

[image4]: ./project_output/images/solidWhiteCurve_combination.jpeg "Combination"
![alt text][image4]


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be what happen the Canny found a lot of edges too close and with the similiary size. It makes the pipeline found false positives.

Another shortcoming could be too much noises in different types of road, causing frequently the noise detection as being part of the lane lines detection. 

Other shortcoming could be the polygon made to find the region of the interest does not be enough for all cases in a real driving on the road. 



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to allow all parameters being configured by a standard file settings or something like that.

Another potential improvement could be to make the pipeline more dynamic, allowing it redefine the region of the interest and parameters as fast as needed to be more assertive along the lane lines detection.

It could be very usefull to improve the Kernel size of the Blur Gaussian Filter according differents types of road, colors, straight or curve, etc. I realized depending whith image is, the kernel can put in or out noise according with its size.
