# 📊 Telco Customer Churn Prediction Project

## Dataset Information
- **Customers who left within the last month** – the column is called `Churn`
- **Services that each customer has signed up for** – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- **Customer account information** – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
- **Demographic info about customers** – gender, age range, and if they have partners and dependents

## The dataset is available in Kaggle,
https://www.kaggle.com/datasets/blastchar/telco-customer-churn

## 🚀 Project Overview
- **Objective:** Predict which telecom customers are likely to churn (leave the service).
- **Business Value:** Retain high-risk customers and reduce revenue loss.
- **Dataset:** Telco Customer Churn (7,000+ customers, 21 features).

## 📂 Project Structure
- `data/`: Contains the Telco Customer Churn dataset.
- `notebooks/`: Jupyter Notebooks for data analysis and modeling.
- `models/`: Saved XGBoost and Ridge Classifier models (`.pkl` files).
- `app/`: Flask API and HTML frontend for deployment.
- `README.md`: Project documentation.

## ⚡ Data Understanding
- Key Features:
  - **Customer Demographics:** Gender, SeniorCitizen, Partner, Dependents
  - **Service Details:** PhoneService, InternetService, StreamingTV
  - **Account Info:** Tenure, Contract, PaymentMethod
  - **Financials:** MonthlyCharges, TotalCharges
- **Target Variable:** Churn (Yes/No)

## 🧹 Data Preparation
- Missing values in `TotalCharges` were handled (removed).
- Converted `SeniorCitizen` to categorical (Yes/No).
- Label encoded binary columns and one-hot encoded multi-category columns.
- Engineered `tenure_group` feature for better interpretation.
- Train/Test split with stratification (80/20).

## 🚦 Model Building
- Models trained and compared:
  - ✅ Logistic Regression
  - ✅ Decision Tree
  - ✅ Random Forest (Tuned)
  - ✅ XGBoost (Tuned)
  - ✅ Ridge Classifier (L2 Regularization)
- Hyperparameter tuning applied to Random Forest and XGBoost.

## ✅ Model Evaluation
| Model | Precision | Recall | F1-Score | ROC-AUC |
|:------|:----------|:-------|:---------|:--------|
| Logistic Regression | 0.69 | 0.56 | 0.62 | 0.81 |
| Decision Tree | 0.57 | 0.51 | 0.54 | 0.71 |
| Random Forest | 0.78 | 0.68 | 0.72 | 0.87 |
| XGBoost | 0.80 | 0.70 | 0.74 | 0.89 |
| Ridge Classifier | 0.75 | 0.71 | 0.73 | 0.85 |

- **Best Model:** XGBoost (highest Recall, F1-Score, ROC-AUC)
- **Second Best:** Ridge Classifier (high interpretability)

## 🔍 Feature Importance
- Key Drivers of Churn (XGBoost and Ridge):
  - `Contract_Month-to-month`: High churn risk.
  - `Tenure`: Short tenure = higher risk.
  - `PaymentMethod_Electronic check`: High churn rate.
  - `MonthlyCharges`: Higher charges = higher churn.

## 🚀 Deployment
- Models saved as `.pkl` files:
  - `best_xgboost_model.pkl`
  - `best_ridge_classifier_model.pkl`
- Flask API built to serve predictions (model choice: XGBoost or Ridge).
- HTML frontend for user-friendly prediction interface.

## ⚡ How to Run Locally
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Start the Flask API:
   ```bash
   python app/churn_api.py
   ```
3. Open the HTML frontend (`app/churn_prediction.html`) in your browser.

## 📌 Recommendations
- Target month-to-month customers for retention.
- Offer discounts to high-risk customers (short tenure, high charges).
- Consider changing the default payment method (Electronic Check).
- Monitor model performance monthly.

## 🔧 Next Steps
- Deploy full app (HTML + Flask) to Heroku/AWS.
- Add API authentication (secure access).
- Set up automated model retraining (quarterly).
