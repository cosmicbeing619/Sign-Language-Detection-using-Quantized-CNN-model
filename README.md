# Real-Time Sign Language Translator

![Python](https://img.shields.io/badge/Python-3.9-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-DeepLearning-orange)
![Computer Vision](https://img.shields.io/badge/ComputerVision-ASL-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

A **real-time American Sign Language (ASL) recognition system** that converts **hand gestures into text** using **computer vision and deep learning**.  
The project focuses on **building lightweight models optimized for real-time inference on edge devices** through **model quantization techniques**.

---

# Project Motivation

Sign language is the primary communication medium for millions of people with hearing impairments. However, many people are not familiar with sign language, which creates a communication barrier.

This project aims to build a **real-time sign language translation system** capable of recognizing ASL alphabet gestures from a camera feed and converting them into readable text.

The system combines:

- Computer Vision
- Deep Learning
- Hand Landmark Detection
- Model Optimization
- Quantized Neural Networks

to create an **efficient and deployable solution for sign language recognition**.

---

# Key Features

- Real-time hand gesture detection
- American Sign Language (ASL) alphabet recognition
- MediaPipe hand landmark extraction
- CNN-based gesture classification
- Lightweight models suitable for edge deployment
- Model compression using **Post Training Quantization (PTQ)** and **Quantization Aware Training (QAT)**
- Performance comparison across multiple model architectures

---

# System Pipeline

The recognition pipeline follows these steps:

1. Live camera feed captures hand gestures
2. MediaPipe detects and tracks the hand
3. 21 hand landmarks are extracted
4. Image preprocessing and normalization
5. CNN model classifies the gesture
6. Predicted gesture is converted into text output

---

# Datasets

## ASL Alphabet Dataset

- ~87,000 labeled images
- Covers **26 ASL alphabet signs**
- Images collected in different environments
- RGB images (~200×200 resolution)

## Sign Language MNIST

- 28×28 grayscale images
- Signs from **A–Y (excluding J and Z)**
- Used for baseline experimentation and model benchmarking

---

# Models Implemented

The project compares **four model configurations** to evaluate trade-offs between accuracy and efficiency.

---

## 1. MediaPipe + CNN Model

- Uses MediaPipe for **hand landmark extraction**
- CNN classifier trained on landmark-based features
- Computationally efficient and robust

**Accuracy:** 93.10%

---

## 2. Baseline CNN (Float32)

Standard convolutional neural network trained on RGB gesture images.

Architecture:

- 4 convolution blocks
- Batch normalization
- Max pooling
- Dense layer (256 units)
- Dropout regularization

**Accuracy:** 77.79%  
**Model Size:** 118 MB

---

## 3. PTQ Model (Post Training Quantization)

The baseline CNN was compressed using **TensorFlow Lite Post Training Quantization**.

Key benefits:

- Converts weights from **float32 to INT8**
- Significant reduction in model size
- Faster inference for edge devices

**Accuracy:** 75.72%  
**Model Size:** 9.86 MB

---

## 4. QAT Model (Quantization Aware Training)

Quantization effects are simulated during training, allowing the model to adapt to reduced precision.

Advantages:

- Maintains higher accuracy compared to PTQ
- Same compressed model size
- More stable deployment performance

**Accuracy:** 78.20%  
**Model Size:** 9.86 MB

---

# Performance Comparison

| Model | Accuracy | Precision | Recall | F1 Score | Model Size |
|------|------|------|------|------|------|
| MediaPipe + CNN | 93.10% | 0.9326 | 0.9310 | 0.9327 | 67 MB |
| CNN Baseline | 77.79% | 0.8061 | 0.7779 | 0.7772 | 118 MB |
| PTQ Model | 75.72% | 0.7938 | 0.7572 | 0.7595 | 9.86 MB |
| QAT Model | 78.20% | 0.8070 | 0.7820 | 0.7829 | 9.86 MB |

---

# Technologies Used

- Python
- TensorFlow / Keras
- TensorFlow Lite
- MediaPipe
- OpenCV
- NumPy
- Matplotlib

