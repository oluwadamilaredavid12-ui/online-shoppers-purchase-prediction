# 🛒 Online Shoppers Purchasing Intention
## Team Daffodils | Group 4

> Exploratory Data Analysis on the Online Shoppers Purchasing Intention dataset to uncover behavioural patterns that predict customer purchases — by Team Daffodils.

---

## 📋 Project Overview

This project analyses the Online Shoppers Purchasing Intention dataset to understand what drives a website visitor to make a purchase. The work is organised across two Jupyter notebooks covering EDA, statistical analysis, and machine learning.

| Fact | Value |
|------|-------|
| Sessions | 12,205 |
| Features | 19 |
| Target | Revenue (1 = Purchase, 0 = No Purchase) |
| Class Balance | 84.4% No Purchase · 15.6% Purchase |
| Random State | 42 (all notebooks) |

---

## 📁 Repository Structure

```
online-shoppers-purchase-prediction/
├── 📁 data/
│   └── cleaned_online_shoppers_intention_for_viz.csv
├── Team_Daffodils_EDA_Complete.ipynb
├── ML_MODEL_DAFFODILS.ipynb
├── Model_Evaluation_Report.docx
├── requirements.txt
├── README.md
└── LICENSE
```

---

## 📓 Notebooks

### Notebook 1 — EDA & Statistical Analysis
**File:** `Team_Daffodils_EDA_Complete.ipynb`

**Part A — Exploratory Data Analysis (15 sections)**
- Class balance and target distribution
- Univariate and bivariate analysis
- Feature distributions by purchase outcome (boxplots, histograms, density plots)
- Correlation heatmap and revenue correlation bar chart
- Categorical analysis — Month, VisitorType, Weekend
- Traffic Type and Region analysis
- Outlier detection using the IQR method

**Part B — Statistical Analysis**
- Shapiro-Wilk & D'Agostino normality tests
- Mann-Whitney U & Chi-Square hypothesis tests
- Point-Biserial correlation
- Cohen's d effect sizes
- Logistic Regression odds ratios
- Random Forest feature importance
- VIF multicollinearity check
- Outlier detection & Excel export

---

### Notebook 2 — Machine Learning Pipeline
**File:** `ML_MODEL_DAFFODILS.ipynb`

**Models trained and compared:**
- Logistic Regression (interpretable baseline)
- Random Forest (ensemble)
- XGBoost (gradient boosting)

**Pipeline steps:**
- Feature engineering — 9 interaction & ratio features (e.g. Admin_TimePerPage, Engagement_Score, PageValue_Per_Product)
- Multicollinearity removal — features with |r| > 0.85 dropped
- Stratified 80/20 train/test split
- SMOTE applied inside each CV fold — no data leakage
- 5-fold stratified cross-validation
- Hyperparameter tuning
- Confusion matrix, ROC curve, feature importance charts for each model

**Evaluation metrics used:**
| Metric | Why |
|--------|-----|
| ROC-AUC | Overall discriminative ability |
| F1-Score | Balance of precision and recall for the minority class |
| Precision | How many predicted buyers actually bought |
| Recall | How many actual buyers were correctly identified |
| Accuracy | Overall — less reliable due to class imbalance |

---

## 📊 Key Findings

| # | Finding | Implication |
|---|---------|-------------|
| 1 | 84.4% No Purchase vs 15.6% Purchase (5.4:1 imbalance) | Use SMOTE + F1/AUC metrics, not raw accuracy |
| 2 | PageValues — strongest predictor (correlation 0.492) | Most dominant signal in every model |
| 3 | 80.6% of buyers have non-zero PageValues vs 11.6% non-buyers | PageValues > 0 is a near-definitive purchase signal |
| 4 | BounceRates & ExitRates lower for buyers | High engagement = higher conversion |
| 5 | November converts at 25.5% — February only 1.7% | Seasonal patterns are critical |
| 6 | All 10 numeric features are highly skewed | log1p transformation needed before modelling |
| 7 | XGBoost ROC-AUC 0.932 | Best discriminative ability |
| 8 | Random Forest F1 0.685 | Best precision-recall balance |

---

## ⚙️ Installation & Setup

**1. Clone the repository**
```bash
git clone git clone https://github.com/oluwadamilaredavid12-ui/online-shoppers-purchase-prediction.git
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Update the file path**

At the top of each notebook update the path to point to the CSV on your machine:
```python
DATA_PATH = r'your/local/path/to/cleaned_online_shoppers_intention_for_viz.csv'
```

**4. Run in this order**
```
Step 1 — Team_Daffodils_EDA_Complete.ipynb    (understand the data first)
Step 2 — ML_MODEL_DAFFODILS.ipynb             (build and evaluate models)
```

> Each notebook is self-contained and can also be run independently.

---

## 🛠️ Requirements

```
numpy
pandas
matplotlib
seaborn
scipy
scikit-learn
statsmodels
imbalanced-learn
xgboost
openpyxl
joblib
jinja2
```

Install all at once:
```bash
pip install -r requirements.txt
```

---

## 👥 Authors

**Group 4 — Team Daffodils 🌼**

- Dataset: UCI Machine Learning Repository — Online Shoppers Purchasing Intention Dataset
- All analysis and modelling done in Python 3
- `RANDOM_STATE = 42` used throughout for reproducibility
- Licence: MIT
