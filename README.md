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
from scratch rather than relying pure