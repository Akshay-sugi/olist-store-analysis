<!--
  ╔══════════════════════════════════════════════════════╗
  ║  BEFORE PUBLISHING: Replace the placeholders below: ║
  ║  YOUR_USERNAME  →  your GitHub username              ║
  ║  YOUR_REPO      →  your repository name              ║
  ║  YOUR_LINKEDIN  →  your LinkedIn profile slug        ║
  ║  YOUR_EMAIL     →  your email address                ║
  ╚══════════════════════════════════════════════════════╝
-->

<h1 align="center">🛒 Olist E-Commerce Store Analysis</h1>

<p align="center">
  <b>An end-to-end Data Analytics project using MySQL · Excel · Power BI · Tableau</b><br/>
  <i>Uncovering sales trends, customer behaviour, and delivery insights from Brazil's largest e-commerce marketplace</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/MySQL-Data%20Engineering-orange?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Microsoft%20Excel-Dashboard-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white"/>
  <img src="https://img.shields.io/badge/Power%20BI-Analytics%20Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black"/>
  <img src="https://img.shields.io/badge/Tableau-Sales%20Dashboard-1F4E79?style=for-the-badge&logo=tableau&logoColor=white"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Domain-E--Commerce%20%26%20Retail-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/Records-99%2C441%20Orders-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Period-2016--2018-purple?style=flat-square"/>
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square"/>
</p>

---

> 🚀 **This project dives deep into 99,441 real orders from Olist — Brazil's largest e-commerce platform — to answer critical business questions around delivery performance, customer satisfaction, revenue patterns, and payment behaviour. Built end-to-end across four tools: MySQL for data engineering, and Excel, Power BI & Tableau for interactive dashboards.**

---

## 📑 Table of Contents

