# 📊 Finance Loan Distribution Analysis  
*Mini Project – MS Excel & Power BI*

---

## 📂 Data Source
- Dataset collected from **Kaggle** in CSV format.  
- Converted to **Excel** for cleaning and transformation.  
- No duplicates found in `Customer ID` column.  

---

## 🧹 Data Cleaning & Imputation
### Categorical Imputation
- Missing values in **Employment Status** filled using:  
  `=IF(ISBLANK(), "Unknown", ())`

### Numerical Imputation
- Missing values in **Annual Income**, **Credit Score**, **Loan Amount**, **Interest Rate**, **Loan Tenure**, and **DTI Ratio** imputed using averages grouped by **Education** and **Loan Purpose**:  
  `=IF(ISBLANK(), AVERAGEIF(), ())`

### Additional Columns
- **Credit Status**:  
  - `>= 750 → Excellent`  
  - `>= 600 → Good`  
  - `>= 450 → Average`  
  - `< 450 → Bad`

- **Approval Status** (based on DTI Ratio):  
  - `>= 60 → Rejected`  
  - `>= 25 → Need More Proof`  
  - `<= 25 → Approved`

- **Risk Factor**:  
  - `Loan Default = 0 → No Risk`  
  - `Loan Default > 0 → Risk`

- **Customer City** and **Customer State** added for Power BI mapping.

---

## 🔢 Index Matching (Optional)
- Implemented `INDEX(MODE(MATCH()))` formula to analyze gender distribution.  
- Insight: **Female customers dominate loan uptake**, highlighting empowerment trends.

---

## ⚙️ Power BI Transformation
### Power Query Editor
- Converted **Loan Amount** & **Annual Income** to Fixed Decimal.  
- Converted **Date** column to Date format.  

### DAX & Measures
- **Number of Customers**:  
  ```DAX
  Number Of Customers = COUNTA(finance_loan_default_dataset[Customer ID])
  Total Loan Amount = SUM(finance_loan_default_dataset[Loan Amount])
  Each Loan Disbursed YTD =
CALCULATE(
  SUM(finance_loan_default_dataset[Loan Amount]),
  DATESYTD(CalendarTable[Date])
)


