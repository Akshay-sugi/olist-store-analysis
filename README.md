�

�
🛒 Olist E-Commerce Store Analysis


�
An end-to-end Data Analytics project using MySQL · Excel · Power BI · Tableau
Uncovering sales trends, customer behaviour, and delivery insights from Brazil's largest e-commerce marketplace 


�
￼ ￼ ￼ ￼ 


�
￼ ￼ ￼ ￼ 


📑 Table of Contents
#
Section
1
Project Overview
2
Team
3
Tools & Tech Stack
4
Dataset Description
5
Problem Statement
6
SQL Analysis & KPIs
7
Excel Dashboard
8
Tableau Dashboard
9
Power BI Dashboard
10
Key KPIs at a Glance
11
Business Insights & Suggestions
12
Key Learnings
13
Project Structure
14
How to Run
📌 Project Overview
Objective: Analyze Olist's complete e-commerce operations — from order volumes and payment behaviour to delivery performance and customer satisfaction — and surface actionable business insights through interactive multi-tool dashboards.
Olist is Brazil's largest e-commerce marketplace, connecting thousands of sellers to customers across the country. This project follows a complete end-to-end analytics pipeline covering:
Code
Key questions answered:
📅 How do weekday vs weekend sales patterns differ?
⭐ How does delivery time impact customer review scores?
🏙️ Which cities and categories drive the most revenue?
💳 What payment methods do customers prefer?
🚚 What is the average delivery time by product category?
👥 Team
Group 4
#
Name
1
Rushikesh R Kale
2
G Poorna Sai Kumar
3
Anushsree D
4
Vilas V Katpure
5
Akshay Sugi
🛠 Tools & Tech Stack
�
ToolVersion / TypePurpose🗄️ MySQLMySQL Workbench + MySQL 8.0+Database setup, FK relationships, multi-table JOINs, all KPI queries📊 Microsoft ExcelExcel 2016+ (.xlsm)Pivot tables, interactive slicers, conditional formatting dashboards📊 Power BIPower BI Desktop (.pbix)DAX measures, KPI cards, interactive slicers, multi-page report📊 TableauTableau Desktop / Public (.twbx)Geo-spatial visualizations, calculated fields, dashboard storytelling
📂 Dataset Description
Source: Kaggle — Olist Brazilian E-Commerce Public Dataset
The project uses a MySQL database (olist_db) with 9 core tables spanning 2016–2018.
Table
Key Fields
Description
customers
customer_id, customer_city, customer_state
Customer location data
orders
order_id, customer_id, order_status, order_purchase_timestamp, order_delivered_customer_date
Full order lifecycle with timestamps
order_items
order_id, product_id, seller_id, price, freight_value
Item-level price and freight
order_payments
order_id, payment_type, payment_value, payment_installments
Payment method and value
order_reviews
order_id, review_score, review_comment_message
Customer ratings (1–5 stars)
products
product_id, product_category_name
Product catalog with categories
sellers
seller_id, seller_city, seller_state
Seller location
geolocation
geolocation_zip_code_prefix, geolocation_lat, geolocation_lng
Lat/lng for mapping
category_translation
product_category_name, product_category_name_english
Portuguese → English category names
Dataset scale: 99,441 orders · 8 interconnected tables · R$15.74M total revenue
❓ Problem Statement
#
Business Question
1
Which cities and categories drive the most revenue?
2
How does delivery time impact customer review scores?
3
What are the weekday vs weekend sales patterns?
4
What payment methods do customers prefer?
5
What is the average delivery performance by category?
🗄️ SQL Analysis & KPIs
Database Setup
Sql
�
📊 Click to expand — All KPI Queries
Sql
�

📊 Excel Dashboard
The Excel workbook contains pivot table–based dashboards with interactive slicers for filtering by payment type and state.
Features:
Pivot tables for category & city-level analysis
Interactive slicers for filtering by payment type and state
Conditional formatting for performance indicators
📊 Tableau Dashboard
The Tableau packaged workbook (.twbx) includes embedded data — no additional data connection is required.
Visualizations:
Visual
Insight
Monthly Sales Trend
Line chart showing revenue growth from 2016 → 2018
Delivery Time vs Review Score
Scatter / bar showing inverse relationship
Top 10 Categories by Revenue
Horizontal bar — cama_mesa_banho leads
KPIs surfaced:
KPI
Value
Credit Card Orders
57,080
Total Orders
99,440
Pet Shop Avg Delivery
11.3 days
Total Sales
R$16.01M
Filters: Payment Type · Order Year · Customer State · Product Category
📊 Power BI Dashboard
The Power BI file (.pbix) delivers a fully interactive, multi-page analytics report with DAX measures and dynamic slicers.
Page 1 — Operations Overview
Visual
Insight
Avg Payment & Price — São Paulo
Card KPIs for Brazil's top city
Delivery Time vs Review Score
Bar chart showing satisfaction drop with longer delivery
Total Sales by Day Type
Weekday vs Weekend revenue split
Header KPIs:
Avg Shipping
Five-Star Credit Orders
Total Sales
Total Orders
11.31 days
44,000
R$16.01M
96,000
Page 2 — Growth & Category Breakdown
Visual
Insight
Total Sales by Year (Line)
R0.1M (2016) → R7.2M (2017) → R$8.7M (2018)
Orders by Category (Bar)
Top categories ranked by order volume
Order Status Distribution (Donut)
97.02% of orders successfully delivered
Filters: Order Year · Payment Type · Customer State · Order Status
📈 Key KPIs at a Glance
�
Total Orders

