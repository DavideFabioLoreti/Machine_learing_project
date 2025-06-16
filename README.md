# Heart Disease Prediction using Machine Learning

## Project Overview

This **university project**, developed primarily with **KNIME**, focuses on predicting heart disease using machine learning. We analyzed a clinical dataset to enhance diagnostic processes and support clinical decision-making.

## Group Members

* Alberto Cera
* Fabio Focchi
* Davide Fabio Loreti
* Carlo Pegoraro
* Flavio Yzeiri

## Introduction

Early detection of heart disease is crucial. This study investigates how machine learning models can integrate various clinical attributes (demographic, physiological, diagnostic) to predict heart disease presence, augmenting traditional diagnostic methods.

## Dataset

The project uses a Kaggle dataset containing 1025 patient records with 14 features, including age, sex, chest pain type, blood pressure, cholesterol, and other diagnostic indicators.

You can find the dataset on [Kaggle Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset/data).

## Preprocessing

Key preprocessing steps included:

* **Duplicate Removal:** Removed 723 duplicate rows, leaving 302 unique entries.
* **Categorical Handling:** Merged inconsistent categories for 'ca' and 'thal'.
* **Feature Filtration:** Removed low-correlation features ('chol', 'fbs', 'restecg').
* **Outlier Management & Skewness:** Removed outliers from numerical variables and applied square root transformation to 'oldpeak' to reduce skewness.
* **Encoding & Scaling:** Applied one-hot encoding to categorical features and normalized numerical features (0-1 range).
* **Data Split:** Divided data into 80% training and 20% testing sets.

## Models

We trained and evaluated four classification algorithms:

* **Logistic Regression (LR)**
* **Support Vector Machine (SVM)**
* **Decision Tree (DT)**
* **Random Forest (RF)**

Each model was assessed using three approaches: default parameters, 10-fold cross-validation, and optimized parameter selection.

## Evaluation

Model performance was evaluated using accuracy, precision, recall, and AUC-ROC.

**Key Findings:**

* The **Random Forest Model** consistently performed best across all evaluation methods.
* With optimized parameters, Random Forest achieved **87.72% accuracy** and an **AUC of 0.929**.
* The Decision Tree model generally showed the lowest performance.
* Cross-validation confirmed the robustness of Random Forest, Logistic Regression, and SVM on unseen data.

## Conclusion

Machine learning shows significant potential as a supplementary tool for early heart disease diagnosis. The Random Forest model proved to be the most effective classifier in this study, demonstrating high accuracy and robust performance. Future work could explore more advanced models and expanded datasets.
