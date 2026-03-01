# Kaggle House Prices: Advanced Regression Techniques

## Overview
This repository contains my end-to-end solution for the Kaggle competition **House Prices: Advanced Regression Techniques**, covering exploratory analysis, data preprocessing, feature engineering, model training, and evaluation.

## Leaderboard Performance
- **Best score/position:** Top **[insert your % or rank — e.g., Top 15%]** on the official Kaggle leaderboard.

## Dataset
The dataset includes **79 explanatory features** describing almost every aspect of residential homes in Ames, Iowa (material quality, room areas, neighborhood characteristics, zoning type, proximity to roads/railroads, etc.).

- **Training set size:** 1460 rows, 81 columns (including the target `SalePrice`)
- **Feature types:** A balanced mix of numerical variables (continuous/discrete) and categorical variables (nominal/ordinal)

## Methodology

### 1. Data Cleaning & Missing-Value Handling
The dataset contains many missing values, handled with a feature-aware strategy:

- **Categorical features**
  - Imputed with the **mode** when missingness is not structurally meaningful.
  - Created explicit categories such as **"None" / "No"** for physically absent items (e.g., no pool, no fence, no alley access).

- **Numerical features**
  - Imputed with the **median** or **mean** depending on distribution.
  - Used **0** when missingness indicates absence (e.g., garage area when there is no garage).

### 2. Feature Engineering
- **Encoding**
  - **One-Hot Encoding** for nominal categorical variables.
  - **Label/Ordinal Encoding** for ordered quality-related features (e.g., `Ex`, `Gd`, `TA`, `Fa` for kitchen/basement quality).

- **Transformations**
  - Reduced skewness in numerical variables.
  - Applied a log transformation to the target:
    - `SalePrice_log = log(1 + SalePrice)` (i.e., `log1p`) to stabilize variance and improve model performance.

- **Feature creation (optional)**
  - Add here if you created custom features, e.g.:
    - `TotalSF = TotalBsmtSF + 1stFlrSF + 2ndFlrSF`

### 3. Predictive Modeling
To capture non-linear relationships and interactions, multiple algorithms were tested, such as:
- **XGBoost** — robust to outliers and strong performance on tabular data
- **Regularized Linear Models (Lasso/Ridge)** — strong baselines and useful for feature selection

**Evaluation**
- Models were evaluated using **Root Mean Squared Error (RMSE)** computed on log-transformed prices, in line with the competition rules.
- Hyperparameter tuning was performed using **GridSearchCV** / **RandomizedSearchCV**.

## Tech Stack
- **Language:** Python 3
- **Data:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn, XGBoost (if used)
- **Environment:** Jupyter Notebook

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/omargrif/house-prices-advanced-regression.git
   cd house-prices-advanced-regression
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebook:
   - `House_Prices_Prediction.ipynb`

## Notes
- Kaggle datasets are not included in this repository. Download them from the competition page and place them locally as needed.
