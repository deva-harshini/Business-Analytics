# DAX Measures Documentation

This document describes the key DAX measures used in the **Power BI Business Decision Intelligence** project.

Only core analytical and advanced measures are documented here.

---

## 📊 Base Measures

### Total Actual
**Description:** Calculates total actual spend.

```DAX
Total Actual =
SUM ( Finance_Clean[Actual] )
```
### Total Budget

**Description:** Calculates total planned (budgeted) spend.

```DAX
Total Budget =
SUM ( Finance_Clean[Budget] )
```
### Total Variance

**Description:** Difference between actual spend and original budget.
```DAX
Total Variance =
[Total Actual] - [Total Budget]
```
### Variance %

**Description:** Percentage variance against original budget.
```DAX
Variance % =
DIVIDE ( [Total Variance], [Total Budget] )
```
## 🔁 Scenario & What-If Measures
### Adjusted Budget

**Description:** Dynamically adjusts the budget based on user-selected What-If parameter.

Adjusted Budget =
[Total Budget] *
(
    1 +
    SELECTEDVALUE (
        'Budget Adjustment %'[Budget Adjustment %],
        0
    )
)

### Scenario Variance

**Description:** Difference between actual spend and adjusted budget.
```DAX
Scenario Variance =
[Total Actual] - [Adjusted Budget]
```
### Scenario Variance %

**Description:** Percentage variance against adjusted budget.
```DAX
Scenario Variance % =
DIVIDE ( [Scenario Variance], [Adjusted Budget] )
```
## 🎛️ Dynamic Metric Selection
Selected Metric Value

**Description:** Dynamically switches the displayed metric based on user selection.
```DAX
Selected Metric Value =
SWITCH (
    SELECTEDVALUE ( 'Metric Selector'[Metric] ),
    "Actual Spend", [Total Actual],
    "Adjusted Budget", [Adjusted Budget],
    "Scenario Variance", [Scenario Variance],
    "Scenario Variance %", [Scenario Variance %],
    BLANK()
)
```

**Purpose:**

- Reduces visual clutter

- Enables flexible analysis

- Demonstrates advanced DAX usage

## 🏷️ Context Measures
Selected Budget Scenario

**Description:** Displays the active budget scenario for user context.
```DAX
Selected Budget Scenario =
VAR adj =
SELECTEDVALUE ( 'Budget Adjustment %'[Budget Adjustment %], 0 )
RETURN
IF (
    adj = 0,
    "Base Budget Scenario",
    "Budget Adjusted by " & FORMAT ( adj, "0%" )
)
```
##📌 Best Practices Followed

- Measures used instead of calculated columns

- SELECTEDVALUE used with safe defaults

- Disconnected tables used for parameters

- Clear separation of base vs scenario logic

🎯 Conclusion

The DAX layer focuses on clarity, reusability, and analytical correctness, enabling advanced features such as scenario analysis and dynamic metric switching without compromising model stability.


