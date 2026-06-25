# E-Commerce Product Classification using DistilBERT and Hybrid Neural Networks

## Abstract

Accurate product categorization in e-commerce platforms remains a critical challenge in Natural Language Processing (NLP). This project investigates DistilBERT combined with SMOTE augmentation and hybrid neural network architectures for automated product classification.

Using the PriceRunner dataset containing **35,311 product titles across 10 categories**, five different architectures were evaluated. While the vanilla DistilBERT model achieved **99.07% accuracy**, the **DistilBERT + BiGRU + Attention** architecture achieved the highest accuracy of **99.15%**. The study also analyzes the trade-off between computational complexity and classification performance for real-world deployment.

---

# Dataset

## PriceRunner Product Dataset

* Total Samples: **35,311**
* Categories: **10**
* Task: Multi-Class Product Classification
* Domain: E-Commerce NLP

### Challenges Addressed

* Inconsistent product naming conventions
* High intra-class similarity
* Class imbalance across categories
* Long-tail product distributions
* Short-text classification complexity

---

# Tech Stack

## Programming & Development

* Python
* Jupyter Notebook
* Git
* GitHub

## Deep Learning & NLP

* TensorFlow
* Keras
* Hugging Face Transformers
* DistilBERT

## Data Processing

* Pandas
* NumPy
* Scikit-Learn

## Data Augmentation

* SMOTE
* Imbalanced-Learn

## Hyperparameter Optimization

* Optuna (Bayesian Optimization)

## Visualization

* Matplotlib
* Seaborn

---

# Objectives

* Benchmark multiple DistilBERT-based architectures
* Analyze the impact of SMOTE augmentation
* Evaluate hybrid neural architectures
* Improve minority-class performance
* Optimize model hyperparameters using Optuna
* Identify the best model for production deployment

---

# System Architecture

```text
Product Title
      │
      ▼
Text Preprocessing
      │
      ▼
Tokenization
      │
      ▼
DistilBERT Embeddings
      │
      ├──► Vanilla DistilBERT
      │
      ├──► DistilBERT + SMOTE
      │
      ├──► DistilBERT + CNN
      │
      ├──► DistilBERT + BiLSTM
      │
      └──► DistilBERT + BiGRU + Attention
                    │
                    ▼
         Product Category Prediction
```

---

# Models Evaluated

## 1. Vanilla DistilBERT

### Description

* Fine-tuned DistilBERT baseline
* 6 Transformer layers
* 768-dimensional embeddings
* Lightweight and efficient architecture

---

## 2. DistilBERT + SMOTE

### Description

* TF-IDF feature extraction
* SMOTE-based class balancing
* Improved minority-class learning

---

## 3. DistilBERT + CNN

### Architecture

```text
DistilBERT Embeddings
        │
        ▼
Parallel Conv1D Layers
 (3, 4, 5 Kernels)
        │
        ▼
Global Max Pooling
        │
        ▼
Dense Layer
        │
        ▼
Classification
```

### Purpose

* Capture local n-gram patterns
* Improve feature extraction

---

## 4. DistilBERT + BiLSTM

### Architecture

```text
DistilBERT Embeddings
        │
        ▼
 BiLSTM (256 Units)
        │
        ▼
 Dense Layer
        │
        ▼
 Classification
```

### Purpose

* Capture sequential contextual information
* Evaluate recurrent-transformer hybridization

---

## 5. DistilBERT + BiGRU + Attention

### Architecture

```text
DistilBERT Embeddings
        │
        ▼
      BiGRU
        │
        ▼
 Attention Layer
        │
        ▼
 Dense Layer
        │
        ▼
 Classification
```

### Purpose

* Context-aware feature weighting
* Enhanced sequence representation

---

# Hyperparameter Optimization

## Optimization Technique

* Optuna Bayesian Optimization

### Best Parameters

| Parameter     | Value                           |
| ------------- | ------------------------------- |
| Learning Rate | 2.13e-05                        |
| Dropout       | 0.262                           |
| Optimizer     | AdamW                           |
| Loss Function | Sparse Categorical Crossentropy |

---

# Experimental Results

## Performance Comparison

| Model                          | Accuracy   | F1-Score   | Precision  | Recall     |
| ------------------------------ | ---------- | ---------- | ---------- | ---------- |
| DistilBERT                     | 99.07%     | 0.9907     | 0.9908     | 0.9891     |
| DistilBERT + SMOTE             | 99.10%     | 0.9911     | 0.9912     | 0.9911     |
| DistilBERT + CNN               | 98.92%     | 0.9893     | 0.9895     | 0.9889     |
| DistilBERT + BiLSTM            | 89.62%     | 0.8965     | 0.8972     | 0.8951     |
| DistilBERT + BiGRU + Attention | **99.15%** | **0.9917** | **0.9918** | **0.9913** |

---

# Computational Analysis

| Model                          | Training Time | Model Size | Inference Time |
| ------------------------------ | ------------- | ---------- | -------------- |
| DistilBERT                     | 45 min        | 268 MB     | 8.3 ms         |
| DistilBERT + CNN               | 52 min        | 285 MB     | 9.7 ms         |
| DistilBERT + BiLSTM            | 67 min        | 312 MB     | 12.1 ms        |
| DistilBERT + BiGRU + Attention | 71 min        | 298 MB     | 11.8 ms        |

---

# Key Findings

## Performance vs Efficiency

### DistilBERT

* Best deployment efficiency
* Lowest computational overhead
* Near state-of-the-art performance

### DistilBERT + BiGRU + Attention

* Highest classification accuracy
* Better contextual feature representation
* Increased training cost

### DistilBERT + CNN

* Effective local pattern extraction
* Moderate computational requirements

### DistilBERT + BiLSTM

* Significant performance degradation
* Higher latency
* Poor compatibility with transformer embeddings

---

# Impact of SMOTE

## Benefits

* Improved minority-class F1-score
* Better category balance
* Reduced model bias

## Best Use Cases

* Highly imbalanced datasets
* Rare-category prediction
* Business-critical minority classes

---

# Recommendations

## Production Deployment

### Recommended Model

**Vanilla DistilBERT**

### Reasons

* 99.07% Accuracy
* Fastest inference
* Small model size
* Best cost-to-performance ratio

---

## Research Deployment

### Recommended Model

**DistilBERT + BiGRU + Attention**

### Reasons

* Highest overall accuracy
* Better contextual learning
* Strongest classification performance

---

# Future Work

* Multimodal Product Classification (Text + Image)
* Ensemble Transformer Models
* Domain-Specific Pretraining
* Knowledge Distillation
* Retrieval-Augmented Classification
* Large Language Model Fine-Tuning

---

# Keywords

* DistilBERT
* Transformer Models
* Product Classification
* E-Commerce NLP
* Text Classification
* SMOTE
* Hybrid Neural Networks
* Attention Mechanisms
* Deep Learning
* Data Augmentation
* Bayesian Optimization
* Optuna


