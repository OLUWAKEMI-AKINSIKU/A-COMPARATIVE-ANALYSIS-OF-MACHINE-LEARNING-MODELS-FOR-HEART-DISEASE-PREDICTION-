# 🫀 Comparative Analysis of Machine Learning Models for Heart Disease Prediction

This project investigates multiple machine learning models to predict the likelihood of heart disease based on clinical patient data. The goal is to compare models, evaluate performance metrics, and determine which model generalizes best to new unseen patients.

---

## 📊 Dataset Overview

- **Dataset Shape:** (920 rows, 16 columns)
- **Target Variable:** `num` (0 = No heart disease, 1 = Heart disease)

### **Data Dictionary**

| Column | Description |
|--------|-------------|
| id | Unique ID for each patient |
| age | Age (years) |
| origin | Dataset source |
| sex | Male/Female |
| cp | Chest pain type |
| trestbps | Resting blood pressure (mmHg) |
| chol | Serum cholesterol (mg/dl) |
| fbs | Fasting blood sugar > 120 mg/dl (True/False) |
| restecg | Resting ECG results |
| thalch | Maximum heart rate achieved |
| exang | Exercise-induced angina (True/False) |
| oldpeak | ST depression induced by exercise |
| slope | Slope of the peak exercise ST segment |
| ca | Number of major vessels (0–3) colored by fluoroscopy |
| thal | Thallium heart scan result |
| num | Target variable: Presence of heart disease |



## 🧹 Data Preprocessing

### Missing Value Analysis
10 columns contained missing values. Two columns (`ca` and `thal`) had **critical missing levels (>50%)**.

| Column | Missing % | Severity |
|--------|-----------|----------|
| ca | 66.41% | Critical |
| thal | 52.83% | Critical |
| slope | 33.59% | High |
| fbs | 9.78% | Moderate |
| oldpeak | 6.74% | Moderate |
| trestbps | 6.41% | Moderate |
| thalch | 5.98% | Moderate |
| exang | 5.98 | Moderate |
| chol | 3.26% | Low |
| restecg | 0.22% | Negligible|

Dropping these columns would result in significant information loss.

✅ **Solution:** Applied **KNN Imputer** to impute missing values while preserving dataset integrity and improving model performance.



## 🤖 Models Trained

1. Logistic Regression  
2. Random Forest Classifier  
3. Support Vector Machine (SVM)  
4. K-Nearest Neighbors (KNN)



## 🧾 Model Performance Summary

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC | CV Mean Accuracy |
|------|---------|-----------|--------|----------|---------|------------------|
| Logistic Regression | 0.793 | 0.820 | 0.804 | 0.812 | 0.860 | 0.820 |
| Random Forest | 0.793 | 0.791 | 0.853 | 0.821 | 0.875 | 0.822 |
| SVM | 0.788 | 0.800 | 0.824 | 0.812 | 0.859 | 0.712 |
| KNN | **0.804** | 0.806 | 0.853 | **0.829** | 0.829 | 0.685 |



## 🏆 Best Model

### **Random Forest Classifier**

Chosen as the best model because it provides the strongest **balance across metrics**:

- Accuracy: **0.793**
- Recall: **0.853**
- AUC: **0.875**
- Cross-Validation Mean Accuracy: **0.822**

🎯 **Reason:** This model is powerful, stable, and generalizes well to new patients — making it suitable for **real-world medical prediction tasks**.



## 📂 Project Structure (if organiPreprocessing
