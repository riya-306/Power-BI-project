
Sales data analysis-Dashboard



## Problem Statement

This project analyzes sales performance data to track revenue, quantity, and profit trends across products and time. The goal is to help businesses identify top-performing products, detect underperforming ones, and monitor overall sales growth.

## Key Goals-
1) Top/Bottom 5 product by Sales/Profit/Quantity Sold.
2) How do sales trends vary over time (daily, monthly, quarterly, annually)
3) Show relationship between sales & profit.
4) Compare sales/profit/quantity sold between any two periods selected by the user.
5) Average discount offered in each discount category.6) Total number of orders.
7) Show Sales/Profit/Discount/Net Sales/All remaining fields for each order that could be filtered using visual filters. (Product/Date/Customer ID/Promotion Categories).
8) Show sales by different cities.


### Steps followed -

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : converted key IDs to Text data type, corrected other column data types (numeric vs text), moved first row to headers in Promotions table, created a new numeric percentage column using conditional logic for  promotions
- Step 5 : . Data Cleaning & Joins – Merged Fact Table with Dimension Product table to bring in **Price per Unit**, ensured correct data types, and removed redundant null-value columns.

- snap of new calculated column ,

<img width="169" height="487" alt="Image" src="https://github.com/user-attachments/assets/5e70802a-a5c7-458d-a449-802526c3ddcb" />

- Step 6 : .Derived Columns – Created new calculated fields: Total Sales (Unit Sold × Price per Unit), Discount Value (Total Sales × Discount % ÷ 100), and Net Sales (Total Sales – Discount Value).
  
- Step 7 :Promotion Data Integration – Merged with Promotion table to fetch Discount %, replaced null values with 0, and finalized structured Fact Table for reporting.
  
- Step 8 : Building Relationships (Star Schema) – Created a data model in Power BI by connecting Fact Table with three Dimension Tables (Customer, Product, Promotion) using their respective primary–foreign keys (Customer ID, Product ID, Promotion ID). Ensured correct cardinality (1-to-many) and single-direction cross-filtering for accurate filtering and reporting

<img width="1250" height="492" alt="Image" src="https://github.com/user-attachments/assets/6b91491f-0975-4e62-8e19-0b5a0e02abbd" />


- Step 9 :

  
   1.**Creating Profit Column & Data Modeling–**
   
     o	Added a new calculated column Profit in
            Power Query (Profit = 0.1 * Net Sales).
   
     o	Ensured correct data types and applied
            changes.
   
     o	Used star schema relationships between
            Fact    Table and Dimension Tables
            (Product, Customer, Promotion).
   
     2.**visuals for Requirement 1–**
        o Built bar charts to display:
  
      Top 5 Products by Sales, Quantity Sold, and Profit.

      Bottom 5 Products by Sales, Quantity  Sold,and Profit.

     o	Applied visual-level filters (Top N
          Bottom N) for each chart.

     o	Customized formatting: titles, data 
         abels, colors, borders, and improved
         readability for long product names.

  <img width="877" height="488" alt="Image" src="https://github.com/user-attachments/assets/45c0ac3c-2335-4d86-a026-96c688c1884c" />
  

- Step 10 : **Sales Trends Over Time-**
      
   1.Line Chart for Trend Analysis
  
     o	Built a line chart to show Net Sales over time (using the Date field from FactTable).
  
     o	Implemented hierarchical drill-down (YeaR → Quarter → Month → Day)to  allow interactive exploration of sales atterns.
  
     o	Enabled drill-up and drill-down navigation, so users can analyze trends at any desired granularity.
  
    2.Formatting & Enhancements
  
     o	Customized chart with titles, markers smooth lines, and styled axes for clarity.

     o	Added data labels and improved  readability  by disabling gridlines, resizing fonts  and aligning visuals.

     o	Finalized chart to clearly highlights daily, monthly, quarterly, and annual sales variations.


- Step 11 :**Relationship between Sales & Profit-**
  
     •	Built a Scatter Plot with Profit on the  X-axis and Net Sales on the Y-axis.
  
     •	Changed aggregation to Don’t Summarize so each point represents an individual record.
  
     •	Observed a linear relationship (Profit = 10% of Net Sales, as defined transformations).
  
     •	Highlighted data density zones (most points  concentrated where Profit ≈ 10k & Sales ≈100k).
  
     •	Customized formatting: titles, axis labels marker colors, and removed gridlines.
  
  <img width="326" height="291" alt="Image" src="https://github.com/user-attachments/assets/7f7ff4fc-9802-4ea6-91a3-8f1600dbd514" />


