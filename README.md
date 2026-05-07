# Prompt Injection Detection & Text Mining Project

This project implements a machine learning pipeline designed to detect and categorize Prompt Injection attacks in Large Language Models (LLMs). Using a combination of semantic analysis (TF-IDF) and structural feature engineering, the system identifies malicious attempts to bypass system instructions.

## 🚀 Project Overview

The core objective is to classify prompts into three security tiers:
- **Benign**: Standard user queries without malicious intent.
- **Suspicious**: Prompts containing unusual patterns or structural anomalies.
- **Prompt Injection**: Active adversarial attacks designed to hijack the model's behavior.

## 📁 Project Structure

```text
.
├── 1_data_mapping_and_audit.ipynb  # Phase 1: Data loading, validation, and directory setup
├── 2_EDA_and_prepocessing.ipynb    # Phase 2: Exploratory Data Analysis, Modeling, and Evaluation
├── README.md                       # Project documentation
├── requirements.txt                # Python dependencies
├── data/
│   ├── raw/                        # Original dataset (spml_prompt_injection.csv)
│   └── processed/                  # Cleaned and engineered datasets
└── outputs/
    ├── figures/                    # Generated plots and charts
    ├── models/                     # Serialized ML models (security_pipeline.pkl)
    ├── reports/                    # Metrics and audit summaries
    └── visualizations/             # High-level performance visualizations
```

## 🛠️ Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd sprint_13_proyecto_promp_injection_text_minning
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## 📊 Methodology

### 1. Data Mapping & Audit
- Environment setup and custom visualization styling.
- Validation of security columns and class distribution.

### 2. Exploratory Data Analysis (EDA)
- **Length Analysis**: Comparison of character and word counts across classes.
- **Vocabulary Inspection**: Top n-grams and differential Word Clouds to identify attack signatures (e.g., "ignore previous", "system instructions").
- **T-SNE Projection**: 3D visualization of prompt embeddings to identify clusters and anomalies.

### 3. Feature Engineering
- **Security-Preserving Cleaning**: Normalization that retains structural symbols ( `:`, `#`, `[`, `]` ) critical for injection patterns.
- **TF-IDF Vectorization**: Capture semantic context using unigrams and bigrams.
- **Structural Features**: Extraction of `text_length`, `uppercase_ratio`, and `special_char_ratio` to detect scale, "shouting" or escape sequences.

### 4. Modeling & Evaluation
- **Algorithm**: Logistic Regression with balanced class weights.
- **Pipeline**: Integrated preprocessing and classification for real-time inference.
- **Security Audit**: Focus on **Recall** for the `prompt_injection` class to minimize False Negatives (leaked attacks).

## 📈 Results

The model performance is documented in `outputs/reports/metrics_summary.txt`. Key visualizations like the **Security Confusion Matrix** and **Precision-Recall Curves** are available in the `outputs/visualizations/` directory.

## 🔍 Interactive Testing

The `2_EDA_and_prepocessing.ipynb` notebook includes an `interactive_security_test()` function that allows real-time analysis of custom prompts using the trained model.

---
*Developed as part of the Bootcamp Data Analytics - IT Academy 2026.*
