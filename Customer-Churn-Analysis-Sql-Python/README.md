# Customer Churn Analysis — SQL + Python

A technical deep-dive into identifying, understanding, and reducing customer churn using SQL, Python, and data engineering best practices.

## Business Problem

- **Who** — Identify which customers are churning
- **Why** — Understand why they're churning
- **Impact** — Quantify the revenue impact of churn
- **Actions** — Recommend actions to improve retention

## Tech Stack

| Category | Tools |
|---|---|
| Database | SQLite (.db) |
| Language | Python 3 (Jupyter Notebook) |
| Libraries | sqlite3, pandas, numpy, matplotlib, seaborn |
| Export | CSV, HTML → PDF |

## Dataset

The database contains three related tables:

- **customers** — demographics: name, age, gender, country, state
- **subscriptions** — plan type, contract type, subscription channel, monthly charges, start/cancellation dates, churn score
- **support** — complaint records, escalation status, CSAT score

## Data Cleaning & Validation

1. Renamed ambiguous columns; dropped irrelevant fields
2. Converted date columns to datetime; standardized categorical values
3. Fixed duplicate support records by aggregating the latest complaint per customer
4. Validated join integrity before merging tables

## Feature Engineering

- **churn_flag** — created (1/0) from presence of a cancellation date
- **tenure_days** — subscription duration, in days
- **churn_risk** — Low/Medium/High, bucketed from churn_score
- **Ordinal encoding** — applied to categorical fields by business priority

## Key Metrics

| Metric | Value |
|---|---|
| Churn Rate | 28.57% |
| Retention Rate | 71.43% |
| Escalation Rate | 19.05% |
| Avg Tenure | ~1,452 days |
| Escalation ↔ Churn Correlation | 0.77 (strong positive) |

## Visualizations

- **Line chart** — monthly churn trend over time
- **Bar charts** — churn by plan type, churn by state
- **Heatmap** — correlation matrix across encoded features
- **Pair plot & cat plot** — multi-variable relationships

## Key Insights

- **Basic plan subscribers churn at 60%** — far higher than Standard (22%) or Premium (14%)
- **Escalation ↔ Churn: 0.77 correlation** — customers who escalated complaints show a strong correlation with churning
- **Regional & temporal spikes** — Karnataka had the highest state-level churn; September showed a churn spike

## Recommended Actions

- **Investigate Basic-Plan Churn** — root causes such as pricing, feature gaps, or service quality
- **Tiered Retention Outreach** — prioritize outreach by churn_risk tier, starting with high-value Premium customers
- **Audit Support Resolution** — reduce escalations by fixing recurring complaint themes
- **Cross-Reference Churn Spikes** — compare churn spikes against product/pricing change timelines

## Skills Demonstrated

SQL · SQLite · Python · Pandas · Data Cleaning · Feature Engineering · Exploratory Data Analysis · Data Visualization

## Repository Contents

| File | Description |
|---|---|
| `churn_analysis.ipynb` | Full analysis notebook (SQL queries, Python cleaning, feature engineering, visualizations) |
| `customer_churn_db.db` | SQLite database with `customers`, `subscriptions`, and `support` tables |
| `data.xlsx` | Raw source data |
| `Customer-Churn-Analysis-SQL-Python.pptx` | Project presentation summarizing findings |

## How to Run

1. Clone this repository
2. Open `churn_analysis.ipynb` in Jupyter Notebook or JupyterLab
3. Run all cells — the notebook connects to `customer_churn_db.db` and reproduces the full analysis

