# Manufacturing Operations & ERP BOM Analytics  
### Engineering Data Integrity & Operational KPI Intelligence (Mock Dataset)

---

## Overview

This project demonstrates manufacturing operations analytics using a simulated ERP Bill of Materials (BOM) validation and revision control dataset.

The goal is to model structured engineering data discrepancies, analyze operational impact, and surface decision-ready KPIs that improve production data integrity and release quality.

All data is fully simulated to protect employer confidentiality while reflecting realistic manufacturing workflows.

---

## Business Context

In high-volume manufacturing environments, ERP BOM errors and revision inconsistencies can lead to:

- Rework on the shop floor  
- Delays in production release  
- Incorrect configurations  
- Increased operational cost  
- Engineering change bottlenecks  

This project simulates how a Manufacturing or Engineering Operations Analyst would monitor, analyze, and improve BOM data quality.

---

## Project Objectives

- Identify trends in BOM errors over time  
- Quantify rework rate and resolution efficiency  
- Analyze cost impact of configuration discrepancies  
- Track revision change activity  
- Provide executive-level operational visibility  

---

## Dataset Structure

The model is built on two primary simulated datasets:

### 1️⃣ BOM_Error_Data
Tracks structured ERP configuration issues.

Key Fields:
- Date  
- Unit_ID  
- Error_Type  
- Stage_Detected  
- Department_Origin  
- Time_to_Resolve_Hours  
- Rework_Required  
- Estimated_Impact_Cost_USD  

### 2️⃣ Revision_Change_Log
Tracks revision updates across part configurations.

Key Fields:
- Date  
- Unit_ID  
- Part_Number  
- Old_Revision  
- New_Revision  
- Change_Reason  
- Rework_Required  

---

## Analytical KPIs

The dashboard includes:

- Total BOM Errors  
- Rework Rate (%)  
- Average Time to Resolve  
- Estimated Cost Impact  
- Monthly Error Trend  
- Error Distribution by Stage  
- Error Distribution by Department  
- Revision Change Frequency  

---

## Key Analytical Questions Answered

- Which error types contribute the highest cost impact?  
- Which stages detect the most configuration issues?  
- What is the monthly trend in BOM discrepancies?  
- How often do revision changes trigger rework?  
- Which departments contribute most to configuration risk?  

---

## Tools Used

- Microsoft Excel  
  - PivotTables  
  - Power Query  
  - Structured Calculations  
  - KPI Dashboards  

---

## Data Governance Features

- Simulated structured ERP schema  
- Controlled error categorization  
- Cost impact modeling  
- Resolution time tracking  
- Rework indicator logic  

---

## Why This Project Matters

Manufacturing organizations depend on accurate ERP configuration data to maintain production stability.

This project demonstrates:

- Structured operational analytics  
- Manufacturing domain awareness  
- KPI modeling for engineering workflows  
- Data-driven process improvement  

---

## Future Enhancements

- PostgreSQL data mart version  
- Power BI executive dashboard  
- Python automation for weekly KPI reporting  
- Anomaly detection on error spikes  

---

## Author

Yengkong Sayaovong  
Manufacturing & Engineering Operations Analytics Focus  
LinkedIn: https://www.linkedin.com/in/ysayaovong
