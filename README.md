# 🏠 House Prices - Advanced Regression Techniques (Kaggle)

[![Kaggle Competition](https://img.shields.io/badge/Kaggle-Competition-20BEFF?style=for-the-badge&logo=kaggle)](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python)](https://www.python.org/)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=for-the-badge&logo=scikit-learn)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Gradient%20Boosting-EB5B2A?style=for-the-badge)](https://xgboost.readthedocs.io/)

An end-to-end machine learning solution for the Kaggle **House Prices** competition, combining **robust preprocessing**, **feature engineering**, and **strong regression models** to predict home sale prices in Ames, Iowa.

> **Leaderboard result**: Top **[ADD YOUR % / RANK]** on the official Kaggle leaderboard.

---

## 📊 Dataset

The dataset contains **79 explanatory variables** describing most aspects of residential homes (materials, room areas, neighborhood, zoning, proximity to roads/railways, basements/garages, etc.).

- **Training set**: 1460 rows, 81 columns (including `SalePrice`)
- **Feature types**:
  - Numerical: continuous + discrete
  - Categorical: nominal + ordinal

---

## 🛠️ Methodology

### 1) Data Cleaning & Missing Values

This competition is known for having many missing values, so preprocessing is a key part of the pipeline:

- **Categorical features**
  - Imputed with **mode** when missingness is not structurally meaningful
  - Introduced an explicit **"None" / "No" category** for physically absent elements (e.g., no pool, no fence, no alley)

- **Numerical features**
  - Imputed using **median** or **mean** depending on distribution
  - Replaced with **0** when the absence implies zero quantity (e.g., garage area when no garage exists)

---

### 2) Feature Engineering

- **Encoding**
  - **One-Hot Encoding** for nominal categories
  - **Label/Ordinal Encoding** for ordered quality features (e.g., `Ex > Gd > TA > Fa > Po`)

- **Transformations**
  - Handled skewed numerical distributions
  - Applied a log transform to the target:
    - `SalePrice_log = log1p(SalePrice)`
  - Optional scaling using **RobustScaler** to reduce sensitivity to outliers

- **Custom features (optional)**
  - Example: `TotalSF` = total floor/basement surface aggregated from multiple columns  
  *(Add the exact engineered features you created if applicable.)*

---

### 3) Predictive Modeling

To capture both linear and non-linear relationships, multiple models were tested and compared:

- **Baseline / regularized regression**
  - e.g., **Lasso / Ridge** for strong linear baselines with regularization
- **Gradient boosting**
  - e.g., **XGBoost** for high performance on tabular data with non-linear interactions

#### Evaluation
Models are evaluated using **RMSE on log-transformed prices** (`log1p(SalePrice)`), as required by the competition.

#### Optimization
Hyperparameter tuning performed with:
- `GridSearchCV` and/or `RandomizedSearchCV`
- Cross-validation strategy (e.g., K-Fold)

---

## 💻 Tech Stack

- **Language**: Python 3
- **Data handling**: pandas, numpy
- **Visualization**: matplotlib, seaborn
- **Machine Learning**: scikit-learn, XGBoost *(if used)*
- **Environment**: Jupyter Notebook

---

## 🚀 Quick Start

### 1) Clone repository
```bash
git clone https://github.com/omargrif/house-prices-prediction.git
cd house-prices-prediction
```

### 2) Install dependencies
```bash
pip install -r requirements.txt
```

### 3) Run the notebook
Open the notebook (recommended rename):
- `Untitled25.ipynb` → `House_Prices_Prediction.ipynb`

```bash
jupyter notebook
```

---

## 📂 Project Structure (suggested)

```
.
├── notebooks/
│   └── House_Prices_Prediction.ipynb
├── data/
│   ├── train.csv
│   └── test.csv
├── submission/
│   └── submission.csv
├── data_description.txt
├── requirements.txt
└── README.md
```

> Note: If you publish this repo, avoid committing Kaggle data directly unless you are allowed to. A common practice is to keep `data/` ignored and document how to download it.

---

## 📌 Notes & Next Improvements

- [ ] Add a clean training pipeline script (`train.py`) for reproducibility
- [ ] Add feature importance (Permutation / SHAP)
- [ ] Add cross-validated stacking / blending
- [ ] Add experiment tracking (MLflow / Weights & Biases)

---

## 📧 Contact

**Omar Grifat**
- GitHub: [@omargrif](https://github.com/omargrif)
- LinkedIn: *(add link)*
- Email: *(add email)*