- Step 12 :**Average Discount by Promotion  Category-**
       
     •	Created a Bar Chart showing Average 
          Discount for each Promotion Category.
  
     •	Handled blank category (appeared due to
          orders with no discount / invalid  promotion ID) by filtering it out.
  
     •	Added consistent formatting (Times New Roman font, borders, aligned titles).
  
     •	Final chart highlights which promotions offered higher average discounts

  <img width="275" height="199" alt="image" src="https://github.com/user-attachments/assets/6eb8576b-6f16-45d7-ae1d-6d1515560802" />


- Step 13 :**Sales by City-**

     •	Used a Map Visual to represent Net Sales
          across different cities.
  
     •	Configured City field as geographical data
          to ensure correct mapping.
  
     •	Bubbles sized by Net Sales → larger bubble
          = higher sales.
  
     •	Enabled hover tooltips to display City
          Name + Net Sales.
  
    •	Added category labels & custom formatting
          for clearer insights.
  
  <img width="255" height="298" alt="image" src="https://github.com/user-attachments/assets/0ef80460-a110-4577-9d25-912a2c7aa807" />


- Step 14 :**Total Number of Orders-**

     •	Created a Card Visual showing the distinct
          count of orders (3510).
  
     •	Added an Index Column in Power Query
          (renamed to Order ID) to uniquely
          identify each order.
  
     •	Changed data type to Text to avoid
          unnecessary aggregations.
  
     •	Customized formatting (title, border, font
          styles, callout size) for professional
          readability

  <img width="274" height="91" alt="image" src="https://github.com/user-attachments/assets/c3dd3eb0-b211-4c6d-bf14-6adc4a70818e" />


  - Step 15 :**Compare Sales, Profit, and Quantity Sold Between Any Two Periods-**

1.	Setup Date Tables

o	Create Date Table 1 and Date Table 2 using CALENDARAUTO() DAX function.

o	Ensure both date columns are in Date format with Long Date formatting.

o	Establish relationships:

	Date Table 1 → Fact Table: Active (solid line).

	Date Table 2 → Fact Table: Inactive (dotted line).

2.	Add Date Slicers

o	Add two slicers on the report:

	Date Filter 1 (from Date Table 1).

	Date Filter 2 (from Date Table 2).

o	These let the user pick two periods for comparison.

3.	Create Measures (DAX)

o	Sales (Measure for Date Table 2 relationship)

o	Sales_2 = CALCULATE( SUM(Fact[Net Sales]),  ALL('Date Table 1'), USERELATIONSHIP('Date Table 2'[Date], Fact[Date])	)o

Similarly, create measures for Profit_2 and Quantity_2 using SUM(Fact[Profit]) and SUM(Fact[Units Sold]).

o	Keep Sales_1, Profit_1, Quantity_1 directly from fact table (default active relationship with Date Table 1).

4.	Build Visuals

o	Use Clustered Column Charts for:

	Total Sales (Sales_1 vs Sales_2).

	Total Profit (Profit_1 vs Profit_2).

	Total Quantity Sold (Quantity_1 vs Quantity_2).

o	Add legends/colors to clearly distinguish Period 1 vs Period 2.

5.	Formatting

o	Add borders, titles, change gridlines, adjust colors (e.g., purple vs blue).

o	Rename series:

	Sales_1 → Sales (Period 1)

	Sales_2 → Sales (Period 2)

	Similarly for Profit and Quantity


<img width="865" height="481" alt="image" src="https://github.com/user-attachments/assets/6c07077b-ba6f-4795-a81f-5090485ca369" />

        
 - Step 16 :
   
  •  Created a detailed table view showing all Fact Table fields (Order ID, Customer, Date, Sales, Profit, Discount, Quantity, etc.).
  
  •  Added slicers from dimension tables (Date, Customer, Product, Promotion) to filter the table dynamically.
  
  •  Enabled users to explore full order-level details with flexible filtering across multiple dimensions.

 
<img width="870" height="492" alt="image" src="https://github.com/user-attachments/assets/09123a63-b21e-417d-ace7-97711b6ad792" />

 
 
 # Snapshot of Dashboard (Power BI Service)

<img width="874" height="484" alt="image" src="https://github.com/user-attachments/assets/10b507a4-59e7-4779-8634-ab5df1518158" />


 


# Dashboard features-


1).Interactive slicers for Product, Customer, Date, and Promotion filters.

2).Drill-down functionality (Year → Quarter → Month → Day).

3).Comparative analysis across different time periods.

4).Order-level detailed reporting with multiple filters.

5).City-wise Sales & Profit distribution.


