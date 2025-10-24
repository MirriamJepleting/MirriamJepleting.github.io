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

## Dashboard Design and Visualization  
The final deliverable was an **interactive Power BI dashboard** designed to communicate insights intuitively and effectively.  

### Key Features  
- **KPI Cards:** Displayed metrics such as total revenue, occupancy rate, and total bookings.  
- **Bar and Column Charts:** Compared performance across hotel types, cities, and time periods.  
- **Pie Charts:** Illustrated the distribution of bookings by region or market segment.  
- **Line Charts:** Highlighted revenue and occupancy trends over time.  
- **Slicers and Filters:** Enabled dynamic exploration by date, city, hotel type, and customer category.

### Dashboard Impact  
The dashboard transformed complex datasets into visual narratives that supported executive decision-making.  
Managers could quickly identify high-performing branches, analyze revenue trends, and detect low-occupancy periods for strategic planning.

---

## Insights and Findings  
- **Revenue Drivers:** Luxury hotels consistently outperformed budget categories, though the latter maintained steady occupancy levels.  
- **Seasonality:** Peak booking months correlated with tourist seasons and holiday periods.  
- **Customer Segmentation:** Direct bookings yielded higher revenue margins compared to agent-based reservations.  
- **Geographic Trends:** Hotels located in metropolitan areas exhibited higher occupancy but tighter competition on pricing.

These insights demonstrated how BI tools can uncover business patterns and support data-driven strategy development.

---

## Challenges and Solutions  
One of the key challenges was ensuring proper relationships among multiple datasets. Some tables lacked consistent keys, causing early model inconsistencies.  
Through iterative testing and schema refinement, relationship errors were resolved.  

Another challenge involved optimizing **DAX formulas** to avoid circular dependencies and improve performance. By restructuring certain calculations into measures instead of calculated columns, query performance improved significantly.

---

## Skills Demonstrated  
- **Data Cleaning and Transformation** using Power Query  
- **Data Modeling** with the Star Schema  
- **DAX Formula Writing** for dynamic and comparative analytics  
- **Dashboard Design and Visualization** aligned with business goals  
- **Storytelling with Data** to communicate insights effectively  

---

## Project Access  
🔗 [View Project Files and Dashboard on Google Drive](https://drive.google.com/drive/folders/1WYdPr5EocDcnIDWXpmjgZziaHc-TpQEk?usp=sharing)

---

## DAX Implementation  

### 🧮 Calculated Columns  

| **Name** | **Purpose** | **Formula** | **Table** |
|-----------|-------------|-------------|------------|
| **Week Number (`wn`)** | Extracts the week number from the date column for time-based analysis. | `wn = WEEKNUM(dim_date[date])` | `dim_date` |
| **Day Type (`day type`)** | Categorizes each date as a weekday or weekend. | ```DAX
day type = 
VAR wkd = WEEKDAY(dim_date[date], 2)
RETURN
IF(wkd >= 6, "Weekend", "Weekday")
``` | `dim_date` |

---

### 📊 Measures  

| **Measure Name** | **Purpose / Description** | **DAX Formula** |
|-------------------|----------------------------|-----------------|
| **Total Revenue** | Calculates total revenue from hotel bookings. | `Total Revenue = SUM(Fact_Booking[revenue])` |
| **Total Bookings** | Counts total booking transactions. | `Total Bookings = COUNT(Fact_Booking[booking_id])` |
| **Average Daily Rate (ADR)** | Computes the average room rate per occupied room. | `ADR = DIVIDE([Total Revenue], [Total Occupied Rooms])` |
| **Occupancy Rate** | Measures the percentage of occupied rooms out of all available rooms. | `Occupancy Rate = DIVIDE([Total Occupied Rooms], [Total Available Rooms])` |
| **Revenue Per Available Room (RevPAR)** | Calculates revenue performance per available room. | `RevPAR = DIVIDE([Total Revenue], [Total Available Rooms])` |
| **Booking Growth %** | Measures month-over-month growth in bookings. | ```DAX
Booking Growth % =
VAR PrevMonth = CALCULATE([Total Bookings], DATEADD(dim_date[date], -1, MONTH))
RETURN
DIVIDE([Total Bookings] - PrevMonth, PrevMonth)
``` |
| **Revenue Growth %** | Tracks month-over-month revenue growth. | ```DAX
Revenue Growth % =
VAR PrevMonth = CALCULATE([Total Revenue], DATEADD(dim_date[date], -1, MONTH))
RETURN
DIVIDE([Total Revenue] - PrevMonth, PrevMonth)
``` |
| **Total Customers** | Counts total unique customers. | `Total Customers = DISTINCTCOUNT(Fact_Booking[customer_id])` |
| **Average Stay Duration** | Calculates the average number of nights stayed per booking. | `Average Stay Duration = AVERAGE(Fact_Booking[nights])` |

---

## Conclusion  
This Power BI project demonstrates how **data modeling**, **DAX-driven analytics**, and **interactive dashboarding** can transform operational data into actionable business insights.  
Through systematic analysis and visualization, the project delivers a powerful BI solution that enhances visibility, supports strategic planning, and enables evidence-based decision-making.

---

**Prepared by:** *Mirriam Jepleting*  
**Date:** October 24, 2025
