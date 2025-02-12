# Housing Price Prediction: Exploratory Data Analysis (EDA) & Model Development

## Project Overview

This project presents an **Exploratory Data Analysis (EDA)** and the development of a **predictive model** for housing price prediction using a real estate dataset. The analysis covers key tasks such as data preprocessing, missing value handling, feature engineering, correlation analysis, outlier detection, and model evaluation. The goal is to predict housing prices using various factors such as location, house features, and overall quality.

---

## 1. Dataset Overview

- **Total Entries:** 1460
- **Total Features:** 81
- **Data Types:**
  - **Numerical Features:** 36
  - **Categorical Features:** 45
- **Target Variable:** SalePrice

- **Key Objective:** Predict housing prices based on various property characteristics.

---

## 2. Data Exploration & Handling Missing Values

### 2.1 Dataset Structure & Summary

- The dataset consists of multiple **numerical** and **categorical** features.
- Statistical summary provides the minimum, maximum, mean, and standard deviation for continuous variables.
- Notable feature: **LotFrontage** has a high standard deviation, indicating large variability.

### 2.2 Missing Value Analysis

- **Alley (93.77%)** → Dropped.
- **PoolQC (99.52%)** → Dropped due to the low presence of pools.
- **GarageYrBlt (5.55%)** → Imputed using the median value of the garage construction year.
- **MasVnrType (59.73%)** → Imputed based on MasVnrArea.

### 2.3 Missing Value Handling Strategies

- Features with **>80% missing data** are dropped.
- **Numerical features:** Imputed with median values.
- **Categorical features:** Imputed using the most frequent category.

---

## 3. Numerical Feature Analysis

### 3.1 Key Observations

- **OverallQual** and **GrLivArea** are the most important predictors of **SalePrice**.
- **SalePrice** shows a right-skewed distribution, requiring a log transformation for better normality.
- **Highly skewed variables** include LotArea, 1stFlrSF, and BsmtFinSF1.

### 3.2 Feature Scaling & Transformations

- **Normalization:** Applied MinMaxScaler to scale numerical features.
- **Log Transformations:** Applied to SalePrice and other skewed features.

---

## 4. Categorical Feature Analysis

### 4.1 Key Features

- **Neighborhood:** Strong correlation with SalePrice, highlighting the importance of location.
- **HouseStyle** & **RoofStyle:** Influence the perceived value of properties.
- **Exterior Features:** Impact house valuation based on materials used.

### 4.2 Low Variance Features

- **Utilities:** Dropped due to little variation.
- **MiscFeature:** Sparse data that doesn’t significantly affect pricing.

### 4.3 Encoding Strategy

- **One-Hot Encoding (OHE):** Applied to high-cardinality categorical variables.
- **Label Encoding:** Used for ordinal features like ExterQual, BsmtQual, and KitchenQual.

---

## 5. Outlier Detection & Impact

Outliers were detected in key numerical features:
- **GrLivArea:** Extremely large homes.
- **LotFrontage:** Large variations in values.
- **SalePrice:** Extreme values affecting regression models.

### 5.1 Handling Outliers

- **IQR** methods were used to remove or transform extreme outliers.
- **Log transformation** applied to normalize skewed features.

---

## 6. Correlation Analysis & Feature Importance

### 6.1 Strongly Correlated Features with SalePrice

- **OverallQual (0.79)**
- **GrLivArea (0.71)**
- **GarageCars (0.64)**
- **TotalBsmtSF (0.61)**

### 6.2 Weakly or Negatively Correlated Features

- **MoSold & YrSold**: Minimal effect on pricing.
- **Condition2 & MiscFeature**: Little impact on house value.

### 6.3 Feature Selection Strategy

- Dropped weakly correlated features to reduce noise.
- Applied **Principal Component Analysis (PCA)** to reduce dimensionality.

---

## 7. Model Development & Evaluation

### 7.1 Random Forest Model Testing

- **Model Used:** Random Forest Regressor.
- **Train-Test Split:** 80-20 ratio.
- **Hyperparameter Tuning:** GridSearchCV was used to fine-tune the model.
- **Evaluation Metrics:**
  - **Mean Squared Error (MSE):** Measures the prediction error.
  - **R² Score:** Indicates how well the model fits the data.
  - **Mean Absolute Error (MAE):** Measures average deviation.

### 7.2 Model Performance

- **Random Forest Results:**
  - **RMSE:** Lower error compared to Linear Regression.
  - **R² Score:** Significant improvement in model accuracy.
  - **Feature Importance:** OverallQual, GrLivArea, and GarageCars are the top predictors.

---

## 8. Conclusion & Next Steps

### 8.1 Key Findings

- **Random Forest** outperforms **Linear Regression** in predicting SalePrice.
- The key predictors of housing prices are **OverallQual**, **GrLivArea**, and **GarageCars**.
- Proper handling of missing values and outliers is essential for accurate predictions.
- **Feature Engineering** (encoding, transformations) significantly improves model performance.

### 8.2 Next Steps

1. **Further Model Enhancements:**
   - Explore boosting algorithms like **XGBoost** and **LightGBM**.
   - Combine multiple models using ensemble techniques.
2. **Hyperparameter Tuning:** 
   - Explore more advanced tuning techniques, such as **Bayesian Optimization**.
3. **Model Deployment:**
   - Build an interactive web application for housing price prediction.

By refining these strategies, we aim to develop a highly accurate housing price prediction model.

---

## Requirements

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn


