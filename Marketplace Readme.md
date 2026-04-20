# Marketplace Seller Governance & Risk Intelligence Dashboard

An Excel-based analytics project that identifies risky marketplace sellers by combining governance metrics, policy violations, and supplier risk signals into a single seller-level risk scoring model.

## Recommended repository name
`marketplace-governance-risk-dashboard`

## Project summary
This project builds an end-to-end governance and risk dashboard for an e-commerce marketplace. It integrates seller master data, governance metrics, violation logs, and supplier-risk records into a unified analytical model that classifies sellers into **Low**, **Medium**, and **High** risk categories.

The workbook is structured as a complete reporting pipeline:
- **Raw data sheets** for source tables
- **Cleaned data sheets** for analysis-ready datasets
- **Intermediate summary sheet** for seller-year violation aggregation
- **Seller risk analysis sheet** with lookup logic, risk flags, weighted scoring, and final classification
- **Pivot and dashboard sheets** for business-facing reporting

## Business problem
Marketplace platforms need to detect sellers that are more likely to create operational, financial, compliance, or trust-related issues. Looking only at one signal such as refund rate or fraud flag is weak. This project combines multiple governance and risk indicators into a single framework so decision-makers can prioritize reviews, suspensions, monitoring, and preventive action.

## Objectives
- Consolidate multi-source marketplace risk data into one analysis model
- Create seller-year level risk profiles
- Build explainable rule-based flags for operational and compliance risks
- Generate a weighted risk score for each seller
- Present the results in a dashboard suitable for management review

## Dataset structure
The workbook contains the following main layers:

### 1) Raw source sheets
- `Raw_Violation_Log`
- `Raw_Governance_Metrics`
- `Raw_Seller_Master`
- `Raw_Supplier_Risk`

### 2) Cleaned data sheets
- `Cleaned_Violation_Log`
- `Cleaned_Governance_Metrics`
- `Cleaned_Seller_Master`
- `Cleaned_Supplier_Risk`

### 3) Analytical sheets
- `Violation_Summary_Seller_Year`
- `Seller_Risk_Analysis`
- `Pivot_Risk_Reports`
- `Dashboard`

## Core methodology
The final seller risk score is created from five rule-based flags in `Seller_Risk_Analysis`:

1. **Refund Risk Flag**  
   - 2 if refund rate >= 10%  
   - 1 if refund rate >= 5%  
   - 0 otherwise

2. **User Report Risk Flag**  
   - 2 if user reports >= 8  
   - 1 if user reports >= 4  
   - 0 otherwise

3. **Violation Severity Flag**  
   Triggered using critical/high-severity counts and total violation counts.

4. **Fraud Concern Flag**  
   Triggered using fraud flags and fraud-linked violations.

5. **Governance Action Severity Flag**  
   Uses governance statuses such as Suspended, Blocked, Review Required, Restricted, and Watchlist.

### Weighted score formula
```text
Overall Risk Score =
(Refund Risk Flag × 25) +
(User Report Risk Flag × 25) +
(Violation Severity Flag × 20) +
(Fraud Concern Flag × 20) +
(Governance Action Severity Flag × 10)
```

### Final classification
- **High Risk**: score >= 120
- **Medium Risk**: score >= 60 and < 120
- **Low Risk**: score < 60

## Key project facts
- **Unique sellers:** 100
- **Seller-year records analyzed:** 479
- **Violation records:** 1646
- **Governance metric records:** 479
- **Supplier risk records:** 1800
- **Analysis period:** 2021-2025

## Key findings from the workbook
- Overall seller risk distribution: **High = 308**, **Medium = 146**, **Low = 25**
- High-risk sellers represent **64.3%** of all seller-year observations
- High-risk share rises from **58.8% in 2021** to **75.5% in 2025**
- Average refund rate is highest for high-risk sellers (**7.17%**) compared with medium (**4.79%**) and low (**3.25%**)
- High-risk sellers also show the highest average user reports (**20.9**) and average violation count (**4.3**)

## Dashboard features
The dashboard and pivot reports allow the user to:
- Track seller counts by final risk level and year
- Review seller-level governance outcomes
- Identify concentration of risk across time periods
- Support compliance escalation and management reporting

## Tools used
- **Microsoft Excel**
- Pivot tables
- Lookup formulas (`VLOOKUP`, `INDEX/MATCH`)
- Conditional rule-based scoring
- Dashboard reporting

## Repository structure
```text
marketplace-governance-risk-dashboard/
│
├── README.md
├── reports/
│   └── Project_Report_Marketplace_Governance_Risk_Dashboard.docx
├── assets/
│   └── ECommerce_Governance_Risk_Analysis_v2_Dashboard.xlsx
├── screenshots/
│   └── dashboard-overview.png   # optional
└── docs/
    └── submission-guide.md
```

## What to upload to GitHub
At minimum, upload:
- the Excel workbook
- this README
- the project report
- one or two dashboard screenshots if possible

## Suggested GitHub description
**Excel dashboard project for seller governance, compliance monitoring, and marketplace risk scoring using multi-source e-commerce data.**

## Why this project is worth showing
This project demonstrates:
- data cleaning and structuring
- multi-table integration
- analytical thinking
- explainable risk scoring
- dashboard design for decision support
- business understanding of governance and compliance use cases

## How to present this project to recruiters or companies
When you share the repository, describe it in one line like this:

> Built an Excel-based seller governance and risk intelligence dashboard that integrates violations, governance metrics, and supplier risk data to classify marketplace sellers into actionable risk categories.

## Note
This repository is intended as a portfolio project. The workbook is the main deliverable and should be opened in Microsoft Excel for full dashboard and pivot functionality.
