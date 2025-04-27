# Python for Computer Vision with OpenCV and Deep Learning 2021-3 **Course Practiced Files**
These files serve as my personal notes and hands-on practice to solidify my understanding of computer vision. 

- In [2 - NumPy and Image Basics](Files/2%20-%20NumPy%20and%20Image%20Basics) Started learning how to work with NumPy and arrays and then Learned how to open images using NumPy and Matplotlib, and got introduced to color channels and color mapping.

- In [3 - Image Basics with OpenCV](Files/3%20-%20Image%20Basics%20with%20OpenCV)  , I learned how to open images using the cv2 module of the OpenCV library, along with other operations such as opening images, changing color formats, copying images, flipping images, and adding shapes like rectangles, circles, and polygons.
Finally, I wrote code to open an image and draw a circle on it, as well as another piece of code that opens a window where you can draw a rectangle.

23- blending and pasting images: 
> cv2.addWeighted : this is used to blend two image on each other (opacity)


25- image thresholding:
> itroduction to: cv2.threshold , first of all you turn image into gray. then you try using threshold to add some effect on image.

> a function to show images in customized size: 
```
def show_pic(img):
    fig = plt.figure(figsize=(15,15))
    ax = fig.add_subplot(111)
    ax.imshow(img,cmap='gray'
```
```
show_pic(img)
```
> cv2.adaptiveThreshold : this will look into neighberhood pixels to make the changes 



> **Note:** The "DATA" folder is assets for the whole progress.
