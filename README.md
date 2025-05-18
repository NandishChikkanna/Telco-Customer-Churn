# Overview

### Dataset Information

- **Customers who left within the last month** – the column is called `Churn`
- **Services that each customer has signed up for** – phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies
- **Customer account information** – how long they’ve been a customer, contract, payment method, paperless billing, monthly charges, and total charges
- **Demographic info about customers** – gender, age range, and if they have partners and dependents

### The dataset is available in Kaggle,

https://www.kaggle.com/datasets/blastchar/telco-customer-churn

### Business Understanding Goal

> "Business goal is to reduce churn."

> "Our analysis shows that customers on month-to-month contracts paying via electronic check are 5x more likely to churn. Each churned customer costs about $1,450 in lost revenue. Targeting this group with retention offers could prevent ~$2M+ in losses annually."

- Predict customer churn.
- Understand key reasons for churn.

### Why
- Retaining customers is cheaper than acquiring new ones.
- Targeted retention strategies (e.g., loyalty offers) can reduce churn.

## Success Criteria
- A predictive model with high recall (i.e., correctly identifies churners).
- Interpretability: Business should understand why customers are churning (important for action).

### Data Understanding

After considering the business understanding, we want to get familiar with our data.  Write down some steps that you would take to get to know the dataset and identify any quality issues within.  Take time to get to know the dataset and explore what information it contains and how this could be used to inform your business understanding.

### Summary: Data Understanding Outputs

| Step                | Insight                                             |
|---------------------|-----------------------------------------------------|
| **Data overview**   | 7,000 rows, 21 columns                              |
| **Missing values**  | Only in `TotalCharges`, handled                     |
| **Data types**      | Mostly correct after minor fixes                    |
| **Categorical variables** | Many binary / 3–4 class fields                 |
| **Numeric variables** | `tenure`, `MonthlyCharges`, `TotalCharges` are key |
| **Target variable** | Imbalanced (~26% churn)                             |
| **Risks**           | Class imbalance and careful use of `TotalCharges`   |
| **Hypotheses**      | Low tenure + month-to-month + electronic check = risky |

### Modeling

With your (almost?) final dataset in hand, it is now time to build some models.  Here, you should build a number of different regression models with the price as the target.  In building your models, you should explore different parameters and be sure to cross-validate your findings.

### Example of Final Output Table

| Model                | Precision | Recall | F1-Score | ROC-AUC |
|----------------------|-----------|--------|----------|---------|
| **Logistic Regression** | 0.69      | 0.56   | 0.62     | 0.81    |
| **Decision Tree**    | 0.57      | 0.51   | 0.54     | 0.71    |
| **Random Forest**    | 0.78      | 0.65   | 0.71     | 0.86    |
| **XGBoost**          | 0.80      | 0.67   | 0.73     | 0.88    |

### Evaluation

With some modeling accomplished, we aim to reflect on what we identify as a high-quality model and what we are able to learn from this.  We should review our business objective and explore how well we can provide meaningful insight into drivers of used car prices.  Your goal now is to distill your findings and determine whether the earlier phases need revisitation and adjustment or if you have information of value to bring back to your client.

### Evaluate Results

### Metrics Used
- **Precision**
- **Recall**
- **F1-Score**
- **ROC-AUC**

### Why These Metrics?
- **Recall** is critical: We want to catch churners even if we get some false positives.
- **F1-Score** balances catching churners (Recall) and not over-alerting (Precision).
- **ROC-AUC** shows overall quality: how well the model separates churners from non-churners.

# Introducing New Beta Ridge regression model:

# 📊 Key Insights

### 🎯 Precision
- **XGBoost** and **Random Forest** have the highest precision (fewer false positives).

### 🔍 Recall (Most Critical)
- **XGBoost** has the highest recall (best at catching churners).
- **Ridge Classifier** is a strong second.

### ⚖️ F1-Score (Balance)
- **XGBoost** leads, followed closely by **Ridge Classifier**.

### 📈 ROC-AUC (Overall Model Quality)
- **XGBoost** is the highest.
- **Random Forest** and **Ridge Classifier** are also strong.

---

# ✅ Conclusion

- **XGBoost** remains your best model:
  - Highest **Recall**, **F1-Score**, and **ROC-AUC**.
- **Ridge Classifier** is a strong second:
  - Offers **clear coefficients** and **good performance**.
- **Random Forest** is reliable but slightly behind.
- **Logistic Regression** and **Decision Tree** are clearly outperformed.


