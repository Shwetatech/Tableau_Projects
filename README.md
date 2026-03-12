# Tableau_Projects
A collection of interactive Tableau dashboards designed to transform raw data into clear, insightful, and visually compelling stories. This repository showcases end‑to‑end data analysis workflows—from data cleaning and preparation to visualization and interpretation.
# What’s Inside
- Interactive Dashboards: Professionally designed Tableau visualizations for business, education, and exploratory analytics.
- Datasets: Cleaned and structured datasets used for building dashboards.
- Documentation: Step‑by‑step explanations, insights, and key findings for each project.
- Project Files: Tableau workbooks (.twb / .twbx) for easy reuse and customization.
# Purpose
This repository serves as a portfolio of Tableau skills, demonstrating:
- Data storytelling
- Dashboard design best practices
- KPI tracking and performance analysis
- Trend identification and decision‑support insights

# Project 1: Heart Disease Prediction
## Project Overview
This project investigates the prediction of heart disease presence or absence in patients using the **Statlog (Heart) Dataset** from Kaggle. It combines exploratory data analysis (EDA) in Tableau with supervised machine learning (J48 Decision Tree) in Weka to uncover patterns in clinical data.

**Key Question:** Can we predict whether a patient has heart disease based on clinical attributes like cholesterol, blood pressure, thalassemia, and chest pain type?
## 📊 Dataset

