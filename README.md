```markdown
# 🫀 Heart Disease Diagnosis Prediction Pipeline

An end-to-end medical data engineering and machine learning optimization pipeline. This project ingests diagnostic health metrics from the UCI Machine Learning repository, models relational structural boundaries using SQLite, evaluates baseline performance anomalies, and tunes a Random Forest Classifier to project generalizable patient outcomes with high accuracy.

---

## 📂 Repository Architecture
* [cite_start]**`data/raw/`**: Untouched original source file extraction[cite: 330].
* [cite_start]**`data/gold/`**: Cleansed diagnostic data optimized for modeling pipelines[cite: 334].
* [cite_start]**`database/`**: Production-ready normalized relational SQLite architecture system[cite: 341].
* [cite_start]**`notebooks/`**: Comprehensive data science exploratory analysis, hypothesis metrics validation, and optimization code[cite: 386, 395, 426].

---

## 🗄️ Relational Schema & Database Boundaries (Part 3)
[cite_start]To minimize record redundancy and maintain clinical tracking integrity, the 14 source columns are parsed into 3 distinct normalized entities [cite: 341-343]:

* [cite_start]**`Patients` table**: Houses direct demographic keys (`age`, `sex`)[cite: 344].
* [cite_start]**`Clinical_Metrics` table**: Documents vital clinical check parameters (`cp`, `trestbps`, `chol`, `fbs`, `restecg`) mapped via strict schema validation fences[cite: 345].
* [cite_start]**`Test_Results` table**: Archives exercise stress test diagnostic outcomes (`thalach`, `exang`, `oldpeak`, `slope`, `ca`, `thal`, `target`)[cite: 346].

```sql
-- Normalization constraint mapping pattern example
CREATE TABLE Patients (
    patient_id INTEGER PRIMARY KEY AUTOINCREMENT,
    age INTEGER NOT NULL CHECK (age >= 0 AND age <= 120),
    sex INTEGER NOT NULL CHECK (sex IN (0, 1))
);
```

---

## 📊 Core Data Science Metrics & Insights (Part 4)

### Strongest Predictive Risk Indicators
Our exploratory correlation diagnostics programmatically isolated the three defining clinical predictors scaling core output outcomes:
1. [cite_start]**`thalach` (Max Heart Rate achieved)**: Normal performance drops under high stress mark prominent indicator boundaries [cite: 402, 431-432].
2. [cite_start]**`cp` (Chest Pain Type)**: Specific symptomatic representations dictate definitive tree partitions [cite: 423, 469, 472-473].
3. [cite_start]**`ca` (Major Vessels by Fluoroscopy)**: Direct structural checks mapping localized vascular restrictions [cite: 469, 474-475].

### Validated Diagnostic Hypotheses
* [cite_start]**Gender Disparity Matrix**: Checked metrics highlight that male patient profiles carry a significantly higher baseline diagnosis distribution percentage (~55.3%) compared to female profiles (~25.8%) [cite: 440-441].
* [cite_start]**ST Depression (`oldpeak`)**: Positive correlation checking shows abnormal segment depression levels scale nearly three times higher among positive target diagnostics [cite: 448-449].

---

## 🤖 Machine Learning Model Tuning Summary (Part 5)

### Baselines Cross-Validation Results
* [cite_start]**Logistic Regression Baseline**: 83.16% accuracy [cite: 458]
* [cite_start]**Gradient Boosting Baseline**: 79.51% accuracy [cite: 458]
* [cite_start]**Random Forest Baseline**: 83.81% accuracy [cite: 458, 461]

### Post-Tuning Optimization Improvements (`GridSearchCV`)
[cite_start]Our baseline Random Forest implementation showed structural overfitting constraints, executing at **100.00% training accuracy** while falling to **88.52% on testing splits**[cite: 502, 504]. [cite_start]By applying hyperparameter bounds via `GridSearchCV` (`max_depth: 5`, `min_samples_split: 10`, `n_estimators: 100`), tree complexity was successfully pruned[cite: 502, 506]:

| Model Stage Configuration | Train Accuracy (%) | Test Accuracy (%) | Overfitting Variance Gap |
| :--- | :---: | :---: | :---: |
| **Baseline Configuration** | 100.00% | 88.52% | [cite_start]11.48% gap [cite: 502] |
| **Optimized Tuned System** | 90.91% | **91.80%** | [cite_start]**-0.89%** (Normalized) [cite: 502] |

---

## 🧬 Feature Interpretation Analysis via SHAP
[cite_start]Our models integrate unified SHAP interpretability metrics to detail specific patient prediction paths[cite: 487]. [cite_start]For individual validation checks (e.g., Patient 0), local probability expectations trace precisely how protective components (like `ca = 0` removing -0.13 risk weight) shift clinical outcomes down into healthy diagnostic limits, neutralizing adjacent high-risk markers like advanced age [cite: 494-498].
