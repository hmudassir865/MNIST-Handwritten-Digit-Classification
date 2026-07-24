# MNIST Handwritten Digit Classification with CNN

[![Python](https://img.shields.io/badge/Python-3.10-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.12-orange)](https://www.tensorflow.org/)
[![Keras](https://img.shields.io/badge/Keras-2.12-red)](https://keras.io/)

A **Convolutional Neural Network (CNN)** built with TensorFlow/Keras to classify handwritten digits (0–9) from the MNIST dataset. This project covers the complete deep learning workflow: data loading, exploration, model building, training, evaluation, and inference.

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Pipeline](#pipeline)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Installation](#installation)
- [Usage](#usage)
- [Author](#author)

---

## Overview

The **MNIST dataset** is a classic benchmark in computer vision — 70,000 grayscale images of handwritten digits (0–9). This project implements a compact CNN that achieves **~98.3% test accuracy**.

**Key highlights:**
- Lightweight CNN with only **4,440 parameters** (~17 KB)
- **98.28% test accuracy** after just 5 epochs
- End-to-end pipeline: data loading → preprocessing → training → evaluation → prediction
- Model saved as `model.h5` for reuse

---

## Dataset

- **Source:** [MNIST Database](http://yann.lecun.com/exdb/mnist/) via `keras.datasets.mnist`
- **Training set:** 60,000 images
- **Test set:** 10,000 images
- **Image size:** 28 × 28 grayscale (1 channel)
- **Classes:** 10 digits (0–9)

---

## Project Structure

```
MNIST_Handwritten_Digit_Classification/
├── MNIST with CNN.ipynb        # Main notebook
├── models_saved/
│   └── model.h5                # Saved trained model
├── requirements.txt            # Dependencies
└── README.md                   # Project documentation
```

---

## Pipeline

1. **Import Libraries** — TensorFlow/Keras, Matplotlib
2. **Data Loading** — Load MNIST via `keras.datasets.mnist.load_data()`
3. **Exploratory Data Analysis** — Visualize sample images, inspect shapes, pixel values
4. **Data Preprocessing** — Normalize pixel values (0–255 → 0–1), reshape to 4D tensors
5. **Model Building** — Sequential CNN with Conv2D, MaxPooling2D, Flatten, Dense layers
6. **Compilation** — Adam optimizer, SparseCategoricalCrossentropy loss, accuracy metric
7. **Training** — 5 epochs, batch size 64, 80/20 train/validation split
8. **Evaluation** — Test accuracy & loss on held-out 10,000 images
9. **Prediction** — Single-image inference with probability outputs

---

## Model Architecture

| Layer              | Output Shape    | Parameters |
|--------------------|-----------------|------------|
| Conv2D (10, 3×3)   | (26, 26, 10)    | 100        |
| Conv2D (10, 3×3)   | (24, 24, 10)    | 910        |
| MaxPooling2D (2×2)  | (12, 12, 10)    | 0          |
| Conv2D (10, 3×3)   | (10, 10, 10)    | 910        |
| Conv2D (10, 3×3)   | (8, 8, 10)      | 910        |
| MaxPooling2D (2×2)  | (4, 4, 10)      | 0          |
| Flatten            | 160             | 0          |
| Dense (10, Softmax)| 10              | 1,610      |

**Total params:** 4,440 (17.34 KB)

---

## Results

| Metric        | Score  |
|---------------|--------|
| **Test Accuracy** | **98.28%** |
| Test Loss     | 0.0518 |

Training converged rapidly — validation accuracy reached **98.15%** by epoch 4 with no signs of overfitting.

---

## Installation

```bash
# Clone the repository
git clone https://github.com/hmudassir865/MNIST_Handwritten_Digit_Classification.git
cd MNIST_Handwritten_Digit_Classification

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

```bash
jupyter notebook "MNIST with CNN.ipynb"
```

Run all cells sequentially. The notebook will:
- Load the MNIST dataset (downloaded automatically by Keras)
- Train the CNN model (5 epochs)
- Evaluate on the test set
- Save the model to `models_saved/model.h5`
- Run inference on a sample image

---

## Author

**Mudassir Hussain**

[![Email](https://img.shields.io/badge/Email-hmudassir865%40gmail.com-red)](mailto:hmudassir865@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-hmudassir865-black)](https://github.com/hmudassir865)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Mudassir%20Hussain-blue)](https://www.linkedin.com/in/mudassir-hussain-877347207/)
