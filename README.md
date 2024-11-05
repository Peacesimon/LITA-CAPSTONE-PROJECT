# LITA-CAPSTONE-PROJECT 1

### Project Title: Sales Data Analysis

### Project Overview
---
The Sales Data Analysis Project aims to uncover valauble insights from sales data  This Project aimed to analyze, visualize and Provide insights from regions and product sold.The Project utilized dataset spanning from 2023 to 2024, comprising of 9,922 record of sales transaction. The  By analysing the various parameters in the data received we seek to gather enough reasonable decisions which then enabe us to tell compelling stories around our data for the insights gotten and to know the best performance from our data.

### Objectives
---
This project aimed to achieve the following objectives:
- Determine the total revenue generated by each region
- Determine the Average Revenue generated by Each Region
- Identify  Top selling Product
- Average Sales per Product
- Monthly Sales Trend
- Inform Data driven decision for future sales strategy and resource allocation  

### Data Collected
---
The Sales Data analyzed in this Project comprised of 9,922 number of record spanning from 2023 - 2024 and included the following variables:
#### Variables
- OderID: Unique Ientifer
- CustomerID: unique Identifer
- Region: Geograghical region where sales occurred(e.g North, East, South and West)
- Product: product sold in the region( Hats, Gloves, Socks, Shoes, Jacket and shirt)
- OderDate: date of Transaction
- Unit Price: Price per unit
- Quantity: Number of quantity sold 
- Revenue: Tota sales revenue

### Tools Used
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. For Data Cleaning
  2. For Analysing
  3. For Visualization
     
- SQL- Structured Query Language for querying of data
- Power BI (for creating a report)
- GITHUB for portfolio Building

### Methodology
---
  1. Data Cleaning and preparation
  2. Exploratory Data Analysis
  3. Formula Used
  4. Visualization of Key Metrics
     
### Data Cleaning and Preparation
---
In the initial cleaning phase of the data cleaning and preparation, we perform the follwing actions;
 1. Data Loading and Inspection
 2. Data cleaning and Removing of duplicate columns

### Exploratory Data Analysis
---
EDA involves the exploring of the data to answer some questions about the Data such as;
  1. What is the total revenue by Region?
  2. What is the Average Revenue by Region?
  3. What is the total sales per Product
  5. What is the Top selling Product?

### Formula Used
``` MS EXCEL
Total Sales = Quantity * Unit price
```

