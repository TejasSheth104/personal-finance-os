# Personal Finance OS (MVP)

A cash-flow-first, credit-card-aware personal finance tracker built for power users.

This project solves a common but poorly handled problem: **understanding real financial health when credit cards, savings buckets, and automation are involved**.

Unlike traditional budget apps, this system:
- Separates *spending behavior* from *cash flow*
- Treats savings and investments as asset allocation, not expenses
- Handles credit card carryovers correctly
- Tracks month-to-month financial state

---

## 🎯 Problem Statement

Most personal finance tools:
- Misclassify savings as expenses
- Hide credit card liabilities
- Break down when spending spikes in one month
- Lack a concept of "financial state" over time

This leads to anxiety, false negatives ("you overspent"), and poor decision-making.

**Personal Finance OS** is designed to reflect how money *actually* works.

---

## 🧠 Core Concepts

### 1. Transactions ≠ Cash Flow
- Expenses happen when swiped
- Cash leaves when paid
- Credit cards are liabilities, not bank accounts

### 2. Savings Buckets
- Emergency Fund
- Loan Savings
- Investments
- Travel (sinking fund)

Savings are **intentional reallocations**, not spending.

### 3. Monthly Financial State
At the end of each month, the system:
- Freezes balances
- Rolls credit card debt
- Carries savings buckets
- Computes net worth

This creates continuity across months.

---

## 🏗️ System Architecture (MVP)

```
┌─────────────┐
│  Streamlit  │  ← UI (manual entry, charts)
└──────┬──────┘
       │
┌──────▼──────┐
│  FastAPI    │  ← Business logic & snapshot engine
└──────┬──────┘
       │
┌──────▼──────┐
│  SQLite DB  │  ← Local persistent storage
└─────────────┘
```

---

## 🛠️ Tech Stack

### Backend
- Python 3.11+
- FastAPI
- SQLAlchemy ORM
- Pydantic
- SQLite (local-first MVP)

### Frontend
- Streamlit
- Native Streamlit charts

### Tooling
- VS Code
- GitHub

---

## 📦 Data Models (Initial)

### Account
- id
- name
- type (checking / savings / investment)
- balance

### CreditCard
- id
- name
- balance
- statement_day

### SavingsBucket
- id
- name
- target_monthly
- balance

### Transaction
- id
- date
- description
- category
- amount (positive)
- payment_method (CC / ACH / Debit)
- source_id (account or card)

### MonthlySnapshot
- month
- total_income
- total_expense
- cash_outflow
- savings_added
- total_cc_balance
- net_worth

---

## 🔥 Killer Feature: Monthly Snapshot Engine

A manual "Close Month" action that:
- Computes final balances
- Rolls liabilities forward
- Carries savings buckets
- Generates projections

This is the core differentiator vs spreadsheets.

---

## 🗺️ MVP Feature Scope

### Included
- Manual transaction entry
- Credit card–aware tracking
- Savings buckets
- Monthly snapshot
- Dashboard charts

### Excluded (Intentionally)
- Bank integrations
- Notifications
- Mobile app
- AI categorization

---

## 🚀 2-Day Sprint Goal

By end of Sunday:
- Working local app
- One full month tracked
- Snapshot created
- Dashboard answering: "Am I actually okay financially?"

---

## 📌 Future Ideas (Not MVP)
- CSV imports
- Scenario simulator
- Net worth forecasting
- Multi-user support

---

## 🧑‍💻 Author

Built as a weekend project to explore a more honest approach to personal finance tracking.

