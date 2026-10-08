# Cattle Breed Recognition with Imbalance Analysis

This project investigates image-based recognition of five indigenous Indian cattle breeds using a Simple Convolutional Neural Network (CNN) and MobileNetV2 transfer learning.

## Project Overview

The study focuses on cattle breed classification and examines how class imbalance affects classification performance. The five selected cattle breeds are:

- Bargur
- Gir
- Hallikar
- Ongole
- Tharparkar

The dataset contains 7,226 labelled cattle images.

## Dataset

The study uses the **Annotated Multiview Image Dataset of Prominent Indigenous Indian Cattle Breeds (IICBD)** from Mendeley Data.

Dataset DOI:

`10.17632/xc3j9v382w.1`

The dataset is publicly available from Mendeley Data.

The class distribution used in this study is:

| Breed | Images |
|---|---:|
| Bargur | 470 |
| Gir | 3,648 |
| Hallikar | 1,951 |
| Ongole | 343 |
| Tharparkar | 814 |
| **Total** | **7,226** |

## Models

Two image-classification approaches were evaluated:

1. **Simple CNN baseline**
2. **MobileNetV2 transfer learning**

MobileNetV2 used pretrained ImageNet features, with the feature-extraction layers frozen and a new five-class classification layer trained for the cattle-breed task.

## Experimental Setup

- Image size: `224 × 224`
- Optimizer: Adam
- Learning rate: `0.001`
- Loss function: Cross-Entropy Loss
- Training epochs: 5
- Training augmentation: random horizontal flipping and rotation up to ±10°
- Evaluation: held-out test set
- GPU: NVIDIA GeForce RTX 3050 Laptop GPU, 4 GB

The final dataset partitions contained:

- Training: 5,009 images
- Validation: 1,036 images
- Test: 1,181 images

## Results

| Model | Test Accuracy | Macro F1 |
|---|---:|---:|
| Simple CNN | 63.25% | 47.61% |
| MobileNetV2 | 98.73% | 98.08% |

MobileNetV2 substantially outperformed the Simple CNN under the experimental conditions of this study.

The study also evaluates per-breed recall to examine the effect of the imbalanced class distribution.

## Reproducibility

The repository contains the source code and supporting files required to reproduce the experiments.

The cattle image dataset is not included in this repository. Users should obtain the dataset from the original Mendeley Data source and arrange the images according to the dataset structure described in the project documentation.

## Research Questions

The study investigates:

1. What is the accuracy of classification of the five selected cattle breeds from the presented images?
2. How does the image-classification baseline compare to the transfer-learning model?
3. How does the class imbalance affect the classification results for the five cattle breeds?
4. Which cattle breeds were recognized with the highest and lowest recall?
5. Does the quantity of images influence the quality of classification for each breed?
6. Is there an improvement in the recognition of minority classes with transfer learning compared to the baseline?

## Limitations

The experiments used one training run per model and did not include dedicated robustness testing or detailed explainability analysis. The MobileNetV2 feature-extraction layers were frozen rather than fine-tuned. Grouping information was not available at the same level for all five breeds, so complete elimination of all possible near-duplicate or source-related leakage cannot be guaranteed.

## Reference

Kam, K., Mohamed Mansoor Roomi, S., & Shanmugavadivu, P. (2026). *Annotated Multiview Image Dataset of Prominent Indigenous Indian Cattle Breeds*. Mendeley Data. https://doi.org/10.17632/xc3j9v382w.1