| Property | Details |
|---|---|
| **Source** | [Statlog (Heart) Dataset — Kaggle](https://www.kaggle.com/) |
| **Institutions** | Cleveland Clinical Foundation, Hungarian Institute of Cardiology, V.A. Medical Center (Long Beach) |
| **Instances** | 270 patients |
| **Attributes** | 14 (13 features + 1 target class) |
| **Target Variable** | `Class`: `0 = No Disease`, `1 = Disease Present` |
| **Missing Values** | None |
| **Outliers** | None |

### Attribute Summary

| # | Attribute | Type | Description |
|---|---|---|---|
| 1 | Age | Numerical | Patient age (29–77 years) |
| 2 | Sex | Binary | 0 = Female, 1 = Male |
| 3 | CP | Categorical | Chest pain type (4 types) |
| 4 | BP | Numerical | Resting blood pressure (94–200) |
| 5 | Chol | Numerical | Serum cholesterol (116–409) |
| 6 | B_sugar | Binary | Fasting blood sugar (0=Normal, 1=High) |
| 7 | ECG | Categorical | Resting ECG result (0–2) |
| 8 | H_Rate | Numerical | Maximum heart rate (71–200) |
| 9 | Ex_Angina | Binary | Exercise-induced angina (0=No, 1=Yes) |
| 10 | Oldpeak | Numerical | ST depression induced by exercise |
| 11 | Slope | Categorical | Slope of peak exercise ST segment |
| 12 | Vessel | Categorical | Major vessels coloured by fluoroscopy (0–3) |
| 13 | Thalassemia | Categorical | Defect type (Normal / Fixed / Reversible) |
| 14 | Class | Target | Heart disease absent (0) or present (1) |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Tableau** | Exploratory Data Analysis & Visualization |
| **Weka** | Data Mining (J48 Decision Tree Algorithm) |
| **Microsoft Excel** | Data Pre-processing & Categorization |

---

## 📈 Key Findings

### From Tableau EDA

- **120 patients** have heart disease; **150** do not (44.4% vs 55.6%)
- **37% of males** have heart disease vs only **7.4% of females**
- Most common age group with heart disease: **U60 (50–59 years)**
- High BP + High-Risk Cholesterol affects **76 individuals**
- Patients with **coloured vessels + high cholesterol** are at significantly elevated risk
- Exercise-induced angina is a strong indicator — males show much higher rates

### From Weka J48 Decision Tree

- **Classification Accuracy: 92.3%** (87 instances, 66% train/test split)
- **Confusion Matrix:** 45 TP, 40 TN, 4 FP, 3 FN
- **ROC Area: 0.964** (excellent discrimination)
- **Tree Size:** 17 nodes, 11 leaves (pruned)

### Decision Tree Rules

1. Vessels = Coloured + Chol = High Risk → **Disease PRESENT**
2. Vessels = Coloured + Chol = Normal → **Disease ABSENT**
3. Vessels = Coloured + Chol = High + Thalassemia = No → **Disease ABSENT**
4. Vessels = Coloured + Chol = High + Thalassemia = Fixed/Reversible → **Disease PRESENT**
5. Vessels = Not Coloured + CP = Asymptomatic + BP = High → **Disease PRESENT**
6. Vessels = Not Coloured + CP = Typical Angina + B_sugar = High → **Disease PRESENT**
7. Vessels = Not Coloured + CP = Non-anginal/Atypical → **Disease ABSENT**

---

## 🔄 Methodology

```
Raw Dataset
    │
    ▼
Data Pre-processing (Excel)
  • Numerical → Categorical conversion
  • Age grouped: U30–U80
  • Chol: Normal / High / High Risk
  • BP: Normal / High
  • H_Rate: Normal / High
  • Oldpeak: Low / High
    │
    ▼
Exploratory Data Analysis (Tableau)
  • Distribution analysis
  • Top-N parameter filtering
  • Correlation visualizations
  • Multi-attribute relationship views
    │
    ▼
Data Mining (Weka — J48 Algorithm)
  • 66% train / 34% test split
  • Cross-validation: 10 folds
  • Pruned decision tree (C=0.25, M=2)
    │
    ▼
Results & Insights
```

---

## 📂 Project Structure

```
heart-disease-analysis/
├── data/
│   ├── heart_disease_raw.csv          # Original dataset
│   └── heart_disease_categorical.csv  # Pre-processed dataset
├── tableau/
│   └── heart_disease_dashboard.twbx   # Tableau workbook
├── weka/
│   └── heart_disease_model.arff       # Weka-ready ARFF file
├── report/
│   └── Heart_disease_analysis.pdf     # Full coursework report
└── README.md
```

---

## 🧠 Algorithm: J48 Decision Tree

The **J48** algorithm (Weka's implementation of C4.5) was selected because:

- The dataset has a clear **categorical target variable** (present/absent)
- Decision trees handle both **numerical and categorical** features effectively
- Results are **interpretable** — producing readable IF-THEN rules
- Strong performance on **small-to-medium datasets** (270 instances)
- Pruning reduces overfitting and improves generalizability

---

## ⚖️ Data Ethics

This project involves sensitive health data. Key ethical considerations include:

- **Informed Consent** — Participants must be aware of how their data is used
- **Bias** — The dataset skews male (183 males vs 87 females); findings may not generalize equally
- **Privacy** — Data must be anonymized and stored securely per **GDPR** guidelines
- **Transparency** — Predictive models in healthcare must be explainable and auditable
- **Data Security** — Clinical data is a high-value target; robust protection is essential

---

## 📉 Limitations

- Small dataset (270 instances) — results may not generalize to broader populations
- Gender imbalance (68% male) may skew predictions
- Dataset drawn from only 3–4 institutions, limiting geographic diversity
- Categorical conversion of continuous variables may lose predictive granularity

---

## 🚀 Future Work

- [ ] Expand dataset size for improved generalization
- [ ] Test additional algorithms: Random Forest, SVM, Neural Networks
- [ ] Build a web-based prediction tool using the trained model
- [ ] Incorporate additional risk factors (lifestyle, family history)
- [ ] Address class and gender imbalance with SMOTE or similar techniques

---

## 📚 References

- Decision Tree Algorithm Examples in Data Mining — softwaretestinghelp.com
- What Is Data Ethics? — Cognizant
- What is Data Mining? — TechTarget
- What is GDPR? — gdpr.eu
- Statlog (Heart) Dataset — UCI Machine Learning Repository / Kaggle

---

## 🏫 Academic Context

| Field | Details |
|---|---|
| **Module** | Business Intelligence (CST3340) |
| **Institution** | Middlesex University London |
| **Department** | Computer Engineering & Informatics |
| **Academic Year** | 2021–22 |
| **Submission** | April 15, 2022 |

