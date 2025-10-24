---
layout: post
title: "Business Intelligence with Power BI: Hotel Performance Analysis"
author: "Mirriam Jepleting"
tags: [Power BI, Data Analytics, Business Intelligence, Dashboard, Data Modeling, DAX]
---

# Business Intelligence with Power BI: Hotel Performance Analysis  
**Author:** Mirriam Jepleting  

---

## Introduction  
This project demonstrates the application of **Business Intelligence (BI)** techniques using **Power BI** to analyze and visualize hotel performance data.  
The goal was to transform raw, multi-source datasets into actionable insights that could support strategic decision-making in the hospitality sector.

The analysis highlights the use of **data modeling, transformation, and DAX-driven analytics** to uncover key trends in occupancy, revenue, and customer behavior.  
By integrating interactive dashboards and dynamic reporting features, the project showcases how Power BI enables organizations to make data-driven decisions with clarity and precision.

**Dataset Source:** [Codebasics End-to-End Data Analyst Project](https://codebasics.io/resources/end-to-end-data-analyst-project)

---

## Objectives  
- Develop a robust and optimized data model suitable for business intelligence reporting.  
- Utilize Power Query to clean, transform, and prepare multiple datasets for analysis.  
- Create DAX measures for revenue, occupancy, and performance tracking.  
- Design an interactive dashboard with user-friendly filters and KPIs.  
- Present insights that reveal key business trends and performance indicators.

---

## Data Preparation and Transformation  
The dataset contained multiple CSV files representing different entities such as hotels, bookings, customers, and dates.  
Using **Power Query Editor**, the data was cleaned, formatted, and integrated into a unified structure.  

### Key Data Wrangling Steps  
- Imported all datasets using the **folder path method**, enabling automatic refresh and synchronization.  
- Standardized column names and data types for consistency.  
- Removed redundant fields such as `date_type` from the `dim_dates` table.  
- Handled missing and duplicate values to maintain data quality.  
- Created calculated columns to enrich contextual information.  

The result was a clean, well-structured dataset ready for advanced modeling and visualization.

---

## Data Modeling  
A **Star Schema** model was implemented to organize the data efficiently.  
- The **Fact Table** captured transactional details such as revenue, room nights, and bookings.  
- The **Dimension Tables** provided descriptive attributes for hotels, customers, agents, and dates.  

All necessary relationships were defined and validated to ensure seamless filtering and cross-table analysis.  
This modeling approach improved report responsiveness, reduced redundancy, and supported accurate data aggregation.

---

## DAX Implementation  
To enhance analytical capability, several **DAX (Data Analysis Expressions)** measures and calculated columns were created.

### Key DAX Components  
- **Revenue Analysis:**  
  ```DAX
  Total Revenue = SUM(FactBookings[Revenue])
