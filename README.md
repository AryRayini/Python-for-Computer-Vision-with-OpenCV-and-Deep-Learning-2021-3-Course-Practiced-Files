https://github.com/user-attachments/assets/077d66d2-effb-4656-b36f-e4c1b6ea6cf6

https://github.com/user-attachments/assets/bf767f45-ced2-4267-82a9-cd31dc337945

https://github.com/user-attachments/assets/d0d468ac-be6d-40a6-8ddc-749ee86fa4ad
# My Practices on Computer Vision

These files serve as my personal notes and hands-on practice to solidify my understanding of computer vision. 

- In [2 - NumPy and Image Basics](Files/2%20-%20NumPy%20and%20Image%20Basics) Started learning how to work with NumPy and arrays and then Learned how to open images using NumPy and Matplotlib, and got introduced to color channels and color mapping.

- In [3 - Image Basics with OpenCV](Files/3%20-%20Image%20Basics%20with%20OpenCV)  , I learned how to open images using the cv2 module of the OpenCV library, along with other operations such as opening images, changing color formats, copying images, flipping images, and adding shapes like rectangles, circles, and polygons.
Finally, I wrote code to open an image and draw a circle on it, as well as another piece of code that opens a window where you can draw a rectangle.

- In [4 - Image Processing](Files/4%20-%20Image%20Processing) , We've learnt about color mappings, blending images, image thresholding, blurring and smoothing images to find edges better,
morphological operators, gradient and histogram and histogram equalization.
<details>
  <summary>Click to expand Section 4!</summary>
    23- blending and pasting images: 
> cv2.addWeighted : this is used to blend two image on each other (opacity)


25- image thresholding:
> itroduction to: cv2.threshold , first of all you turn image into gray. then you try using threshold to add some effect on image.

> a function to show images in customized size (this will display image a little larger): 
```
def show_pic(img):
    fig = plt.figure(figsize=(15,15))
    ax = fig.add_subplot(111)
    ax.imshow(img,cmap='gray')
```
```
show_pic(img)
```
> cv2.adaptiveThreshold : this will look into neighberhood pixels to make the changes 

26- blurring and smoothing images: it will help to reduce the noise, or help a computer vision application to focus on details. **blurring and moothing** always combined with *edge detection*. edge detection algorithm detects too many edges when a high resolution picture shows up without any blurring.
**gamma correction** : this will help to make the picture brighter or darker.
**kernel based filters** : kernel filters are some matrices and they will apply some mathematic operation to pixels to make the new image. 

27- **blurring**: blurring is used to blur images if they are noisy or reduce the image detail to detect edges better. we use brick image because it is easy to see outline of each brick.

> if you choose a gamma value less than 1, then you make the picture brighter. example : 1/4
```
gamma = 1/4
# to effect the image we use np.power. also power is related to the same power in math.
# it's trying to increase the value of power of pixels by the power, and power comes from gamma variable.
result = np.power(i,gamma) 
display_img(result)
```

> *Blurring* : first we make a kernel. then we apply a 2D filter on it.
```
kernel = np.ones(shape = (5,5),dtype = np.float32)/25
```
```
# -1 means input depth is the same as output depth
dst = cv2.filter2D(img , -1,kernel)
display_img(dst)
```
> *blurring gaussian and median methods*:
```
# guassian
blurred_img = cv2.GaussianBlur(img,(5,5),10)
display_img(blurred_img)
```
```
# median
median = cv2.medianBlur(noise_img,5)
display_img(median)
```
```
# bilateral
blur = cv2.bilateralFilter(img, 9,75,75)
display_img(blur)
```
**there are many ways to make a blur img and things like this, it's guess and check most of the time**

28-  **morphological operators** : this is sets of kernels that can achieve a variety of effects, such as reducing noise. certain operators are very good at reducing black points on a white background ( and vice versa )

