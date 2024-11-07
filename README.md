# LITA-CAPSTONE-DATASET-1

## SALES DATA ANALYSIS PROJECT


### [Project Overview](#project-overview)
---

This project collects and analyse sales data from various regions with the aim to show different products ordered by various customers.
The goal is to provide insight into sales revenue, products type, unit price and quantity purchased over two years period of time.

However, the analysis will be narrowed down to focus on understanding and calculating:

- Top selling products
- Regional performance using various metrics
- Monthly sales trends

### [Project Aims and Objectives](#projectaims-andobjectives)
---

1. Revenue by Region - Is to determine the Total Sales generated in each region
2. Total Sales by product- To analyzed the unit price of all products sold to identify the most patronized one
3. Monthly Total sales - To Calculate the sum revenue generated in each month
4. Quantity sold per region and percentage - To Analyze the number of quantity sold across different regions to identity the highest selling locations
5. Top ten monthly sales - This is to articulate the highest top ten monthly revenue generated between year 2023 & 2024 reviewed
6. Average monthly quantity sold - To Calculate the average quantity sold in each month to assess performance, etc

### [Data Sources](#data-sources)
 ---
 
 The data set includes the following key column;
 
- OrderBy: This is a unique code that identifies each customers request
-  Customer: An individual who patronizes or buys products
-  Product : The name of items sold in a particular qeographical location
-  Region :  This is the geographical area where the products are been sold
-  OrderDate :It is the specific day customer placed an order
-  Quantity : This is the number of items purchased by customers
-  Unit Price : It is the amount tagged on each product
-  Revenue : Is the total monetary value generated for the sale of a product at a unit price

### [Tools Used](#tools-used)
---

- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. Data Cleaning
  2. Data Analysis
  3. Visualizations
  
 ### Tools And Methods Used
 ---

  1. Data Analysis: The data was arranged and analyzed using Microsoft Excel, utilizing Pivot Tables to arrange, summarize and filter the data for better interpretation.
  2. Data Visualization: Bar charts and Pie charts were created in Excel to visually represent the key insight.


     ### Visual Analysis & Inferences
     ---

 - Sales Revenue by Region



![image](https://github.com/user-attachments/assets/9dee7052-d061-4f05-a0d2-da2667c4f22a)



From the above analysis we can see that the South Region has the highest revenue to a tune of #4,675,000  


  
  ![image](https://github.com/user-attachments/assets/86018c3b-2f43-4226-a8fe-00cd7d049f0a)







- Revenue of Products Sold Per Region



 
![image](https://github.com/user-attachments/assets/56504f41-e3d8-42aa-8573-a3959fc6de9e)





![image](https://github.com/user-attachments/assets/23ee496f-b1b4-4fea-a053-983e17a3e038)



The analysis above shows that the East and North Region generate highest revenue from the sale of Shirts, Shoes from South and Hats from West.  


- Monthly Sales By Revenue 



![image](https://github.com/user-attachments/assets/83410df9-9b64-45c5-9446-4ee18e120ff1)





![image](https://github.com/user-attachments/assets/3e5d49cc-e524-49b4-a810-c0d37477d577)




MONTHLY SALES REVENUE FOR 2023 & 2024 analyzed

 
![image](https://github.com/user-attachments/assets/49557263-cf0c-45db-90f5-1080895fff5c)




The peak selling period is month of February as displayed on charts for year 2023 & 2024 reviewed

- Average Sales Per Product



![image](https://github.com/user-attachments/assets/029d1419-46c5-4a4f-bce4-11c5d6a20cfc)




  ![image](https://github.com/user-attachments/assets/16a50ea5-bcb8-4412-940c-9084aba404b3)



- Top Selling Product by Quantity


![image](https://github.com/user-attachments/assets/f2488f30-40ac-48bd-bbff-a0b12efc213e)


![image](https://github.com/user-attachments/assets/754a8919-0f11-4b46-8fbb-4ed39136171d)

As deduced from the above analysis, Hat remains the peak selling product, followed by shoes, Gloves and shirts shared the same figure and down to the least patronized product.


  # Furthermore, the structured query language loaded for the analyzed dataset is as follows:

  ```` SQL


create database LITA_CAPSTONE

SELECT *FROM [dbo].[LITA Capstone Dataset N]

-----retrieve the total sales for each product category.

Select Product, Sum (Revenue) as Revenue from [dbo].[LITA Capstone Dataset N]
Group by Product


-----find the number of sales transactions in each region

Select Region, count(Orderid) As noofrevenuetransaction from [dbo].[LITA Capstone Dataset N]
Group by Region


-------find the highest-selling product by total sales value.

Select Product, max(Revenue) as totalsalesvalue from [dbo].[LITA Capstone Dataset N]
Group by Product


-------calculate total revenue per product.

Select Product, sum(Revenue) as totalrevenue_per_product from [dbo].[LITA Capstone Dataset N]
Group by Product
 

 -------calculate monthly sales totals for the current year.

Select OrderDate, Sum(Revenue) as monthlyrevenue from [dbo].[LITA Capstone Dataset N]
Where Orderdate between '2024-01-01' and '2024-12-31'
Group by Orderdate
Order by Orderdate


-----Find the top 5 customers by total purchase amount---------

Select Top 5 Customer_id, Sum(Revenue) as Totalpurchase from [dbo].[LITA Capstone Dataset N]
Group by Customer_id
Order by Totalpurchase desc


-----calculate the percentage of total sales contributed by each region.

Select Region, Sum(revenue)
As Total_Revenue, Sum(revenue)* 100.0 /(2101090) As Percentage_Revenue_By_Region from [dbo].[LITA Capstone Dataset N]
Group by Region
Order by Percentage_Revenue_by_Region Desc;
Select Sum(revenue) from [dbo].[LITA Capstone Dataset N]


-----identify products with no sales in the last quarter.

Select Product, OrderDate, OrderId, Revenue from [dbo].[LITA Capstone Dataset N]
Where Product not in (select Product from [dbo].[LITA Capstone Dataset N]
Where OrderDate >=DATEADD(QUARTER, -1, GETDATE()));
````
