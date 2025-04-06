# Telco Customer Churn Prediction

![image](https://github.com/user-attachments/assets/d38ab77a-5b20-4253-972f-f0e5cc924e11)


## 📌 Introduction

### Hypothetical Scenario

Telco, a leading telecommunications provider established in 2000, offers a wide range of services including mobile and landline communications, high-speed internet (broadband, fiber, wireless), TV and streaming, and online security solutions.

The company assigned me the task of developing a **machine learning-based churn prediction model** using historical customer data. The primary objective is to identify customers at risk of churning so the marketing team can implement targeted retention strategies—ultimately reducing attrition and increasing customer loyalty.

---

## 🎯 Project Objectives

### 1. Exploratory Data Analysis (EDA) & Data Cleaning

- Handled missing values, duplicates and outliers.
- Identified patterns, correlations, and distributions within the data.

#### Key Insights:
- **High correlation** between `tenure` and `total charges` (r = 0.83), which may negatively affect model performance and interpretability.
  
  ![image](https://github.com/user-attachments/assets/c24cd614-e965-4163-803f-942616b0f4c3)

- The dataset is **imbalanced**, with more non-churn instances.
  
  ![image](https://github.com/user-attachments/assets/ed73c358-90ce-4b1b-a5d1-66b7d2b09847)

- Null values existed for 11 new customers—these were removed due to insufficient data.

---

### 2. Feature Engineering

- Transformed categorical variables using **replace** and **one-hot encoding** to make them suitable for machine learning algorithms.

---

### 3. Model Development

- **Data Splitting**: Separated features and target and split the data into training and testing sets.
- **Feature Scaling**: Standardized features to ensure equal importance, preventing features with larger scales from dominating.
  
#### Evaluation Metrics:
- **Accuracy**: Correct predictions (both churn and non-churn) over total predictions.
- **Precision**: Correct positive predictions over total predicted positives.
- **Recall**: Correct positive predictions over all actual positives (important for minimizing false negatives).
- **F1 Score**: Harmonic mean of precision and recall—helpful when both false positives and false negatives are important.

> 💡 **Business Focus**: The company prioritizes **recall** for the churn class (class 1) because **missing a potential churner (false negative)** is more costly than falsely identifying one (false positive).

---

### 4. Model Iterations

#### 🔁 First Attempt:
- Applied **basic Random Forest**.
- Performed well on non-churn (class 0), poorly on churn (class 1) due to **class imbalance**.

#### ⚖️ Balancing the Dataset:
- Applied **undersampling** to reduce class imbalance.
  
![image](https://github.com/user-attachments/assets/9c6d1d82-49d7-4beb-931a-d6fda1137c73)

- Re-split and scaled the data.

#### 🔁 Second Attempt:
- Evaluated multiple models: **Random Forest, XGBoost, Logistic Regression, SVM, LightGBM**.
- **Logistic Regression** performed best with balanced prediction across classes.
- Analyzed **feature importance**.

![image](https://github.com/user-attachments/assets/b916db2b-6b49-4a77-a49e-a8be7a301677)


#### 🔁 Third Attempt:
- Reduced feature set to **top 10 most important features**.
- Achieved **similar recall scores** as with full feature set—preferred due to simpler and more interpretable model.

#### 🔧 Hyperparameter Tuning:
- **Grid Search** applied but did not yield significant performance improvement.

#### 🧪 Feature Reduction:
- Removed `tenure` (highly correlated with `total charges`), but saw no improvement.

---

## ✅ Final Model & Results

- **Best Model**: Logistic Regression
- **Recall**:
  - Class 0 (No Churn): **0.71**
  - Class 1 (Churn): **0.81**
- **Accuracy**: **0.75**

---
## 📝 Conclusion

This project demonstrates how machine learning can be leveraged to solve a real-world business problem. By focusing on **recall**, we successfully prioritized the detection of potential churners, supporting Telco’s customer retention efforts through data-driven decisions.





