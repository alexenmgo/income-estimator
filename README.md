# AI-Powered Income Estimator
### Client Financial Profiling with Credit Score Data — TransUnion

> **Role:** Data & Compliance Specialist · CCI Puesto de Bolsa  
> **Tools:** Python · AI/ML · TransUnion API · BigQuery · Google Apps Script  AWS
---

## 📌 Overview

An AI-powered income estimation tool that combines **TransUnion credit score data** with machine learning to produce a calibrated financial profile for each client. Designed to support the compliance and onboarding process at a Dominican securities broker, the tool estimates monthly and annual adjusted income, savings capacity, and assigns a financial risk classification (PLAFT profile) — all from a single ID lookup.

> ⚠️ *All data shown is for demonstration purposes using anonymized records. No real client information is disclosed.*

---

## 🖥️ Tool Preview

### Income Estimator — Output Screen
![Income Estimator - Calculadora de Legitimación CCI](images/income_estimator.png)

*The tool returns an adjusted monthly income, projected annual income, savings capacity, and a narrative AI-generated analytical recommendation — in seconds.*

---

## 🔍 How It Works

```
User inputs:  National ID (Cédula)
              Optional: Bank statements (PDF upload)
        │
        ▼
Step 1: Query BigQuery database
        └── Retrieves credit score, debt profile, payment history from TransUnion
        │
        ▼
Step 2 (Optional): Analyze bank statements
        └── PDF parsing → income/expense extraction
        │
        ▼
AI Model: Income Estimation
        ├── Uses credit score, debt levels, mora (delinquency), payment behavior
        ├── Applies adjustment factors based on risk indicators
        │     └── e.g. score > 600 + low mora → income adjusted +30%
        ├── Calculates savings capacity (≈ 30% of adjusted income)
        └── Assigns PLAFT risk profile: Low / Medium / High
        │
        ▼
Output:
        ├── Adjusted Monthly Income (RD$)
        ├── Projected Annual Income (RD$)
        ├── Savings Capacity (RD$)
        ├── PLAFT Risk Classification
        ├── AI Analytical Recommendation (narrative)
        └── Downloadable Evidence Document
```

---

## 📊 Output Fields

| Field | Description |
|-------|-------------|
| **Adjusted Monthly Income** | Estimated monthly income after risk-based adjustment |
| **Projected Annual Income** | Annualized income estimate |
| **Savings Capacity** | Estimated available monthly savings |
| **Data Origin Date** | Reference date of the credit data used |
| **PLAFT Profile** | Risk classification: Low / Medium / High |
| **AI Recommendation** | Narrative analysis explaining the estimation logic and key credit factors |
| **Evidence Document** | Downloadable PDF report for compliance file |

---

## 🤖 AI & Model Details

- The model uses **TransUnion credit score variables** as primary predictors: score value, total active debts, mora (delinquency rate), payment behavior, and credit product mix.
- An **adjustment layer** applies factor-based corrections based on behavioral credit signals — for example, a score above 600 with low mora and active debt suggests the base model income may be conservative, triggering an upward adjustment.
- The **PLAFT risk profile** is assigned based on the adjusted income estimate, score tier, and debt-to-income indicators.
- An **AI-generated narrative** (using LLM integration) explains the reasoning behind the estimate in plain language — making the output interpretable for compliance officers without a data science background.

---

## ⚙️ Technical Stack

```
Frontend:    Google Apps Script (Web App interface)
Database:    BigQuery (credit score data warehouse)
AI Layer:    Python + LLM integration (narrative generation)
Data:        TransUnion API (credit score & debt data)
Output:      PDF report generation (evidence document)
```

---

## 🎯 Business Use Cases

- **Client onboarding** — estimate income capacity before opening a financial product
- **Product eligibility assessment** — determine if a client qualifies for investment products based on estimated capacity
- **AML/Compliance screening** — flag discrepancies between declared income and estimated capacity
- **Repayment capacity analysis** — support credit risk decisions with data-driven income estimates

---

## 🛠️ Tech Stack

`Python` · `BigQuery` · `Google Apps Script` · `TransUnion API` · `AI/LLM` · `PDF Generation` · `AML/PLAFT Framework`

---

*Tool built for internal compliance use at a regulated financial institution. Data shown is anonymized.*
