# Computer Vision Roadmap — Beginner to Advanced

This document is the canonical, ordered learning roadmap for the Computer-Vision repository. Use this as a course index: follow module-by-module, complete the exercises, and use linked notebooks/projects to build a portfolio.

---

## How to use this roadmap
- Follow modules in order. Each module lists objectives, key topics, recommended exercises/projects, and suggested resources.
- Estimated time is guidance only (depends on prior experience).
- After each major module, build the suggested project to consolidate learning.
- Keep a learning log (notebook) with links to code, datasets, metrics, and short reflections.

---

## Quick overview (high-level syllabus)
1. Foundations (Prerequisites)
2. Classical Computer Vision
3. Geometry, Multi-view & Motion
4. Machine Learning for Vision
5. Deep Learning Foundations
6. Object Detection & Segmentation
7. Advanced Architectures & Methods
8. 3D, Neural Rendering & Video
9. Evaluation, Robustness & Interpretability
10. Deployment, Optimization & Production
11. Research & Cutting-edge Topics
12. Capstone Projects & Portfolio

---

## Module A — Foundations (1–3 weeks)
Objective: Prepare the math and tooling baseline.
- Key topics:
  - Python, NumPy, Matplotlib
  - Image basics: color spaces, bit-depth, sampling
  - Linear algebra refresher: vectors, matrices, dot products
  - Basic calculus: derivatives, gradients (intuitive)
- Exercises / Projects:
  - Implement image I/O, channel split/merge, display histograms
  - Small notebook: pixel indexing & image statistics
- Suggested resources:
  - NumPy quickstart, CS231n first lectures, Szeliski (selected chapters)

---

## Module B — Classical Computer Vision (2–4 weeks)
Objective: Learn filtering, feature detection and early vision algorithms.
- Key topics:
  - Convolution, correlation, separability
  - Spatial filters: mean, median, Gaussian, bilateral
  - Edges & gradients: Sobel, Prewitt, Canny
  - Morphology: erosion, dilation, opening/closing
  - Feature detectors/descriptors: Harris, SIFT, SURF, ORB
  - Matching: brute-force, FLANN, RANSAC
- Exercises / Projects:
  - Build an edge-based lane detector and tracker
  - Feature matching panorama with homography
- Tools / Notebooks:
  - OpenCV tutorials, notebooks in `notebooks/classical/`

---

## Module C — Geometry, Multi-view & Motion (2–4 weeks)
Objective: Reason about 3D geometry and motion from images.
- Key topics:
  - Pinhole camera model, intrinsics, extrinsics
  - Epipolar geometry, essential & fundamental matrices
  - Stereo vision: disparity, depth maps
  - Optical flow: Lucas-Kanade, Horn-Schunck
  - RANSAC for robust estimation, basic bundle adjustment intuition
- Exercises / Projects:
  - Compute disparity map & visualize depth point cloud
  - Use optical flow for motion segmentation on video
- Resources:
  - Hartley & Zisserman chapters, OpenCV stereo/flow tutorials

---

## Module D — Machine Learning for Vision (2–4 weeks)
Objective: Apply classic ML approaches to image problems.
- Key topics:
  - Feature extraction (HOG, LBP), bag-of-visual-words
  - Classifiers: SVM, k-NN, decision trees
  - Model selection, cross-validation, metrics
- Exercises / Projects:
  - HOG + SVM classifier for a small dataset (e.g., pedestrian vs background)
- Tools:
  - scikit-learn, skimage

---

## Module E — Deep Learning Foundations (3–6 weeks)
Objective: Build, train and evaluate convolutional neural networks.
- Key topics:
  - NN basics: backprop, SGD, Adam, regularization
  - CNN building blocks: conv, pooling, batchnorm, activations
  - Transfer learning & fine-tuning (ResNet, EfficientNet)
  - Data augmentation,
