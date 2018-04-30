# **Finding Lane Lines on the Road** 



---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipline consists of the following steps:
1. convert the image to grayscale
2. apply Gaussian smoothing
3. create masked edges image
4. perform Hough transformation
5. add the Hough lines to the original image
6. Create two continuous lines for left and right lane marking
    6.1. First I calculated the slope of each line
    6.2. I rejected all lines, that did not satifsy the slope condition for lane markings, e.g. vertical and horizontal lines
    6.3. I assigned the lines to the left or right lane by the corresponding slope value and x,y-values
    6.4. I computed the mean of the slope and position for left/right side
    6.5. With the line equation y=mx+t I calculated the y-intersect t=y-mx 
    6.6. The y-values of the final lane lines are given by the region of interest
    6.7. The y-values of the final lane lines are given by x = (y-t)/m



### 2. Identify potential shortcomings with your current pipeline


The shortcomings of the solution are:
- Only lines can be detecte but no sharp bends, as only a straight line is fitted to the image
- The algorithm is quite sensitive to the choice of parameters 


### 3. Suggest possible improvements to your pipeline

Improvements to the pipeline are:
- fit a polynomial or clothoid function to the data
- Use a robust least squares algorithm to merge the hough transforms into a lane instead of averaging the houg lines
- As lane markings do not disapear in a fraction of seconds, I would use the found lane marking from the previous frame to calculate the current lane marking position