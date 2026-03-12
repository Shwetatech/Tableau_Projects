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

## Project 2 — Error Management Dashboard

Monitors system errors across 6 global locations in real time. Covers daily trend analysis, severity breakdown, incident log, location comparison, and a weekly heatmap.

| KPI | Value |
|-----|-------|
| Total Errors (30d) | 4,821 |
| Critical Incidents | 183 |
| MTTR (Average) | 2.4 hours |
| Resolution Rate | 91% |

**Datasets used:**
- `project1_daily_errors.csv` — 30 days of error counts by severity
- `project1_incident_log.csv` — 25 individual incident records
- `project1_errors_by_location.csv` — Aggregated totals per location

**Key Calculated Fields:**
```tableau
// Rolling 7-Day Error Rate (LOD + Window)
WINDOW_SUM({ FIXED [Date] : SUM([Error Count]) }, -6, 0) 
  / WINDOW_SUM(SUM([Total Events]), -6, 0)

// MTTR — handles open incidents with NOW()
DATEDIFF('hour', [Created Timestamp], 
  IF [Status]='Resolved' THEN [Resolved Timestamp] ELSE NOW() END)
```

---

## Project 3 — KPI & Stakeholder Performance Dashboard

Tracks analytics delivery KPIs, user story completion, ad-hoc request turnaround, and Tableau calculated field performance for executive stakeholders.

| KPI | Target | Actual | Status |
|-----|--------|--------|--------|
| Dashboard Delivery Rate | 95% | 97% | ✅ On Track |
| Data Accuracy SLA | 99.5% | 99.2% | ⚠️ Watch |
| Error Resolution SLA | 90% | 85% | 🔴 At Risk |
| Ad-Hoc Turnaround | 48h | 36h | ✅ On Track |
| Calc Field Optimization | 20% | 28% | ⭐ Exceeded |
| Stakeholder CSAT | 4.5/5 | 4.7/5 | ⭐ Exceeded |

**Datasets used:**
- `project2_kpi_scorecard.csv` — 10 KPI metrics with targets and RAG status
- `project2_user_stories.csv` — 15 user stories with team, priority, and timeline
- `project2_monthly_kpi_trend.csv` — 6-month trend across all KPIs

**Key Calculated Fields:**
```tableau
// Weighted Severity Score
([Critical]*4 + [High]*3 + [Medium]*2 + [Low]*1) / [Total Errors]

// Story Completion Rate
SUM(IF [Status]='Done' THEN 1 ELSE 0 END) / COUNT([Story ID])
```

---

## Project 4 — Global Operations Dashboard

Unified global view across 6 international locations. Features a dashboard health radar, cross-region error comparison, user story tracker, and live activity feed.

| Location | Open Errors | Uptime | Health Score |
|----------|-------------|--------|--------------|
| Frankfurt 🇩🇪 | 12 | 99.4% | 88 |
| Singapore 🇸🇬 | 8 | 99.7% | 91 |
| Chicago 🇺🇸 | 3 | 99.9% | 96 |
| London 🇬🇧 | 4 | 99.8% | 94 |
| Dubai 🇦🇪 | 5 | 99.6% | 90 |
| São Paulo 🇧🇷 | 2 | 99.9% | 97 |

**Datasets used:**
- `project3_location_status.csv` — Real-time KPIs per location
- `project3_weekly_errors_by_region.csv` — Error counts by day and region
- `project3_dashboard_health_radar.csv` — 6-dimension health scores vs targets
- `project3_activity_log.csv` — Collaboration events across teams

**Dashboard Health Radar Dimensions:**

| Dimension | Current | Target |
|-----------|---------|--------|
| Accuracy | 92 | 95 |
| Performance | 88 | 90 |
| Coverage | 76 ⚠️ | 90 |
| Stability | 95 | 95 |
| Adoption | 82 | 90 |
| Freshness | 90 | 95 |

---

## Project 5 -  Online Retail Analytics 

 **📌 Project Overview:**
This project analyzes online retail data to uncover insights about country performance, customer buying behavior, product profitability, and RFM-based customer segmentation. The dashboard empowers business teams to make data-driven decisions.

   **📊 Key Insights:**
- EIRE, Netherlands, and Germany are top performers outside the UK.
- EIRE shows the strongest sales growth in the last 3 months.
- 19% of customers spend more on their second purchase.
- Majority of customers are one-time buyers.
- RFM segmentation identifies 262 Best Customers and 937 Occasional Buyers.
- Top product: POST ($27,204). Lowest: 22941 ($9).

 **🧩 Dashboard Components:**
1. Country Performance Overview  
2. Monthly Sales Trend  
3. Customer Purchase Behaviour  
4. Product Profitability  
5. RFM Segmentation  

 **🛠 Tools Used:**
- Tableau  
- Excel  
- Data Cleaning & Preparation  

---

## 🚀 How to Use

### Connect CSVs or Excel to Tableau
1. Open Tableau Desktop
2. Click **Connect → Text File**
3. Select a `.csv` from the `/datasets/` folder
4. Build views using the field names documented in each report

### Open HTML Dashboards
Open any `.html` file in the `/dashboards/` folder directly in a browser — no server needed. Dashboards use Chart.js (loaded from CDN) and are fully interactive.

### Read the Reports
Open any `.docx` file from `/reports/` in Microsoft Word, Google Docs, or LibreOffice. Each report includes executive summary, KPI analysis, dataset documentation, calculated field code, and recommendations.

---


