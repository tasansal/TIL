# Add Borders for Semantic Segmentation

## Summary
If you want to add borders to your segmentation masks, you can achieve instance segmentation by post-processing the predictions using Watershed Transformation method (see [#5](#5-image-segmentation-and-mathemetical-morphology)).

Once you convert your binary mask to a mask with borders, your segmentation becomes multi-class. This means you'll have to modify your model to be a multi-class segmentation model. Usually this is as simple as using a `softmax` activation in the final layer, and modifying your loss function to something like `CategoricalCrossentropy` (one-hot) or `SparseCategoricalCrossentropy` (integer labels).

A binary mask with borders looks like this. Keep in mind its not "binary" anymore:
<center>

![](https://keras.io/img/examples/vision/oxford_pets_image_segmentation/oxford_pets_image_segmentation_16_0.jpeg)![](https://keras.io/img/examples/vision/oxford_pets_image_segmentation/oxford_pets_image_segmentation_16_1.png)  
Image Credit [#2](#2-keras---image-segmentation-with-a-u-net-like-architecture)
</center>

In a different workflow, the authors of [#3](#3-methods-for-segmentation-and-classification-of-digital-microscopy-tissue-images) show that by using separate border masks and blob mask, they can also do instance segmentation of nuclei cores and cells.

<center>

![](https://www.frontiersin.org/files/Articles/433738/fbioe-07-00053-HTML/image_m/fbioe-07-00053-g001.jpg)  
Image Credit [#3](#3-methods-for-segmentation-and-classification-of-digital-microscopy-tissue-images)
</center>  

In general, you can take a binary mask and apply erosion and dilation options from [`OpenCV`](https://opencv.org/) or [`scipy.ndimage.morphology`](https://docs.scipy.org/doc/scipy/reference/ndimage.html#morphology) functions to achieve this.

The code in [#1](#1-generating-borders-around-objects-for-use-in-semantic-segmentation) has an example function that generates the borders. The YT channel also has a very nice explanation of it!

Shortened version of the above code reference:
```python
import cv2
import numpy as np

def generate_border(image, border_size=5, n_erosions=1):
    # Start by eroding edge pixels
    erosion_kernel = np.ones((3,3), np.uint8)
    eroded_image = cv2.erode(image, erosion_kernel, iterations=n_erosions)  
 
    # Calculate dilation kernel based on the desired border size
    # Add 1 to keep it odd (and symmetric)
    kernel_size = 2*border_size + 1 
    dilation_kernel = np.ones((kernel_size, kernel_size), np.uint8)

    # Apply dilation
    # Replace 255 values to 127 for all pixels.
    # Eventually we will only define border pixels with 255
    dilated  = cv2.dilate(eroded_image, dilation_kernel, iterations = 1) 
    dilated_127 = np.where(dilated == 255, 127, dilated) 	
    
    # What's remaining with a value of 127 would be the boundary pixels. 
    original_with_border = np.where(eroded_image > 127, 255, dilated_127)
    
    return original_with_border
```

Function can also be modified to return separate border masks and binary mask without border.

### Useful Links:
#### 1. Generating borders around objects for use in semantic segmentation
[Youtube](https://www.youtube.com/watch?v=65qPtD6khzg) - 
[GitHub](https://github.com/bnsreenu/python_for_microscopists/blob/master/tips_tricks_31_generating_borders_around_objects.py)

#### 2. Keras - Image segmentation with a U-Net-like architecture
[Website](https://keras.io/examples/vision/oxford_pets_image_segmentation/)

#### 3. Methods for Segmentation and Classification of Digital Microscopy Tissue Images
[Article](https://www.frontiersin.org/articles/10.3389/fbioe.2019.00053/full)

#### 4. Scipy's Morphology Functions
[Docs](https://docs.scipy.org/doc/scipy/reference/ndimage.html#morphology)

#### 5. Image Segmentation and Mathemetical Morphology
[Website](https://people.cmm.minesparis.psl.eu/users/beucher/wtshed.html) - 
[OpenCV Example](https://docs.opencv.org/4.x/d3/db4/tutorial_py_watershed.html)