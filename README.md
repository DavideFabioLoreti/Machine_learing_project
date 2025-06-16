# Heart Disease Prediction using Machine Learning

## Project Overview

This is a **university project** that explores the application of machine learning techniques to predict the presence of heart disease in patients. Utilizing a clinical dataset from Kaggle, the study aims to enhance diagnostic workflows and support clinical decision-making for cardiovascular health management. We trained and evaluated multiple classification models, highlighting the potential of computational tools to augment traditional diagnostic practices. The project was primarily developed using **KNIME**, a data analytics, reporting, and integration platform.

## Group Members

* [cite_start]Alberto Cera [cite: 1]
* [cite_start]Fabio Focchi [cite: 1]
* [cite_start]Davide Fabio Loreti [cite: 1]
* [cite_start]Carlo Pegoraro [cite: 1]
* [cite_start]Flavio Yzeiri [cite: 1]

## Introduction

[cite_start]Clinical diagnosis of heart disease typically relies on a combination of demographic, physiological, and diagnostic markers, such as age, cholesterol levels, chest pain patterns, and electrocardiographic results[cite: 9]. [cite_start]While individual factors like elevated blood pressure or abnormal heart rate can raise suspicion, the interaction of these attributes creates a complex diagnostic landscape[cite: 10]. [cite_start]This study investigates whether machine learning models can effectively integrate these multifaceted clinical attributes to predict the presence of heart disease[cite: 13].

## Dataset

[cite_start]The dataset, sourced from Kaggle, includes 1025 patient records with 14 diagnostic features[cite: 3, 14]. These features include:

* [cite_start]**Age:** Patient's age in years[cite: 20].
* [cite_start]**Sex:** Biological sex (0 = female, 1 = male)[cite: 21].
* [cite_start]**Chest pain type:** Type of chest pain experienced (e.g., typical angina, atypical angina, non-anginal pain, asymptomatic)[cite: 22].
* [cite_start]**Resting blood pressure:** Blood pressure (mmHg) measured at rest[cite: 23].
* [cite_start]**Serum cholesterol:** Serum cholesterol level in mg/dl[cite: 24].
* [cite_start]**Fasting blood sugar > 120 mg/dl:** Binary indicator of fasting blood sugar exceeding 120 mg/dl (1 = yes, 0 = no)[cite: 25].
* [cite_start]**Resting electrocardiographic results:** ECG findings at rest[cite: 25].
* [cite_start]**Maximum heart rate achieved:** Highest heart rate (beats/minute) recorded during exercise[cite: 25].
* [cite_start]**Exercise induced angina:** Presence of chest pain triggered by exercise (1 = yes, 0 = no)[cite: 25].
* [cite_start]**Oldpeak:** ST segment depression (on ECG) during exercise compared to rest[cite: 25].
* [cite_start]**Slope of the peak exercise ST segment:** Slope of ST segment during peak exercise, reflecting ischemic changes[cite: 25, 26].
* [cite_start]**Number of major vessels:** Number of major blood vessels visible via fluoroscopy[cite: 25].
* [cite_start]**Thal:** Blood flow observation via thalassemia stress test (0 = normal, 1 = fixed defect, 2 = reversible defect)[cite: 26].
* [cite_start]**Target:** Whether a person has heart disease or not (0 = No, 1 = Yes)[cite: 27].

## Preprocessing

To prepare the dataset for modeling, several preprocessing steps were applied:

1.  [cite_start]**Duplicate Removal:** 723 duplicate rows were removed from the data [cite: 42][cite_start], leaving 302 unique rows[cite: 42].
2.  [cite_start]**Categorical Pre-processing:** For categorical attributes 'ca' and 'thal', categories that were not aligned with the dataset owner's information were merged with the most frequently occurring categories to ensure data accuracy[cite: 44, 45, 46, 47]. [cite_start]No missing values were found[cite: 48].
3.  [cite_start]**Feature Filtration:** Correlation analysis was performed [cite: 50][cite_start], and features with very low correlation to the target variable ('chol', 'fbs', 'restecg') were removed [cite: 55][cite_start], reducing the dataset to 10 features[cite: 56].
4.  **Outlier Detection and Skewness Adjustment:**
    * [cite_start]For 'trestbps' (normally distributed), values outside 2 standard deviations were removed (15 values) [cite: 60, 61][cite_start], reducing the dataset to 287 rows[cite: 62].
    * [cite_start]For skewed numerical variables like 'thalach' and 'oldpeak' [cite: 63][cite_start], the interquartile range (IQR) method (with a factor of 1.5) was used to identify and remove outliers (5 outliers were removed) [cite: 65, 66][cite_start], resulting in 282 rows[cite: 67].
    * [cite_start]The 'oldpeak' variable, with a skewness of 0.9279 [cite: 69][cite_start], was transformed using a square root to reduce its skewness to 0.0671, achieving a more normal distribution[cite: 70, 71].
