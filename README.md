## Abstract
Accurate product categorization in e-commerce platforms represents a critical challenge in natural language processing (NLP). This study investigates DistilBERT combined with SMOTE augmentation and hybrid neural network architectures. Using the PriceRunner dataset (35,311 titles across 10 categories), five modeling approaches are evaluated. While vanilla DistilBERT achieves 99.07% accuracy, the BiGRU + Attention variant marginally leads with 99.15%. The study provides a practical trade-off analysis between computational complexity and classification performance.

---

## 1. Introduction
The exponential growth of e-commerce platforms necessitates automated catalog management systems.

### Key Challenges
- Inconsistent product naming conventions  
- High intra-class similarity  
- Severe class imbalance (e.g., Mobile Phones vs niche appliances)  
- Bias toward majority classes in standard models  

---

## 1.1 Objectives & Contributions
- Benchmark four distinct modeling approaches on e-commerce data  
- Quantify the impact of SMOTE-based augmentation on minority classes  
- Design hybrid architectures combining CNN, BiLSTM, and BiGRU + Attention with transformer embeddings  
- Optimize hyperparameters using Bayesian Optimization (Optuna)  

---

## 2. Methodology & Architectures

### 2.1 Evaluated Models

| Architecture | Description |
|-------------|------------|
| **Vanilla DistilBERT** | Fine-tuned baseline (6 layers, 768-dim embeddings) |
| **DistilBERT + SMOTE** | SMOTE applied on TF-IDF features for class balancing |
| **DistilBERT + CNN** | 3 parallel Conv1D layers (kernel sizes: 3, 4, 5) |
| **DistilBERT + BiLSTM** | Bidirectional LSTM (256 units) |
| **DistilBERT + BiGRU + Attention** | BiGRU with multiplicative attention mechanism |

---


---

## 3. Experimental Results

### 3.1 Performance Comparison

| Model | Accuracy | F1-Score | Precision | Recall |
|------|----------|----------|-----------|--------|
| DistilBERT (Baseline) | 99.07% | 0.9907 | 0.9908 | 0.9891 |
| DistilBERT + SMOTE | 99.10% | 0.9911 | 0.9912 | 0.9911 |
| DistilBERT + CNN | 98.92% | 0.9893 | 0.9895 | 0.9889 |
| DistilBERT + BiLSTM | 89.62% | 0.8965 | 0.8972 | 0.8951 |
| DistilBERT + BiGRU + Attn | **99.15%** | **0.9917** | **0.9918** | **0.9913** |

---

### 3.2 Computational Analysis

| Model | Training Time | Model Size | Inference Time |
|------|--------------|------------|----------------|
| DistilBERT | 45 min | 268 MB | 8.3 ms |
| DistilBERT + CNN | 52 min | 285 MB | 9.7 ms |
| DistilBERT + BiLSTM | 67 min | 312 MB | 12.1 ms |
| DistilBERT + BiGRU + Attn | 71 min | 298 MB | 11.8 ms |

---

## 4. Key Findings & Discussion

### Efficiency vs Performance
- Vanilla DistilBERT provides the best return on investment (ROI)  
- BiGRU + Attention improves accuracy marginally (+0.08%)  
- Training cost increases by ~58%  

### Impact of SMOTE
- Improves minority class F1-score by ~1.1%  
- Effective for long-tail categories (e.g., CPUs, Freezers)  

### Architectural Insights
- CNN captures local n-gram patterns effectively  
- BiGRU + Attention enhances contextual weighting  
- BiLSTM shows **performance degradation** due to mismatch with transformer representations  

---

## 5. Conclusions & Recommendations

### Recommended Approach
- Use **Vanilla DistilBERT** for production systems  
- Best balance of accuracy, speed, and model size  

### When to Use SMOTE
- Required for:
  - Imbalanced datasets  
  - Minority class critical applications  

### Avoid
- Recurrent hybrids (BiLSTM):
  - Increased latency  
  - No performance gain  

### Optimization Strategy
- Use **Optuna (Bayesian Optimization)**  
- Best configuration:
  - Learning Rate: `2.13e-05`  
  - Dropout: `0.262`  

---

## Keywords
- Transformer Models  
- DistilBERT  
- SMOTE  
- Hybrid Neural Networks  
- Text Classification  
- E-Commerce NLP  
- Data Augmentation  
