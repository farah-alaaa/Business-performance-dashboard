# 🚀 Business Performance Dashboard

This project provides a comprehensive **Business Performance Dashboard** built with Power BI to track, analyze, and visualize key business metrics. The dashboard uses **DAX** (Data Analysis Expressions) to calculate key performance indicators (KPIs) and create custom metrics for deeper business insights. It includes various performance indicators, including tax analysis, sales distribution, package count analysis, and employee performance. This tool is ideal for monitoring business health and making data-driven decisions.📈💡

## 🌍 Project Overview

This dashboard paints a clear picture of your business operations across various regions and team members. Key insights include:

- 💸 **Total Tax Amount**: Visualizes tax contributions by region and their effect on financial health.
- 📅 **Sales Growth**: Monthly trends that help you spot growth patterns and take action.
- 👨‍💼 **Employee Sales Analysis**: Understand how each team member is performing.
- 🗺️ **Regional Analysis**: Sales and population data across states help prioritize key markets.
- 📦 **Package Distribution**: Breakdown of package types and how they move across regions.
- 🌐 **Sales Across Countries & Cities**: Highlight top-performing areas and uncover untapped potential.
- 📊 **Product Sales Over the Years**: Uncover trends over time and make historical comparisons.
 
### 🔥 Key Features

- 🖱️ **Interactive Dashboard**: Click, drill, filter — explore your data the way *you* want!
- 💰 **Sales & Profit Overview**: Instantly view top-line numbers for fast decisions.
- 🧮 **Population vs. Sales**: Correlate demographics with business performance for smarter targeting.
- 📆 **Employee Monthly Breakdown**: Zoom in on individual contributions month by month.
- 🎨 **Engaging Visuals**: Clean, colorful charts (pie, bar, line, and maps) turn data into insight at a glance.
 
#### 🧠DAX Calculations

In this project, **DAX** is used extensively to calculate key business metrics and enable dynamic reporting. Some of the key DAX measures and calculated columns include:

- 💵 **Total Sales**: A DAX measure that sums up sales from various transactions.
  ```DAX
  Total Sales = SUM(Sales[Amount])

- 📈**Sales Growth**: A DAX measure to calculate the month-over-month sales growth.
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
 - 🧑‍💼**Employee Performance**: A custom measure to calculate total sales for each employee.
  ```DAX
  Employee Sales = 
  SUMX(
      FILTER(Sales, Sales[Employee] = EARLIER(Employees[EmployeeID])), 
      Sales[Amount]
      )
