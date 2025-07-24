# CAPSTONE_PROJECT 1

### Project Title :  Sales Performance Analysis for a Retail Store (F.M Stores)

### Project Objective 
The Sales Data analysis project aims to provide comprehensive insights into the sales performance across various dimensions such as product, region, and time. By leveraging data analytics, the project seeks to uncover patterns, trends, and actionable insights to support strategic decision-making, optimize sales operations, and enhance overall business performance.

### Data Sources
The dataset was derived from the Sales Data provided from the Sales Department of F.M Stores. The Data given is a table that have an array of columns like OrderID, Customer Id, Product, Region, OrderDate, Quantity Sold and UnitPrice.

### Tools Used
- Microsoft Excel for Data cleaning and analysis  [Download Here](https://www.microsoft.com/en-ng/)
- Structured Query Language(SQL) for quering of the Data
- Microsoft PowerBI for visualization
- Github for portfolio building

### Scope
The project focuses on analyzing a dataset containing transaction records, including details like product names, categories, sales quantities, prices, regions, and sales dates. The key areas of analysis include:

1. Sales Overview:
- Calculation of total sales and revenue across the entire dataset.
- Identification of sales trends over time, including monthly and yearly sales growth.

2. Top-Performing Products:
-  Ranking products based on total sales and revenue contribution.
- Identification of the top-selling products and product categories.
  
3. Regional Breakdown:
- Analysis of sales distribution across different regions.
- Identification of high-performing regions and potential areas for improvement.

### Methodology:
1. Data Cleaning and Preparation:
- Removal of duplicates 
- Creation of derived fields like TotalSales, Month, and Year for enhanced analysis.
  
2. Exploratory Data Analysis (EDA):
- Use of pivot tables, charts, and summary statistics to explore the dataset.
- Identification of key metrics such as total sales, average sales per product, and revenue by region.
  
3. Visualization:
- Development of interactive dashboards in Power BI to visualize sales performance.
- Use of charts such as line charts, bar charts, and pie charts to communicate insights effectively.
  
4. Advanced Analysis:
- SQL queries to extract specific insights, such as monthly sales totals, top customers, and regional performance.
- DAX measures in Power BI for dynamic calculations and insights.

### Expected Impact:
The insights derived from the SalesData analysis will empower stakeholders to:
- Make data-driven decisions to boost sales performance.
- Identify and leverage top-performing products and regions.
- Improve customer targeting and retention strategies.
- Enhance operational efficiency by identifying bottlenecks and opportunities.
  
### Deliverables:
A. Excel Report: [Download Here](https://onedrive.live.com/personal/281b96814f584b5c/_layouts/15/doc.aspx?resid=845e85eb-85f5-409c-a830-3496c8d93a31&cid=281b96814f584b5c&wdOrigin=MARKETING.FREE.GO-TO-EXCEL%2CAPPHOME-WEB.FILEBROWSER.RECENT&wdPreviousSession=c3b51228-c0e6-46b7-af95-0618f2293007&wdPreviousSessionSrc=AppHomeWeb&ct=1730741765374)
- Summarized data with pivot tables and calculated metrics.
- Visual representations of key insights through charts.
  
B. SQL Queries:
- Repository of SQL queries used to extract key insights.
- Documentation of findings from the SQL analysis.

SELECT * FROM SalesData;

--- 1. retrieve the total sales for each product category.---
- SELECT Product, SUM(UnitPrice * Quantity) AS TotalSales
FROM SalesData
GROUP BY Product

--- 2. find the number of sales transactions in each region.---
- SELECT Region, COUNT(*) AS NumberOfSales
FROM SalesData
GROUP BY Region

-- 3. find the highest-selling product by total sales value.--
- SELECT SELECT Product, SUM(UnitPrice * Quantity) AS TotalSales
FROM SalesData
GROUP BY Product
ORDER BY TotalSales DESC

--- 4. calculate total revenue per product.---
- SELECT Product, SUM(UnitPrice * Quantity) AS TotalRevenue
FROM SalesData
GROUP BY Product

-- 5. calculate monthly sales totals for the current year
- SELECT MONTH(OrderDate) AS Month, SUM(UnitPrice * Quantity) AS MonthlySales
FROM SalesData
WHERE YEAR(OrderDate) = 2024
GROUP BY MONTH(OrderDate)
ORDER BY Month

-- 6. find the top 5 customers by total purchase amount.---
- SELECT customer_id, SUM(UnitPrice * Quantity) AS TotalPurchase
FROM SalesData
GROUP BY customer_id
ORDER BY TotalPurchase DESC

-- 7. calculate the percentage of total sales contributed by each region.---
- SELECT Region, 
SUM(UnitPrice * Quantity) AS RegionalSales,
(SUM(UnitPrice * Quantity) / (SELECT SUM(UnitPrice * Quantity) FROM CapstoneSalesData) * 100) AS SalesPercentage
FROM SalesData
GROUP BY Region

-- 8. identify products with no sales in the last quarter.---
- SELECT Product
FROM SalesData
WHERE OrderDate BETWEEN '2024-06-01' AND '2024-08-31'
GROUP BY Product
HAVING SUM(UnitPrice * Quantity) = 0
  
C. Power BI Dashboard:
- Interactive dashboard showcasing a sales overview, top products, and regional breakdowns.
- Filters and slicers for dynamic exploration of the data.

1. Sales Overview
   
![image](https://github.com/user-attachments/assets/441123ea-3fe8-41b6-a1a8-3780405aca4c)

![image](https://github.com/user-attachments/assets/5e81105a-818f-440b-a6ad-de81cf6e350f)

![image](https://github.com/user-attachments/assets/d6054c4a-4f08-40e8-b0b9-63336180958f)

2. Top Products

![image](https://github.com/user-attachments/assets/c851d21c-0fce-4c21-a29c-b9acf316089c)

![image](https://github.com/user-attachments/assets/52268455-b7c1-4668-b404-03dbf90d15a2)

![image](https://github.com/user-attachments/assets/891d9062-c7c6-4c98-b550-154e0672e57a)

3. Regional Breakdowns

![image](https://github.com/user-attachments/assets/960d9911-a9fc-4398-8625-8262801b0c04)

![image](https://github.com/user-attachments/assets/80f19360-3a63-432c-b470-afe205bf6f8b)

![image](https://github.com/user-attachments/assets/a0812091-252d-4d46-8e31-f4dd871297ea)

### DASHBOARD HIGHLIGHT KEY VISUALS

![image](https://github.com/user-attachments/assets/b02f135e-a491-4e98-8ad2-d4a34609c615)

### Key Findings
1. Sales Trends Over Time
- Looking at the sales trend, there is a flunctuation through out the year. There was a decline in sales in January, a groth in February, which drops again in March and remained unstable over time, leaving February to having the peak sales.

2. Top-Performing Products
- Shoes, Shirt, Hats and Gloves products consistently generate higher revenue but Shoes having the highest revenue. There should be a focus on inventory to maintain this trend and marketing efforts to boost sales on Jackets and socks.

3.  Regional Sales Distribution
- East, West, South and North regions contribute differently to the total sales. South region shows the highest revenue which indicates a more effective sales strategy or higher market demand in that area. North and West may need targeted strategies to improve sales.

### Recommendations:
- Focus on High-Performing Products and Regions: Enhance marketing and stock for top products and regions.
- Analyze Low-Performing Areas: Develop strategies to boost sales in lower-performing regions.
- Seasonal Promotions: Leverage peak sales months for targeted promotions.
- Customer Loyalty Programs: Implement strategies to retain customers in high-performing regions.

### Conclusion
This project lays the foundation for continuous sales performance monitoring and strategic planning, fostering growth and competitive advantage.

