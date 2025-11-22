# Churn Prediction and Revenue Impact Modeling Improving Retention
Increasing Customer Lifetime Value, Protecting Recurring Revenue

Executive Summary

Customer churn directly reduces recurring revenue and increases acquisition costs. Using machine learning (CatBoost), SHAP explainability, and financial forecasting, this project identifies why customers churn, predicts who is likely to churn next, and quantifies the financial impact of churn.

Key Findings:

Approximately 2,920 customers are expected to churn soon (probability-weighted prediction).

An estimated $213,429 in monthly recurring revenue is at risk.

Current Customer Lifetime Value (CLV) is $244.

Reducing churn by just 5% increases CLV to $256.89.

Churn is primarily driven by:

Month-to-month contracts, Fiber optic internet service , Low tenure, Lack of tech support and online security, Electronic check payment method (price-sensitive segment)

This project provides clear, data-driven recommendations to reduce churn, improve customer satisfaction, and protect long-term revenue.

**1. Business Problem**

Subscription-based businesses lose millions due to churn. Retaining an existing customer is significantly cheaper and more profitable than acquiring a new one.

This project aims to:

Predict customers at risk of churning.

Understand the drivers of churn.

Quantify the financial impact of churn.

Provide actionable retention recommendations.

**2. Dataset Overview**

The dataset includes demographic, service, financial, and account-level features:

Customer Profile

gender, SeniorCitizen, Partner, Dependents

Account & Services

tenure, PhoneService, InternetService, OnlineSecurity, TechSupport, Contract, PaymentMethod

Financial

MonthlyCharges, TotalCharges

Target

Churn (Yes/No)

<img width="695" height="454" alt="Screenshot 2025-11-22 170550" src="https://github.com/user-attachments/assets/326a4e19-0acb-4f22-9847-d236e7495c6e" />

**3. Exploratory Data Analysis (EDA)**

The EDA revealed important early churn indicators.

Tenure vs Churn

Customers with low tenure (especially under 6 months) churn the most.
This highlights onboarding and early customer experience issues.

Tenure vs Churn Plot
<img width="938" height="453" alt="Screenshot 2025-11-22 170538" src="https://github.com/user-attachments/assets/9a6d2dc8-d7a1-4fd2-b9d7-a01c39141695" />


Monthly Charges vs Churn

<img width="759" height="463" alt="Screenshot 2025-11-22 170600" src="https://github.com/user-attachments/assets/58a003a1-92f3-4d00-adff-2a6158a3ff7f" />


Churners tend to have higher monthly charges, suggesting price sensitivity.


Churn by Contract Type

<img width="624" height="451" alt="Screenshot 2025-11-22 170609" src="https://github.com/user-attachments/assets/3d4a5229-7f48-4b82-a9ac-647d5ff72c56" />


Contract type is the strongest churn differentiator.

Month-to-month customers churn the most.

One-year and two-year contracts dramatically reduce churn.


**4. Modeling Approach**
**Preprocessing**

Removed missing values

Converted TotalCharges to numeric

Encoded categorical variables

Scaled numeric features

Addressed class imbalance using SMOTE and class weights

Models Evaluated

Logistic Regression

Random Forest (with SMOTE)

CatBoost (final selected model)

Why CatBoost?

Excellent performance on categorical data

Works well with class imbalance

Produces interpretable results with SHAP

Robust and stable predictions

**5. Final Model Performance**

The final CatBoost model achieved:

AUC: ~0.84

Accuracy: ~80%

Strong recall for the churn class

Balanced predictions without overfitting


Classification Report:


| Class        | Precision | Recall | F1-Score | Support |
|--------------|-----------|--------|---------|---------|
| 0 (No Churn) | **0.91**  | **0.72** | **0.80** | 1035    |
| 1 (Churn)    | **0.51**  | **0.80** | **0.62** | 374     |
| **Accuracy** |           |        | **0.74** | 1409    |
| Macro Avg    | 0.71      | 0.76   | 0.71    | 1409    |
| Weighted Avg | 0.80      | 0.74   | 0.75    | 1409    |

**6. Explainable AI (SHAP Analysis)**

SHAP was used to interpret feature importance and understand why customers churn.

Global Feature Importance (Top Drivers)

Contract

InternetService

Tenure

OnlineSecurity

TechSupport

PaymentMethod

OnlineBackup


<img width="644" height="600" alt="Screenshot 2025-11-22 170345" src="https://github.com/user-attachments/assets/5f2673e8-3669-4d55-8a8c-30c774f3af83" />


<img width="655" height="590" alt="Screenshot 2025-11-22 170418" src="https://github.com/user-attachments/assets/d21d1acd-5b0d-468c-be4d-74f6c363a9a4" />


<img width="1153" height="467" alt="Screenshot 2025-11-22 164238" src="https://github.com/user-attachments/assets/176fdbfd-28e7-4764-9e96-66642671cc5b" />


Customer-Level Explanation

SHAP force plots reveal the reasons behind individual churn predictions, such as:

High monthly charges

Month-to-month contract

No tech support

No online security

Low tenure


**7. Churn Forecasting & Revenue Impact**

Using churn probabilities from the model:

Expected churners: 2,920.57

Monthly revenue at risk: $213,429

Current CLV: $244.04

Improved CLV with 5% lower churn: $256.89

Why this matters:

Even small reductions in churn create compounding long-term value.

Financial forecasting provides executives with a clear ROI for retention investments.

**8. Recommendations**
Convert Month-to-Month Customers

Offer discounts, loyalty incentives, or contract upgrade benefits.
This is the largest driver of churn.

Strengthen Early Onboarding

Most churn happens in the first few months.
Implement guided onboarding, personalized communication, and support follow-ups.

Promote Security and Support Add-Ons

Customers with OnlineSecurity or TechSupport churn significantly less.
Offer bundled packages or free trials.

Retain Fiber Optic Customers

Fiber customers churn at higher rates due to price sensitivity or performance expectations.
Provide loyalty rewards, speed upgrades, or enhanced support.

Address Price-Sensitive Segments

Electronic check customers show high churn.
Target them with budget-friendly plans and retention messaging.

**9. Conclusion**

This project demonstrates a complete end-to-end churn analysis pipeline:

Data preparation

EDA and customer insights

Machine learning modeling

Explainability with SHAP

Financial forecasting

Actionable recommendations

It combines technical depth with business strategy, providing real organizational value.
