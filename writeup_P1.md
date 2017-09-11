# **Finding Lane Lines on the Road** 

## Project Report

### Udacity Self Drive Car Nano-Degree Term 1, Project 1

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:

* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]:  ./test_images_output/gray.png "Grayscale"

[image2]:  ./test_images_output/blur_gray.png "Gaussian"

[image3]:  ./test_images_output/edges.png "canny"

[image4]:  ./test_images_output/masked_edges.png "region"

[image5]:  ./test_images_output/line_image.png "lines"

[image6]:  ./test_images_output/lines_edges.png "processed"

[image7]:  ./test_images_output/line_image_full.png "lines_full"

---

### Reflection

### 1. Process pipeline.

My pipeline consisted of 5 steps.

1. I converted the images to grayscale
![alt text][image1]
2. Applied Gaussian smoothing
![alt text][image2]
3. Used canny for edge detection
![alt text][image3]
4. Limited edges by region of interest
![alt text][image4]
5. Used Hough transform to find lane lines
![alt text][image5]
6. Drew lines on the origin image
![alt text][image6]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 

1. grouping lines into "left" and "right" groups. The lines with slope larger than 0.1 are belong to right lane, while ones with slope smaller than -0.1 are belong to left lane.
2. averaging slope and intercept of each group are averaged to get one line for each group. 
3. drawing lines by calculating slope, intercept with the boundary of the size of the full image. 
![alt text][image7]
4. calling region_of_interest to limited the lines size.
![alt text][image5]




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that lines are straight by real lane lines could be curved, especially when the freeway is making turns.

Another shortcoming could be that the camera is not mounted at the front center, therefore the region of interest is alternated. 


### 3. Suggest possible improvements to your pipeline

A possible improvement for curved lane line would be to segmantally find lines, and connect them together.

Another potential improvement could be to pass camera location info into process pipeline to set the correct region of interest.