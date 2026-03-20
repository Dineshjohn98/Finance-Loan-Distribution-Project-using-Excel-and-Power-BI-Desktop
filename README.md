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

### 📈 Visualizations
- Clustered Column Chart → Customers by Gender & Education
- Pie Chart → Customers by Credit Status
- Line Chart → Customers by Month
- Map Visual → City-wise Loan Distribution
- Funnel Chart → State-wise Accounts Enrolled
- Tree Map → Annual Income vs Loan Purpose
- Interactive Dashboard → Slicer-enabled dynamic exploration

### 🔍 Insights
- Female customers are the majority loan applicants.
- Personal Loans dominate, contributing significantly to revenue due to higher interest rates.
- Approval Rate: Most loans approved; <2% rejected due to high DTI Ratio.
- Risk Factor:
- ~75% customers show No Risk (timely repayment).
- ~25% customers flagged as Risk (defaults present).

### 📌 Recommendations
- Recruit authorized personnel for collections.
- Use tele-calling follow-ups as primary strategy.
- Escalate to field visits only if customers remain unresponsive.
- Ensure compliance with RBI guidelines during recovery processes.

### 🛠️ Tools Used
- MS Excel → Data Cleaning & Imputation
- Power BI → Data Transformation, DAX, Visualizations, Dashboard

### ✅ Conclusion
This project demonstrates how Excel + Power BI can be leveraged for:
- Cleaning and imputing financial datasets
- Creating calculated columns and measures
- Building interactive dashboards
- Extracting actionable insights for loan distribution and risk management


