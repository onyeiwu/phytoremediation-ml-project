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

Model	CV Mean R²	CV STD	Test R²	MAE	RMSE	MSE
0	XGBoost	0.6754	0.2586	0.9361	101.2310	150.4008	22620.3955
1	Decision Tree	0.5590	0.2793	0.9156	126.5079	172.8249	29868.4459
2	Random Forest	0.8097	0.0513	0.8659	129.1698	217.8024	47437.8907
3	Linear Regression	0.5924	0.0884	0.7356	225.5348	305.8236	93528.0463


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
Python 3.x
Pandas Data manipulation
NumPy Numerical computation
Matplotlib Data visualization
Seaborn Statistical visualization
Scikit-learn Machine learning models
XGBoost Gradient boosting model
Joblib Model saving and loading
Jupyter Interactive development

---

## 📁 Project Structure

phytoremediation-ml-project/
│
├── Chemistry Dataset.ipynb # Main Jupyter Notebook
├── best_xgboost_model.pkl # Saved best model
├── phytoremediation_dataset.csv # Dataset
├── images/ # Visualization screenshots
│ ├── actual_vs_predicted.png
│ ├── residual_plot.png
│ └── feature_importance.png
└── README.md # Project documentation

---

## 👨‍💻 Author

**Onyeiwu Gabriel Chibuzor**
University Project — Department of [Your Department]
Supervised by: [Your Supervisor Name]

---

## 📜 License

This project is submitted as an academic project.
All rights reserved © 2026 Onyeiwu Gabriel Chibuzor
