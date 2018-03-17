# Project: Finding lane lines on the road


Overview
---
The aim of this project is to find the lane lines on the road for a self driving car.


Pipeline of the lane detection
---
The image processing pipeline to find the lines involves following steps
* Input is an 3-channel color image (an image or a frame of the video). This is our `original image`
* Conversion from `original image` to `grayscale image`
* Blurring the `grayscale image` using _Gaussian Filter_ to obtain `blurred image`
* Applying _Canny edge detection_ for the `blurred image` to obtain the `edge image`
* Selecting suitable region of interest in this `edge image`. Output of this stage is `roi image`
* Use of _hough lines_ algorithm to find lines. Input is `roi image` and output is `line image` and the `line segments`
* With the `line segments` left and right lines are identified and extrapolated them to fill the entire line
* Finally this `extrapolated lines` are superimposed on the `original image` to obtain `final output image`


Detailed description of the pipeline
---

#### Step1: Original Image
<img src="test_images/solidWhiteCurve.jpg" width="480" />

#### Step2: Grayscale Image
<img src="test_images_output/gray.jpg" width="480" />

In this step original image is converted to grayscale image using the helper function.

#### Step3: Blurring
<img src="test_images_output/blurred.jpg" width="480" />

In this step, grayscale image is blurred using gaussian blur helper function. `Kernel size` value is chosen as `7`.

#### Step4: Edge Detection
<img src="test_images_output/canny_edge.jpg" width="480" />

In this step, blurred image is passed on to canny edge detector. `Lower threshold` and `Upper threshold` is chosen to be `80` and `240` respectively.

#### Step5: ROI Selection
<img src="test_images_output/roi_image.jpg" width="480" />

In this step Region of Interest is selected in a trapezoidal form with `vertices`: `(0.4*width, 0.56*height)`, `[0.15*width, height]`, `[0.95*width, height]` and `[0.6*width, 0.56*height]`.

#### Step6: Line Detection
<img src="test_images_output/hough_lines.jpg" width="480" />

