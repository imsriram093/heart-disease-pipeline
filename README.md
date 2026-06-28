# **🫀 Heart Disease Diagnosis Prediction Pipeline**

An end-to-end medical data engineering and machine learning optimization pipeline. This project ingests diagnostic health metrics from the UCI Machine Learning repository, models relational structural boundaries using SQLite, evaluates baseline performance anomalies, and tunes a Random Forest Classifier to project generalizable patient outcomes with high accuracy.

## **📂 Repository Architecture**

* **data/raw/**: Untouched original source file extraction.  
* **data/gold/**: Cleansed diagnostic data optimized for modeling pipelines.  
* **database/**: Production-ready normalized relational SQLite database system.  
* **notebooks/**: Comprehensive data science exploratory analysis, hypothesis metrics validation, and optimization code.

## **🗃️ Relational Schema & Database Boundaries (Part 3\)**

To minimize record redundancy and maintain clinical tracking integrity, the 14 source columns are parsed into 3 distinct normalized entities:

* **Patients table**: Houses direct demographic keys (age, sex).  
* **Clinical\_Metrics table**: Documents vital clinical check parameters (cp, trestbps, chol, fbs, restecg) mapped via strict schema validation fences.  
* **Test\_Results table**: Archives exercise stress test diagnostic outcomes (thalach, exang, oldpeak, slope, ca, thal, target).

\-- Normalization constraint mapping pattern example  
CREATE TABLE Patients (  
    patient\_id INTEGER PRIMARY KEY AUTOINCREMENT,  
    age INTEGER NOT NULL CHECK (age \>= 0 AND age \<= 120),  
    sex INTEGER NOT NULL CHECK (sex IN (0, 1))  
);

## **📊 Core Data Science Metrics & Insights (Part 4\)**

### **Strongest Predictive Risk Indicators**

Our exploratory correlation diagnostics programmatically isolated the three defining clinical predictors scaling core output outcomes:

1. **thalach (Max Heart Rate achieved)**: Normal performance drops under high stress mark prominent indicator boundaries.  
2. **cp (Chest Pain Type)**: Specific symptomatic representations dictate definitive tree partitions.  
3. **ca (Major Vessels by Fluoroscopy)**: Direct structural checks mapping localized vascular restrictions.

### **Validated Diagnostic Hypotheses**

* **Gender Disparity Matrix**: Checked metrics highlight that male patient profiles carry a significantly higher baseline diagnosis distribution percentage (\~55.3%) compared to female profiles (\~25.8%).  
* **ST Depression (oldpeak)**: Positive correlation checking shows abnormal segment depression levels scale nearly three times higher among positive target diagnostics.

## **🤖 Machine Learning Model Tuning Summary (Part 5\)**

### **Baselines Cross-Validation Results**

* **Logistic Regression Baseline**: 83.16% accuracy  
* **Gradient Boosting Baseline**: 79.51% accuracy  
* **Random Forest Baseline**: 83.81% accuracy

### **Post-Tuning Optimization Improvements (GridSearchCV)**

Our baseline Random Forest implementation showed structural overfitting constraints, executing at **100.00% training accuracy** while falling to **88.52% on testing splits**. By applying hyperparameter bounds via GridSearchCV (max\_depth: 5, min\_samples\_split: 10, n\_estimators: 100), tree complexity was successfully pruned:

| Model Stage Configuration | Train Accuracy (%) | Test Accuracy (%) | Overfitting Variance Gap |
| :---- | :---- | :---- | :---- |
| **Baseline Configuration** | 100.00% | 88.52% | 11.48% gap |
| **Optimized Tuned System** | 90.91% | **91.80%** | **\-0.89%** (Normalized) |

## **🧬 Feature Interpretation Analysis via SHAP**

Our models integrate unified SHAP interpretability metrics to detail specific patient prediction paths. For individual validation checks (e.g., Patient 0), local probability expectations trace precisely how protective components (like ca \= 0 removing \-0.13 risk weight) shift clinical outcomes down into healthy diagnostic limits, neutralizing adjacent high-risk markers like advanced age.