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
 
## Features

- **Interactive Dashboard**: Allows users to interact with the data, drill down into specific regions, cities, employees, and more.
- **Sales and Profit Overview**: Provides insights into total sales and profits for quick analysis.
- **Population & Sales Correlation**: Displays population counts alongside sales data for different states.
- **Detailed Breakdown**: Includes detailed metrics for each employee and their respective monthly performance.
- **Visualization**: Beautiful and easy-to-understand visualizations for key metrics, such as pie charts, bar charts, line graphs, and maps.
  
### DAX Calculations

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
  - **Tax Impact**: A measure to compute the tax impact on sales based on region.
  ```DAX
  Tax Impact = SUM(Sales[Amount]) * TaxRate[TaxRate]
