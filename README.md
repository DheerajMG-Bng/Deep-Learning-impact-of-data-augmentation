#### IIITV

## Retinal Disease Classification Using Deep Learning (Data Augmentation)

### A Systematic Study of Data Augmentation Strategies for Multi-Class Fundus Image Classification
---

## Overview

This project investigates **deep learning–based retinal disease classification** using fundus images and systematically evaluates the **impact of different data augmentation strategies**.

The study was designed to understand how augmentation affects **generalization, class balance, and robustness** in a **multi-class retinal disease dataset (39 classes)**.

Through controlled experiments and statistical validation, the study shows that **classical geometric and photometric augmentation significantly improves performance**, while heavy preprocessing and synthetic image mixing methods may degrade anatomical feature learning.

---

## Project Goals

* Develop a **multi-class retinal disease classification model**
* Evaluate **multiple augmentation strategies**
* Perform **statistical validation** of model performance
* Conduct an **ablation study** to determine the most effective augmentation strategy
* Analyze model performance using **cross-validation and statistical testing**

---

## Dataset

* **Total Images:** 1000
* **Classes:** 39 retinal conditions
* **Image Type:** Retinal Fundus Images
* **Task:** Multi-class classification

Dataset characteristics:

* Class imbalance
* Small dataset size
* Fine-grained disease patterns
* High-resolution medical images

These characteristics make augmentation important for improving model generalization.

---

## Model Architecture

The model uses **DenseNet121 pretrained on ImageNet**.

### Why DenseNet121?

* Efficient feature reuse
* Strong performance in medical imaging tasks
* Dense connectivity improves gradient flow
* Works well on smaller datasets

The classifier layer was modified for **39 disease classes**.

---

## Training Pipeline

### Preprocessing

* Image resizing (224×224)
* Image normalization
* Stratified 5-fold cross-validation

### Optimization

* **Loss:** CrossEntropyLoss
* **Optimizer:** Adam
* **Learning Rate:** 1e-4
* **Regularization:** Weight decay
* **Training:** Early stopping for convergence

---

## Experimental Design

Six augmentation strategies were evaluated.

| Experiment | Method                        |
| ---------- | ----------------------------- |
| Exp 1      | Baseline (No Augmentation)    |
| Exp 2      | Classical Augmentation        |
| Exp 3      | Classical + Noise             |
| Exp 4A     | Classical + MixUp             |
| Exp 5      | Domain-Specific Preprocessing |
| Exp 6      | Domain + Classical            |

All experiments used **5-fold stratified cross-validation**.

---

## Results
<img width="443" height="271" alt="image" src="https://github.com/user-attachments/assets/37d32b07-9454-4c4a-8170-9626a1546c66" />

| Experiment                 | Accuracy  | Macro F1  |
| -------------------------- | --------- | --------- |
| Baseline                   | 0.817     | 0.730     |
| **Classical Augmentation** | **0.876** | **0.836** |
| Classical + Noise          | 0.866     | 0.822     |
| Classical + MixUp          | 0.873     | 0.827     |
| Domain Only                | 0.610     | 0.465     |
| Domain + Classical         | 0.719     | 0.604     |


### Best Performing Strategy

**Classical Geometric + Photometric Augmentation**

---

## Statistical Validation

To ensure scientific reliability, statistical testing was performed.

### Paired t-test

Comparison between Classical Augmentation and Baseline:

* **t = 5.48**
* **p = 0.0054**

This indicates a **statistically significant improvement**.

### ANOVA Test

* **F = 109.73**
* **p < 1e-15**

This confirms significant performance differences among augmentation strategies.

---

## Key Findings

1. Classical geometric and photometric augmentation significantly improves model performance.
2. Artificial noise slightly degrades performance.
3. MixUp does not significantly improve retinal classification.
4. Domain-specific preprocessing alone reduces performance.
5. Controlled augmentation improves generalization and minority class detection.

---

## Ablation Study

The ablation analysis shows that **classical augmentation contributes the most to performance improvements**.

| Component Removed      | Performance Impact      |
| ---------------------- | ----------------------- |
| Classical Augmentation | Major performance drop  |
| MixUp                  | No improvement          |
| Noise Augmentation     | Slight degradation      |
| Domain Preprocessing   | Significant degradation |

---

## Why Augmentation Matters in Medical AI

Beyond accuracy improvement, augmentation provides:

* Improved model generalization
* Better minority class detection
* Reduced overfitting
* Increased robustness to imaging variability
* More stable cross-validation results

---

## Technologies Used

* Python
* PyTorch
* Albumentations
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn

---
