
# MAT_SCI 465: Week 03 & 04 Assignment Results
## Classical → ML → Unsupervised Learning for Microscopy Analysis

### Dataset: DOPAD (Dataset Of nanoPArticle Detection)
- 272 TEM images (~1.5M particles total)
- Used: 100 images for analysis
- Resolution: 416×416 pixels
- Citation: Qu et al. - https://dopad.github.io/

---

## TASK 1: Classical Image Analysis Pipeline

### Methodology
1. Noise Reduction: Median filtering
2. Contrast Enhancement: CLAHE (clip limit 0.025)
3. Segmentation: Otsu threshold + Watershed
4. Quantification: 11 morphological features per particle

### Key Results
- Example particles detected (single image): 367
- Total regions analyzed (100 images): 102,362
- SNR before filtering: 4.8529
- SNR after filtering: 3.4510
- Runtime: ~50 ms per image
- Outputs:
  - classical_results.csv
  - classical_pipeline_figure.png

---

## TASK 2: Machine Learning Approaches

### Supervised Learning

- SVM (RBF kernel)
  - F1-Score: 0.9944

- Random Forest (100 trees)
  - F1-Score: 1.0000
  - Best performing supervised model

- Top Features (7 selected):
  area, equiv_diameter, perimeter, compactness,
  circularity, edge_ratio, eccentricity

### Unsupervised Learning

- K-Means tested: k ∈ {3, 5, 7}
- Best cluster: k = 7
- Best Silhouette Score: 0.3037
- Visualization: PCA projection

### Output Files
- ml_results.csv
- ml_confusion_matrices.png
- kmeans_pca_visualization.png

---

## TASK 3: Final Comparison

| Method          | Score    | Data Required |
|---------------|----------|---------------|
| Watershed     | 2.3068   | Single image  |
| SVM           | 0.9944   | 100+ samples  |
| Random Forest | 1.0000   | 100+ samples  |
| K-Means       | 0.3037   | 100+ samples  |

### Summary

- Images processed: 100
- Total regions analyzed: 102,362
- Top ML model: Random Forest (F1 = 1.0000)
- Best clustering: k = 7 (Silhouette = 0.3037)

---

## Recommendations

1. Quick morphology screening → Watershed
2. Classification tasks → Random Forest
3. Exploratory structure analysis → K-Means
4. Production workflow → Hybrid classical + ML

---

## Files Generated

### Data
- classical_results.csv
- ml_results.csv
- method_comparison.csv

### Visualizations
- classical_pipeline_figure.png
- ml_confusion_matrices.png
- kmeans_pca_visualization.png
- final_3x3_visualization.png

---

Course: MAT_SCI 465  
Institution: Northwestern University  
Date: February 2026
