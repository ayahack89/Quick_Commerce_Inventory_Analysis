# Quick Commerce Inventory Analysis

## 1. Overview

This project analyzes a quick-commerce product inventory dataset, currently using Zepto's data to identify inventory availability issues, stock-out patterns, high-value unavailable products, discounting patterns, and inventory distribution across product categories.

The analysis was carried out using **Python** for data auditing, **PostgreSQL** for structured querying and insight extraction, and **Excel** for visualization and the final report.

## 2. Problem

Quick-commerce platforms like Zepto depend heavily on product availability and efficient inventory management. Frequent stock-outs can result in missed sales opportunities, while uneven inventory distribution and aggressive discounting can affect revenue and inventory efficiency.

The purpose of this analysis is to examine the available inventory data and identify where stock availability, product prioritization, discounting, and inventory distribution may require attention.

## 3. Objective

The analysis aims to:

- Measure the overall stock-out rate.
- Identify categories with higher stock-out rates.
- Identify high-value products that are currently unavailable.
- Analyze discount patterns across categories.
- Understand inventory distribution across categories.
- Identify potential areas for inventory optimization.
- Present the findings through an Excel dashboard.

## 4. Dataset

The dataset used is the Zepto quick-commerce dataset, containing **3,732 product records** across **9 columns**.

Key fields include:

- Category
- Product name
- MRP
- Discount percentage
- Available quantity
- Discounted selling price
- Weight
- Out-of-stock status
- Quantity

The dataset covers **14 product categories** and **1,681 unique product names**.

| Check           | Result |
| --------------- | -----: |
| Records         |  3,732 |
| Columns         |      9 |
| Missing values  |      0 |
| Duplicate rows  |      2 |
| Categories      |     14 |
| Unique products |  1,681 |

## 5. Data Preparation & Audit

The audit included:

1. Dataset dimensions
2. Column names and structure
3. Data types
4. Missing values
5. Duplicate records
6. Descriptive statistics

The dataset contained **no missing values** and **2 duplicate records**.

## 6. Data Cleaning & SQL Analysis

Before diving into the analysis, a few foundational questions had to be answered to guide the direction of the insights. The following sections present the key business questions and the SQL queries used to address them.


### A. Overall Inventory Health

**How serious is the stock-out problem?**

```sql
SELECT
    COUNT(*) AS total_products,
    COUNT(*) FILTER (WHERE out_of_stock = TRUE) AS out_of_stock_products,
    COUNT(*) FILTER (WHERE out_of_stock = FALSE) AS available_products,
    ROUND(
        100.0 * COUNT(*) FILTER (WHERE out_of_stock = TRUE) / COUNT(*), 2
    ) AS stockout_rate
FROM products;
```

**Insight:** The overall stock-out rate stands at **12.14%**, meaning roughly 1 in 8 products is currently unavailable.

### B. Stock-out by Category

**Which categories have the highest stock-out rates?**

```sql
SELECT
    category,
    COUNT(*) AS total_products,
    COUNT(*) FILTER (WHERE out_of_stock = TRUE) AS out_of_stock_products,
    ROUND(
        100.0 * COUNT(*) FILTER (WHERE out_of_stock = TRUE) / COUNT(*), 2
    ) AS stockout_rate
FROM products
GROUP BY category
ORDER BY stockout_rate DESC;
```

**Insight:** **Biscuits (28.57%)**, **Beverages (21.71%)**, and **Dairy, Bread & Batter (21.71%)** show the highest stock-out rates — significantly above the overall average.

### C. High-Value Unavailable Products

**Which high-value products are currently unavailable?**

```sql
SELECT
    product_id,
    name,
    category,
    mrp,
    discount_percent,
    discounted_selling_price
FROM products
WHERE out_of_stock = TRUE
ORDER BY mrp DESC
LIMIT 10;
```

**Insight:** High-MRP items such as **Patanjali Cow's Ghee (₹565)**, **MamyPoko Diapers (₹399)**, and **Aashirvaad Atta (₹315)** are among the top unavailable products — representing significant lost revenue opportunities.

### D. Discount Analysis

**How are discounts distributed across categories?**

```sql
SELECT
    category,
    ROUND(AVG(discount_percent), 2) AS avg_discount,
    ROUND(MIN(discount_percent), 2) AS min_discount,
    ROUND(MAX(discount_percent), 2) AS max_discount
FROM products
GROUP BY category
ORDER BY avg_discount DESC;
```

**Insight:** **Fruits & Vegetables (15.46%)** and **Meats, Fish & Eggs (11.03%)** carry the highest average discounts. Most other categories hover between 5–8%, with maximum discounts reaching up to 51% in Biscuits.

### E. Inventory Distribution

**Where is available inventory concentrated?**

```sql
SELECT
    category,
    SUM(available_quantity) AS total_available_inventory,
    ROUND(AVG(available_quantity), 2) AS avg_inventory_per_product
FROM products
WHERE out_of_stock = FALSE
GROUP BY category
ORDER BY total_available_inventory DESC;
```

**Insight:** **Munchies** and **Cooking Essentials** hold the largest available inventory (2,186 units each), while **Meats, Fish & Eggs (152 units)** and **Fruits & Vegetables (275 units)** hold the least — suggesting potential under-stocking in perishable categories.

## 8. Key Findings

- The overall stock-out rate is **12.14%** a meaningful availability gap.
- **Biscuits, Beverages, and Dairy/Bread/Batter** are the most stock-out-prone categories.
- Several **high-MRP products** are currently out of stock, pointing to revenue leakage.
- Discounting is **uneven** fresh categories are discounted more aggressively than packaged ones.
- Inventory is **concentrated in Munchies and Cooking Essentials**, while perishables run lean.

## 9. Recommendations

- Prioritize replenishment for **Biscuits, Beverages, and Dairy** categories.
- Flag high-MRP out-of-stock SKUs for urgent restocking.
- Re-evaluate discount strategy in **Fruits & Vegetables** to balance volume and margin.
- Consider increasing buffer stock for **Meats, Fish & Eggs** to reduce stock-out risk.
- Build a recurring inventory health dashboard in Excel for ongoing monitoring.

## 10. Limitations

- The analysis is based on a **single snapshot** of inventory data no time-series trends.
- Only **Zepto's dataset** is used; cross-platform comparisons are not possible.
- Demand-side data (sales velocity, customer searches) is not included.
- Duplicate records (2) were minor but may slightly affect category-level aggregates.
- Discounts and MRP are treated as given; promotional context is unknown.

## 11. Final Analysis

This analysis highlights that while Zepto's overall inventory health is reasonable, there are clear pockets of concern particularly in **Biscuits, Beverages, and Dairy**, and among **high-value SKUs**. Discounting is skewed toward fresh produce, and inventory is unevenly distributed across categories. Addressing these gaps through targeted replenishment, smarter discounting, and better inventory balancing can directly improve both availability and revenue efficiency.
