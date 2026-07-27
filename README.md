# 🌿 Phytoremediation Prediction Using Machine Learning

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![ML](https://img.shields.io/badge/Machine%20Learning-XGBoost-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Project Overview

This project investigates the use of **Machine Learning** to predict 
**Remediation Time (RT)** — the number of weeks required for 
selected plant species to completely extract heavy metals from 
contaminated soil through a process called **Phytoremediation**.

Phytoremediation is an eco-friendly, cost-effective approach to 
environmental cleanup that uses plants to absorb, accumulate, and 
remove toxic heavy metals from polluted soil.

---

## 🎯 Problem Statement

Heavy metal contamination of soil poses a serious threat to human 
health, agriculture, and ecosystems. Traditional soil remediation 
methods are expensive and disruptive. This project explores whether 
Machine Learning can accurately predict how long it will take for 
specific plant species to clean contaminated soil — helping 
environmental scientists plan cleanup projects more efficiently.

---

## 📂 Dataset Description

The dataset contains **150 observations** and **17 variables** 
collected from a phytoremediation experiment involving:

- **5 Plant Species** — Talinum triangulare, Corchorus capsularis, 
  Vigna unguiculata, Helianthus annuus, Amaranthus spinosus
- **6 Heavy Metals** — Fe, Zn, Cd, Pb, Cu, Ni
- **5 Time Points** — Week 0, 2, 4, 6, 8

### Key Variables

| Variable | Description | Unit |
|----------|-------------|------|
| `C0_soil_initial` | Initial soil metal concentration | mg/kg |
| `Soil (So)` | Current soil metal concentration | mg/kg |
| `Root (Ro)` | Metal concentration in plant roots | mg/kg |
| `Leaf (Le)` | Metal concentration in plant leaves | mg/kg |
| `TF` | Transfer Factor — root to leaf movement | ratio |
| `pH` | Soil pH level | — |
| `CEC` | Cation Exchange Capacity | cmol(+)/kg |
| `OC` | Organic Carbon in soil | g/kg |
| `HM_x` | Heavy metal electronegativity | — |
| `HM_r` | Ionic radius of heavy metal | nm |
| `Yield` | Plant biomass produced | kg |
| `MER` | Metal Extraction Rate | % |
| `RT` | Remediation Time *(Target Variable)* | weeks |

---

## 🧹 Data Preprocessing

- Removed **Week 0 rows** — no remediation activity at baseline
- Extracted numeric week values from text e.g. `2 wks` → `2`
- Applied **OneHotEncoding** on `Plant` and `Metal` columns
- Applied **StandardScaler** on all numerical features
- Final cleaned dataset: **120 rows × 19 columns**

---

## 🤖 Machine Learning Models

Three regression models were trained and compared:

| Model | Description |
|-------|-------------|
| **Linear Regression** | Simple baseline model |
| **Decision Tree** | Ensemble of decision trees |
| **Random Forest** | Ensemble of decision trees |
| **XGBoost** | Gradient boosting — best performer |

### Model Evaluation Metrics

| Metric | Description |
|--------|-------------|
| **R²** | How much of the pattern the model explained |
| **MAE** | Average error in weeks |
| **RMSE** | Penalises large prediction errors |
| **MSE** | Mean squared prediction error |

---

## 📊 Results

### Model Comparison

| Model | R² Score | MAE | RMSE |
|-------|----------|-----|------|
| Linear Regression | — | — | — |
|Decision Tree | — | — | — |
| Random Forest | — | — | — |
| **XGBoost** ✅ | **0.9361** | **101.23** | **150.40** |

### 🏆 Best Model — XGBoost
- Model : XGBoost
- R² Score : 0.9361
- MAE : 101.23 weeks
- RMSE : 150.40 weeks
- MSE : 22620.39

> The XGBoost model explained **93.61%** of the variance in 
> Remediation Time — meaning it can predict with high accuracy 
> how long a plant will take to clean contaminated soil.

---

## 📈 Visualizations

### Actual vs Predicted RT
![Actual vs Predicted](images/actual_vs_predicted.png)

### Residual Plot
![Residual Plot](images/residual_plot.png)

### Feature Importance
![Feature Importance](images/feature_importance.png)

---

## 💡 Key Findings

- **Helianthus annuus** (Sunflower) showed the fastest remediation 
  time across most heavy metals
- **Cadmium (Cd)** and **Zinc (Zn)** were extracted more efficiently 
  than **Lead (Pb)**
- **Plant biomass (Yield)** and **week number** were the most 
  important predictors of RT
- Remediation time decreases significantly as weeks progress — 
  showing plants become more effective over time

---

## ✅ Recommendations

1. **Use Helianthus annuus** for heavy metal contaminated sites 
   requiring fast cleanup
2. **Monitor plants at 2-week intervals** as the model shows 
   significant improvement at each time point
3. **Combine multiple plant species** for sites contaminated with 
   multiple metals simultaneously
4. **Use the XGBoost model** to estimate cleanup timelines before 
   starting remediation projects

---

## 🛠️ Technologies Used
