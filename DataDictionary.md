# Data Dictionary

This document describes the principal fields used in the Telco Customer Churn dashboard.

## Original Dataset Fields

| Field | Description |
|---|---|
| Customer ID | Unique identifier assigned to each customer |
| Gender | Customer gender |
| Senior Citizen | Indicates whether the customer is a senior citizen |
| Partner | Indicates whether the customer has a partner |
| Dependents | Indicates whether the customer has dependents |
| Tenure | Number of months the customer has remained with the company |
| Phone Service | Indicates whether the customer has phone service |
| Multiple Lines | Indicates whether the customer has multiple phone lines |
| Internet Service | Customer internet service type: DSL, Fiber optic, or No |
| Online Security | Indicates whether the customer has online security |
| Online Backup | Indicates whether the customer has online backup |
| Device Protection | Indicates whether the customer has device protection |
| Tech Support | Indicates whether the customer has technical support |
| Streaming TV | Indicates whether the customer has streaming television |
| Streaming Movies | Indicates whether the customer has streaming movies |
| Contract | Customer contract type |
| Paperless Billing | Indicates whether the customer uses paperless billing |
| Payment Method | Customer payment method |
| Monthly Charges | Amount charged to the customer each month |
| Total Charges | Total amount charged during the customer relationship |
| Churn | Indicates whether the customer left the company |

## Created Analytical Fields

| Field | Description |
|---|---|
| Tenure Group | Groups customers into tenure ranges |
| Monthly Charge Group | Groups customers according to monthly charges |
| Tenure Risk Points | Risk points based on customer tenure |
| Contract Risk Points | Risk points based on contract type |
| Support Risk Points | Risk points based on technical-support adoption |
| Security Risk Points | Risk points based on online-security adoption |
| Risk Score | Combined rule-based customer risk score |
| Risk Category | High-, medium-, or low-risk customer classification |
| Service Count | Number of selected telecommunications services used by the customer |