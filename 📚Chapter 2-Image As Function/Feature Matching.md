# Feature Matching

How can we match detected features from one image to another?  
Feature matching involves comparing key attributes in different images to find similarities.

Feature matching is useful in many computer vision applications, including:
- Scene understanding
- Image stitching
- Object tracking
- Pattern recognition

---

# Brute-Force Search

Imagine you have a giant box of puzzle pieces, and you’re trying to find a specific piece that fits into your puzzle.

This is similar to searching for matching features in images.

Instead of having any special strategy, you decide to check every piece, one by one, until you find the right one. This straightforward method is a **brute-force search**.

The advantage of brute force is its simplicity. You don’t need any special tricks — just patience.

However, it can be time-consuming, especially if there are a lot of pieces to check.

In the context of feature matching, this brute-force approach is akin to comparing every pixel in one image to every pixel in another to see if they match.

It’s exhaustive, and it might take a lot of time, especially for large images.

---

# Install and Import Libraries

```python
!pip install opencv-python
```

```python
import cv2
import numpy as np
```

---

# Brute Force with SIFT

## Initialize SIFT Detector

```python
sift = cv2.SIFT_create()
```

## Find Keypoints and Descriptors

```python
kp1, des1 = sift.detectAndCompute(img1, None)
kp2, des2 = sift.detectAndCompute(img2, None)
```

## Find Matches Using k-Nearest Neighbors

```python
bf = cv2.BFMatcher()
matches = bf.knnMatch(des1, des2, k=2)
```

## Apply Ratio Test

```python
good = []

for m, n in matches:
    if m.distance < 0.75 * n.distance:
        good.append([m])
```

## Draw the Matches

```python
img3 = cv2.drawMatchesKnn(
    img1,
    kp1,
    img2,
    kp2,
    good,
    None,
    flags=cv2.DrawMatchesFlags_NOT_DRAW_SINGLE_POINTS
)
```

---

# Brute Force with ORB (Binary Descriptors)

## Initialize ORB

```python
orb = cv2.ORB_create()
```

## Find Keypoints and Descriptors

```python
kp1, des1 = orb.detectAndCompute(img1, None)
kp2, des2 = orb.detectAndCompute(img2, None)
```

Because ORB is a binary descriptor, we use **Hamming Distance** to compare descriptors.

Hamming distance measures the difference between two binary strings of equal length.

## Create Brute Force Matcher

```python
bf = cv2.BFMatcher(cv2.NORM_HAMMING, crossCheck=True)
```

## Find Matches

```python
matches = bf.match(des1, des2)
```

## Sort Matches by Distance

```python
matches = sorted(matches, key=lambda x: x.distance)
```

## Draw Best Matches

```python
img3 = cv2.drawMatches(
    img1,
    kp1,
    img2,
    kp2,
    matches[:n],
    None,
    flags=cv2.DrawMatchesFlags_NOT_DRAW_SINGLE_POINTS,
)
```

---

# Fast Library for Approximate Nearest Neighbors (FLANN)

FLANN stands for:

**Fast Library for Approximate Nearest Neighbors**

It was proposed in:

> *Fast Approximate Nearest Neighbors With Automatic Algorithm Configuration*  
> by Muja and Lowe.

---

## Intuition Behind FLANN

Let’s continue with the puzzle example.

Imagine a giant puzzle with hundreds of pieces scattered around.

Instead of randomly checking every piece against every other piece, FLANN uses clever shortcuts to quickly figure out which pieces are likely to fit together.

FLANN does not always search for exact matches.

Instead, it searches for **approximately similar** matches, which makes the process much faster.

---

# k-D Trees in FLANN

Under the hood, FLANN uses something called a **k-D tree**.

Think of it as organizing puzzle pieces into smart groups.

Pieces with similar shapes or colors are placed together.

So when you search for a match:
- you don’t search the entire puzzle
- you only search the relevant group

This dramatically improves speed.

---

# FLANN Parameters for SIFT or SURF

```python
FLANN_INDEX_KDTREE = 1

index_params = dict(
    algorithm=FLANN_INDEX_KDTREE,
    trees=5
)
```

---

# FLANN Parameters for ORB

```python
FLANN_INDEX_LSH = 6

index_params = dict(
    algorithm=FLANN_INDEX_LSH,
    table_number=12,
    key_size=20,
    multi_probe_level=2
)
```

---

# Search Parameters

```python
search_params = dict(checks=50)
```

---

# FLANN with SIFT

## Initialize SIFT

```python
sift = cv2.SIFT_create()
```

## Find Keypoints and Descriptors

```python
kp1, des1 = sift.detectAndCompute(img1, None)
kp2, des2 = sift.detectAndCompute(img2, None)
```

## Define FLANN Parameters

```python
FLANN_INDEX_KDTREE = 1

index_params = dict(
    algorithm=FLANN_INDEX_KDTREE,
    trees=5
)

search_params = dict(checks=50)
```

