Below is a **clean, professional, and more detailed rewrite of the README**, written in a **portfolio-ready, recruiter-friendly tone** while keeping everything technically accurate and well-structured.
You can **directly replace your existing README.md** with this.

---

# 🛒 Online Retail Data Analytics Project

**Python · SQL · Power BI**
📄 *End-to-End Data Analytics Pipeline*
📜 License: MIT

---

## 📌 Project Overview

This project demonstrates a **complete data analytics workflow**, starting from raw transactional data and ending with a fully interactive **Power BI dashboard**.

The objective of the project is to **analyze customer behavior, sales performance, and product returns** using a combination of:

* **Python** for ETL and data preprocessing
* **SQL** for structured analysis and feature preparation
* **Power BI** for visualization and business storytelling

Rather than relying solely on Power BI for transformations, this project intentionally integrates **Python and SQL** to reflect a **real-world analytics pipeline** used in industry environments.

---

## 🎯 Business Goals

The project aims to answer key business questions such as:

* Who are the most valuable customers?
* How does customer activity relate to revenue generation?
* What products generate the highest revenue and returns?
* How do sales and returns evolve over time?
* Which countries contribute the most to revenue and risk?

---

## 🧰 Tools & Technologies Used

| Tool                         | Purpose                                           |
| ---------------------------- | ------------------------------------------------- |
| **Python (Pandas)**          | Data loading, cleaning, feature engineering       |
| **SQLite + SQL**             | Querying, aggregation, analytical transformations |
| **Power BI**                 | Interactive dashboards & KPI reporting            |
| **Jupyter / Python Scripts** | End-to-end data pipeline execution                |

---

## 📊 Dataset Description
<img width="1430" height="681" alt="image" src="https://github.com/user-attachments/assets/2761c36c-0b2b-4991-bcd7-c7973bfd63c9" />

* **Source:** UCI Machine Learning Repository – *Online Retail Dataset*
* **Format:** Excel file
* **Sheets:**

  * `Year 2009–2010`
  * `Year 2010–2011`
* **Records:** ~540,000 transactions
* **Features Include:**
  Invoice, Stock Code, Product Description, Quantity, Price, Customer ID, Country, Invoice Date

⚠️ *Raw files are not included in this repository due to GitHub size limitations.*

---

## 🔄 Project Workflow

### 1️⃣ Data Extraction & Combination (Python)

* Loaded both Excel sheets using Pandas
* Combined them into a single unified dataset
* Ensured consistent schema across years

```python
df_comb = pd.concat([df1, df2], ignore_index=True)
```

---

### 2️⃣ Data Cleaning & Feature Engineering (Python)

Key preprocessing steps included:

* Removing missing values and duplicate rows
* Converting invoice dates to datetime format
* Creating time-based features:

  * Year
  * Month
  * Week
  * Quarter
  * Day of Week
* Converting Customer ID to integer type
* Renaming columns for SQL compatibility

```python
df_clean.columns = df_clean.columns.str.lower().str.replace(" ", "_")
```

---

### 3️⃣ Data Storage (SQLite)

* The cleaned dataset was stored in a local **SQLite database**
* This allowed structured querying using SQL while staying inside Python

```python
df_clean.to_sql("retail_data", conn, index=False, if_exists="replace")
```

---

### 4️⃣ SQL Analysis & Data Preparation

All analytics were performed using **SQL queries executed within Python**.

#### 📁 Generated Analytical Tables

| Table                  | Purpose                                     |
| ---------------------- | ------------------------------------------- |
| `sales_summary`        | Sales transactions and revenue calculations |
| `products_by_quantity` | Product demand analysis                     |
| `customer_activity`    | Customer lifetime value & engagement        |
| `returns_summary`      | Returns behavior and return values          |

Each dataset was exported as a CSV file for Power BI ingestion.

---

## 📈 Power BI Dashboard
<img width="1637" height="495" alt="image" src="https://github.com/user-attachments/assets/7e7c3121-93f8-4a22-aff8-b80ec3752db8" />

### 🎨 Dashboard Design Philosophy

Two dashboard versions were created:

#### 🌞 Light Theme

* Best for executive presentations
* Clean, minimal, and print-friendly

#### 🌙 Dark Theme

* Optimized for modern analytics workflows
* High contrast and reduced eye strain
* Ideal for prolonged analysis sessions

Both dashboards deliver **identical insights**, allowing users to choose their preferred viewing experience.

---

## 📊 Key KPIs (DAX Measures)

* **Total Revenue**
* **Total Quantity Sold**
* **Total Invoices**
* **Revenue per Customer**
* **Average Order Value (AOV)**
* **Total Returns Value**
* **Total Returns Count**
* **Returns Percentage**

Example:

```DAX
Total Revenue = SUM(sales_summary[total_revenue])
Returns Percentage = DIVIDE([Total Returns Value], [Total Revenue])
```

---

## 👥 Customer Segmentation Logic

Customers were classified using a calculated column based on **active months**:

| Active Months | Customer Type |
| ------------- | ------------- |
| ≤ 2           | Inactive      |
| 3–5           | Normal        |
| > 5           | Active        |

```DAX
Customer Type =
IF(
    [active_months] <= 2, "Inactive",
    IF([active_months] <= 5, "Normal", "Active")
)
```

This segmentation is used throughout the dashboard as a slicer.

---

## 📊 Dashboard Visuals Explained

### 🔹 Sales Performance

* Total Revenue over time
* Average Order Value trends
* Revenue vs Returns by product

### 🔹 Customer Insights

* Customer activity table (Country, Type, Active Months)
* Revenue contribution by customer segment

### 🔹 Returns Analysis

* Returns value over time
* Returns by country (Treemap)
* Revenue vs Returns comparison

### 🔹 Loyalty Analysis

* Number of customers vs revenue by active months
* Demonstrates how long-term customers drive value

### 🔹 Interactive Filters

* Customer Type
* Year
* Country

---

## 📌 Key Business Insights

### 🟢 Customer Value Concentration

* **27% of customers generated ~80% of total revenue**
* Active customers are the primary revenue drivers
* Strong evidence of the **Pareto Principle (80/20 rule)**

### 🔴 Returns & Risk

* Inactive customers showed higher return rates
* Overall return rate remained under 20%, indicating healthy sales
* UK dominated both revenue and returns due to customer volume

### 📦 Product & Pricing Trends

* *Regency Cakestand 3 Tier* was the top-selling product
* Product prices were stable over time
* AOV showed seasonal peaks, driven by multi-item purchases

---

## 🧠 Key Learnings

* Combining **Python + SQL + Power BI** creates a scalable analytics workflow
* Data cleaning is critical for reliable insights
* Dashboards transform raw data into actionable business intelligence
* Offering multiple visual themes improves usability and adoption

---

## 📜 License

This project is licensed under the **MIT License**.
See the `LICENSE` file for more details.

---
