# AnemiaSense: Non-Invasive Anemia Severity Detection Using Deep Learning

## Overview

Anemia is one of the most common health conditions worldwide and is traditionally diagnosed through invasive blood tests that measure hemoglobin (Hb) levels.

This project proposes a **non-invasive anemia screening system** using **Deep Learning** and **Eye Conjunctiva Images**. The system predicts the patient's hemoglobin level from an eye image and classifies the condition into anemia severity categories.

In addition to prediction, the system provides:

- Severity classification
- Personalized dietary recommendations
- Doctor consultation alerts for severe cases
- Explainable AI visualization (Future Work)

The objective is to create a low-cost, smartphone-friendly screening tool that can be used in rural and resource-limited areas where laboratory testing may not be readily available.

---

# Problem Statement

**"Non-Invasive Anemia Severity Detection and Personalized Dietary Recommendation Using Deep Learning-Based Eye Conjunctiva Image Analysis"**

---

# Motivation

Traditional anemia diagnosis requires:

- Blood sample collection
- Laboratory testing
- Medical equipment
- Trained healthcare professionals

These requirements make frequent screening difficult in many regions.

The conjunctiva (inner lower eyelid) contains rich blood vessels and visibly changes color with decreasing hemoglobin levels.

Deep learning models can learn these visual patterns and estimate anemia severity directly from images.

---

# Proposed Solution

The proposed system uses an eye conjunctiva image as input and performs:

1. Image preprocessing
2. Deep feature extraction using EfficientNetB0
3. Hemoglobin prediction
4. Severity classification
5. Personalized food recommendations
6. Doctor alert generation for severe cases

---

# System Architecture

```text
┌──────────────────────┐
│ Eye Conjunctiva Image│
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Image Preprocessing  │
│                      │
│ • Resize            │
│ • Normalization     │
│ • Augmentation      │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ EfficientNetB0 CNN   │
│ Feature Extraction   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Hb Prediction Model  │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Severity Classifier  │
└──────────┬───────────┘
           │
           ▼
┌─────────────────────────────────┐
│ Normal                          │
│ Mild Anemia                     │
│ Moderate Anemia                 │
│ Severe Anemia                   │
└──────────┬──────────────────────┘
           │
           ▼
┌─────────────────────────────────┐
│ Recommendation Engine           │
│                                 │
│ Veg Diet Suggestions            │
│ Non-Veg Diet Suggestions        │
│ Doctor Alert for Severe Cases   │
└─────────────────────────────────┘
```

---

# Workflow

## Step 1: Image Acquisition

The user uploads an eye conjunctiva image.

Example:

```text
Input:
Eye_001.jpg
```

---

## Step 2: Image Preprocessing

The uploaded image is processed through:

- Resizing
- Normalization
- Data augmentation
- Region extraction

Purpose:

- Remove noise
- Improve model performance
- Reduce overfitting

---

## Step 3: Feature Extraction

EfficientNetB0 is used as the backbone network.

Reasons for selecting EfficientNetB0:

- Lightweight architecture
- Excellent medical imaging performance
- Lower computational cost
- Suitable for mobile deployment

---

## Step 4: Hemoglobin Prediction

The model predicts:

```text
Hb = 9.4 g/dL
```

instead of directly predicting classes.

This follows the actual clinical workflow.

---

## Step 5: Severity Classification

Predicted Hb value is converted into severity levels.

Example thresholds:

| Hemoglobin (g/dL) | Severity |
|-------------------|----------|
| >= 12             | Normal |
| 10 – 11.9         | Mild |
| 8 – 9.9           | Moderate |
| < 8               | Severe |

---

## Step 6: Recommendation Engine

### Vegetarian

Recommended Foods:

- Spinach
- Drumstick leaves
- Beetroot
- Dates
- Raisins
- Lentils
- Chickpeas
- Soybeans
- Sesame seeds

### Non-Vegetarian

Recommended Foods:

- Eggs
- Fish
- Chicken
- Lean meat
- Iron-rich seafood

---

## Step 7: Severe Anemia Alert

If:

```text
Hb < 8 g/dL
```

The system displays:

```text
Severe Anemia Detected

Please consult a physician immediately.

This prediction is only a screening result and
should not replace laboratory diagnosis.
```

---

# Dataset

## Primary Dataset

CP-AnemiC Dataset

Contains:

- 710 conjunctiva images
- Hemoglobin values
- Age
- Gender
- Clinical labels

Dataset Link:

https://data.mendeley.com/datasets/m53vz6b7fx

---

## Secondary Dataset

EYES-DEFY-ANEMIA

Contains:

- Eye conjunctiva images
- Hemoglobin values
- Age
- Gender

Dataset Link:

https://www.kaggle.com/datasets/harshwardhanfartale/eyes-defy-anemia

---

# Deep Learning Model

## Backbone

EfficientNetB0

Advantages:

- Transfer learning support
- High accuracy
- Low computational requirements
- Strong performance on medical datasets

---

# Evaluation Metrics

The system will be evaluated using:

### Classification Metrics

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

### Regression Metrics

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)

---

# Expected Output

Example:

```text
Predicted Hb Level: 9.1 g/dL

Severity:
Moderate Anemia

Diet Type:
Vegetarian

Recommended Foods:
• Spinach
• Dates
• Lentils
• Beetroot
• Chickpeas

Recommendation:
Increase iron-rich food intake and consult a
healthcare professional if symptoms persist.
```

---

# Research Gap

Most existing studies focus on:

- Eye conjunctiva only
- Binary classification
  - Anemic
  - Non-Anemic

Very few studies provide:

- Hemoglobin estimation
- Severity grading
- Personalized dietary recommendations

This project attempts to bridge this gap by combining:

- Hb prediction
- Severity classification
- Diet recommendation

into a single screening framework.

---

# Future Enhancements

## Multi-Modal Detection

Additional body regions:

- Fingernail Images
- Palm Images
- Tongue Images

Architecture:

```text
Eye
     \
Nail  \
        ---> Fusion ---> Prediction
Palm  /
     /
Tongue
```

---

## Explainable AI

Grad-CAM visualization

Benefits:

- Highlights important conjunctiva regions
- Improves clinical trust
- Supports medical interpretation

---

# Key Research Papers

## 1. Deep Learning Model-Based Detection of Anemia from Conjunctiva Images (Recommended Starting Paper)

Link:

https://www.e-hir.org/journal/view.php?number=1237

Why Important:

- Similar project domain
- Uses conjunctiva images
- Compares ML and DL approaches
- Strong baseline for implementation

---

## 2. Vision Transformer-Based Anemia Detection

Link:

https://www.nature.com/articles/s41598-025-32343-w

Highlights:

- Vision Transformer
- Explainable AI
- Attention Maps

---

## 3. Portable System for Prediction of Anemia Based on Ocular Conjunctiva

Link:

https://arxiv.org/abs/1910.12399

Highlights:

- Smartphone-based screening
- Early non-invasive anemia prediction

---

# Tech Stack

Frontend:
- React.js

Backend:
- Flask / FastAPI

Deep Learning:
- TensorFlow
- Keras

Image Processing:
- OpenCV

Visualization:
- Matplotlib
- Grad-CAM

Database:
- MongoDB

---

# Disclaimer

This system is intended only for preliminary screening and educational research purposes.

The predictions generated by the model are not a substitute for professional medical diagnosis, laboratory testing, or treatment.
