# ✍️ Automated Essay Scoring (AES) — Technique Comparison

## 📌 Overview
This project explores different approaches for **automated essay scoring (AES)**.

The goal is to predict a score (1–5) for each essay based on its text. The project compares multiple modeling approaches — from simple feature-based models to neural networks and transformer-based models — and evaluates how well they perform.

---

## 📊 Dataset

The dataset is a CSV file with three columns:

- `essay_id` — unique identifier  
- `full_text` — the essay text  
- `score` — integer score (1–5)  

### Key characteristics:
- Essays come from **multiple prompts/topics** (not explicitly labeled)  
- Typical length: ~200–600 tokens (varies a lot)  
- Scores are **ordinal** (order matters, not just value)  

One challenge is that prompts are mixed, so the model has to generalize across different topics.

---

## 🎯 Task

Predict the **essay score** from the text.

This is treated as an **ordinal regression problem**, meaning:
- Predicting a 4 instead of 5 is better than predicting a 1  
- Evaluation must reflect this (not just accuracy)

---

## 🧠 Approaches

Three types of models are explored:

### A) Classical ML (Feature-Based)
- TF-IDF (word n-grams, character n-grams)  
- Optional shallow features (length, vocabulary richness, etc.)  
- Models: Linear models, SVR, Random Forest, etc.  

### B) Neural Models (Non-Pretrained)
- CNN / BiLSTM over embeddings  
- Handles text sequences directly  
- Uses techniques like dropout and attention  

### C) Transformer Models (Pretrained)
- Models like BERT / DistilBERT  
- Fine-tuned on the dataset  
- Can capture deeper language understanding  

---

## 📈 Evaluation

### Main metric:
- **Quadratic Weighted Kappa (QWK)** — measures agreement with true scores  

### Additional metrics:
- MAE  
- RMSE  
- Spearman correlation  

### Validation setup:
- Stratified train/validation/test split  
- Cross-validation for model selection  
- Test set kept untouched until final evaluation  

---

## ⚠️ Notes

- Essays vary a lot in length and topic  
- No prompt labels → harder generalization problem  
- Preventing data leakage is important  
- Scores are ordinal → standard classification metrics are not enough  

---

## 🚀 What this project shows

- How different modeling approaches behave on text scoring  
- Trade-offs between simple and complex models  
- Impact of features vs learned representations  
- Challenges of real-world NLP tasks with messy data  
