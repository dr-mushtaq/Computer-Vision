##  A. Foundations (prerequisites — 1–3 weeks)

Objectives: get comfortable with Python, NumPy, basic linear algebra and calculus, image basics.
Topics
Python & NumPy array ops, plotting images, I/O, image coordinate systems
Linear algebra refresher (vectors, matrices, eigenvalues), basic calculus (derivatives)
Basics of digital images: color spaces, bit-depth, sampling, quantization
Exercises / projects
Implement grayscale conversion, histogram, pixel statistics, simple filters (mean, median)
Short notebook: image I/O, show channels and pixel indexing
Resources: NumPy docs, Stanford CS231n primer chapters, Szeliski book (selected chapters)
B. Classical Computer Vision (2–4 weeks)
Objectives: understand image filtering, feature detection, geometry, and early vision.
Topics
Linear and nonlinear filters, convolution/correlation, separability
Gradients, Sobel, Canny edge detector
Image morphology (erode/dilate), contours
Template matching, correlation, normalized cross-correlation
Feature detectors & descriptors: Harris, SIFT, SURF (theory + OpenCV usage), ORB
Matching, RANSAC and homography, basic panorama stitching
Exercises / projects
Build an edge-based lane detector
Feature match two images and compute homography to warp/panorama
Resources: OpenCV tutorials, Szeliski & Forsyth, OpenCV implementation notebooks
C. Geometry, Multi-view, and Motion (2–4 weeks)
Objectives: geometric reasoning about 3D and motion in images
Topics
Camera model, pinhole camera, intrinsic/extrinsic matrices
Epipolar geometry, essential/fundamental matrix
Stereo vision basics, disparity maps, depth from stereo
Optical flow (Lucas-Kanade, Horn-Schunck), tracking basics
Structure-from-motion (intro)
Projects
Implement stereo disparity with block matching; visualize point cloud
Compute dense optical flow and use it for motion segmentation
Resources: Hartley & Zisserman (chapters), OpenCV stereo & flow tutorials
D. Machine Learning for Vision (2–4 weeks)
Objectives: apply classical ML and basic ML workflows to image tasks
Topics
Feature vectors from images, SVMs, k-nearest neighbors, decision trees
Feature engineering, HOG descriptors, bag-of-visual-words
Train/val/test splits, metrics, cross-validation for images
Projects
Build a simple classifier using HOG + SVM on a small dataset
Resources: scikit-learn tutorials, HOG papers
E. Deep Learning Foundations (3–6 weeks)
Objectives: understand CNNs, training pipelines, and implement basic models.
Topics
Neural network basics, backpropagation, optimizers, regularization
Convolutional Neural Networks: conv, pooling, batchnorm, ReLU
Transfer learning, fine-tuning pre-trained networks (ResNet, EfficientNet)
Training best practices: learning rates, schedulers, augmentation, mixed precision
Experiment tracking and reproducibility (W&B, TensorBoard)
Projects
Train a classifier on CIFAR-10 or a custom dataset with transfer learning and augmentation
Notebook: hyperparameter sweep using Optuna
Resources: PyTorch tutorials, FastAI course, CS231n, official docs
F. Object Detection & Segmentation (3–6 weeks)
Objectives: learn detection/segmentation tasks and frameworks.
Topics
Detection paradigms: two-stage (Faster R-CNN) vs one-stage (YOLO/SSD)
Anchor boxes, NMS, AP/mAP metrics
Instance segmentation (Mask R-CNN), semantic segmentation (U-Net, DeepLab)
Keypoint detection and pose estimation
Tools: Detectron2, MMDetection, Ultralytics YOLO
Projects
Fine-tune YOLO/Detectron2 on a small custom dataset with Roboflow
Build a segmentation model (U-Net) for a simple medical or road dataset
Resources: Ultralytics docs, Detectron2 examples, Roboflow tutorials
G. Advanced Architectures & Methods (4–8 weeks)
Objectives: study modern SOTA architectures and learning paradigms.
Topics
Vision Transformers (ViT, DeiT), hybrid CNN+Transformer models
Self-supervised learning (SimCLR, MoCo, DINO), contrastive learning
Metric learning (triplet loss, ArcFace, circle loss) — for re-ID
Attention modules, multi-scale features, FPNs
Generative models: VAEs, GANs, Diffusion models (DDPM)
Projects
Pretrain a small model with contrastive learning on an unlabeled dataset
Implement ViT for classification on a subset of ImageNet
Resources: original ViT/DINO/SimCLR papers, Hugging Face tutorials
H. 3D, NeRF, Video & Multi-modal (4–8 weeks)
Objectives: extend skills to 3D reconstruction, neural rendering, and video.
Topics
NeRF basics, multi-view rendering
Video understanding, action recognition, 3D CNNs, Transformers for video
Point clouds (PointNet), depth sensing, multi-modal (text+image)
Projects
Create a small NeRF demo (using an open-source NeRF implementation)
Build an action recognition demo with video frames and 3D augmentation
Resources: NeRF papers and tutorials, PyTorchVideo
I. Evaluation, Robustness & Interpretability (ongoing)
Topics
Metrics for classification/detection/segmentation, confusion matrices and ROC/AP curves
Calibration, uncertainty estimation, adversarial robustness, common corruption tests (ImageNet-C)
Interpretability: Grad-CAM, saliency maps, feature space visualization (t-SNE/UMAP)
Projects
Add Grad-CAM visualizations to trained models; benchmark under noise/corruption
J. Deployment, Optimization & Production (2–6 weeks)
Objectives: take models into production and optimize for inference.
Topics
Export formats: TorchScript, ONNX, TFLite
Acceleration: TensorRT, OpenVINO; quantization (PTQ, QAT), pruning
Containerization, inference APIs (FastAPI), CI for model tests, monitoring
Edge deployment considerations (latency/size/power)
Projects
Export a YOLO model to ONNX and run inference with ONNX Runtime
Build a small REST inference service + CI test for endpoint
Resources: ONNX docs, NVIDIA TensorRT guides, PyTorch quantization docs
K. Research & Cutting-edge Topics (ongoing)
Topics
Foundation models, multimodal models (CLIP, Florence), large-scale pretraining
Diffusion models for image generation and editing
Ethics, dataset bias, model cards and responsible AI
Projects
Reproduce a small experiment from a recent paper and write a short report
How your current chapters map to the roadmap (where to move/expand)
Your Chapter 1–11 (Image as function, Filtering, Convolution, Filters as templates, Edge detection, Hough transforms, Fourier) → map to Foundations and Classical CV (B and A).
Add distinct new chapters for:
Deep Learning Foundations (new chapter)
Object Detection & Segmentation (new chapter)
Modern Architectures & Self-Supervised (new chapter)
3D & Video (new chapter)
Deployment & Production (new chapter)
Tools & Practices: DVC, W&B, dataset labeling (new chapter)
Move long per-topic tables out of the README and into:
docs/SUMMARY.md (course index)
docs/chapter-01-foundations.md, docs/chapter-02-filtering.md, etc.
Add a short “learning path” page with suggested time per module and checkpoints (e.g., pass quizzes, build project).
Suggested course projects and milestones (sample curriculum timeline)
0–4 weeks (Beginner): small projects — image filters, edge detection demo, portfolio notebook
4–10 weeks (Intermediate): classification + transfer learning, feature matching panorama, stereo depth
10–20 weeks (Advanced): detection/segmentation project (custom dataset), deployment of model as API, interpretability report
Ongoing: research reproduction or implementation of a recent CV paper
Repo organization & files to add (practical repo changes)
Move README → concise README.md (landing) and add docs/SUMMARY.md with the full roadmap
Create:
docs/SUMMARY.md (course index mapped to roadmap)
docs/chapter-XX-*.md for each chapter (move your big tables)
assets/ (store images and GIFs)
CONTRIBUTING.md, CODE_OF_CONDUCT.md, LICENSE (MIT recommended)
.github/ISSUE_TEMPLATE & PULL_REQUEST_TEMPLATE
requirements.txt or environment.yml for reproducibility
Add a short starter notebook per module (notebooks/01_intro.ipynb, notebooks/05_filters.ipynb)
Next steps I can do for you (pick any)
Generate a polished docs/SUMMARY.md that implements the roadmap and automatically maps your current chapter headings into the new index (I’ll parse the README and create per-chapter stubs).
Create a clean README.md (short landing) and move the long content into docs/ files — open a PR with changes.
Produce a one-page curriculum with weekly schedule and assignments for learners.
Scan the repo for broken links and produce a broken-links report.
Which of these would you like me to do next?
If you want immediate action: I can create docs/SUMMARY.md + a cleaned README.md and open a PR draft for you. Confirm and I’ll produce those files next. Also tell me your target audience (absolute beginners, university students, or intermediate engineers) and preferred framework (PyTorch / TensorFlow / both) so I can tailor the roadmap and examples.

