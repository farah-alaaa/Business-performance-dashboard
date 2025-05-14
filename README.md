# Business Performance Dashboard

This project provides a comprehensive **Business Performance Dashboard** built with Power BI to track, analyze, and visualize key business metrics. The dashboard uses **DAX** (Data Analysis Expressions) to calculate key performance indicators (KPIs) and create custom metrics for deeper business insights. It includes various performance indicators, including tax analysis, sales distribution, package count analysis, and employee performance. This tool is ideal for monitoring business health and making data-driven decisions.

## Project Overview

This dashboard provides insights into various business operations across different regions and employees. Key metrics include:

- **Total Tax Amount**: Tax data for different regions and its impact on overall financial health.
- **Sales Growth**: Tracking of sales trends month by month.
- **Employee Sales Analysis**: A breakdown of sales performance by employee.
- **Regional Analysis**: Comparison of sales and population data by state.
- **Package Distribution**: Analysis of package types and their distribution.
- **Sales Across Countries & Cities**: Regional breakdown of sales performance, highlighting key cities.
- **Product Sales Over the Years**: Tracking product sales trends over multiple years.

## DAX Calculations

In this project, **DAX** is used extensively to calculate key business metrics and enable dynamic reporting. Some of the key DAX measures and calculated columns include:

- **Total Sales**: A DAX measure that sums up sales from various transactions.
  ```DAX
  Total Sales = SUM(Sales[Amount])

- **Sales Growth**: A DAX measure to calculate the month-over-month sales growth.
```DAX
  Sales Growth = 
  VAR CurrentMonthSales = SUM(Sales[Amount])
  VAR PreviousMonthSales = 
      CALCULATE(SUM(Sales[Amount]), 
                PREVIOUSMONTH(Sales[Date]))
  RETURN 
      IF(PreviousMonthSales = 0, 
         BLANK(), 
         (CurrentMonthSales - PreviousMonthSales) / PreviousMonthSales)
  - **Employee Performance**: A custom measure to calculate total sales for each employee.
  ```DAX
  Employee Sales = 
  SUMX(
      FILTER(Sales, Sales[Employee] = EARLIER(Employees[EmployeeID])), 
      Sales[Amount]
  )
### Explanation:
  **Employee Sales** is a custom measure to aggregate sales per employee.
  **`EARLIER`** is used to refer to the outer row context (the current employee being evaluated).
  **`SUMX`** iterates over the filtered sales data and sums up the sales amount for each employee.
- **Tax Impact**: A measure to compute the tax impact on sales based on region.
  ```DAX
  Tax Impact = SUM(Sales[Amount]) * TaxRate[TaxRate]
  ---

### Explanation:
- **Tax Impact** calculates the tax amount by multiplying the sum of sales (`Sales[Amount]`) by the region-specific tax rate (`TaxRate[TaxRate]`).
- The formula assumes you have a `TaxRate` table where tax rates are defined for each region.
