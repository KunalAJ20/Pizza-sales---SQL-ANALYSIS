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

**Order Day**  **Total Orders**
Sunday	          2624
Monday	          2794
Tuesday	          2973
Wednesday	        3024
Thursday	        3239
Friday	          3538
Saturday	        3158

- **Monthly Trend:** Sales peaked significantly in **July** (1,935 orders) and May, while dipping to their lowest points in September and October.

**Order Month**   **Total Orders** 
April  	         1799
August	         1841
December	       1680
February	       1685
January	         1845
July	           1935
June	           1773
March	           1840
May	             1853
November	       1792
October	         1646
September	       1661

### 3. Category & Size Breakdowns
- **Category Popularity:** The **Classic** pizza category is the highest revenue generator (26.91% of total sales), though Supreme, Chicken, and Veggie categories follow closely behind, each accounting for roughly ~23-25% of total sales.

**Percentage of Sales by Pizza Category**
Pizza    Total Sales  Pct Sales
Classic	 220053.1	    26.91
Supreme	 208197	      25.46
Chicken	 195919.5	    23.96
Veggie	 193690.45	   23.68

- **Size Preferences:** **Large (L)** size pizzas dominate the market, generating **45.89%** of the total company revenue. Extra Large (XL) and Double Extra Large (XXL) sizes account for less than 2% combined.

**Percentage of Sales by Pizza Size**
Pizza Size  Total sales  Pct sales
L	          375318.7	   45.89
M	          249382.25	   30.49
S	          178076.5	   21.77
XL	        14076	       1.72
XXL	        1006.6	     0.12

**Total Pizzas Sold by Pizza Category**
pizza_category  Total_Pizzas_Sold
Classic	         14888
Supreme	         11987
Veggie	         11649
Chicken	         11050


### 4. Product Performance Rankings
 **Top 5 pizzas sold by revenue**
pizza_name                     Total_Revenue
The Thai Chicken Pizza	          43434.25
The Barbecue Chicken Pizza	      42768
The California Chicken Pizza	    41409.5
The Classic Deluxe Pizza	        38180.5
The Spicy Italian Pizza	          34831.25
- **Top Performer (Revenue):** *The Thai Chicken Pizza* ($43,434.25 generated)

**Top 5 Pizzas by Quantity**

pizza_name               Total_Quantity
The Classic Deluxe Pizza	      2453
The Barbecue Chicken Pizza	    2432
The Hawaiian Pizza	            2422
The Pepperoni Pizza	            2418
The Thai Chicken Pizza	        2371
- **Top Performer (Quantity & Orders):** *The Classic Deluxe Pizza* (2,453 pizzas sold across 2,329 distinct orders)


  **Top 5 Pizzas by Total Orders**
  
The Classic Deluxe Pizza	    2329
The Hawaiian Pizza	          2280
The Pepperoni Pizza	          2278
The Barbecue Chicken Pizza	  2273
The Thai Chicken Pizza	      2225

 
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
