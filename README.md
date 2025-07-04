# # 🧠 Palmoria Group HR Analytics - Power BI Case Study

This repository documents an end-to-end HR data analysis and dashboard project for the Palmoria Group, a Nigerian-based manufacturing company, aimed at uncovering and addressing gender-related issues in the organization using **Power BI**.

## 📌 Project Objective

Palmoria Group faced public scrutiny over gender inequality. The CEO commissioned a data-driven HR analysis to:
- Identify gender distribution issues
- Analyze salary disparities
- Check compliance with labor regulations
- Allocate annual performance bonuses

## 📂 Datasets Used

1. `Palmoria Group emp-data.csv`  
   Employee-level dataset containing information on:
   - Gender
   - Department
   - Region
   - Performance Rating
   - Salary

2. `Palmoria Group Bonus Rules.xlsx`  
   A matrix of bonus rates by department and performance rating.

---

## 🔧 Project Steps

### 1. Data Cleaning (Power Query)
- Removed:
  - Ex-employees with null salaries
  - Records with null departments
- Assigned "Undisclosed" to missing gender values
- Trimmed and formatted department/rating text fields
- Created a `BonusKey` column by merging `Department` and `Rating`

### 2. Bonus Rules Transformation
- Unpivoted department columns to rows
- Normalized into:
- Created a `BonusKey` column to match employee data

### 3. Data Modeling (Power BI Model View)
- Established a **one-to-many** relationship between:
### 4. DAX Measures
```DAX
Bonus Amount = RELATED('Bonus Rules'[Bonus Rate]) * 'Employee'[Salary]

Total Compensation = 'Employee'[Salary] + 'Employee'[Bonus Amount]
