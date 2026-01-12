# Data Dictionary

This document describes the datasets used in the **Power BI Business Decision Intelligence** project, including raw and cleaned tables, their purpose, and column definitions.

---

## 📁 Raw Datasets

### 1. `sales_raw.csv`
**Description:** Original sales transaction data before cleaning.

| Column Name | Description |
|------------|-------------|
| Order_ID | Unique identifier for each sales order |
| Order_Date | Date when the order was placed |
| Customer_ID | Unique identifier for the customer |
| Product | Product name |
| Category | Product category |
| Quantity | Number of units sold |
| Sales | Total sales amount for the order |

---

### 2. `finance_raw.csv`
**Description:** Original finance data containing budgeted and actual costs.

| Column Name | Description |
|------------|-------------|
| Month | Month of the financial record |
| Category | Expense category |
| Budget | Planned (budgeted) cost |
| Actual | Actual cost incurred |

---

### 3. `operations_raw.csv`
**Description:** Original operational and HR-related data.

| Column Name | Description |
|------------|-------------|
| Employee_ID | Unique identifier for employee |
| Department | Department name |
| Job_Role | Employee job role |
| Attrition | Whether the employee left the company |
| Overtime | Whether the employee works overtime |
| Performance_Rating | Employee performance score |

---

## 📁 Cleaned Datasets

### 4. `sales_clean.csv`
**Description:** Cleaned and standardized sales data used for analysis.

| Column Name | Description |
|------------|-------------|
| Order_ID | Unique order identifier |
| Order_Date | Cleaned order date (Date type) |
| Customer_ID | Customer identifier |
| Product | Product name |
| Category | Product category |
| Quantity | Units sold |
| Sales_Amount | Total sales value |

**Cleaning Notes:**
- Converted dates to proper Date type  
- Removed null and duplicate records  
- Standardized category names  

---

### 5. `finance_clean.csv`
**Description:** Cleaned finance dataset used for cost and performance analysis.

| Column Name | Description |
|------------|-------------|
| Month | Financial month (date representing the month) |
| Category | Cost category |
| Budget | Planned spend |
| Actual | Actual spend incurred |

**Cleaning Notes:**
- Standardized month format  
- Ensured numeric consistency for budget and actual values  
- Removed incomplete records  

---

### 6. `operations_clean.csv`
**Description:** Cleaned operations and HR dataset used for efficiency and attrition analysis.

| Column Name | Description |
|------------|-------------|
| Employee_ID | Employee identifier |
| Department | Department name |
| Job_Role | Job role |
| Attrition_Flag | Binary indicator of attrition |
| Overtime_Flag | Binary indicator of overtime |
| Performance_Rating | Cleaned performance score |

**Cleaning Notes:**
- Converted categorical values to flags  
- Standardized department and role names  
- Removed invalid performance ratings  

---

## 📊 Dimension Tables

### 7. `Date_Dim`
**Description:** Daily date dimension used for time-based analysis.

| Column Name | Description |
|------------|-------------|
| Date | Calendar date (primary key) |
| Year | Calendar year |
| Month | Month number |
| Month_Name | Month name |
| Month_Year | First date of the month (used for grouping) |

---

### 8. `Month_Dim`
**Description:** Monthly dimension used to align with monthly aggregated finance data.

| Column Name | Description |
|------------|-------------|
| Month_Year | Unique month identifier |

---

## 📌 Notes
- Raw datasets are preserved for data integrity.
- Cleaned datasets are generated using **Power BI Power Query**.
- Dimension tables support proper data modeling and analytics.
- Monthly and daily grains are handled using separate dimensions to ensure accuracy.

---
