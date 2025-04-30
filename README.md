# Alt Mobility Data Analyst Assignment

This repository contains SQL scripts and logic developed as part of the Data Analyst Internship assignment for **Alt Mobility**, focused on analyzing customer orders and payment behavior using Google BigQuery.

---

## 🗂️ Datasets Used
- `customer_orders.customer_orders`: Order-level data
- `customer_orders.payments`: Payment-level data

---

## ✅ Tasks Completed

### 1. 🔍 Data Validation
Checked for missing values in both datasets to ensure data quality:
- Identified nulls in critical fields like `order_id`, `payment_status`, etc.

### 2. 📦 Order and Sales Analysis
Analyzed order distribution and revenue trends:
- Total orders and revenue grouped by `order_status`
- Monthly sales trend visualized using `order_date`

### 3. 🧮 Customer Segmentation (RFM Analysis)
Built an RFM-based segmentation model:
- Created quantile-based percentiles for Recency, Frequency, and Monetary value
- Assigned RFM scores and labeled customers into 11 segments:
  - **Champions, Loyal Customers, Potential Loyalists, Hibernating, Lost**, etc.

### 4. 💳 Payment Status Analysis
Assessed overall and monthly payment performance:
- Count and sum of payments by `payment_status`
- Payment success dynamics over time
- Ranked months by highest payment failures per year

### 5. 🧾 Order Details Report
Created a full view by joining orders and payments:
- Used `LEFT JOIN` to ensure all orders are retained
- Aggregated report shows total orders, payment success rate, and failure rate per customer

### 6. 👥 Customer Ordering Behavior
Analyzed:
- Repeat vs one-time buyers
- Monthly customer activity and order volume trends

### 7. 📈 Customer Retention Analysis (Cohort)
Built cohort-based retention table:
- Assigned each customer a `cohort_month` (month of first purchase)
- Tracked repeat activity month by month using `cohort_index`
- Exported results for visualization in **Tableau**

---

## 📁 Folder Structure

```bash
.
├── sql_queries/
│   ├── missing_value_check.sql
│   ├── order_sales_analysis.sql
│   ├── customer_segmentation_rfm.sql
│   ├── payment_status_analysis.sql
│   ├── order_payment_report.sql
│   ├── customer_behavior_analysis.sql
│   └── retention_cohort_analysis.sql
├── visualizations/
│   └── customer_retention_chart.png
├── output/
│   └── rfm_segments_table.csv
├── summary_of_findings.pdf
└── README.md
