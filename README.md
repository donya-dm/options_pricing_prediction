# Options Pricing Prediction

This repository contains a project focused on **predicting European call option prices** for the S&P 500.

The goal of this project was twofold:
- **Regression Task:** Predict the current value (C) of an option based on market variables.
- **Classification Task:** Predict whether the Black-Scholes estimated price (C_pred) overestimated or underestimated the true value.

## Project Overview

European call options give the holder the right to buy an asset at a specific price on a specific future date. Pricing such options accurately is challenging and often relies on complex mathematical models like the Black-Scholes formula.  
In this project, we take a **purely data-driven** approach — building **statistical and machine learning models** to predict option prices without using the Black-Scholes formula in modeling.

The datasets provided:
- `option_train.csv` — 5,000 historical options with labeled price data
- `option_test_nolabel.csv` — 500 unlabeled options for model testing

Each sample contains:
- **S:** Current stock price
- **K:** Strike price
- **r:** Risk-free interest rate
- **tau:** Time to maturity (in years)

For the training set only:
- **C:** Actual observed option value
- **BS:** Black-Scholes predicted value

## Approach

### 1. Data Preprocessing
- Checked for missing and erroneous values.
- Standardized/normalized numerical features for certain models.
- Created the binary target label for classification: `Over (1)` if `BS > C

### 2. Modeling Techniques
- **Regression (Predict Value C):**
  - Linear Regression
  - Ridge and Lasso Regression
  - Gradient Boosted Regression Trees
  - Random Forest Regression
  - Support Vector Regression (SVR)
  - Deep Neural Networks

- **Classification (Predict Over/Under):**
  - Logistic Regression
  - Decision Trees
  - Random Forest Classifier
  - Gradient Boosting Classifier (XGBoost, LightGBM)
  - Support Vector Machine (SVM)
  - Neural Networks Classifier

### 3. Model Selection
- **For Regression:** Chose the model with the highest cross-validated R² score.
- **For Classification:** Selected the model achieving lowest cross-validated classification error.

---

## Key Results

- **Regression Model:**  
  Final model achieved an **out-of-sample R² = 99.71%** using LightGBM Gradient Boosting

- **Classification Model:**  
  Final model achieved a **classification accuracy 98.69%**, through SVC

---

## Files in This Repository

| File/Folder           | Description                                                          |
|------------------------|----------------------------------------------------------------------|
| `notebooks/`           | Jupyter Notebooks containing EDA, modeling experiments, and results |
| `group_x_prediction.csv` | Final submission file with Value and BS predictions                 |
| `group_x_report.pdf`   | Final project report detailing methodology, results, and insights   |
| `README.md`            | This project overview                                               |

---