| # | Section |
|---|---------|
| 1 | [Project Overview](#-project-overview) |
| 2 | [Tools & Tech Stack](#-tools--tech-stack) |
| 3 | [Dataset Description](#-dataset-description) |
| 4 | [SQL Analysis & KPIs](#-sql-analysis--kpis) |
| 5 | [Excel Dashboard](#-excel-dashboard) |
| 6 | [Power BI Dashboard](#-power-bi-dashboard) |
| 7 | [Tableau Dashboard](#-tableau-dashboard) |
| 8 | [Key KPIs at a Glance](#-key-kpis-at-a-glance) |
| 9 | [Business Insights & Suggestions](#-business-insights--suggestions) |
| 10 | [Key Learnings](#-key-learnings) |
| 11 | [Project Structure](#-project-structure) |
| 12 | [How to Run](#-how-to-run) |

---

## 📌 Project Overview

> **Objective:** Analyze Olist's complete e-commerce operations — from order volumes and payment behaviour to delivery performance and customer satisfaction — and surface actionable business insights through interactive multi-tool dashboards.

This project follows a **complete end-to-end analytics pipeline** built on a single MySQL database:

```
olist_db (MySQL)
  ├── customers              ──►  Customer city & state distribution
  ├── orders                 ──►  Order volume, status, weekday vs weekend trends
  ├── order_items            ──►  Product-level revenue and category breakdown
  ├── order_payments         ──►  Payment method preferences and transaction values
  ├── order_reviews          ──►  Review scores and customer satisfaction
  ├── products               ──►  Category-level performance
  ├── sellers                ──►  Seller geography and activity
  ├── geolocation            ──►  Lat/lng mapping for cities and states
  └── category_translation   ──►  English translation of product categories
```

**Key questions answered:**
- 📅 How do weekday vs weekend sales patterns compare in revenue and volume?
- ⭐ How strongly does delivery time impact customer review scores?
- 🏙️ Which cities and product categories drive the most revenue?
- 💳 What payment methods do customers prefer — and how does it relate to satisfaction?
- 🚚 What is the average delivery performance by product category?

---

## 🛠 Tools & Tech Stack

<table>
  <tr>
    <th>Tool</th>
    <th>Version / Type</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td>🗄️ <b>MySQL</b></td>
    <td>MySQL Workbench + MySQL 8.0+</td>
    <td>Database setup, FK relationships, multi-table JOINs, window functions, all KPI queries</td>
  </tr>
  <tr>
    <td>📊 <b>Microsoft Excel</b></td>
    <td>Excel 2016+ (.xlsm)</td>
    <td>Raw data storage, pivot analysis, interactive dashboards with slicers and conditional formatting</td>
  </tr>
  <tr>
    <td>📊 <b>Power BI</b></td>
    <td>Power BI Desktop (.pbix)</td>
    <td>DAX measures, KPI cards, interactive slicers, multi-page analytics report</td>
  </tr>
  <tr>
    <td>📊 <b>Tableau</b></td>
    <td>Tableau Desktop / Public (.twbx)</td>
    <td>Geo-spatial visualizations, calculated fields, dashboard storytelling — embedded data, no extra connection needed</td>
  </tr>
</table>

---

## 📂 Dataset Description

The project uses a MySQL database (`olist_db`) with **9 core tables** spanning orders placed between **2016 and 2018**.

<details>
<summary><b>📋 Click to expand — All Dataset Tables</b></summary>

| Table | Key Fields | Description |
|-------|-----------|-------------|
| `customers` | `customer_id`, `customer_city`, `customer_state` | Customer location and demographics |
| `orders` | `order_id`, `customer_id`, `order_status`, `order_purchase_timestamp`, `order_delivered_customer_date` | Full order lifecycle with timestamps |
| `order_items` | `order_id`, `product_id`, `seller_id`, `price`, `freight_value` | Item-level price and freight details |
| `order_payments` | `order_id`, `payment_type`, `payment_value`, `payment_installments` | Payment method and transaction value |
| `order_reviews` | `order_id`, `review_score`, `review_comment_message` | Customer ratings (1–5 stars) and comments |
| `products` | `product_id`, `product_category_name` | Product catalog with category names |
| `sellers` | `seller_id`, `seller_city`, `seller_state` | Seller location data |
| `geolocation` | `geolocation_zip_code_prefix`, `geolocation_lat`, `geolocation_lng` | Lat/lng coordinates for geo mapping |
| `category_translation` | `product_category_name`, `product_category_name_english` | Portuguese → English category name mapping |

</details>

---

## 🗄️ SQL Analysis & KPIs

### Database Setup
```sql
CREATE DATABASE olist_db;
USE olist_db;
```

### KPI Queries

<details>
<summary><b>📊 Click to expand — All KPI Queries with Outputs</b></summary>

```sql
-- Q1: Weekday vs Weekend Sales
SELECT
    CASE
        WHEN DAYOFWEEK(o.order_purchase_timestamp) IN (1, 7) THEN 'Weekend'
        ELSE 'Weekday'
    END AS day_type,
    COUNT(DISTINCT o.order_id)     AS total_orders,
    ROUND(SUM(p.payment_value), 2) AS total_revenue
FROM orders o
JOIN order_payments p ON o.order_id = p.order_id
GROUP BY day_type;
-- ✅ Output: Weekday → R$12.37M (76,593 orders)  |  Weekend → R$3.64M (22,847 orders)

-- Q2: Orders with 5-Star Reviews AND Credit Card Payment
SELECT COUNT(DISTINCT o.order_id) AS qualifying_orders
FROM orders o
JOIN order_reviews  r ON o.order_id = r.order_id
JOIN order_payments p ON o.order_id = p.order_id
WHERE r.review_score = 5
  AND p.payment_type = 'credit_card';
-- ✅ Output: 43,981 qualifying orders

-- Q3: Average Delivery Time — Pet Shop Category
SELECT
    ROUND(AVG(DATEDIFF(
        o.order_delivered_customer_date,
        o.order_purchase_timestamp
    )), 2) AS avg_delivery_days
FROM orders o
JOIN order_items          oi ON o.order_id    = oi.order_id
JOIN products             pr ON oi.product_id = pr.product_id
JOIN category_translation ct ON pr.product_category_name = ct.product_category_name
WHERE ct.product_category_name_english = 'pet_shop'
  AND o.order_delivered_customer_date IS NOT NULL;
-- ✅ Output: 11.17 days average delivery time

-- Q4: São Paulo — Average Price & Payment Value
SELECT
    ROUND(AVG(oi.price), 2)        AS avg_price,
    ROUND(AVG(p.payment_value), 2) AS avg_payment_value
FROM orders o
JOIN customers      c  ON o.customer_id  = c.customer_id
JOIN order_items    oi ON o.order_id     = oi.order_id
JOIN order_payments p  ON o.order_id     = p.order_id
WHERE LOWER(c.customer_city) = 'sao paulo';
-- ✅ Output: Avg Price → R$108.03  |  Avg Payment → R$152.77

-- Q5: Review Score vs Average Delivery Days
SELECT
    r.review_score,
    ROUND(AVG(DATEDIFF(
        o.order_delivered_customer_date,
        o.order_purchase_timestamp
    )), 1) AS avg_delivery_days
FROM orders o
JOIN order_reviews r ON o.order_id = r.order_id
WHERE o.order_delivered_customer_date IS NOT NULL
GROUP BY r.review_score
ORDER BY r.review_score;
-- ✅ Output: Score 1 → 21.3 days  |  Score 3 → 14.2 days  |  Score 5 → 10.6 days
```

</details>

---

## 📊 Excel Dashboard

The Excel workbook contains pivot table–based interactive dashboards with slicers for real-time filtering.

| Visual | Type | Description |
|--------|------|-------------|
| KPI Cards | Metric tiles | Total Orders · Total Revenue · Avg Delivery Days · Top City |
| Category Revenue | Bar chart | Top product categories ranked by total revenue |
| City-wise Orders | Bar chart | Order volume across top Brazilian cities |
| Payment Method Split | Donut chart | Credit Card vs Boleto vs Voucher vs Debit Card |
| Weekday vs Weekend | Grouped bar | Revenue and order volume side-by-side comparison |
| Delivery vs Review Score | Bar / line | Average delivery days mapped against each review score |

**Filters:** `Payment Type` · `Customer State` · `Order Year`

---

## 📊 Power BI Dashboard

The Power BI file (`.pbix`) delivers a fully interactive, multi-page analytics report with DAX measures and dynamic slicers.

**📄 Page 1 — Operations Overview**

| Visual | Insight |
|--------|---------|
| Avg Payment & Price — São Paulo | KPI cards for Brazil's highest-revenue city |
| Delivery Time vs Review Score | Bar chart — satisfaction drops sharply as delivery time rises |
| Total Sales by Day Type | Weekday dominates at 77% · Weekend at 23% |

**Header KPIs:**

| Avg Shipping | 5★ + Credit Card Orders | Total Sales | Total Orders |
|:-:|:-:|:-:|:-:|
| 11.31 days | 44,000 | R$16.01M | 96,000 |

> *Values populate from your connected data source after refresh.*

**📄 Page 2 — Growth & Category Breakdown**

| Visual | Insight |
|--------|---------|
| Total Sales by Year (Line) | R$0.1M (2016) → R$7.2M (2017) → R$8.7M (2018) |
| Orders by Category (Bar) | Top categories ranked by order volume |
| Order Status Distribution (Donut) | 97.02% of all orders successfully delivered |

**Filters:** `Order Year` · `Payment Type` · `Customer State` · `Order Status`

---

## 📊 Tableau Dashboard

The Tableau packaged workbook (`.twbx`) includes embedded data — **no additional data connection required**.

| Visual | Insight |
|--------|---------|
| Monthly Sales Trend | Line chart showing revenue trajectory from 2016 → 2018 |
| Delivery Time vs Review Score | Clear inverse relationship between delay and satisfaction |
| Top 10 Categories by Revenue | Bed, Bath & Table leads with 11,115 orders |

**KPIs surfaced:**

| KPI | Value |
|-----|-------|
| 💳 Credit Card Orders | 57,080 |
| 📦 Total Orders | 99,440 |
| 🚚 Pet Shop Avg Delivery | 11.3 days |
| 💰 Total Sales | R$16.01M |

**Filters:** `Payment Type` · `Order Year` · `Product Category` · `Customer State`

---

## 📈 Key KPIs at a Glance

<table align="center">
  <tr>
    <td align="center"><b>📦 Total Orders</b><br/><h3>99,441</h3><i>2016 – 2018</i></td>
    <td align="center"><b>💰 Total Revenue</b><br/><h3>R$15.74M</h3><i>Payment value</i></td>
    <td align="center"><b>🚚 Avg Delivery</b><br/><h3>12.1 days</h3><i>From purchase to door</i></td>
    <td align="center"><b>⭐ Top Combo</b><br/><h3>43,981</h3><i>5★ + Credit Card orders</i></td>
  </tr>
  <tr>
    <td align="center"><b>📅 Weekday Revenue</b><br/><h3>77%</h3><i>R$12.16M of total</i></td>
    <td align="center"><b>🏙️ Top City</b><br/><h3>São Paulo</h3><i>15,540 orders · R$1.91M</i></td>
    <td align="center"><b>✅ Delivery Success</b><br/><h3>97.02%</h3><i>Orders delivered</i></td>
    <td align="center"><b>📊 Dashboards Built</b><br/><h3>3</h3><i>Excel · Power BI · Tableau</i></td>
  </tr>
</table>

---

## 💡 Business Insights & Suggestions

<details>
<summary><b>1️⃣ 🚚 Reduce Delivery Time to Directly Boost Review Scores</b></summary>
<br/>
Score 1 orders average <b>21.3 delivery days</b> versus just <b>10.6 days</b> for Score 5 — a clear, measurable inverse relationship. Partnering with regional logistics providers to push average delivery below 7 days would have a direct, proven impact on customer satisfaction and repeat purchases.
<br/><br/>
</details>

<details>
<summary><b>2️⃣ 📣 Launch Weekend Campaigns to Close the Revenue Gap</b></summary>
<br/>
Weekdays drive <b>77% of total revenue</b> (R$12.16M) while weekends contribute only R$3.58M. Launching weekend-exclusive flash sales, targeted push notifications, and limited-time offers on Friday evening through Sunday could meaningfully grow weekend revenue share.
<br/><br/>
</details>

<details>
<summary><b>3️⃣ 📍 Expand Seller & Warehouse Presence Beyond São Paulo</b></summary>
<br/>
São Paulo accounts for ~15% of all orders. Investing in warehouse infrastructure and seller onboarding in underserved states like Bahia and Paraná would diversify geographic revenue concentration, reduce delivery distances, and improve delivery times nationally.
<br/><br/>
</details>

<details>
<summary><b>4️⃣ 💳 Reward Credit Card Buyers — the Highest-Value Segment</b></summary>
<br/>
43,981 orders carried both a credit card payment AND a 5-star review — the best-performing segment in the dataset. Introducing cashback offers, flexible installment plans, and loyalty points for this cohort reinforces the behaviour that drives both revenue and satisfaction at once.
<br/><br/>
</details>

<details>
<summary><b>5️⃣ 🛏 Double Down on Top-Performing Categories</b></summary>
<br/>
<b>Bed, Bath & Table</b> leads with 11,115 orders. Prioritizing seller recruitment, stock depth, and targeted advertising in the top 3 categories maximises returns on both marketing spend and fulfilment investment with lower acquisition risk.
<br/><br/>
</details>

<details>
<summary><b>6️⃣ ⭐ Proactively Act on Low Review Scores</b></summary>
<br/>
Automated follow-ups for Score 1–2 orders, proactive refund or discount offers, and flagging high-delay sellers for performance review would reduce churn and protect brand reputation — especially critical on a marketplace where trust drives repeat purchase behaviour.
<br/><br/>
</details>

---

## 📚 Key Learnings

| Tool | Skills Developed |
|------|-----------------|
| 🗄️ **MySQL** | Data modeling, FK relationships, complex multi-table JOINs, window functions, data cleaning during import |
| 📊 **Power BI** | DAX measures, interactive slicers, multi-page KPI dashboards for business stakeholders |
| 📊 **Tableau** | Geo-spatial visualizations, calculated fields, and narrative dashboard design |
| 📊 **Excel** | Pivot tables, conditional formatting, and slicer-based interactive dashboards |

---

## 📁 Project Structure

```
📦 Olist-Ecommerce-Analytics/
│
├── 📄 README.md
│
├── 🗄️ olist_analytics.sql                  ←  DB setup + all 5 KPI queries
│
├── 📊 Olist_Analytics.xlsm                 ←  Excel workbook: raw data + interactive dashboard
│
├── 📊 Olist_PowerBI_Dashboard.pbix         ←  Power BI multi-page dashboard
│
└── 📊 Olist_Tableau_Dashboard.twbx         ←  Tableau dashboard (self-contained, embedded data)
```

---

## 🚀 How to Run

### 🗄️ SQL (MySQL)
1. Open **MySQL Workbench** and create a new schema named `olist_db`.
2. Import all CSV files into the corresponding tables.
3. Run `olist_analytics.sql` to set up the database and execute all KPI queries.

```sql
SOURCE olist_analytics.sql;
```

### 📊 Excel
1. Open `Olist_Analytics.xlsm` in **Excel 2016+**.
2. Enable macros if prompted.
3. Navigate to the **Dashboard** sheet.
4. Use the slicers to filter by Payment Type, State, or Order Year.

### 📊 Power BI
1. Open `Olist_PowerBI_Dashboard.pbix` in **Power BI Desktop**.
2. Click **Refresh** if connected to a live source, or explore pre-loaded visuals directly.
3. Use the filter panel to drill into specific years, states, categories, or payment types.

### 📊 Tableau
1. Open `Olist_Tableau_Dashboard.twbx` in **Tableau Desktop** or **Tableau Public**.
2. Data is embedded — no CSV import or external connection needed.
3. Use filter controls to slice by Year, State, Category, or Payment Type.

---

## 📋 Requirements

| Tool | Requirement |
|------|-------------|
| MySQL | 8.0+ (required for window function support) |
| Microsoft Excel | 2016+ with macro support (`.xlsm`) |
| Power BI Desktop | Free — [Download here](https://powerbi.microsoft.com/desktop/) |
| Tableau | Desktop or Public (free) — [Download here](https://public.tableau.com/) |
| MySQL Workbench | Free — [Download here](https://www.mysql.com/products/workbench/) |

---

<h3 align="center">⭐ If this project helped you, please consider giving it a star! ⭐</h3>

<p align="center">
  <a href="https://linkedin.com/in/YOUR_LINKEDIN">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
  &nbsp;
  <a href="https://github.com/YOUR_USERNAME">
    <img src="https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white"/>
  </a>
  &nbsp;
  <a href="mailto:YOUR_EMAIL">
    <img src="https://img.shields.io/badge/Gmail-Contact-D14836?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>
</p>
