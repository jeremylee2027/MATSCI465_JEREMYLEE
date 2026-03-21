# Data Efficiency in Deep Learning for TEM Nanoparticle Segmentation

## Overview

This project investigates the data efficiency of deep learning for segmenting nanoparticles in transmission electron microscopy (TEM) images. Specifically, it compares a classical image processing pipeline with a U-Net convolutional neural network trained on manually annotated segmentation masks.

The primary goal is to determine how segmentation performance improves as the number of labeled training images increases, and to identify the point at which a learning-based approach becomes more effective than classical methods.

---

## Key Questions

* How does segmentation accuracy scale with labeled data?
* When does a U-Net model outperform classical image processing?
* What is the tradeoff between annotation effort and model performance?

---

## Dataset

The dataset consists of grayscale TEM images containing nanoscale particles.

* Particles appear as dark regions on a lighter background
* Ground truth masks were manually created using Fiji
* Each mask is binary (particle = 1, background = 0)

### Folder Structure

```
data/
├── 30_images/
├── 30_labels/
├── 40_images/
├── 40_labels/
├── 50_images/
└── 50_labels/
```

---

## Methods

### 1. Classical Segmentation Pipeline

The baseline approach uses standard image processing techniques:

* Gaussian blur (noise reduction)
* CLAHE (contrast enhancement)
* Otsu thresholding (binary segmentation)
* Morphological operations (cleanup)
* Distance transform + watershed (particle separation)

---

### 2. Deep Learning (U-Net)

A U-Net convolutional neural network was implemented in PyTorch.

* Encoder-decoder architecture with skip connections
* Input: TEM image
* Output: pixel-wise probability mask
* Loss: segmentation error vs Fiji ground truth
* Training performed across varying dataset sizes

---

## Evaluation Metrics

### Intersection over Union (IoU)

Measures overlap between prediction and ground truth:

[
IoU = \frac{|Prediction \cap GroundTruth|}{|Prediction \cup GroundTruth|}
]

### Dice Coefficient

Measures similarity between masks:

[
Dice = \frac{2|Prediction \cap GroundTruth|}{|Prediction| + |GroundTruth|}
]

* IoU is the primary metric
* Dice is used as a supplementary validation metric

---

## Results Summary

* Performance improves rapidly with small increases in labeled data
* Gains plateau as dataset size increases
* Variability (error bars) is highest for small datasets

### Dataset Comparisons

* **30 images:** Classical method outperforms U-Net
* **40 images:** Break-even point observed (~7–8 labeled images)
* **50 images:** U-Net consistently outperforms classical baseline

### Key Insight

Deep learning requires an initial annotation investment but becomes more effective once sufficient labeled data is available.

---

## Break-even Analysis

The break-even point is defined as the number of labeled images required for the U-Net model to match or exceed classical performance.

* Estimated break-even: ~7.3 labeled images (40-image subset)
* Calculated using interpolation of IoU learning curves
* Converted to **Total Annotation Time (TAT)** using average labeling time per image

This provides a practical interpretation of when deep learning becomes worthwhile.

---

## Repository Structure

```
project/
├── notebooks/
│   ├── preprocessing.ipynb
│   ├── classical_pipeline.ipynb
│   ├── train_unet.ipynb
│   └── evaluation.ipynb
│
├── outputs/
│   ├── plots/
│   ├── qualitative_examples/
│   └── tables/
│
├── data/
│   └── (image + label folders)
│
├── README.md
└── requirements.txt
```

---

## How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Run pipeline

* Run preprocessing and classical pipeline notebook
* Train U-Net model using selected dataset size
* Evaluate results and generate plots

---

## Requirements

* Python 3.8+
* PyTorch
* NumPy
* OpenCV
* scikit-image
* matplotlib

---

## Limitations

* Dataset contains relatively uniform particle shapes
* Classical pipeline parameters are fixed (not optimized per image)
* Annotation quality may introduce variability

---

## Future Work

* Test on more complex datasets (varying contrast, irregular shapes)
* Explore data augmentation to improve performance with small datasets
* Compare with alternative architectures (e.g., Mask R-CNN)

---

## Author

Jeremy Lee
Materials Science and Engineering
Northwestern University

---

## Acknowledgments

* Fiji (ImageJ) for annotation tools
* PyTorch for deep learning framework
