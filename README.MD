# Customer Churn Prediction
Kaggle Playground Series - Season 6 Episode 3

## Project Overview
Binary classification task to predict the probability of customer churn for a telecom company.  
The output is a probability score (0~1) for each customer, where 1 = churned.

## Dataset
Source: [Kaggle - Playground Series S6E3](https://www.kaggle.com/competitions/playground-series-s6e3/data)

| File | Description |
|------|-------------|
| `train.csv` | Training set with `Churn` label |
| `test.csv` | Test set for prediction |
| `sample_submission.csv` | Submission format |

## Features
| Feature | Description |
|---------|-------------|
| `gender` | Customer gender |
| `SeniorCitizen` | Whether the customer is a senior citizen (0/1) |
| `Partner` | Whether the customer has a partner |
| `Dependents` | Whether the customer has dependents |
| `tenure` | Number of months the customer has stayed |
| `PhoneService` | Whether the customer has phone service |
| `MultipleLines` | Whether the customer has multiple lines |
| `InternetService` | Internet service type (DSL / Fiber optic / No) |
| `OnlineSecurity` | Whether the customer has online security |
| `OnlineBackup` | Whether the customer has online backup |
| `DeviceProtection` | Whether the customer has device protection |
| `TechSupport` | Whether the customer has tech support |
| `StreamingTV` | Whether the customer has streaming TV |
| `StreamingMovies` | Whether the customer has streaming movies |
| `Contract` | Contract type (Month-to-month / One year / Two year) |
| `PaperlessBilling` | Whether the customer has paperless billing |
| `PaymentMethod` | Payment method |
| `MonthlyCharges` | Monthly charges |
| `TotalCharges` | Total charges |

## Approach

### Preprocessing
- Label Encoding for all categorical features
- Combined train and test before encoding to ensure consistency

### Models
Three gradient boosting models trained with 5-Fold Stratified Cross Validation:

| Model | OOF AUC |
|-------|---------|
| LightGBM | 0.91603 |
| XGBoost | 0.91641 |
| CatBoost | 0.91613 |
| **Ensemble (equal weight average)** | **0.91652** |

### Ensemble
Simple equal-weight averaging of predicted probabilities from all three models.

## Results
| Metric | Score |
|--------|-------|
| OOF AUC (local) | 0.91652 |
| Kaggle Public LB | 0.91387 |
| Kaggle Ranking | 1855 / 4136 |

## Project Structure
```
├── predict-customer-churn.ipynb  # Full pipeline: EDA + preprocessing + modeling
├── submission.csv # Final results
└── README.md
```

## Requirements
```
lightgbm
xgboost
catboost
scikit-learn
pandas
numpy
matplotlib
seaborn
```
