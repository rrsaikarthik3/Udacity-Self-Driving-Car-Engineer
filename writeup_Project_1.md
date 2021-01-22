# **Finding Lane Lines on the Road** 



**Finding Lane Lines on the Road**

The goal of this project to mark lanes on the road observed through a camera. This was solved step by step. As the first step, few
images are taken as training example and the tunable parameters are tuned and the pipeline was set up. Once this had the desired performance, then the same functions were used for a video clip and the parameters were further tuned to fit the video as well as the image. 



### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the folliowing steps: 
Given Image : 
[/test_images/solidWhiteCurve.jpg]

1. Convert the given image to grayscale. 5 steps. First, I converted the images to grayscale.
[/test_images_output/grayscale_solidWhiteCurve.jpg]

2.The next step was to blur the image using Guassian Blur. This helped in having distinct edge detection through Canny edge function (the next step)
[/test_images_output/guassian_blur_solidWhiteCurve.jpg]

3. Then the blurred image was passed through the Canny edge algorithm to identify the edges 
[/test_images_output/canny_solidWhiteCurve.jpg]

4. Once the edges were identified, an area of interest in the image was selceted by constructing a polygon that covers the area of interest. This helps us to eliminate the edges found outside this region and only focus on the edges detected inside this. 

5. After identifying the region of interest, number of hough lines are drawn inside the region of interest.

6. These lines were grouped together to form a single line that streched from the bottom edge of the given image and ended at the last point where hough lines could be draw. 
The method to extrapolate were : 
a. Group the lines as left edge or the right edge based on their location of the bottom point with respect to the image and also having an additional check on the magnitude of the slope. This is done in order to eliminate lines that did not belong to  the lanes from the Hough Lines function
b. Find the average slope for each group 
c. Find the average intercept point for each group (point the line would meet the bottom edge of the image) 
d. Once these were identified, find the top most point among each group
e. Using the average slope information and the top most point, and the 'y' value of the bottom most point (i.e. the bottom edge of the image) the bottom 'x' value was found.
f. Using the line determined through the previous step, top point 'x' was again re-calculated by selecting the 'y' which streched the farthest from the bottom edge. This helped in drawing the logest line possible.


7. Once the solid lines were drawn to mark the lane, the lines were combined with the original image using weighted addition.
[/test_images_output/hough_line_solidsolidWhiteCurve.jpg]



### 2. Identify potential shortcomings with your current pipeline
1. One of the potential shortcoming I found with this approach was that it failed to identify the lanes properly in the 'optional assignment' video particularly when there background road was not in complete contrast with the lane. 

2. Additionally the lane detection might not work properly when encountering a sharp 90 degree turn. 


### 3. Suggest possible improvements to your pipeline
1. One possible improvement can be having a Sobel_x operator before applying the Canny edge algorithm to find the edges.
2.Another improvement can be to improve the algorithm that collects the individual lines and draws one single line. This algorithm can be improved if there is a way to use the line information found from the previous instances of the video and have a small learning through the previous images.