## Create FLANN Matcher

```python
flann = cv2.FlannBasedMatcher(index_params, search_params)
```

## Find Matches

```python
matches = flann.knnMatch(des1, des2, k=2)
```

## Create Match Mask

```python
matchesMask = [[0, 0] for i in range(len(matches))]
```

## Ratio Test

```python
for i, (m, n) in enumerate(matches):
    if m.distance < 0.7 * n.distance:
        matchesMask[i] = [1, 0]
```

## Visualize Matches

```python
draw_params = dict(
    matchColor=(0, 255, 0),
    singlePointColor=(255, 0, 0),
    matchesMask=matchesMask,
    flags=cv2.DrawMatchesFlags_DEFAULT,
)

img3 = cv2.drawMatchesKnn(
    img1,
    kp1,
    img2,
    kp2,
    matches,
    None,
    **draw_params
)
```

---

# Local Feature Matching with Transformers (LoFTR)

LoFTR was proposed in:

> *LoFTR: Detector-Free Local Feature Matching with Transformers*  
> by Sun et al.

Unlike traditional methods, LoFTR uses a **deep learning-based approach** instead of handcrafted feature detectors.

---

# Understanding LoFTR Intuitively

Imagine solving a puzzle again.

Instead of manually checking edges or corners, LoFTR learns what good matches look like directly from data.

It identifies:
- landmarks
- corners
- edges
- important structures

And it can still recognize them even if:
- the image is rotated
- resized
- viewed from another angle
- captured under different lighting

---

# Install Dependencies

```python
!pip install kornia kornia-rs kornia_moons opencv-python --upgrade
```

---

# Import Libraries

```python
import cv2
import kornia as K
import kornia.feature as KF
import matplotlib.pyplot as plt
import numpy as np
import torch

from kornia_moons.viz import draw_LAF_matches
```

---

# Load and Resize Images

```python
from kornia.feature import LoFTR

img1 = K.io.load_image(
    "image1.jpg",
    K.io.ImageLoadType.RGB32
)[None, ...]

img2 = K.io.load_image(
    "image2.jpg",
    K.io.ImageLoadType.RGB32
)[None, ...]

img1 = K.geometry.resize(
    img1,
    (512, 512),
    antialias=True
)

img2 = K.geometry.resize(
    img2,
    (512, 512),
    antialias=True
)
```

---

# Initialize LoFTR

Choose whether the images are:
- indoor
- outdoor

```python
matcher = LoFTR(pretrained="outdoor")
```

---

# Convert Images to Grayscale

LoFTR works on grayscale images.

```python
input_dict = {
    "image0": K.color.rgb_to_grayscale(img1),
    "image1": K.color.rgb_to_grayscale(img2),
}
```

---

# Run Inference

```python
with torch.inference_mode():
    correspondences = matcher(input_dict)
```

---

# Clean Correspondences with RANSAC

RANSAC helps remove noisy or incorrect matches.

```python
mkpts0 = correspondences["keypoints0"].cpu().numpy()
mkpts1 = correspondences["keypoints1"].cpu().numpy()

Fm, inliers = cv2.findFundamentalMat(
    mkpts0,
    mkpts1,
    cv2.USAC_MAGSAC,
    0.5,
    0.999,
    100000
)

inliers = inliers > 0
```

---

# Visualize LoFTR Matches

```python
draw_LAF_matches(
    KF.laf_from_center_scale_ori(
        torch.from_numpy(mkpts0).view(1, -1, 2),
        torch.ones(mkpts0.shape[0]).view(1, -1, 1, 1),
        torch.ones(mkpts0.shape[0]).view(1, -1, 1),
    ),

    KF.laf_from_center_scale_ori(
        torch.from_numpy(mkpts1).view(1, -1, 2),
        torch.ones(mkpts1.shape[0]).view(1, -1, 1, 1),
        torch.ones(mkpts1.shape[0]).view(1, -1, 1),
    ),

    torch.arange(mkpts0.shape[0]).view(-1, 1).repeat(1, 2),

    K.tensor_to_image(img1),
    K.tensor_to_image(img2),

    inliers,

    draw_dict={
        "inlier_color": (0.1, 1, 0.1, 0.5),
        "tentative_color": None,
        "feature_color": (0.2, 0.2, 1, 0.5),
        "vertical": False,
    },
)
```

The best matches are shown in green, while uncertain matches are shown in blue.

---

# Resources and Further Reading

- FLANN Github
- OpenCV Github
- LoFTR Github
- Kornia Tutorial on Image Matching
- OpenCV Feature Matching Tutorial
- ORB (Oriented FAST and Rotated BRIEF) Tutorial
- OpenGlue: Open Source Graph Neural Net Based Pipeline for Image Matching
- Image Matching Using SIFT, SURF, BRIEF and ORB: Performance Comparison for Distorted Images
