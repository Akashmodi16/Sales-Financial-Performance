📊 Sales Financial Performance Dashboard
MySQL • Power BI • KPI Analysis • Financial Insights • Data Analytics Project

This project presents a complete Sales & Financial Performance Dashboard built using MySQL for backend data processing and Power BI for visualization.
It highlights key business metrics such as Revenue, Profit, Customer Segments, Category Performance, Top Products, and City-Level Sales Trends—similar to real-world BI Analyst workflows.

🚀 Project Overview

The primary objective of this project is to analyze and visualize sales data to uncover insights related to:
Revenue & profit trends
Customer demographics (gender, age groups)
Product & category performance
Best-selling items
City-wise contribution
Repeat customer behavior
This project simulates the analytics work done in an e-commerce company.

🛠 Tools & Technologies Used
Tool	Purpose
MySQL	Data modeling, transformation, KPI calculations
Power BI	Dashboard design, reporting, visualization
DAX	Calculated measures for analysis
Power Query	Data cleaning & shaping
📂 Project Structure
Sales-Financial-Performance/
│
├── powerbi-dashboard/
│     └── Sales-Financial-Performance-Dashboard.pbix
│
├── sql-queries/
│     └── sales_financial_performance.sql
│
└── snapshots/
      ├── dashboard_overview.png
      ├── revenue_trend.png
      └── category_performance.png

🧱 Database Design (MySQL Schema)
customers

customer_id
age
gender
register_date
city

products
product_id
category
sub_category
brand

orders
order_id
order_date
customer_id
product_id
quantity
selling_price
cost_price
discount
revenue (calculated)
profit (calculated)

🧮 Key SQL Operations (Summary)

Highlights from the SQL logic used in this project:

✔ Revenue & Profit Calculation
ALTER TABLE orders
ADD Column revenue DECIMAL(10,2),
ADD Column profit DECIMAL(10,2);
UPDATE orders
SET
revenue = selling_price * quantity,
profit = (selling_price - cost_price) * quantity;

✔ KPI Summary
SELECT
SUM(revenue) AS total_revenue,
SUM(profit) AS total_profit,
COUNT(order_id) AS total_orders
FROM orders;

✔ Category-Level Analysis
SELECT 
    p.category,
    SUM(o.revenue) AS category_revenue,
    SUM(o.profit) AS category_profit
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.category
ORDER BY category_revenue DESC;

✔ Best-Selling Products
SELECT 
    p.product_id,
    p.category,
    p.sub_category,
    SUM(o.quantity) AS units_sold
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.product_id, p.category, p.sub_category
ORDER BY units_sold DESC
LIMIT 10;

📊 Power BI Dashboard Highlights

The Power BI report includes:

🔹 1. KPI Cards

Total Revenue
Total Profit
Total Orders

🔹 2. Revenue & Profit Trend (Line Chart)

Shows monthly performance over time.

🔹 3. Category Performance (Bar Chart)

Identifies top-performing product categories.

🔹 4. Gender Analysis

Male vs. Female purchasing patterns.

🔹 5. City-Level Sales

Finds geographic markets contributing most revenue.

🔹 6. Best-Selling Products

Top items based on units sold.

🔹 7. Repeat Customer Analysis

Customer behavior & retention insights.

💡 Key Insights Derived

✔ Majority of revenue is driven by certain high-performing categories
✔ Profit contribution varies significantly between products
✔ Age group 26–35 shows strong purchasing behavior
✔ Female shoppers (or male, depending on dataset) influence high revenue in some segments
✔ Some products have high sales volume but low profit → pricing optimization needed
✔ Specific cities dominate sales share

📌 How to Use This Project
1. Clone the Repository
git clone https://github.com/YOUR_USERNAME/Sales-Financial-Performance.git

2. Run SQL Script in MySQL
source sql-queries/sales_financial_performance.sql;

3. Open Power BI Report
powerbi-dashboard/Sales-Financial-Performance-Dashboard.pbix

4. Refresh the data model

Reconnect to your MySQL database if needed.

📝 Conclusion

This project demonstrates the complete workflow of a BI Analyst / Data Analyst:
Data modeling using SQL
KPI computation
Visualization & storytelling using Power BI
Extracting meaningful business insights

It showcases technical skills + business understanding required for analytics roles.
🤝 Connect With Me
If you found this project valuable, feel free to ⭐ the repository or reach out!
