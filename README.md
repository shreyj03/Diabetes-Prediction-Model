# 🩺 Diabetes Prediction Model

**BA476 Final Project – Group 5**  
**Contributors:** Arhan, Binh, Eytan, and Shrey

## 📌 Overview

This project aims to **predict diabetes** in individuals using machine learning models applied to structured medical data. By analyzing key features like age, BMI, hypertension, and HbA1c levels, we help support **early detection and targeted interventions** for diabetes care.

## 🔍 Problem Statement

Our goal is to accurately **predict whether an individual has diabetes** using structured metadata. This can assist healthcare providers and public health orgs in prioritizing high-risk individuals for preventive interventions.

---

## 📊 Dataset

- **Source**: [Kaggle - Diabetes Health Dataset](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)
- **Original Size**: 100,000 records
- **Features**: Age, BMI, HbA1c levels, hypertension, heart disease, gender, smoking history, etc.
- **Class Imbalance**: Original ratio of non-diabetic to diabetic was **10.76:1**
- **Resampling**: Final working dataset had a **2:1 ratio** with 25,500 rows and 17 columns

---

## 📈 Descriptive & Exploratory Analysis

We performed descriptive stats and visualizations to understand feature distributions and relationships with the diabetes target variable. Some key observations:

- HbA1c and glucose levels are strong predictors.
- Older age, hypertension, and heart disease are correlated with higher diabetes likelihood.

---

## 🧠 Models Used

We trained and evaluated **10 models**:

- Logistic Regression (L1, L2)
- K-Nearest Neighbors
- Decision Trees
- Random Forest
- Bagging
- Gradient Boosting
- XGBoost
- AdaBoost
- Ridge and Lasso Regression

---

## 🥇 Results & Final Model Selection

### ✅ Top 3 Performing Models:

| Model             | Accuracy | Recall |
|------------------|----------|--------|
| **Gradient Boosting** | 0.92     | 0.84   |
| XGBoost           | 0.91     | 0.84   |
| Bagging           | 0.91     | 0.84   |

> 🔥 **Final Model Chosen:** **Gradient Boosting**  
> We selected Gradient Boosting based on its top recall and accuracy scores, and it consistently outperformed across validation folds.

---

## 🛠️ Feature Engineering

We engineered additional features to boost performance:

- `comorbidity` = `hypertension` + `heart_disease`
- `age_bmi_interaction` = `age * BMI`

---

## 🔧 Model Tuning

- **Method**: Nested Cross-Validation (5-fold)
- **Tool**: `GridSearchCV`
- **Final Model**: Gradient Boosting Classifier

### 🎯 Tuned Hyperparameters:

- `max_depth`: 5
- `learning_rate`: 0.1
- `min_samples_split`: 2
- `min_samples_leaf`: 1
- `n_estimators`: 100

### Final Metrics:

- **Accuracy**: 91%
- **Recall**: 84%
- **Precision**: 89%

---

## ⚖️ Simplicity vs. Complexity

- Logistic Regression performed surprisingly well (Accuracy: 89%)
- However, boosting methods captured subtle non-linearities
- Tradeoff: Higher performance vs. lower interpretability
- For medical prediction tasks, **maximizing performance is often worth it**

---

## 🚧 Challenges

- Having unbalanced data, so we were not sure how to resample the dataset — finally set it to **2:1 ratio**
- Figuring out which features to select for feature engineering
- Difficulty deciding an acceptable tradeoff between **recall and other metrics** (like **F1-score**) in selecting models

---

## 📚 Key Learnings

- **Balanced data** is critical for model fairness
- Model performance is limited by **data quality**
- **Hyperparameter tuning** + **feature engineering** + **cross-validation** is key to success
- Simpler models can still deliver competitive performance with interpretable outputs
