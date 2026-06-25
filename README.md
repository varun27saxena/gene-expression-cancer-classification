# 🧬 Multi-Class Cancer Classification using RNA-Seq Gene Expression Data
<p align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>

<img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>

<img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>

<img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/>

<img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=plotly&logoColor=white"/>

<img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white"/>

</p>
## Overview

Cancer diagnosis using gene expression data is one of the most important applications of Machine Learning in Bioinformatics. RNA-Seq technology measures the expression levels of thousands of genes, allowing machine learning models to identify complex biological patterns associated with different cancer types.

This project presents a comparative study of multiple machine learning algorithms for classifying cancer types using high-dimensional RNA-Seq gene expression data. In addition to building predictive models, the project investigates the impact of Principal Component Analysis (PCA) on different machine learning algorithms and demonstrates how preprocessing choices affect model performance.

---

## Problem Statement

Given RNA-Seq gene expression levels from patients, predict the type of cancer among the following five classes:

* BRCA (Breast Cancer)
* COAD (Colon Adenocarcinoma)
* KIRC (Kidney Renal Clear Cell Carcinoma)
* LUAD (Lung Adenocarcinoma)
* PRAD (Prostate Adenocarcinoma)

This is a **multi-class classification** problem.

---

# Dataset Information

| Property | Value                           |
| -------- | ------------------------------- |
| Dataset  | UCI Machine Learning Repository |
| Samples  | 801                             |
| Features | 20,531 Gene Expression Features |
| Classes  | 5                               |
| Task     | Multi-Class Classification      |

Each row represents one patient, while each column represents the expression level of a particular gene.

---

# Project Workflow

```text
Raw Dataset
      │
      ▼
Data Validation
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Train-Test Split (Stratified)
      │
      ▼
Data Preprocessing
      │
      ├── StandardScaler
      │
      └── Principal Component Analysis (PCA)
      │
      ▼
Model Training
      │
      ├── Logistic Regression
      ├── Support Vector Machine
      ├── K-Nearest Neighbors
      ├── Decision Tree
      ├── Random Forest
      └── Gaussian Naive Bayes
      │
      ▼
Performance Evaluation
      │
      ▼
Experimental Analysis
```

---

# Exploratory Data Analysis

The following data quality checks were performed before model training:

* Missing Value Analysis
* Duplicate Row Detection
* Duplicate Patient ID Verification
* Class Distribution Analysis
* Feature Type Inspection

### Observations

* No missing values
* No duplicate rows
* No duplicate patient IDs
* Moderate class imbalance
* 20,531 numerical gene expression features

---

# Data Preprocessing

The following preprocessing pipeline was implemented:

* Removed patient identifiers
* Label encoded target classes
* Stratified Train-Test Split
* Standardized numerical features
* Applied Principal Component Analysis (PCA)

---

# Principal Component Analysis

The original dataset contained **20,531 features**, making it computationally expensive and susceptible to the curse of dimensionality.

PCA was applied to reduce dimensionality while preserving the majority of the variance.

Experiments were conducted using:

* 95% Explained Variance
* 90% Explained Variance

Interestingly, retaining only **90%** of the variance produced the same predictive performance as retaining **95%**, while requiring fewer principal components.

---

# Experiments

Two independent experimental settings were evaluated.

## Experiment 1 — Models with PCA

| Model                  | Accuracy |
| ---------------------- | -------: |
| Logistic Regression    | **100%** |
| Support Vector Machine |      98% |
| K-Nearest Neighbors    |      97% |
| Decision Tree          |      90% |
| Random Forest          |      92% |
| Gaussian Naive Bayes   |      44% |

---

## Experiment 2 — Models without PCA

| Model                  |  Accuracy |
| ---------------------- | --------: |
| Logistic Regression    |       98% |
| Support Vector Machine |       98% |
| K-Nearest Neighbors    |       97% |
| Decision Tree          |       95% |
| Random Forest          | **99.8%** |
| Gaussian Naive Bayes   |       57% |

---

# Key Findings

This project demonstrates that **preprocessing techniques should be selected based on the learning algorithm rather than applying a single preprocessing pipeline to every model.**

### Important observations

* PCA significantly improved Logistic Regression performance (98% → 100%).
* SVM and KNN showed minimal performance differences with and without PCA.
* PCA reduced the performance of Decision Trees and Random Forest.
* Random Forest achieved nearly perfect performance using the original gene expression features.
* Preserving 90% explained variance achieved identical performance to preserving 95%, making it a more computationally efficient choice.

---

# Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-Learn
* Google Colab

---

# What I Learned

This project helped me develop a practical understanding of the complete machine learning workflow, including:

* Data validation and preprocessing
* Exploratory Data Analysis
* Data leakage prevention
* Stratified train-test splitting
* Principal Component Analysis
* Model comparison
* Experimental analysis
* Drawing conclusions from empirical results rather than assumptions

---

# Results Summary

This project demonstrates that **there is no universally optimal preprocessing pipeline**.

Different machine learning algorithms respond differently to dimensionality reduction. Through systematic experimentation, it was observed that PCA substantially improved linear models while reducing the effectiveness of tree-based models.

Rather than selecting algorithms based on popularity, this project emphasizes selecting preprocessing techniques and models based on experimental evidence.
