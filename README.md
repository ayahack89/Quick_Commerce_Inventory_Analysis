# quick-commerce-inventory-analysis

Dataset: Publicly available Zepto inventory dataset sourced from Kaggle.

## Overview

An end-to-end data analysis project on quick-commerce inventory data, focused on identifying stock-out patterns, high-value unavailable products, discounting behaviour, and inventory distribution across product categories.

## Tools Used

- **Python (Pandas)** — data auditing and cleaning
- **PostgreSQL** — structured querying and insight extraction
- **Excel** — visualization and final report

## Dataset

- Source: Kaggle (Zepto quick-commerce inventory dataset)
- Records: 3,732 products
- Columns: 9
- Categories: 14
- Unique products: 1,681

## Project Structure

```
quick-commerce-inventory-analysis/
│
├── data/               # Raw dataset
├── python/             # Data audit & cleaning scripts
├── sql/                # SQL queries used for analysis
├── excel/              # Dashboard and final report
└── README.md
```

## Key Findings

- Overall stock-out rate: **12.14%** (453 of 3,732 products)
- Highest stock-out categories: **Biscuits (28.57%)**, **Beverages (21.71%)**, **Dairy, Bread & Batter (21.71%)**
- High-value unavailable products include **Patanjali Cow's Ghee (₹565)** and **MamyPoko Diapers (₹399)**
- Discounting is highest in **Fruits & Vegetables (15.46%)** and lowest in **Home & Cleaning (5.68%)**
- Inventory is concentrated in **Munchies** and **Cooking Essentials** (2,186 units each)

## Objective

To surface actionable inventory insights that can help quick-commerce platforms reduce stock-outs, prioritize high-value SKUs, and optimize discounting and inventory allocation.

## How to Use

1. Load the dataset from `data/`
2. Run the audit scripts in `python/`
3. Execute SQL queries in `sql/` against a PostgreSQL instance
4. Open the Excel dashboard in `excel/` for the visual report