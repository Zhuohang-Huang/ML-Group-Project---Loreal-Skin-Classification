# L'Oréal Hackathon – Skin Condition Classification Using Sustainable ML

> Developed as part of the L'Oréal Skin Condition Classification Hackathon at KEDGE Business School (Jan 2025)

---

## 🧴 Project Overview

In this project, we developed a **sustainable and efficient multi-label machine learning model** capable of classifying skin conditions based on beauty product descriptions. The dataset contains **6,240 labelled product descriptions** with **33 skin condition labels** — covering skin concerns, skin types, demographics, product actions, and usage timing.

Rather than chasing complex deep learning models, we adopted a **data-centric philosophy**: clean data, smart label engineering, and lightweight models that can be deployed in production with minimal carbon footprint.

---

## 🎯 Problem Statement

Given a short English description of a beauty product (~115 words on average), predict which of 33 skin condition labels apply (multi-label classification).

**Labels include:**
- Skin Concerns: `dark_pigmentation`, `acne`, `wrinkles_fine-lines`, `pores`, `eye-wrinkles`, etc.
- Skin Types: `dry`, `oily`, `normal`, `combination`, `sensitivity-high`, `sensitivity-low`
- Demographics: `18-34`, `35-54`, `55-99`, `male`, `female`
- Product Actions: `cleanse`, `prepare`, `treat`, `moisturize`, `protect`
- Usage: `day`, `night`

---

## ✅ Results

| Metric | Score |
|--------|-------|
| **F1 Score (Train)** | 76% |
| **F1 Score (Test)** | 66% |
| **Precision** | 58% |
| **CO₂ Emissions** | ≤ 0.100 kg |

> Model chosen: **Ridge Classifier** — simple, fast, robust, and environmentally responsible.

---

## 🔬 Methodology

### 1. Data Exploration & Label Analysis
- Identified strong **long-tail distribution** across 33 labels
- Used **25th percentile (410 samples)** as threshold to flag under-represented labels

### 2. Label Restructuring
- Merged overlapping labels (e.g., `wrinkle` + `fine-line` → unified label)
- Consolidated low-frequency demographic labels (e.g., age groups)
- Removed logically contradictory label co-occurrences

### 3. Text Preprocessing
- Lowercasing, punctuation removal
- Stop word removal (NLTK)
- Stemming with SnowballStemmer

### 4. Feature Extraction
- **TF-IDF Vectorizer** with N-gram range (1, 2)
- Tuned `max_features` for efficiency

### 5. Handling Class Imbalance
- **Smart oversampling** for labels below the 25th percentile threshold
- Sparse matrix stacking to keep memory footprint low

### 6. Model Training & Carbon Tracking
- Evaluated: Logistic Regression, Ridge Classifier, SGD Classifier, LinearSVC
- **Ridge Classifier** selected for best balance of performance + efficiency
- Carbon emissions tracked with **CodeCarbon** (`EmissionsTracker`)

---

## 🌱 Sustainability Principles

We intentionally avoided:
- ❌ Large pre-trained language models (BERT, GPT, etc.)
- ❌ Extensive hyperparameter grid search
- ❌ Domain-specific handcrafted rule engines

We prioritized:
- ✅ Data-centric over model-centric approach
- ✅ Simplicity under noisy supervision
- ✅ Efficiency as a first-class constraint

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas / NumPy | Data manipulation |
| Scikit-learn | ML models & TF-IDF |
| NLTK | Text preprocessing |
| imbalanced-learn | Oversampling |
| CodeCarbon | CO₂ emission tracking |
| Jupyter Notebook | Development environment |

---

## 📁 Repository Structure

```
├── Loreal_submit_cleaning_25_Jan_v1.ipynb   # Full pipeline: preprocessing → training → evaluation
├── dataset__1_.xlsx                          # Labelled dataset (6,240 samples, 33 labels)
├── Instruction__1_.pdf                       # Official hackathon brief
├── Hints_1_.pdf                              # Technical guidance provided
└── README.md
```

---

## 👥 Team

- Huang Zhuohang  
- Muhammad Ridha Syurgawi  
- Sonia Vinithadas  
- Wang Yuzhe  

*Associated with KEDGE Business School*

---

## 📌 Key Takeaways

- Impressive F1 performance (66% test) is achievable **without** large language models
- Label quality matters more than model complexity in noisy multi-label settings
- Sustainable ML is not a trade-off — it's a design choice from day one
