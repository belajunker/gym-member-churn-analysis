# 🏋️ Gym Member Churn Analysis

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?logo=postgresql&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)

## Project Overview

This project analyzes churn behavior among 4,000 gym members using SQL (PostgreSQL) and Python to identify the key drivers of membership cancellation. Behavioral, contractual, and demographic features are examined to derive actionable retention insights. Results are exported as structured CSV files and visualized in a Power BI dashboard.

## Key Questions Answered

1. What is the overall churn rate across all members?
2. Does contract length (monthly, semi-annual, annual) affect churn?
3. Do inactive members churn more frequently than engaged ones?
4. Is churn influenced by age or gender?

## Tools Used

| Tool | Purpose |
|---|---|
| Python 3.14.5 | Data loading, export, and pipeline orchestration |
| PostgreSQL | SQL-based churn analysis via `psycopg2` |
| Pandas | DataFrame handling and CSV export |
| Power BI | KPI dashboard and visual reporting |

## Repository Structure

```
gym-churn-analysis/
│
├── gym_churn_us.ipynb        # Main analysis notebook (SQL + Python)
├── gym_churn_us.csv          # Raw dataset (4,000 members, 14 features)
│
├── exports/
│   ├── churn_by_contract.csv # Churn rate per contract period
│   ├── churn_by_activity.csv # Avg. class frequency by churn status
│   ├── churn_by_age.csv      # Avg. age by churn status
│   ├── churn_by_gender.csv   # Churn rate by gender
│   └── churn_kpi.csv         # KPI summary for Power BI
│
└── README.md
```

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/gym-churn-analysis.git
cd gym-churn-analysis
```

### 2. Install Dependencies

```bash
pip install pandas psycopg2-binary
```

### 3. Set Up PostgreSQL

Create a local database and import the dataset:

```sql
CREATE DATABASE gym_churn;
```

Then configure your connection credentials in the notebook (`psycopg2.connect(...)`).

### 4. Run the Notebook

Open `gym_churn_us.ipynb` in VS Code or Jupyter and run all cells in order. CSV exports will be written to the project directory automatically.

### 5. Load into Power BI

Import the exported CSV files from `exports/` into Power BI to replicate the dashboard.

## Key Findings

- **Overall churn rate:** 26.53% of all gym members cancelled their membership
- **Contract length is the strongest churn predictor:** monthly contracts show a churn rate of **42.32%**, dropping to **12.48%** for semi-annual and just **2.40%** for annual contracts
- **Inactive members churn at nearly twice the rate:** churned members attended an average of **1.04 classes/month**, compared to **2.03 classes/month** for retained members
- **Younger members churn more frequently:** average age of churned members is **26.99 years**, versus **29.98 years** for retained members
- **Gender has no meaningful predictive power:** churn rates are virtually identical across genders (26.49% vs. 26.56%), making it a non-predictive feature for retention modeling

## Data Source

**Dataset:** [Gym Member Churn — Kaggle](https://www.kaggle.com/datasets/hassaan2580/churn-prediction-gym-members-dataset)  
**Records:** 4,000 gym members | **Features:** 14 columns
