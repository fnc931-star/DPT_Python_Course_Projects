# Fashion-MNIST CNN Image Classifier

A complete end-to-end **Convolutional Neural Network (CNN)** built with **TensorFlow / Keras** to classify the 10 clothing categories in the Fashion-MNIST dataset.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Project Structure](#project-structure)
4. [Requirements](#requirements)
5. [Installation](#installation)
6. [How to Run](#how-to-run)
7. [Task Breakdown](#task-breakdown)
8. [Model Architecture](#model-architecture)
9. [Results](#results)
10. [Output Files](#output-files)
11. [Notes](#notes)

---

## Project Overview

This project demonstrates a full Deep Learning workflow for image classification:

- Loading and preprocessing image data
- Designing a multi-layer CNN
- Training with a validation split to monitor overfitting
- Evaluating on unseen test data
- Visualising training curves, confusion matrix, and predictions

---

## Dataset

| Property | Value |
|---|---|
| **Name** | Fashion-MNIST |
| **Source** | `keras.datasets.fashion_mnist` |
| **Training samples** | 60,000 |
| **Test samples** | 10,000 |
| **Image size** | 28 × 28 pixels (grayscale) |
| **Classes** | 10 (T-shirt, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot) |

---

## Project Structure

```
fashion-mnist-cnn/
│
├── fashion_mnist_cnn.py          # Main Python script (all 5 tasks)
├── README.md                     # This file
│
└── outputs/                      # Generated after running the script
    ├── task1_sample_images.png
    ├── task4_confusion_matrix.png
    ├── task5_training_curves.png
    └── task5_predictions.png
```

---

## Requirements

- Python 3.8 or higher
- TensorFlow 2.x
- NumPy
- Matplotlib
- Seaborn
- scikit-learn

> **Note:** PyTorch is **not** used. This project is TensorFlow / Keras only.

---

## Installation

```bash
# 1. Clone or download the repository
git clone https://github.com/fnc931-star/DPT_Python_Course_Projects/fashion-mnist-cnn.git
cd fashion-mnist-cnn

# 2. (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# 3. Install dependencies
pip install tensorflow numpy matplotlib seaborn scikit-learn
```

---

## How to Run

```bash
python fashion_mnist_cnn.py
```

The script will:
1. Automatically download the Fashion-MNIST dataset on first run
2. Print progress for each task to the terminal
3. Display and save all visualisation plots

Alternatively, paste each task section into **Jupyter Notebook** or **Google Colab** and run cell by cell.

---

## Task Breakdown

### Task 1 — Data Loading and Preprocessing
- Loads Fashion-MNIST from `keras.datasets`
- Normalises pixel values from `[0, 255]` → `[0, 1]`
- Reshapes images to `(28, 28, 1)` for CNN input
- Displays 10 sample images with their class labels

### Task 2 — Design / Build the CNN Model
- 2 convolutional blocks (2 Conv2D layers each)
- MaxPooling after each block to reduce spatial dimensions
- Dropout layers (0.25 and 0.50) to prevent overfitting
- Flatten → Dense(256) → Dense(10, softmax) output
- Compiled with **Adam** optimiser and **sparse categorical cross-entropy** loss

### Task 3 — Compile and Train the Model
- Trains for **20 epochs** with batch size **64**
- Uses a **15% validation split** to monitor generalisation
- Prints training and validation accuracy / loss per epoch

### Task 4 — Model Evaluation
- Evaluates the trained model on the **unseen test set**
- Reports **test accuracy** and **test loss**
- Generates a **confusion matrix** (heatmap)
- Prints a full **classification report** (precision, recall, F1-score per class)

### Task 5 — Visualisation and Analysis
- Plots **accuracy and loss curves** across all epochs
- Displays **15 random test images** with predicted and true labels (green = correct, red = incorrect)

---

## Model Architecture

```
Model: "FashionMNIST_CNN"
_____________________________________________________________
Layer (type)             Output Shape          Param #
=============================================================
conv2d (Conv2D)          (None, 28, 28, 32)    320
conv2d_1 (Conv2D)        (None, 28, 28, 32)    9,248
max_pooling2d            (None, 14, 14, 32)    0
dropout (Dropout 0.25)   (None, 14, 14, 32)    0
conv2d_2 (Conv2D)        (None, 14, 14, 64)    18,496
conv2d_3 (Conv2D)        (None, 14, 14, 64)    36,928
max_pooling2d_1          (None, 7, 7, 64)      0
dropout_1 (Dropout 0.25) (None, 7, 7, 64)      0
flatten                  (None, 3136)           0
dense (Dense 256)        (None, 256)            803,072
dropout_2 (Dropout 0.50) (None, 256)            0
dense_1 (Dense 10)       (None, 10)             2,570
=============================================================
Total params: 870,634
```

---

## Results

| Metric | Value |
|---|---|
| Test Accuracy | ~92% |
| Test Loss | ~0.22 |

> Actual values may vary slightly between runs due to random weight initialisation.

---

## Output Files

| File | Description |
|---|---|
| `task1_sample_images.png` | Grid of 10 sample training images with labels |
| `task4_confusion_matrix.png` | Heatmap of true vs predicted classes |
| `task5_training_curves.png` | Accuracy and loss curves across epochs |
| `task5_predictions.png` | 15 test images with predicted and true labels |

---

## Notes

- The dataset is downloaded automatically by Keras on first run (~30 MB).
- For **Google Colab**, the script runs as-is without any changes.
- Screenshots of the code and its output should be pasted into the submission `.docx` file as required.
- All 5 tasks are contained in a single script for simplicity; they can also be split into separate notebook cells.

---

*Built with TensorFlow / Keras — Deep Learning & Computer Vision Exercise*