# Surface Crack Detection using Custom Canny Algorithm 🔍🏗️

This repository contains a complete Computer Vision pipeline for the automated detection, isolation, and measurement of surface cracks in construction materials (e.g., concrete, asphalt, painted surfaces). 

The goal of this project is to replace subjective human visual inspections with exact, quantitative pixel measurements, ultimately improving structural safety and automation.

## 🚀 Key Features & Approach

Instead of relying on black-box functions like `cv2.Canny()`, we **built the Canny Edge Detection mathematical pipeline from scratch** using `NumPy` and `OpenCV`. This allowed us to perform deep hyperparameter tuning and conquer high-noise environments (such as porous concrete or transparent image watermarks).

The pipeline consists of:
1. **Spatial Filtering:** Gaussian Blur applied dynamically depending on the surface texture.
2. **Gradient Calculation:** Applying the **Sobel Operator** to compute edge magnitude and direction.
3. **Non-Maximum Suppression (NMS):** Mathematical thinning of thick edges down to a strict 1-pixel width by analyzing 8-connected neighborhoods.
4. **Vectorized Double Thresholding:** Implementing dynamic, relative thresholds based on the maximum gradient (`max_gradient * 0.15`) instead of static intensity numbers.
5. **Hysteresis:** Connecting weak edges only if they intersect with strong structural edges.
6. **Morphological Operations:** Dilation and Closing applied to connect fragmented crack segments.
7. **Geometric Filtering:** A custom logic layer that removes false positives (noise, watermarks, oil stains) by analyzing **Minimum Perimeter** and **Circularity** (`C < 0.2`).

## Tech Stack
* **Python 3**
* **OpenCV** (Spatial processing and contours)
* **NumPy** (Vectorized matrix operations and mathematical logic)
* **Matplotlib** (Data visualization)

## Repository Structure
* `Surface_Crack_Detection.ipynb`: The main Jupyter/Colab notebook containing the step-by-step implementation and algorithms.
* `Surface_Crack_Detection.html`: An exported HTML version of the notebook for quick viewing of the code and output images without running the environment.
* `test_images/`: A directory containing the baseline and challenging images used for testing (e.g., heavily watermarked surfaces, highly branched cracks).

## Authors
Developed by **Andra Aflorei** & **Sabina Aflorei** as part of the *Digital Video Analysis Techniques* university project.
