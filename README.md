# Legal Clause Similarity – Deep Learning Assignment #2  


## Overview

This repository contains a **complete implementation** of **Assignment #2** for the **Deep Learning (CS452)** course.  
The goal is to **build and compare two NLP models** (from scratch) to predict whether **two legal clauses are semantically similar** or not — **without using any pre-trained models**.


| Requirement | Status |
|------------|--------|
| Use Kaggle Legal Clause Dataset | Done |
| Fix dataset (no `clause`/`label` columns) | Done (filename = label) |
| Create balanced pairs (similar/different) | Done |
| Implement **2 different models** | Done: **BiLSTM+Attention** & **Siamese CNN** |
| Train from scratch | Done |
| Compute **Accuracy, Precision, Recall, F1, ROC-AUC** | Done |
| Show **training graphs** | Done |
| Qualitative analysis (correct/incorrect examples) | Done |
| Modular, clean, documented code | Done |
| PDF Report (`<FASTID>_<NAME>_A2-CS452.pdf`) | Done |
| GitHub submission (no Colab link) | Done |

---

## Models Implemented

| Model | Architecture | Key Features |
|------|--------------|-------------|
| **BiLSTM + Attention** | Siamese | Custom dot-product attention (Keras layer) |
| **Siamese CNN** | Siamese | 3×Conv1D(3,4,5) + GlobalMaxPool |

> **No BERT, No LegalBERT, No pre-trained embeddings.**

---

## Results

| Model | Accuracy | F1 | ROC-AUC | Training Time |
|-------|----------|----|---------|---------------|
| BiLSTM+Attention | **0.892** | **0.891** | **0.958** | 248s |
| Siamese CNN | 0.878 | 0.875 | 0.941 | **112s** |

**Best for accuracy & semantics:** BiLSTM+Attention  
**Best for speed & scale:** Siamese CNN

---

## Dataset

- **Source:** [Kaggle Legal Clause Dataset](https://www.kaggle.com/datasets/bahushruth/legalclausedataset)  
- **Fix:** CSVs have **no `label`** → **filename used as label**  
- **Total Clauses:** 1,247  
- **Labels:** 28  
- **Pairs:** 6,000 (3,000 similar, 3,000 different)  
- **Splits:** 70% Train / 15% Val / 15% Test

---

## Qualitative Examples

### Correctly Predicted Similar
```text
Clause 1: agreement the parties to this agreement intending to be legally bound agree as follows
Clause 2: agreement now therefore in consideration of the foregoing... the parties hereby agree as follows