5.  [cite_start]**Encoding Categorical Variables:** One-hot encoding was applied to categorical variables which had more than 2 categories[cite: 76]. [cite_start]Binary categorical variables remained as they were[cite: 76]. [cite_start]The target class was converted to a string format for model compatibility[cite: 77].
6.  [cite_start]**Feature Scaling:** All numerical variables were normalized to a range between 0 and 1[cite: 82, 83].
7.  [cite_start]**Class Imbalance Check:** The ratio of target class categories was 1.27 [cite: 85][cite_start], which is less than the threshold of 3, indicating no significant class imbalance[cite: 86].
8.  [cite_start]**Data Split:** The data was split into training (80%) and test (20%) sets using linear sampling[cite: 88, 89].

## Models

[cite_start]Four classification algorithms were employed[cite: 99]:

* [cite_start]**Logistic Regression (LR):** Models binary outcomes using a sigmoid function and linear combinations of input features[cite: 99].
* [cite_start]**Support Vector Machine (SVM):** Leverages kernel-based transforms to maximize margin hyperplanes[cite: 100].
* [cite_start]**Decision Tree (DT):** Splits data using entropy/Gini criteria to form classification rules, following CART methodology[cite: 101].
* [cite_start]**Random Forest (RF):** An ensemble of decision trees that aggregates predictions via majority voting to reduce overfitting[cite: 102].

[cite_start]Each algorithm was trained using three different approaches[cite: 103]:

1.  [cite_start]**Default Parameter Selection:** Models were trained with their default hyperparameters to establish a baseline performance[cite: 104].
2.  [cite_start]**Cross-Validation:** Each classifier was evaluated using 10-fold cross-validation to assess robustness and generalization, averaging performance metrics across all folds[cite: 107, 110].
3.  [cite_start]**Optimized Parameter Selection:** Hyperparameters for each model were tuned to achieve maximum accuracy[cite: 114]. [cite_start]For example, `sigma` and `stepsize` were tuned for Logistic Regression [cite: 116][cite_start], `number of records per node` and `number of threads` for Decision Tree [cite: 117][cite_start], `overlapping penalty` for SVM [cite: 118][cite_start], and `number of models` for Random Forest[cite: 119].

## Evaluation

[cite_start]Model performance was evaluated using accuracy, precision, recall, and AUC-ROC metrics[cite: 120].

### Key Results:

* **Default Parameter Selection:**
    * [cite_start]Random Forest showed the best performance with an accuracy of 85.97%, recall of 0.89, precision of 0.83, and an AUC of 0.928[cite: 136].
    * [cite_start]Decision Tree had the lowest accuracy at 77.19% and an AUC of 0.752[cite: 125, 127].

* **Optimized Parameter Selection:**
    * [cite_start]Random Forest, Logistic Regression, and Support Vector Machine all achieved an accuracy of 87.72%, with Random Forest having the highest AUC of 0.929[cite: 144, 146].
    * [cite_start]Decision Tree's accuracy improved significantly to 84.21% and AUC to 0.910 after optimization[cite: 138, 139].

* **Cross-Validation (10-fold):**
    * [cite_start]Logistic Regression, Support Vector Machine, and Random Forest all demonstrated an accuracy of 89.65%[cite: 148, 154, 157]. [cite_start]These models showed good performance on unseen data, indicating no overfitting or underfitting[cite: 150, 155, 156, 158].
    * [cite_start]Decision Tree's performance was 79.31% accuracy, indicating potential overfitting[cite: 151, 153].

[cite_start]Ultimately, the **Random Forest Model** was concluded to be the best-performing model, exhibiting the highest accuracy as well as precision, and a good value for recall, with the highest AUC value among all models[cite: 159, 160].

## Conclusion

[cite_start]Predicting heart disease using measurable clinical attributes is a complex challenge due to the interplay of subjective symptoms and objective biomarkers[cite: 162]. [cite_start]The Random Forest model emerged as the most effective classifier, delivering the highest accuracy (87.72%), precision (86%), recall (89%), and AUC-ROC (0.929)[cite: 165]. [cite_start]Its ensemble design effectively captured intricate feature interactions, outperforming simpler models[cite: 167]. [cite_start]While promising, further improvements could involve integrating advanced techniques like neural networks or gradient-boosted trees, refining preprocessing, or expanding the dataset with additional variables[cite: 169, 170, 171]. [cite_start]This work highlights the viability of machine learning as a supplementary tool for early diagnosis[cite: 172].








