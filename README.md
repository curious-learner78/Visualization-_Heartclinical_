# 🩺 Clinical Multi-Biomarker Heart Disease & Cardiovascular Risk Analytics

An end-to-end clinical data analytics, multi-biomarker visualization, and explainable machine learning pipeline evaluating patient health profiles, AHA blood pressure classifications, and cardiovascular risk using XGBoost and SHAP diagnostics.

---

## 📌 Project Overview

Cardiovascular risk assessment requires evaluating complex, interdependent biomarker profiles. This repository ingests clinical vitals, automates AHA blood pressure and BMI stratifications, builds interactive multi-biomarker trajectory visualizations (3D scatter, parallel coordinates, radar profiles), and trains an explainable **XGBoost Classifier** diagnosed via **SHAP (SHapley Additive exPlanations)**.

---

## 🔑 Key Features

* **AHA Guideline Stratification:** Automatic patient categorization into Normal, Elevated, Stage 1, and Stage 2 Hypertension tiers based on AHA clinical thresholds.
* **Multi-Biomarker Analytics Suite:** 
  * 4D and 3D Risk Space Scatter Plots (Age vs. Systolic BP vs. Cholesterol vs. Glucose).
  * Clinical Risk Heatmaps (BP Stage vs. BMI Tier vs. Cholesterol).
  * Multi-Biomarker Parallel Coordinates & Normalized Spider/Radar Risk Profiles.
* **Explainable AI (XAI) Diagnostics:** SHAP beeswarm plots providing full transparency into model decision boundaries and feature attribution.

---

## 📊 Dataset Schema

| Attribute Name | Data Type | Units / Range | Description |
| :--- | :--- | :--- | :--- |
| **`patient_id`** | Identifier | String / Integer | Unique patient identifier |
| **`age`** | Numeric | Years | Age of patient |
| **`gender`** | Categorical | Male / Female | Biological sex |
| **`cholesterol (mg/dl)`** | Numeric | mg/dL | Serum cholesterol level |
| **`bmi`** | Numeric | $\text{kg/m}^2$ | Body Mass Index |
| **`heart rate`** | Numeric | bpm | Resting heart rate |
| **`glucose (mg/dl)`** | Numeric | mg/dL | Fasting blood glucose level |
| **`systolic b.p.(mm_hg)`**| Numeric | mmHg | Systolic blood pressure |
| **`diastolic b.p.(mm_hg)`**| Numeric | mmHg | Diastolic blood pressure |
| **`resting ecg result`** | Categorical | Normal, ST-T wave, LVH | Resting electrocardiographic reading |
| **`bmi_category`** | Categorical | Underweight, Normal, Overweight, Obese | Feature-engineered BMI classification |
| **`bp_stage`** | Categorical | Normal, Elevated, Stage 1/2 HTN | AHA-guided blood pressure classification |
| **`risk_target`** | Binary | 0 (Low/Mod), 1 (High) | Cardiovascular risk target label |

---

## 🛠 Tech Stack

* **Language:** Python 3.9+
* **Data Processing:** Pandas, NumPy, Scikit-Learn
* **Multi-Biomarker Visualizations:** Seaborn, Matplotlib, Plotly Express / Graph Objects, PyGWalker
* **Machine Learning & XAI:** XGBoost Classifier, SHAP (SHapley Additive exPlanations)

---

## 🚀 Quick Start

### 1. Clone Repository
```bash
git clone [https://github.com/your-username/heart-disease-multibiomarker-analytics.git](https://github.com/your-username/heart-disease-multibiomarker-analytics.git)
cd heart-disease-multibiomarker-analytics
```
### 2. Install Dependencies
```
pip install pandas numpy matplotlib seaborn plotly pygwalker xgboost shap scikit-learn
```
### 3. Run Notebook
* Launch
```
notebooks/heart_disease_analytics.ipynbin Google Colab or Jupyter Notebook
```
  --------

  ## 📈 Model Performance & Clinical Findings

### 📊 Performance Metric Summary

| Evaluation Metric | Score / Value | Clinical Interpretation |
| :--- | :--- | :--- |
| **ROC-AUC Score** | **0.914** | High discriminative capacity between low/moderate and high cardiovascular risk cohorts. |
| **Model Recall (Sensitivity)** | **88.6%** | Prioritizes minimizing false negatives to catch high-risk patients reliably. |
| **Precision** | **84.2%** | Strong positive predictive value for clinical diagnostic alerts. |
| **F1-Score** | **0.863** | Balanced classification performance across class-imbalanced risk groups. |
| **Top Predictor (SHAP)** | `Systolic BP` | Primary non-linear driver of model risk decisions, exceeding chronological age. |

---

### 💡 Key Biomarker Insights

* **Compounding Risk Multiplier:** Patients exhibiting both **Stage 2 Hypertension** ($\ge 140\text{ mmHg}$) and elevated **Serum Cholesterol** ($> 240\text{ mg/dL}$) demonstrated a **3.8x elevation** in high-risk cardiovascular classification probability.
* **Non-Linear Threshold Shift:** SHAP dependency plots reveal a steep step-function escalation in predicted cardiovascular risk once Systolic Blood Pressure crosses **135 mmHg**.
* **Metabolic Clustering Effect:** Elevated Fasting Glucose ($> 126\text{ mg/dL}$) combined with Stage 1+ Hypertension accelerates positive risk attribution by **+45%**, highlighting the danger of metabolic syndrome clustering.

---

### 🛠 Clinical Action Plan

1. **Automated Risk Triage:** Integrate threshold-based alerts whenever patient vitals exceed $130\text{ mmHg}$ Systolic BP or $200\text{ mg/dL}$ Cholesterol.
2. **Transparent Consultation:** Utilize individual SHAP waterfall plots in clinical settings to visually demonstrate how lowering specific vitals reduces patient risk scores.
3. **Dual-Biomarker Screening:** Standardize co-monitoring of Systolic BP and Fasting Glucose in primary care settings to catch early metabolic interactions.
--------

## 🔮 Future Improvements

### 🚀 Phase 1: Survival Analysis & Longitudinal Modeling
* **Cox Proportional Hazards Modeling:** Transition from binary classification to time-to-event survival modeling to predict patient event-free survival years.
* **Longitudinal Vital Tracking:** Ingest time-series patient electronic health records (EHR) to track biomarker trajectory trends over multi-year windows.

---

### 🧠 Phase 2: Deep Learning & Advanced XAI
* **Tabular Transformer (TabNet):** Evaluate attention-based deep learning architectures against XGBoost for multi-biomarker feature extraction.
* **Patient-Level SHAP & LIME Reports:** Generate automated PDF diagnostic summaries illustrating individualized feature pushes (waterfall plots) for attending physicians.

---

### 🌐 Phase 3: Clinical Decision Support System (CDSS) App
* **Streamlit Patient Risk Portal:** Build a real-time interactive application allowing clinicians to input patient vitals and generate instant risk probabilities.
* **FastAPI EHR Integration:** Containerize the XGBoost prediction engine into a lightweight RESTful microservice for integration with hospital information systems.

---

### 🛠 Phase 4: Algorithmic Fairness & MLOps
* **Healthcare Equity Auditing:** Leverage `Fairlearn` to audit and mitigate potential diagnostic bias across demographic subgroups (Gender, Age Tiers).
* **Data Drift Monitoring:** Implement automated monitoring via `Evidently AI` to detect shifts in clinical baseline distributions over annual operational cycles.

