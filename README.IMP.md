## 📌 Project Overview
This project focuses on analyzing a comprehensive dataset of a pizza restaurant's sales over a full calendar year. Using **SQL (Structured Query Language)**, I imported, cleaned, and analyzed the raw transactional data to extract critical business metrics and key performance indicators (KPIs). The goal of this analysis is to identify actionable insights regarding sales performance, order trends, product popularity, and revenue distribution.

---

## 🛠️ Tech Stack & Skills Used
- **Database Engine:** MySQL / SQL Server
- **Language:** SQL
- **Concepts Applied:** Data Aggregation (`SUM`, `COUNT`), Data Formatting (`STR_TO_DATE`), Data Grouping (`GROUP BY`, `ORDER BY`), Window Functions/Subqueries, Ranking Limiters (`LIMIT`/`TOP`).

---

## 📈 Key Metrics & Business Insights Discovered

### 1. Executive Summary (Core KPIs)
- **Total Revenue:** $817,860.05
- **Total Orders Placed:** 21,350 unique orders
- **Average Order Value:** $38.31 per order
- **Total Pizzas Sold:** 49,574 individual pizzas
- **Average Pizzas Per Order:** 2.32 pizzas

### 2. Order Trends & Behavior
- **Daily Trend:** **Friday** is the busiest day of the week, capturing the highest volume of order receipts (3,538 orders), closely followed by Thursday and Saturday. Sundays experience the lowest traffic.
- **Monthly Trend:** Sales peaked significantly in **July** (1,935 orders) and May, while dipping to their lowest points in September and October.

### 3. Category & Size Breakdowns
- **Category Popularity:** The **Classic** pizza category is the highest revenue generator (26.91% of total sales), though Supreme, Chicken, and Veggie categories follow closely behind, each accounting for roughly ~23-25% of total sales.
- **Size Preferences:** **Large (L)** size pizzas dominate the market, generating **45.89%** of the total company revenue. Extra Large (XL) and Double Extra Large (XXL) sizes account for less than 2% combined.

### 4. Product Performance Rankings
- **Top Performer (Revenue):** *The Thai Chicken Pizza* ($43,434.25 generated)
- **Top Performer (Quantity & Orders):** *The Classic Deluxe Pizza* (2,453 pizzas sold across 2,329 distinct orders)
- **Worst Performer (All Metrics):** *The Brie Carre Pizza* ($11,588.50 generated, only 490 sold).

---

##  SQL Queries Featured in this Project
This project contains the complete code library to answer crucial business questions. The queries include:
1. **Core KPIs:** Adding up revenue, extracting distinct order counts, and calculating averages safely using decimal multipliers to prevent integer truncation.
2. **Date & Trend Analysis:** Translating text-based dates into standard database datetime objects using `STR_TO_DATE()` and grouping by `DAYNAME()` and `MONTHNAME()`.
3. **Advanced Ratios:** Utilizing dynamic subqueries to inject corporate-wide grand totals into category-specific calculations for exact percentage metrics.
4. **Product Rankings:** Implementing top and bottom filters using ascending/descending sorting paired with strict output limits.

---

** How to Run this Project**
1. Clone this repository to your local machine.
2. Open your preferred SQL Workbench (MySQL, SSMS, etc.).
3. Run the data import wizard to import the `pizza_sales.csv` file.
4. Execute the script inside the `pizza_queries.sql` file to reproduce all metrics.
