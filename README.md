

## 📊 Dashboards Overview

### 1️⃣ Executive Overview
**Purpose:** High-level performance monitoring  
**Key Features:**
- KPI summary
- Trend indicators
- Business health snapshot

---

### 2️⃣ Operations Dashboard
**Purpose:** Operational efficiency and workforce analysis  
**Key Features:**
- Attrition and overtime insights
- Department and role-level analysis
- Risk identification using heatmaps and KPIs

---

### 3️⃣ Cost & Performance Dashboard
**Purpose:** Financial control and cost optimization  
**Key Features:**
- Budget vs Actual comparison
- Variance analysis by category
- Scenario-based insights using What-If analysis

---

## 🧠 Advanced Analytics Implemented

### 🔁 What-If Analysis
- Budget adjustment scenarios using disconnected parameter tables
- Dynamic recalculation of budget and variance metrics

### 🎛️ Dynamic Metric Selector
- Single visual controlled by a metric selector slicer
- Implemented using `SWITCH()` in DAX
- Reduces dashboard clutter while increasing flexibility

### 🧱 Data Modeling
- Star-schema-based modeling
- Separate Date and Month dimensions to handle mixed data granularity
- Single-direction relationships for model stability

---

## 🧮 DAX Highlights
- Scenario-aware budget and variance measures
- Dynamic metric switching using `SWITCH()`
- Safe context handling using `SELECTEDVALUE()`
- Measures preferred over calculated columns

Detailed DAX logic is documented in `docs/dax_measures.md`.

---

## 📁 Data Preparation
- Raw datasets preserved for integrity
- Data cleaned and transformed using **Power BI Power Query**
- Cleaned datasets exported for transparency and reproducibility
- Column definitions and cleaning notes available in `docs/data_dictionary.md`

---

## 🚀 How to Use This Project
1. Download or clone the repository
2. Open `Business_Decision_Intelligence.pbix` in **Power BI Desktop**
3. Interact with slicers and scenario controls
4. Explore dashboards for insights

---

## 🎯 Key Takeaways
- Demonstrates real-world BI modeling and analytics
- Focuses on decision support, not just reporting
- Uses advanced Power BI features suitable for internships and entry-level BI roles

---

## 👤 Author
**Mandali Deva Harshini**


