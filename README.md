# Pizza-sales---SQL-ANALYSIS
A SQL analytics project exploring data from fictional pizza store to tell the revenue , order distributions and top selling products



SQL QUERIES -- 

use azure;

-- SECTION 1: CORE KPI METRICS

-- 1. Total Revenue (Sum of all sales)
select SUM(total_price) AS Total_Revenue 
from `pizza_sales (1)`;

-- 2. Total Orders Placed 
select COUNT(DISTINCT order_id) AS Total_Orders 
from `pizza_sales (1)`;

-- 3. Average Amount Spent per Order
SELECT SUM(total_price) / COUNT(DISTINCT order_id) AS Avg_Order_Value 
FROM `pizza_sales (1)`;

-- 4. Total Pizzas Sold (Sum of physical quantities)
SELECT SUM(quantity) AS Total_Pizzas_Sold 
FROM `pizza_sales (1)`;

-- 5. Average Number of Pizzas Sold per Order
SELECT SUM(quantity) * 1.0 / COUNT(DISTINCT order_id) AS Avg_Pizzas_per_Order 
FROM `pizza_sales (1)`;


-- SECTION 2: TRENDS & CATEGORY BREAKDOWNS 

-- 6. Daily Trend for Total Orders
select DAYNAME(STR_TO_DATE(order_date, '%d-%m-%Y')) AS Order_Day, 
COUNT(DISTINCT order_id) AS Total_Orders
from `pizza_sales (1)`
GROUP BY DAYNAME(STR_TO_DATE(order_date, '%d-%m-%Y'))
ORDER BY FIELD(Order_Day, 'Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday');

-- 7. Monthly Trend for Total Orders

SELECT MONTHNAME(STR_TO_DATE(order_date, '%d-%m-%Y')) AS Month_Name, 
COUNT(DISTINCT order_id) AS Total_Orders
FROM `pizza_sales (1)`
GROUP BY MONTHNAME(STR_TO_DATE(order_date, '%d-%m-%Y'))
ORDER BY MONTHNAME(STR_TO_DATE(order_date, '%d-%m-%Y'));

-- 8. Percentage of Sales by Pizza Category

select pizza_category, ROUND(SUM(total_price), 2) AS Total_Sales,
ROUND((SUM(total_price) / (SELECT SUM(total_price) FROM `pizza_sales (1)`)) * 100, 2) AS PCT_Sales
from `pizza_sales (1)`
GROUP BY pizza_category
ORDER BY PCT_Sales DESC;

-- 9. Percentage of Sales by Pizza Size

SELECT pizza_size, ROUND(SUM(total_price), 2) AS Total_Sales,
ROUND((SUM(total_price) / (SELECT SUM(total_price) FROM `pizza_sales (1)`)) * 100, 2) AS PCT_Sales
FROM `pizza_sales (1)`
GROUP BY pizza_size
ORDER BY PCT_Sales DESC;

-- 10. Total Pizzas Sold by Pizza Category
select pizza_category, SUM(quantity) AS Total_Pizzas_Sold
from `pizza_sales (1)`
GROUP BY pizza_category
ORDER BY Total_Pizzas_Sold DESC;


-- SECTION 3: TOP 5 BEST SELLERS (HIGH TO LOW)

-- 11. Top 5 Pizzas by Revenue (Most Money Made)
select pizza_name, SUM(total_price) AS Total_Revenue
from `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
limit 5;

-- 12. Top 5 Pizzas by Quantity (Most Physical Volume Sold)
select pizza_name, SUM(quantity) AS Total_Quantity
from `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Quantity DESC
limit 5;

-- 13. Top 5 Pizzas by Total Orders 
select pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Orders DESC
limit 5;


-- SECTION 4: BOTTOM 5 WORST SELLERS (LOW TO HIGH)

-- 14. Bottom 5 Pizzas by Revenue 
select pizza_name, ROUND(SUM(total_price), 2) AS Total_Revenue
FROM `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
limit 5;

-- 15. Bottom 5 Pizzas by Quantity (Least Pizzas Sold)
select pizza_name, SUM(quantity) AS Total_Quantity
FROM `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Quantity ASC
limit 5;

-- 16. Bottom 5 Pizzas by Total Orders (Appeared on Fewest Receipts)
select pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM `pizza_sales (1)`
GROUP BY pizza_name
ORDER BY Total_Orders ASC
limit 5;
