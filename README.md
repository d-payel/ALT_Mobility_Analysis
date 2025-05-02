# 📊 Alt Mobility Data Analyst Assignment

This repository contains SQL analysis and a Tableau visualization developed as part of the **Data Analyst Internship assignment** for **Alt Mobility**. The project focuses on analyzing customer orders, payment behavior, customer segmentation, and retention trends using **Google BigQuery** and **Tableau**.

---

## 🗂️ Datasets Used

- `customer_orders.customer_orders`: Order-level data
- `customer_orders.payments`: Payment-level data

---

## ✅ Tasks Completed

### 1. 🧹 Data Quality Check

Performed null-value checks on both datasets to assess completeness:
- Checked for missing `order_id`, `payment_id`, `order_amount`, `payment_status`, etc in both the tables.
- Result: Neither Customer Order nor Payment table had null values in any of the columns.
  ![check for null values in the customer order table](check_null.png)

### 2. 📦 Order and Sales Analysis

- Computed total orders and revenue grouped by `order_status`
- Created a **monthly revenue trend** view and used **`DENSE_RANK()`** to identify top 3 revenue-generating months per year
- View created: `orders_with_date_parts` with pre-extracted `year` and `month`

### 3. 🧮 Customer Segmentation (RFM Analysis)

- Built quantile-based RFM segments using:
  - `Recency`: days since last order
  - `Frequency`: orders per active month
  - `Monetary`: total order value
- Created scores from 1 to 5 for each metric and assigned customers to **RFM segments** like:
  - Champions, Loyal Customers, Potential Loyalists, At Risk, Hibernating, Lost, etc.
- Final table: `quantile` with segment labels

### 4. 💳 Payment Status Analysis

- Analyzed total transactions and revenue grouped by `payment_status`
- Created a **monthly payment trend report** using a view `payments_with_date_parts`
- Used `DENSE_RANK()` on success rates to identify **top 3 months per year** with highest payment success
- Highlighted months with highest payment failures and analyzed status trends

### 5. ❌ Missing Payments Report

- Created a full joined table of orders and payments using `LEFT JOIN`
- Aggregated missing `payment_id`s across different `order_status`
- Calculated the percentage of missing payments by status  
  **Example:** `"Pending" orders had ~27% missing payments`
  ![Distribution of Missing Payments](percentage_of_missing_payments.png)
- Calculated Payment Success Rate of each Customer 
  ![Distribution of Payment Success Rate at Individual Customer Level](payment_success-rate_by-customer.png)

### 6. 📊 Order-Payment Summary Per Customer

- Summarized each customer’s transaction footprint:
  - Total orders, total payment amount, success/failure/pending counts
  - Computed **payment success rate** and **failure rate** per customer

### 7. 📈 Customer Retention Analysis (Cohort)

- Created cohort months using the first order month of each customer
- Calculated **cohort index** (elapsed time since first order in months)
- Measured monthly retention as:  
  `retention_rate = active_customers / cohort_size * 100`
- Exported retention matrix for **Tableau heatmap**

---

## 📊 Tableau Visualization

### **Customer Cohort Retention Heatmap**

![Customer Retention Heatmap](retention_rate_visualization_task5.png)

- X-axis: `Elapsed Time` (in months since first order)
- Y-axis: `Cohort Quarter` (customer's first purchase quarter)
- Cell color: `Retention Rate (%)`  
  **Insight:** Retention drops steeply after Month 1; long-term retention stabilizes around 6–9%

---

## 📁 Folder Structure

```bash
.
├── sql_queries/
│   ├── data_quality_check.sql
│   ├── order_sales_analysis.sql
│   ├── customer_segmentation_rfm.sql
│   ├── payment_status_analysis.sql
│   ├── order_payment_summary.sql
│   ├── missing_payment_report.sql
│   └── retention_cohort_analysis.sql
├── visualizations/
│   └── retention_rate_visualization_task5.png
├── output/
│   └── rfm_segments_table.csv
├── summary_of_findings.pdf
└── README.md
