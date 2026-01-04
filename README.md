# Amazon Sales Report — Data Cleaning & Exploratory Data Analysis (SQL)

A complete, end-to-end **SQL analytics project** that transforms raw Amazon sales data into a clean, analysis-ready table and produces **business-ready insights** through structured exploratory data analysis (EDA).
## Dataset Used
- <a href="https://github.com/AMK67/Data-Analysis-of-Amazon-Sales-Report-using-SQL/blob/main/Amazon%20Sale%20Report.csv">Amazon Sales Data </a>


This repository demonstrates practical skills in:
- **Data quality validation**
- **Deduplication using window functions**
- **Standardization (city/state normalization, casing, special character removal)**
- **Schema improvements (date type conversion, dropping sparse columns)**
- **Sales analytics and KPI reporting**

---

## Why this project matters

Raw e-commerce datasets are messy: duplicates, inconsistent location names, mixed formats, and unnecessary columns can distort insights.  
This project solves those problems using SQL-only workflows and delivers clean insights that can directly support:
- Growth strategy (top states/cities)
- Product strategy (category performance)
- Operations (delivery vs cancellation/return rates)
- Fulfillment optimization (Amazon vs Merchant, shipping service levels)

---

## Project Workflow

### 1) Data Understanding
- Count total records
- Review table structure and data types

### 2) Data Cleaning (SQL)
✅ **Duplicate detection** using `ROW_NUMBER()` across key columns  
✅ **Duplicate removal** by filtering `row_num > 1`  
✅ **City standardization**
- Removes special characters using `REGEXP_REPLACE`
- Trims + converts to uppercase
- Maps inconsistent city values (e.g., *BANGALORE → BENGALURU*)

✅ **State standardization**
- Maps abbreviated / inconsistent values (e.g., *PB → PUNJAB*)
- Converts to uppercase

✅ **Order Status normalization**
- Example: `Shipped` → `Shipped - Delivered to Buyer`

✅ **Date conversion**
- Converts string dates using `STR_TO_DATE`
- Alters column to `DATE`

✅ **Schema cleanup**
- Drops columns with >50% nulls:
  - `fulfilled-by`, `New`, `PendingS`, `row_num`

### 3) Exploratory Data Analysis (EDA)
SQL queries answer key business questions:
- Total orders and total sales
- Top states and cities by sales
- Best-performing product categories
- Order status distribution (delivered/cancelled/returned)
- Shipping service level preference
- Amazon vs Merchant fulfillment split
- B2B vs B2C contribution
- Monthly sales trend

---

## Key Insights (from EDA)

Here are the headline insights generated from the queries:

- **Dataset timeline:** March 31, 2022 → May 31, 2022  
- **Total Orders:** **60,945**
- **Total Sales:** **~41.8 million** (currency as per dataset)
- **Top State by Sales:** **Maharashtra**
- **Lowest State by Sales:** **Pondicherry**
- **Top cities dominating sales:** Bengaluru, Hyderabad, Mumbai, New Delhi, Chennai, Pune, Kolkata
- **Top Category:** **T-shirts** (highest sales + quantity)
- **Least Popular Category (in top 10 view):** **Shoes** (needs strategy review)
- **Order outcomes:**
  - **~89.06% delivered**
  - **~8.9% cancelled**
  - **~1% returned**
- **Shipping preference:** Expedited is significantly more used than Standard
- **Fulfillment mix:**
  - **Amazon fulfillment:** ~67.7%
  - **Merchant fulfillment:** ~32.3%
- **B2B vs B2C:** B2C dominates; **B2B is <1%**
- **Monthly trend:** **April shows the highest sales** in the period

---

## Tech Stack

- **SQL (MySQL compatible)**
- Window functions (`ROW_NUMBER`)
- Regex cleaning (`REGEXP_REPLACE`)
- String + date transformation (`UPPER`, `TRIM`, `STR_TO_DATE`)
- Aggregations + KPI analytics (`SUM`, `COUNT DISTINCT`, `AVG`)

---

## Repository Structure

```bash
.
├── Data_Cleaning_Queries.sql          # Cleaning pipeline: dedupe, standardize, transform schema
├── Exploratory data analysis.sql      # EDA + KPI queries + business insights
└── README.md
