# Data Modeling Notes

This document explains the data modeling decisions used in the **Power BI Business Decision Intelligence** project.

The model is designed to support accurate analysis, scenario simulation, and executive-level reporting.

---

## 🧱 Modeling Approach

A **star schema–based approach** was used wherever possible, with clear separation between:

- Fact tables (events / measurements)
- Dimension tables (descriptive context)

This ensures:
- Better performance
- Simpler DAX
- Correct filtering behavior

---

## 📊 Fact Tables

### 1. Sales_Clean
**Grain:** One row per sales transaction  
**Purpose:** Revenue and sales performance analysis  

Connected to:
- `Date_Dim` via `Order_Date`

---

### 2. Finance_Clean
**Grain:** Monthly aggregated financial data  
**Purpose:** Budget vs actual and cost performance analysis  

Key characteristics:
- Data is aggregated at **month level**
- Does not support daily analysis

Because of this, it is **not directly joined** to `Date_Dim` at the daily level.

---

### 3. Operations_Clean
**Grain:** One row per employee record  
**Purpose:** Attrition, overtime, and performance analysis  

This table is analyzed mostly through categorical and KPI-based metrics.

---

## 🗓️ Dimension Tables

### Date_Dim
**Grain:** Daily  
**Primary Key:** `Date`

Used for:
- Sales time analysis
- Time intelligence (MoM, trends)

Important:
- Attributes like Month, Month_Year, and Year are **not unique**
- This is intentional and correct for a date dimension

---

### Month_Dim
**Grain:** Monthly  
**Primary Key:** `Month_Year`

Why it exists:
- Finance data is aggregated monthly
- Month_Year in Date_Dim is not unique
- Creating Month_Dim avoids invalid relationships

Used for:
- Monthly finance visuals
- Budget vs actual analysis

---

## 🔗 Relationships Summary

| From Table | Column | To Table | Column |
|----------|--------|---------|--------|
| Sales_Clean | Order_Date | Date_Dim | Date |
| Finance_Clean | Month | Month_Dim | Month_Year |

Relationship rules:
- Single-direction filtering
- No bidirectional relationships
- No relationships involving parameter tables

---

## 🧮 Disconnected Tables

### Budget Adjustment %
A disconnected table created using Power BI What-If parameters.

Purpose:
- Enables scenario-based budget simulation
- Does not alter underlying data
- Drives DAX logic only

This approach is commonly used in enterprise BI models.

---

## 🎯 Key Design Decisions

- Separate Date and Month dimensions to handle mixed granularity
- Avoid forced or invalid relationships
- Prefer measures over calculated columns
- Preserve raw data integrity

---

## 📌 Conclusion

The final model balances correctness, performance, and analytical flexibility, enabling advanced features such as scenario analysis and dynamic metric selection without compromising data integrity.