*Erode* :
```
this will erode edges.
result = cv2.erode(img,kernel,iterations= 4)
```
*Opening* : 
```
# using opening ( morphological operator ) to get rid of this noise 
opening = cv2.morphologyEx(noise_img,cv2.MORPH_OPEN,kernel)
```
*closing*: 
```
# closing 
closing = cv2.morphologyEx(black_noise_img,cv2.MORPH_CLOSE,kernel)
```
*morphological gradient*:
```
gradient = cv2.morphologyEx(img,cv2.MORPH_GRADIENT,kernel)
```


> *Most used codes around the projects* : 
```
# imports
import cv2 
import numpy as np
import matplotlib.pyplot as plt
```
```
# img loadmentory
 def load_img():
     blank_img = np.zeros((600,600))
     font = cv2.FONT_HERSHEY_SIMPLEX
     cv2.putText(blank_img,text = 'ABCDE' , org = (50,300) , fontFace = font , fontScale = 5 , color = (255,255,255),thickness = 4)
     return blank_img
```
38 : Drawing Shape on live video ( this technique will be used on obj detection ) 
</details>

- In [5 - Video Basics with Python and OpenCV](Files/5%20-%20Video%20Basics%20with%20Python%20and%20OpenCV) i experienced how to open camera and record and save it or opening a saved video and even drawing on a live camera. it was a easy and simple section!

- In [6 - Object Detection with OpenCV and Python](6%20-%20Object%20Detection%20with%20OpenCV%20and%20Python) started learning template matching which you can find a object in image using piece of that object as a image. after that i learnt how to detect corners using harris corner detection algorithm and after that i learnt how to work with shitomasi corner detection algorithm ( goodfeaturestotrack ). head to the next episode, i learned how to detect edges ( you better make the images a little blur tho ). next one was grid detection. after that we met contour detection, there were two expression called : 1- inner contour and 2- external contour ( inner is the things inside of object and external is the round of object ). next part we exprienced feature matching, it has two algorithm, 1- ORB match detector 2-SIFT detector, by using these algorithms you can find the key parts on a image and then find the target on another image.


<details>
  <summary>Click to expand Section 6!</summary>
  42- Template Matching: we find our "x" data using "y" data. we can use these methods: 
  ['cv2.TM_CCOEFF', 'cv2.TM_CCOEFF_NORMED', 'cv2.TM_CCORR','cv2.TM_CCORR_NORMED', 'cv2.TM_SQDIFF', 'cv2.TM_SQDIFF_NORMED']

  43 & 44- Corner detection: we will look at some of the most popular algorithms: 1- harris corner detection 2- shi-tomasi corner detection

  45 - edge detection : in this lecture we learn how to work with canny edge detector which is one of the most popular edge detection algorithms. it developed in 1986 by john canny and it's multi-stage algorithm (A multi-stage algorithm is a method that solves a problem through a sequence of steps or stages, where the solution at one stage depends on the results of the previous stages. It breaks down a complex problem into simpler subproblems, solves them step-by-step, and combines these solutions to get the final answer). *the first step is to apply gaussian filter to smooth image in order to remove noise. in the next step we apply non-maximum suppression to get rid of suprious response to edge detection. then apply double threshold to determine potential edges. then it will finalize the detection of edges by supperssing all the other edges that are weak and not connected to strong edges. **note:** for high resolution images when you only want general edges, it is usually a good idea to apply a custom blur before applying the canny algorithm. also this algorithm requires a user to decide on low and high threshold values.*

  45 - grid detection : this is often used for camera calibration.
  47 - contour detection : contours are a useful tool for shape analysis and object detection and recognition.
  48 & 49 - feature matching : with feature matching you will find the key part of a image from another similar image and you match them.
  50 51 52 - watershed algorithm : with that we segmentate the image.
  53 - Face Detection :  
  
</details>

- In [7 - Object Tracking](7%20-%20Object%20Tracking) it was the time to witness the optical flow. optical flow is a kind of way to track objects. there were two optical flow algorithm. 1- **Lucas-Kenade (Sparse optical flow )** 2- **Gunner Fanreback's (Dense Optical Flow)**

> **Note:** The "DATA" folder is assets for the whole progress.
