# EN3160 — Assignment 1: Intensity Transformations and Neighborhood Filtering

**Course:** EN3160 — Image Processing and Machine Vision
**Student:** Maldeniyap.a.d.g.r.
**Index Number:** 230390A

## Overview

This assignment covers two core areas of digital image processing:

1. **Intensity (point) transformations** — operations that map each pixel's intensity
   to a new value independently of its neighbors, including piecewise-linear
   transformations, gamma correction, vibrance/saturation adjustment, and histogram
   equalization.
2. **Neighborhood (spatial) filtering** — operations where each output pixel depends on
   a local neighborhood of input pixels, including Sobel edge detection, image
   resampling (zooming), foreground/background segmentation, and edge-preserving
   smoothing with the bilateral filter.

All implementations are done in Python using OpenCV, NumPy, and Matplotlib, with several
algorithms (histogram equalization, bilateral filtering, image zooming) implemented
from scratch rather than relying purely on built-in library functions.


## Questions

### Q1 — Piecewise-Linear Intensity Transformation
Implements a general `intensity_transform(im, breakpoints)` function that builds a
256-entry lookup table (LUT) by linearly interpolating between user-supplied
breakpoints, then applies it to a grayscale portrait image. Explores different
breakpoint sets to find a visually pleasing contrast enhancement.

### Q2 — Accentuating White Matter / Gray Matter in an MRI Slice
Applies two different piecewise-linear transformations to a brain proton-density MRI
slice: one that stretches the high-intensity band to emphasize white matter, and
another that stretches the mid-intensity band to emphasize gray matter, guided by the
image's intensity histogram.

### Q3 — Gamma Correction in L\*a\*b\* Color Space
Converts an image to the L\*a\*b\* color space and applies gamma correction to the L
(lightness) channel only, preserving color (a\*, b\*) while recovering shadow/highlight
detail. Reports the gamma value used and compares histograms before/after correction.

### Q4 — Vibrance Enhancement via HSV Saturation
Splits an image into hue, saturation, and value planes, then applies a Gaussian-bump
intensity transformation `f(x) = min(x + a·128·e^(−(x−128)²/2σ²), 255)` to the
saturation plane to boost mid-saturation pixels more than already-vivid or gray ones —
a "vibrance" effect rather than a flat saturation boost. Reports the chosen value of `a`.

### Q5 — Histogram Equalization (From Scratch)
Implements histogram equalization manually (histogram → CDF → normalized LUT) without
using `cv2.equalizeHist`, and compares histograms before and after equalization.

### Q6 — Foreground-Only Histogram Equalization
Splits an image into HSV planes, thresholds an appropriate plane to build a binary
foreground mask, computes the histogram/CDF of the masked foreground only, equalizes
just the foreground, and recombines it with the untouched background.

### Q7 — Sobel Edge Detection (Three Ways)
Computes the Sobel gradient of an image three different ways: (a) using
`cv2.filter2D` with the full 3×3 kernel, (b) a from-scratch manual convolution, and
(c) exploiting the separability of the Sobel kernel into a smoothing column vector
`[1,2,1]ᵀ` and a differencing row vector `[1,0,−1]`. Verifies all three produce
(numerically) identical results.


and computing the normalized sum-of-squared-differences (SSD) against the original
large images.

### Q9 — GrabCut Segmentation and Background Blur
Uses `cv2.grabCut` to segment a flower image into foreground and background, then
composites a heavily Gaussian-blurred background with the sharp foreground to simulate
a shallow depth-of-field (bokeh) effect. Discusses why a dark halo appears just beyond
the flower's edge due to the hard segmentation mask.

### Q10 — Bilateral Filtering: OpenCV vs. From-Scratch
Applies `cv2.bilateralFilter` to smooth an image while preserving edges, compares it
against a similarly-sized Gaussian blur, then implements a bilateral filter from
scratch and quantitatively compares it (via normalized SSD) against OpenCV's built-in
version.

