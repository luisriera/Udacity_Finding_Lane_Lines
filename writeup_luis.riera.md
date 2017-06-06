# **Finding Lane Lines on the Road** 
---
//]: # (Image References)


[Grayscale]: ./test_images_output/gray_solidWhiteCurve.jpg "Grayscale"
[Gaussian]: ./test_images_output/blurred_solidWhiteCurve.jpg "Gaussian"
[Canny]: ./test_images_output/canny_solidWhiteCurve.jpg "Canny"
[Houghed]: ./test_images_output/houghed_solidWhiteCurve.jpg "Houghed"
[Weighted]: ./test_images_output/weighted_solidWhiteCurve.jpg "weighted"
[Draw-line]: ./test_images_output/draw-line_solidWhiteCurve.jpg "Draw-line"


## Reflection

### 1. Pipeline description

To achieve the objective of this project, a Pipeline of 5 steps was
used. The steps were implemented in the following sequence:

1.  **Converting input images to grayscale.** The input images were
    converted to grayscale using the default function given in the
    project template. I did not play with the suggested notes regarding
    saving the image into Black and White as resulted image, show below,
    worked well to achieve the drawing of the line objective.
    ![Grayscale]

2.  **Applying Gaussian filter to the grayscale image.** The Gaussian
    conversion was used to average the pixels in their adjacent areas to
    degrease noise level and improve the gradient different needed for
    the Canny process. A kernel size of 5 provide to be appropriate
    choice to smooths noise and minimizes spurious edges, while keeping
    detail in tricky situations when there is not much contrast in the
    lines.
    ![Gaussian]

3.  **Converting to Canny regional lines.** The resulting
    Gaussian image was converted to Canny space using a `low_threshold =
    50` and `high_threshold = 150`. I experimented with different values,
    but these values give me a good balance of details and low noise. A
    mask was applied to Canny image to preserve only in the lane lines
    edges by setting the everything else to black. The chosen area was
    determinate by a creating a trapezoid, with bottom vertices in the
    corners of the image and top vertices approximately half way in the
    horizon. 
    ![Canny]
    
4.  **Applying Hough Transform.** To detect the lines in the Canny
    image, the helper function hough_lines was executed. This function
    converted the pixels lines in the Canny image to lines segment using
    Hough space transformation, where dots are converted to lines. After
    several tray, the parameters that give better results were:
    `threshold = 3`, `min_line_length = 5`, and `max_line_gap = 20`.
    ![Houghed]

5.  **Fusing Images.** The resulted Hough images fused with the original
    image to provide an image showing the demarked lane lines.
    ![Draw-line]

### 2. Identify potential shortcomings with your current pipeline

The pipeline in my project accomplished satisfactory results for the
test images and two sample videos. However, it was not capable to work
out the curves in the given **Optional Challenge video** as the pipeline
was made for straight lines only. To result this challenge a curve, I
believe that a curve fit will provide the result needed.

Some of the potential shortcoming of the pipeline in my project that I
can think of are

-   Eroded or old-painted lines.

-   Blocking of lines by traffic.

-   Illumination conditions, specially at dusk or night.

-   Variable illumination, including other vehicles lights.

-   Snow, ice, and/or dust

-   Closed low radius curves.

### 3. Suggest possible improvements

Most of the parameters in my pipeline were hardcoded. This can create
issues for the Canny Edges detection and the Hough Transform functions
under different conditions not tested in this pipeline. I believe that
there are not a single set of find parameters that will suit all
possible situations. My proposal consists of coding an optimization
algorithm that compensated the intensity of light, similar to the
professional photo cameras, to compensate for outlier sources of light.
This suggestion is an idea to be tested with not warranty that will
work.
