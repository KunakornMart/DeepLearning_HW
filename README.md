# Thai Prime Ministers Face Classification with Transfer Learning

A computer vision project for classifying **former Thai prime ministers** from face images using **transfer learning** and a **custom-built dataset**.

This project was developed as part of **DADS 7202: Deep Learning** and focuses on the full workflow: data collection, dataset design, preprocessing, augmentation, model benchmarking, and visual interpretation.

---

## Overview

The project uses a self-collected and balanced image dataset of **7 Thai prime minister classes**, with **60 images per class** for a total of **420 images**. Images were collected manually, organized by class, and prepared for training and evaluation.

Three pretrained CNN architectures were benchmarked:

- **VGG16**
- **ResNet50**
- **EfficientNetV2B0**

Among the tested models, **EfficientNetV2B0** delivered the best overall results on the held-out test set while also training faster than the larger alternatives.

---

## Dataset

### Classes

The dataset contains 7 classes:

- Abhisit
- Anand
- Chuan
- Paetongtarn
- Prayut
- Thaksin
- Yingluck

### Dataset size

- **Total images:** 420
- **Images per class:** 60
- **Balanced classes:** Yes
- **Image format:** `.jpg` / `.jpeg`
- **Aspect ratio:** cropped to **1:1**

### Split

- **Train set:** 280 images
- **Validation set:** 70 images
- **Test set:** 70 images

The repository structure also reflects the dataset organization, with separate folders for `Prime_Minister_Data` and `Test_Data`.

---

## Data Preparation

The preprocessing workflow included:

- manual image collection and class labeling
- face image curation by category
- resizing to a consistent input format
- train / validation / test separation
- data augmentation using `ImageDataGenerator`

### Augmentation methods

To improve generalization and reduce overfitting, the training pipeline applied:

- horizontal flip
- rotation
- zoom
- contrast adjustment

---

## Model Architectures

This project compares three transfer-learning backbones.

### 1) VGG16
- pretrained CNN with 16-layer feature extractor
- large parameter count
- strong baseline for image classification

### 2) ResNet50
- deeper residual network
- smaller model size than VGG16
- designed to support more stable deep feature learning

### 3) EfficientNetV2B0
- more parameter-efficient architecture
- smaller model size than VGG16 and ResNet50
- strongest overall performance in this benchmark

### Classification head

Each pretrained feature extractor was used with:

1. `Flatten`
2. `Dense(4096, activation='relu')`
3. `Dense(4096, activation='relu')`
4. `Dense(7, activation='softmax')`

---

## Training Setup

All three models were trained under the same configuration for a fair comparison:

- **Optimizer:** Adam
- **Loss function:** SparseCategoricalCrossentropy
- **Initial learning rate:** 0.0005
- **Batch size:** 32
- **Epochs:** 50
- **EarlyStopping:** enabled
- **Input shape:** 224 × 224 × 3

---

## Benchmark Results

### Pretrained model reference

| Model | Model Size | Top-1 Accuracy | Top-5 Accuracy | Parameters |
|---|---:|---:|---:|---:|
| VGG16 | 528 MB | 71.3% | 90.1% | 138.4 M |
| ResNet50 | 98 MB | 74.9% | 92.1% | 25.6 M |
| EfficientNetV2B0 | 29 MB | 78.7% | 94.3% | 7.2 M |

### Final experimental result

**EfficientNetV2B0** achieved the best performance in the project evaluation:

- **Accuracy:** `0.8314 ± 0.0229`
- **F1-score:** `0.8264 ± 0.0249`
- **Training time:** `93.50 sec / 50 epochs`

This made it the best trade-off between accuracy, F1-score, and computational efficiency among the evaluated models.

---

## Interpretability

Beyond raw classification metrics, the project also used **Grad-CAM** to inspect how the models attended to different facial regions during prediction.

This helps answer an important question:

> Is the model learning meaningful facial features, or is it relying on background artifacts and shortcuts?

Using Grad-CAM made the project more useful as a learning and model-analysis exercise, not just a leaderboard comparison.

---

## Repository Structure

```text
.
├── Prime_Minister_Data/
│   ├── Abhisit/
│   ├── Anand/
│   ├── Chuan/
│   ├── Paetongtarn/
│   ├── Prayut/
│   ├── Thaksin/
│   └── Yingluck/
├── Test_Data/
├── README.md
└── [training / notebook / project files]
```

> Update this section if you add notebooks, scripts, or model checkpoints later.

---

## Skills Demonstrated

- Computer Vision
- Deep Learning
- Image Classification
- Transfer Learning
- TensorFlow / Keras
- Data Augmentation
- Grad-CAM
- Dataset Curation
- Python

---

## Why this project matters

This project is a solid demonstration of practical deep learning work because it goes beyond model training alone. It includes:

- building a dataset from scratch
- keeping class balance under control
- comparing multiple pretrained architectures
- applying a consistent experimental setup
- interpreting model behavior visually

That makes it a cleaner portfolio piece than a typical one-model notebook.

---

## Suggested Repository Name

The current repository name `DeepLearningHW` is too generic. Better options:

### Best choice
- **thai-prime-ministers-face-classification**

### Other strong options
- `thai-prime-ministers-image-classification`
- `thai-pm-face-classifier`
- `transfer-learning-thai-prime-ministers`
- `thai-prime-ministers-cv-project`

If you want it to look strongest on GitHub and LinkedIn, use:

> **thai-prime-ministers-face-classification**

---

## LinkedIn-ready one-line summary

Built a custom face classification project for former Thai prime ministers using a self-collected balanced dataset of 420 images across 7 classes, and benchmarked VGG16, ResNet50, and EfficientNetV2B0 with transfer learning, augmentation, and Grad-CAM-based interpretation.

---

## Notes

This repository was originally created for coursework, but the project is strong enough to stand on its own as a portfolio piece in:

- Deep Learning
- Computer Vision
- Transfer Learning
- Custom Dataset Development

---

## Author

**Kunakorn Pruksakorn**  
Automation Engineer · AI / ML · Data Science  
GitHub: [KunakornMart](https://github.com/KunakornMart)
