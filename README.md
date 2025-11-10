# 🫀 Comparative Analysis of Machine Learning Models for Heart Disease Prediction

This project investigates multiple machine learning models to predict the likelihood of heart disease based on clinical patient data. The goal is to compare models, evaluate performance metrics, and determine which model generalizes best to new unseen patients. By evaluating multiple models, we identify the most accurate, reliable, and generalizable approach.



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


### Handling Missing Data

Columns ca and thal had more than half of their values missing. Dropping them would result in major information loss and weaker models. Therefore, KNN Imputer was used to intelligently estimate and fill missing values based on similarity between patients. This preserved data patterns and improved predictive performance.

Preprocessing Steps

1. Identified and analyzed missing values.


2. Applied KNN Imputer to handle missing data.


3. Encoded categorical variables for model compatibility.


4. Scaled numerical values where needed.


5. Split dataset into training and test sets.


6. Trained and evaluated models.



## 🤖 Models Trained

1. Logistic Regression  
2. Random Forest Classifier  
3. Support Vector Machine (SVM)  
4. K-Nearest Neighbors (KNN)



## 🧾 Model Performance Summary

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC | CV Mean Accuracy |
|------|---------|-----------|--------|----------|---------|------------------|
| Logistic Regression | 0.793 | 0.820 | 0.804 | 0.812 | 0.860 | 0.820 |
| Random Forest | **0.793** | 0.791 | **0.853** | 0.821 | **0.875** | 0.822 |
| SVM | 0.788 | 0.800 | 0.824 | 0.812 | 0.859 | 0.712 |
| KNN | **0.804** | 0.806 | 0.853 | **0.829** | 0.829 | 0.685 |

The Random Forest model demonstrated the strongest performance:

Accuracy: 0.793

Recall: 0.853

AUC: 0.875

Cross-validation score: 0.822


This indicates that Random Forest not only makes accurate predictions but also generalizes well to unseen data.


## 🏆 Best Model

Although **KNN achieved the highest test F1-score**, it has **very low cross-validation performance (0.685)**, indicating **poor generalization**.

✅ **Random Forest Classifier** is the best performing and most reliable model because 

- Accuracy: **0.793**
- Recall: **0.853**
- AUC: **0.875**
- Cross-Validation Mean Accuracy: **0.822**

🎯 **Reason:** This model is powerful, stable, and generalizes well to new patients — making it suitable for **real-world medical prediction tasks**.



## 📂 Project Structure 

📁 project-root
├── notebooks/   
├── data/           
└── README.md




## ✅ Conclusion

The Random Forest model remains the best performing model overall.
Although KNN achieved the highest accuracy and F1-score on the test set, its very low cross-validation score (0.685) indicates that it does not generalize well and is likely overfitting.

Random Forest, on the other hand:

Has strong recall (0.853),

Highest ROC-AUC (0.875) meaning it separates classes best,

And highest CV Mean Accuracy (0.822) meaning it is the most stable and reliable across different subsets of the data.

Therefore, the **Random Forest Classifier** is recommended for real-world heart disease prediction due to its balance of accuracy, recall, AUC performance, and consistent generalization to new data.

Future improvements could include hyperparameter tuning, feature engineering, exploring additional ensemble methods, or deploying the model as a clinical decision support tool.

## 👩‍💻 Author
**Oluwakemi Akinsiku**


