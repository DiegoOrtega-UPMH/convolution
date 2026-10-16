# Interactive Convolution Lab

Author: Diego Ortega  
Student ID: 263220012

## Overview

This standalone web page demonstrates how convolution kernels transform an image. It is built with HTML, CSS, and JavaScript and requires no dependencies or build step.

## How to Use

Open `index.html` in a modern browser. The page starts with a sample image and also lets you upload an image, which is fitted into a 200 × 200 pixel workspace.

1. Choose a filter from the **Kernel** menu.
2. Select a pixel in the image to inspect its 3 × 3 neighborhood.
3. Use **Animate calculation** or the slider to reveal the products and the calculated value for the center pixel.
4. Edit the kernel coefficients to try different weights. Modified values reset to their defaults when you switch filters.
5. Select **Apply** to show the filtered image, or **Original** to restore the source image.
6. Use **Kernel scan** to apply the filter across the image. Choose a 1- or 2-pixel step, set a speed up to 5000x, and pause or resume the scan. A 2-pixel step produces an output with half the width and height.

The interface is available in English and Spanish. The selected language is saved in the browser's local storage.

## Filters

The page includes 21 filters:

- **Identity** leaves the image unchanged.
- **Blur** averages the center pixel and its eight neighbors equally, then divides by 9.
- **Gaussian blur** gives the center pixel more weight and divides by 16.
- **Sharpen**, **Edge detection**, and **Local contrast** emphasize details and brightness changes using positive and negative coefficients.
- **Sobel**, **Prewitt**, **Scharr**, and **Basic gradient** detect vertical or horizontal edges with different weights and levels of smoothing.
- **Motion blur** averages pixels along horizontal, vertical, or diagonal directions.
- **Emboss** adds directional shading.
- **Grayscale** combines the red, green, and blue channels of the same pixel.
- **Black edges · white background** compares the center luminance with its eight neighbors. It divides the response magnitude by 8; values at or above the threshold of 20 become black, and lower values become white.

## Calculation

Spatial filters use a 3 × 3 matrix. Each coefficient multiplies the corresponding pixel color-channel value, and the products are added. Where applicable, a divisor normalizes the result; gradient filters can use the absolute response to detect either edge direction. Output values are clamped to the range 0 to 255.

The animation shows the neighborhood luminance values, coefficients, partial products, running sum, and value written to the output pixel beneath the kernel center. Every calculation uses the original image.
