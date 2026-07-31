# DAX Measures and Calculated Columns

This document contains the primary DAX calculations used in the Telco Customer Churn Power BI dashboard.

---

## Core KPI Measures

### Total Customers

Counts the number of unique customers in the dataset.

```DAX
Total Customers =
DISTINCTCOUNT(
    'Telco Customers'[Customer ID]
)

Churned Customers =
CALCULATE(
    [Total Customers],
    'Telco Customers'[Churn] = "Yes"
)

Retained Customers =
CALCULATE(
    [Total Customers],
    'Telco Customers'[Churn] = "No"
)

Churn Rate =
DIVIDE(
    [Churned Customer],
    [Total Customers],
    0
)

Retention Rate =
DIVIDE(
    [Retained Customer],
    [Total Customers],
    0
)

Avg Monthly Charge =
AVERAGE(
    'Telco Customers'[Monthly Charges]
)


Avg Tenure =
AVERAGE(
    'Telco Customers'[Tenure]
)

High-Risk Customers =
CALCULATE(
    [Total Customers],
    'Telco Customers'[Risk Category] = "High Risk",
    'Telco Customers'[Churn] = "No"
) // This measure counts current retained customers classified as high risk. Excluding customers who already churned makes the measure more actionable.//


High-Risk Customer Rate =
DIVIDE(
    [High-Risk Customers],
    [Retained Customer],
    0
)

Tenure Risk Points =
SWITCH(
    TRUE(),
    'Telco Customers'[Tenure] <= 12, 3,
    'Telco Customers'[Tenure] <= 24, 2,
    'Telco Customers'[Tenure] <= 48, 1,
    0
)

Contract Risk Points =
 SWITCH(
    'Telco Customers'[Contract],
    "Month-to-month", 3,
    "One year", 1,
    "Two year", 0,
    0
 )

Support Risk Points =
IF(
    'Telco Customers'[Tech Support] = "No",
    2,
    0
)

Security Risk Points =
IF(
    'Telco Customers'[Online Security] = "No",
    2,
    0
)

Risk Score =
    'Telco Customers'[Tenure Risk Points]
    + 'Telco Customers'[Contract Risk Points]
    + 'Telco Customers'[Support Risk Points]
    + 'Telco Customers'[Security Risk Points]
    + 'Telco Customers'[Payment Risk Point]
    + 'Telco Customers'[Charge Risk Points]

Risk Category =
SWITCH(
    TRUE(),
    'Telco Customers'[Risk Score] >= 9, "High Risk",
    'Telco Customers'[Risk Score] >= 5, "Medium Risk",
    "Low Risk"
)

Tenure Group =
SWITCH(
    TRUE(),
    'Telco Customers'[Tenure] <= 12, "0-12 Months",
    'Telco Customers'[Tenure] <= 24, "13-24 Months",
    'Telco Customers'[Tenure] <= 48, "25-48 Months",
    "49-72 Months"
)

Monthly Charge Group =
SWITCH(
    TRUE(),
    'Telco Customers'[Monthly Charges] < 40, "Low: Under $40",
    'Telco Customers'[Monthly Charges] < 80, "Medium: $40-$79.99",
    "High: $80+" )

### Important correction

Earlier, your risk score reached **14**, so your actual high-risk cutoff may not be `10`. Use the exact cutoff from your Power BI file.

Do not paste a different formula merely because it looks good in the documentation. Your GitHub documentation must match the finished dashboard.

Save it inside:

```text
Documentation



