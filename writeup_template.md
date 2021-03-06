# **Finding Lane Lines on the Road** 

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The pipeline consists of the following steps:
1. Convert RGB image to a Grayscale image
2. Detect edges from the Grayscale image using Canny edge detection algorithm
3. Define a Region of interest and mask out the undesired region of the binary image (obtained from Canny edge detection algorithm) 
4. Retrieve Hough lines by applying Hough tranform on the edges in the masked image
5. Consolidate collections of Hough lines (by averaging line parameters) to a single line corresponding to each lane, and extrapolate these lines from the position of bottom edge to a chosen edge parallel to the bottom edge of the image 
6. Draw Hough lines on the original image

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming of the pipeline is that it does not work effectively when there is not enough contrast between the lane lines and road surface i.e. either the lane lines are very similar in color to the road surface, or the road surface is quite reflective. Another shortcoming is of mapping lane lines on turns, simply because lane lines are curved and the pipeline tend to fit straight lines on these curved lanes.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to boost the yellow areas of the image so that there is enough contrast between the solid yellow lines and the road surface. This can be done by converting original image from RGB to HSV colorspace and from it isolating the yellow and the white lanes respectively. Further, superimpose these lanes on the darkened grayscale image (done to enhance the contrast) and then following steps 2 to 6 of the pipeline.