### Data Visualization
---
#### Revenue by Region	
![image](https://github.com/user-attachments/assets/0702097a-d0a8-48f7-bb1c-60fa06da7968)


#### Region by Quantity sold
![image](https://github.com/user-attachments/assets/c26428b7-2d82-4589-a286-14553e75baa6)

#### Total Sales per Product
![image](https://github.com/user-attachments/assets/8242de82-93fc-4c03-9e57-f441599b7b28)


#### Average Quantity  per Product
![image](https://github.com/user-attachments/assets/01d270be-1707-4161-a370-27e23422a891)


#### Revenue by Product from Each Region
![image](https://github.com/user-attachments/assets/358ead51-b1f0-4f49-8e1f-fb05525a9086)

#### Monthly Revenue
![image](https://github.com/user-attachments/assets/994340d0-923f-4577-8325-5aeb75b4acd6)


#### Quarterly Revenue
![image](https://github.com/user-attachments/assets/19f76b65-2b79-4d14-b942-19f2048cd540)

### Sales Report using Charts
#### Top 3 selling Product
![image](https://github.com/user-attachments/assets/baa7cce2-283e-4c3f-a673-f1cf3c70af4e)

#### Monthly Sales Trend
![image](https://github.com/user-attachments/assets/96eba40a-4a13-4bd6-b32d-2798490a2c36)








## SQL for Database Management and Quering
---
### Query to retrieve the total sales for each product category----

```SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[SalesData$]
GROUP BY [Product]
```

Query to find the number of sales transactions in each region------
```SQL
SELECT Region, COUNT(OrderID) AS NumberOfTransactions
FROM [dbo].[SalesData$]
GROUP BY Region
```

--------query to find the highest-selling product by total sales value--------
```SQL
SELECT Top 1 Product, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[SalesData$]
GROUP BY Product
ORDER BY TotalSales DESC
```
##### Expected Result
![top selling](https://github.com/user-attachments/assets/e35efcd9-9112-488c-91ac-1cf78fe953f1)

-------query to calculate total revenue per product------
```SQL
SELECT Product, SUM(Quantity * UnitPrice) AS TotalRevenue
FROM [dbo].[SalesData$]
GROUP BY Product
```
##### Expected Result
![total revenue](https://github.com/user-attachments/assets/ea18acd6-7d9d-4f07-b666-ec4342497d04)


--------query to calculate monthly sales totals for the current year------
``` SQL
SELECT FORMAT(OrderDate, 'yyyy-MM') AS Month, SUM(Quantity * UnitPrice) AS TotalSales
FROM [dbo].[SalesData$]
WHERE OrderDate >= DATEFROMPARTS(YEAR(GETDATE()), 1, 1) -- Start of the current year
AND OrderDate < DATEADD(YEAR, 1, DATEFROMPARTS(YEAR(GETDATE()), 1, 1)) -- Start of the next year
GROUP BY FORMAT(OrderDate, 'yyyy-MM')
ORDER BY Month
```
##### Expected Result
![total sales monthly ](https://github.com/user-attachments/assets/0ddd14c7-ac21-4622-8148-a72d37d05e0c)

-------query to find the top 5 customers by total purchase amount-------
```SQL
SELECT TOP 5 [Customer Id], SUM(Quantity * UnitPrice) AS TotalPurchase
FROM [dbo].[SalesData$]
GROUP BY [Customer Id]
ORDER BY TotalPurchase DESC
```
##### Expected Result
![top 5 customers](https://github.com/user-attachments/assets/f4e696a4-8d0b-4c64-a6af-d0b06d93ff8d)

------query to calculate the percentage of total sales contributed by each region-----
```SQL
select Region,
SUM (sales_Revenue) as total_sales,
round ((select sum (sales_Revenue)/ cast((select sum(sales_Revenue)
FROM [dbo].[SalesData$] ) as float) *100), 0) as
percentage_total_sales
FROM [dbo].[SalesData$]
GROUP BY Region
ORDER BY Region DESC
```

--------query to identify products with no sales in the last quarter------
```SQL
SELECT DISTINCT Product
FROM [dbo].[SalesData$]
WHERE Product NOT IN (
SELECT Product
FROM [dbo].[SalesData$]
WHERE OrderDate >= DATEADD(MONTH, -3, GETDATE())
)
```
##### Expected Result
![not made sales](https://github.com/user-attachments/assets/15d1f4a5-18ad-43b6-8dcd-189b33661139)








## POWER BI ( FOR DATA VISUALIZATION)
---

![image](https://github.com/user-attachments/assets/200fc8f6-82b3-47f5-97e2-07ba10848a05)


Looking at this sales report, I can provide several key insights:

1. Overall Performance:
- Total revenue is 2.1M with an average revenue of 212 per unit
- The company sells 6 different products
- Total quantity sold is 68.5K units

2. Regional Performance:
- The East region is the strongest performer with 928K (44%) of revenue
- This is followed by West (486K/23%), South (~300K/14%), and North (386K/19%)
- The East region also leads in quantity sold at ~20K units

3. Product Distribution:
- Looking at the "Region by Quantity sold and Product" chart:
- Gloves appear to be the highest-volume product across regions
- The South region shows particularly strong glove sales
- Jackets have more balanced distribution across regions
- Hat sales appear to be lower overall compared to other products

4. Interesting Patterns:
- Despite the East having the highest revenue, the South shows higher unit sales in some product categories
- This suggests different pricing strategies or product mix by region
- The West region has the lowest quantity sold but generates 23% of revenue, indicating higher price points or premium product mix

5. Potential Opportunities:
- There may be opportunities to replicate the East region's success in other territories
- The North region appears to have room for growth given its lower performance metrics
- Product mix optimization could help boost revenue in lower-performing regions




