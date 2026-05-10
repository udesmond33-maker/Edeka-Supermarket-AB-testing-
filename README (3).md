# Customer Analytics Project – Supermarket Sales (AB Testing & KPIs)

**Ironhack Data Analytics Bootcamp – Module 2**  
**Analyst:** Chukwuka Desmond Ugboaja  

This project uses a real retail supermarket dataset to analyse customer behaviour, measure performance with clear KPIs, and run basic AB‑style hypothesis tests. The goal is to show end‑to‑end analytical thinking: from cleaning raw data to data‑driven recommendations a business stakeholder could act on.

---

## 1. Project Overview

The analysis explores how sales differ across **product categories, regions, customer segments, and shipping modes**. It combines:

- Data cleaning and feature engineering
- Exploratory Data Analysis (EDA)
- KPI design and calculation
- Two hypothesis tests (Welch two‑sample t‑tests)
- Visual storytelling (plots and a KPI "dashboard" style view)

This README is written for both **bootcamp instructors** and **hiring managers** who want to quickly understand what the project does and what decisions it supports.

---

## 2. Dataset

- **Source:** [Kaggle – Supermarket Dataset](https://www.kaggle.com/datasets/eslamessam2025/supermarket)
- **Scope:** 9,789 transaction lines from 2015–2018, covering multiple regions, product categories, customer segments, and shipping modes in the US.
- **Key fields:** Order and ship dates, customer and segment, region, category and sub‑category, product, and sales amount.

---

## 3. Repository Structure

```text
├── Solo-AB-testing-project.ipynb   # Main Jupyter Notebook (EDA, KPIs, tests)
├── supermarket.csv                 # Raw dataset
├── visualizations/
│   ├── viz_01_sales_by_category.png
│   ├── viz_02_sales_by_region.png
│   ├── viz_03_sales_by_segment.png
│   ├── viz_04_shipping_mode.png
│   ├── viz_kpi_summary123.png
│   ├── viz_06_hypothesis1.png
│   └── viz_07_hypothesis2.png
├── README.md
└── presentation.pdf
```

---

## 4. Analysis Steps

### 4.1 Data Exploration & Preparation

- Loaded the raw CSV and inspected shape, column types, and basic statistics.
- Handled missing values (dropped rows with missing postal code) and confirmed there were no duplicate rows.
- Converted date columns and engineered `Year`, `Month`, and `MonthName` for time‑based views.
- Verified the final cleaned dataset: **9,789 rows × 21 columns**, with average `Sales` of about **$230.12** per line.

### 4.2 Exploratory Data Analysis (EDA)

Key questions answered:

1. Which **product categories** generate the most revenue?
2. Which **regions** are the strongest?
3. Which **customer segments** contribute the most orders and sales?
4. Which **shipping modes** drive the most revenue?

---

## 5. KPIs and Main Results

| KPI | Result |
|-----|--------|
| **Total Sales** | ~$2.25M across all regions and categories |
| **Avg Sales per Order Line** | ~$230 per transaction |
| **Top Product Category** | Technology — largest revenue share |
| **Top Region** | West — $710,219.68 in total sales |
| **Top Segment (by orders)** | Consumer — 2,535 unique orders |
| **Top Shipping Mode** | Standard Class — $1,332,617.14 in revenue (59.2%) |

---

## 6. Hypothesis Tests

Two Welch two‑sample t‑tests were run at α = 0.05.

### Test 1 – Consumer vs Corporate (Average Sales per Order)

- **H₀:** Mean sales per order are equal for both segments
- **H₁:** Mean sales per order are different
- **p-value:** ~0.6412
- **Result:** Fail to reject H₀ — no statistically significant difference

### Test 2 – West vs East (Average Sales per Order)

- **H₀:** Mean sales per order are equal for both regions
- **H₁:** Mean sales per order are different
- **p-value:** ~0.4275
- **Result:** Fail to reject H₀ — no statistically significant difference

**Business takeaway:** Performance differences are driven by **order volume**, not order size. Strategies should focus on increasing the number of orders in underperforming segments and regions.

---

## 7. Business Recommendations

1. **Double down on winners** — Prioritise the Consumer segment and West region with targeted retention and upsell campaigns.
2. **Grow underperforming regions through volume** — Use promotions and localised marketing to increase order frequency where average values are already comparable.
3. **Protect the top category** — Monitor stock, pricing, and discounting in Technology to prevent revenue leakage.
4. **Leverage Standard Class shipping** — Offer free Standard Class above a basket threshold to nudge higher order values without increasing delivery costs proportionally.

---

## 8. Tech Stack

| Tool | Purpose |
|------|---------|
| Python (pandas, numpy) | Data cleaning, feature engineering, KPI calculations |
| Matplotlib / Seaborn | EDA charts and KPI visualisations |
| SciPy (stats) | Welch t‑tests |
| Jupyter Notebook | Reproducible analysis workflow |
| Git & GitHub | Version control and portfolio hosting |
| Tableau | Interactive dashboard |

---

## 9. How to Run

```bash
# 1. Clone the repo
git clone <your-repo-url>.git
cd <your-repo-folder>

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# 3. Add dataset
# Download supermarket.csv from Kaggle and place in project root

# 4. Run the notebook
# Open Solo-AB-testing-project.ipynb in Jupyter and run all cells
```

---

*For hiring managers: the notebook shows full reasoning, code, and visuals behind this summary.*  
*For bootcamp evaluators: it demonstrates applied statistics, EDA, and KPI‑driven storytelling on a realistic dataset.*
