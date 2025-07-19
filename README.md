# Used Car Price Predictor

This project predicts the selling price of used cars based on key features like manufacturing year, current price, kilometers driven, fuel type, transmission, and seller type. It uses regression techniques and includes a real-time prediction pipeline, making it suitable for integration into applications or deployment environments.

---

## Problem Statement

Accurately predicting the resale price of used cars is valuable for individual sellers, buyers, and dealerships. The goal of this project is to:

- Understand and process the CarDekho dataset
- Train and evaluate various regression models
- Identify the best-performing model
- Build a real-time prediction pipeline for new data inputs

---

## Dataset

- **Source**: [CarDekho dataset](https://www.kaggle.com/datasets)
- **Size**: 299 rows × 9 columns (after cleaning)
- **Features Used**:
  - `Present_Price` (in lakhs)
  - `Kms_Driven`
  - `Fuel_Type`
  - `Seller_Type`
  - `Transmission`
  - `Owner`
  - `Car_Age` (engineered from `Year`)

- **Target**:
  - `Selling_Price`

---

## Data Preprocessing

- Dropped duplicates and verified absence of missing values
- Feature engineered a new column: `Car_Age = 2025 - Year`
- Dropped `Car_Name` and `Year` columns (not needed for prediction)
- Applied **log transformation** on `Kms_Driven` to reduce skew
- Converted categorical columns (`Fuel_Type`, `Seller_Type`, `Transmission`) using **one-hot encoding**
- Final dataset included 8 features

---

## Exploratory Data Analysis (EDA)

- Visualized feature distributions and correlations
- Found strong correlation between `Present_Price`, `Car_Age`, and `Selling_Price`
- Noted negative impact of older age, individual sellers, and manual transmission on resale price

---

## Model Building

- **Train-Test Split**: 80-20
- **Feature Scaling**: Standardized numerical features using `StandardScaler`
- **Regression Models Applied**:
  - Linear Regression
  - Decision Tree Regressor
  - Random Forest Regressor
  - XGBoost Regressor
  - LightGBM Regressor
  - CatBoost Regressor

### Best Model: **CatBoost Regressor**

| Metric      | Value  |
|-------------|--------|
| MAE         | 0.87   |
| R² Score    | 0.85   |

---

## Real-Time Prediction Pipeline

Built a prediction pipeline for new user inputs using:

- `StandardScaler` for consistent preprocessing
- `joblib` for model and scaler serialization
- Manual feature preprocessing (e.g., one-hot encoding) replicated for real-world inputs