99,441

2016 – 2018Total Revenue

R$15.74M

Payment valueAvg Delivery

12.1 days

From purchaseTop Combo Orders

43,981

5★ + Credit CardWeekday Revenue Share

77%

R$12.16MTop City

São Paulo

15,540 orders · R$1.91MDelivery Rate

97.02%

Successfully deliveredScore 5 Avg Delivery

10.6 days

vs 21.3 days for Score 1
💡 Business Insights & Suggestions
�
🚚 1. Reduce Delivery Time to Boost Review Scores 
Score 1 orders average 21.3 days delivery versus just 10.6 days for Score 5 orders — a clear inverse relationship. Partnering with regional logistics providers to cut delivery below 7 days could have a direct, measurable impact on customer satisfaction and repeat purchase rates. 


�
📣 2. Boost Weekend Sales with Targeted Campaigns 
Weekdays drive 77% of total revenue (R$12.16M vs R$3.58M on weekends). Launching weekend flash sales, exclusive discounts, and push notifications specifically targeting the Fri–Sun window could meaningfully close this gap and grow overall revenue share. 


�
📍 3. Expand Beyond São Paulo 
São Paulo alone accounts for ~15% of all orders (15,540 orders, R$1.91M revenue). Investing in warehouse infrastructure and seller onboarding in underserved states like Bahia and Paraná would diversify revenue concentration and reduce geographic risk. 


�
💳 4. Reward Credit Card Buyers 
Credit card users represent the highest-value segment — 43,981 orders carried both a credit card payment AND a 5-star review. Introducing cashback offers, installment plans, and loyalty points targeted at this cohort would reinforce the behaviour that drives both revenue and satisfaction. 


�
🛏 5. Double Down on Top-Performing Categories 
Bed, Bath & Table (cama_mesa_banho) leads with 11,115 orders. Prioritizing seller recruitment, stock depth, and targeted ads in the top 3 categories would maximize returns on marketing spend and fulfillment investment. 


�
⭐ 6. Actively Address Low Review Scores 
Implementing automated follow-ups for Score 1–2 orders, offering refunds or discount vouchers, and flagging high-delay sellers for performance review would reduce churn and protect brand reputation on Brazil's most competitive e-commerce platform. 


📚 Key Learnings
Tool
Skills Developed
MySQL
Data modeling, FK relationships, complex multi-table JOINs, window functions, data cleaning during import
Power BI
DAX measures, interactive slicers, multi-page KPI dashboards for business stakeholders
Tableau
Geo-spatial visualizations, calculated fields, dashboard storytelling
Excel
Pivot tables, conditional formatting, slicer-based interactive dashboards
📁 Project Structure
Code
🚀 How to Run
🗄️ SQL (MySQL)
Download the Olist dataset from Kaggle.
Open MySQL Workbench and create a new schema named olist_db.
Import the CSV files into the corresponding tables.
Run olist_analytics.sql to execute all KPI queries.
Sql
📊 Excel
Open Olist_Analytics.xlsm in Excel 2016+.
Enable macros if prompted.
Navigate to the Dashboard sheet.
Use the slicers to filter by Payment Type, State, or Year.
📊 Power BI
Open Olist_PowerBI_Dashboard.pbix in Power BI Desktop.
Click Refresh if connected to a live data source, or explore pre-loaded visuals.
Use slicers to drill into specific years, states, categories, or payment types.
📊 Tableau
Open Olist_Tableau_Dashboard.twbx in Tableau Desktop or Tableau Public.
Data is embedded — no additional connection required.
Use filter controls to slice by Year, State, Category, or Payment Type.
📋 Requirements
Tool
Requirement
MySQL
8.0+
Microsoft Excel
2016+ with macro support (.xlsm)
Power BI Desktop
Free — Download here
Tableau
Desktop or Public (free) — Download here
MySQL Workbench
Free — Download here
Dataset
Kaggle — Olist Brazilian E-Commerce
�
⭐ If this project helped you, please consider giving it a star! ⭐


�
￼   ￼   ￼ 


