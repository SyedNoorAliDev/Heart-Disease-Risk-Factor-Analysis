# Heart-Disease-Risk-Factor-Analysis
Statistical analysis of the UCI Heart Disease dataset — SQL queries, conditional probability, Bayesian inference, and distribution modeling to identify clinical risk factors.

A full-stack data analysis project using the UCI Irvine Heart Disease dataset. This notebook walks through SQL-based exploration, data cleaning, feature engineering, descriptive statistics, conditional probability, Bayesian inference, and probability distribution modeling — all documented for a non-technical audience and concluded with a clinical recommendation memo.

---

## 🎯 Objective

This project answers four core questions:

1. **Which patient characteristics are the strongest predictors of heart disease?**
2. **How does risk change conditionally — given sex, age, cholesterol, or blood pressure?**
3. **Can we apply Bayes' Theorem to invert a diagnosis and reason backwards about patient demographics?**
4. **What do statistical distributions tell us about rare events like patient surges?**

The goal is not just to output numbers, but to translate each finding into a clinically actionable insight.

---

## 📂 Dataset

| Property | Details |
|---|---|
| **Source** | [UCI Machine Learning Repository — Heart Disease Dataset](https://archive.ics.uci.edu/dataset/45/heart+disease) |
| **Origin** | Cleveland Clinic Foundation |
| **Size** | 920 patients × 14 features |
| **Target Variable** | `num` — diagnosis severity (0 = no disease, 1–4 = increasing severity), binarized to `target` (0/1) |

**Key features include:** age, sex, resting blood pressure (`trestbps`), cholesterol (`chol`), fasting blood sugar (`fbs`), max heart rate achieved (`thalach`), and exercise-induced angina (`exang`).

---

## 🛠️ Tools & Technologies

| Category | Tools |
|---|---|
| **Language** | Python 3 |
| **Data Manipulation** | Pandas, NumPy |
| **Database / SQL** | SQLite3 (in-memory), SQL via `pd.read_sql` |
| **Visualization** | Matplotlib, Seaborn |
| **Statistical Modeling** | SciPy (`scipy.stats` — Normal, Binomial, Poisson distributions) |
| **Math / Combinatorics** | Python `math` module |
| **Environment** | Jupyter Notebook / Google Colab |

---

## 🔍 Key Findings

### 1. Sex Is the Strongest Binary Risk Differentiator
The conditional probability of heart disease among **male patients is ~0.55**, compared to **~0.26 for female patients** — more than double the rate. Sex alone is the single most discriminating feature in this dataset.

### 2. The 51–60 Age Bracket Carries the Highest Disease Burden
Age-stratified analysis shows a sharp spike in heart disease rate during the sixth decade of life. This is the most critical intervention window before disease becomes entrenched.

### 3. Cholesterol Alone Is a Weaker Predictor Than Expected
Patients with high cholesterol (>240 mg/dL) show a modestly elevated disease probability compared to normal-cholesterol patients — but the gap is smaller than conventional wisdom suggests. **Cholesterol must be evaluated alongside blood pressure and sex to be clinically meaningful.**

### 4. Hospital Surge Days Are Statistically Predictable
Modeling patient arrivals as a Poisson process (λ = 3/day), there is an **~18% probability of 5 or more critical cardiac patients on any given day** — roughly 1 in every 5.5 operating days. This is a quantified basis for staffing decisions.

---

## 📊 Visualizations

| Chart | What It Shows |
|---|---|
| Correlation Heatmap | Feature relationships and predictors of heart disease |
| Age-Stratified Bar Chart | Disease rate by decade — identifies the highest-risk age window |
| Conditional Probability Bar Chart | P(Heart Disease) given each clinical risk factor |
| Box Plots | Cholesterol & blood pressure distributions: Disease vs. No Disease |
| Normal Distribution Fit | Cholesterol modeled with Gaussian PDF overlay |
| Binomial PMF | Probability distribution of disease cases in a group of 10 |
| Poisson PMF | Daily cardiac patient arrival model with annotated P(X ≥ 5) |

---

## 🏥 Conclusion (Recommendation Memo)

> **Hospitals should prioritize dual-threshold screening — cholesterol > 240 mg/dL AND blood pressure > 130 mmHg — in male patients aged 50–60.** This cohort combines the highest-risk sex profile, the most vulnerable age window, and the two most strongly correlated modifiable risk factors. An automated EHR flag for this demographic would capture the majority of preventable diagnoses.

> **Cholesterol screening alone is insufficient.** A multi-factor scoring approach incorporating age, sex, blood pressure, and fasting blood sugar will substantially outperform any single-variable screening rule.

> **Emergency departments should staff for cardiac surge capacity on approximately 1 in 5 days**, based on the Poisson model at λ = 3 arrivals/day.

---

## ▶️ How to Run

**Option 1 — Google Colab (recommended, no setup required):**
1. Upload `Heart_Disease_Risk_Factor_Analysis.ipynb` to [Google Colab](https://colab.research.google.com/)
2. Upload `heart_disease_uci.csv` to the Colab session files
3. Click **Runtime → Run All**

**Option 2 — Jupyter Notebook (local):**
```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# Launch Jupyter
jupyter notebook Heart_Disease_Risk_Factor_Analysis.ipynb
```

Make sure `heart_disease_uci.csv` is in the same directory as the notebook before running.

---

## 📁 Repository Structure

```
heart-disease-analysis/
│
├── Heart_Disease_Risk_Factor_Analysis.ipynb   # Main analysis notebook
├── heart_disease_uci.csv                      # Dataset (UCI Cleveland)
└── README.md                                  # This file
```

---

## 📜 Data Source Credit

Janosi, A., Steinbrunn, W., Pfisterer, M., & Detrano, R. (1988).
*Heart Disease.* UCI Machine Learning Repository.
[https://doi.org/10.24432/C52P4X](https://doi.org/10.24432/C52P4X)
