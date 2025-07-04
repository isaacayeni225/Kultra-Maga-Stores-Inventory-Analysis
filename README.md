# Kultra-Maga-Stores-Inventory-Analysis
## Kultra Mega Stores Inventory Analysis Project

## Overview
Kultra Mega Stores (KMS), a leading office supplies and furniture retailer in Nigeria, has engaged me as a Business Intelligence Analyst to analyze their order data from 2009 to 2012. The analysis aims to provide key insights and findings to inform business decisions and drive growth. And will also provide a clear and concise representation of the data, facilitating informed decision-making by the KMS management team.

## Tools and Methods Used
Data Analysis: Order data from the company, provided in Excel format, was analyzed using SQL to answer the following questions:

1. Which product category had the highest sales?
2. What are the Top3 and Bottom3 regions in terms of sales?
3. What were the total sales of appliances in Ontario?
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method?
6. Who are the most valuable customers, and what products or services do they typically purchase?
7. Which small business customer had the highest sales?
8. Which Corporate Customer placed the most number of orders in 2009 –2012?
9. Which consumer customer was the most profitable one?
10. Which customer returned items, and what segment do they belong to?
11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer 

## Key Objectives

| Objectives | Descriptions |
| --- | --- |
| 1. Product Category Analysis | Identify the product category with the highest sales and analyze sales trends. |
| 2. Regional Sales Performance | Determine the top 3 and bottom 3 regions in terms of sales and provide recommendations for improvement. |
| 3. Customer Analysis | Identify the most valuable customers, their purchasing habits, and provide insights on small business and corporate customers. |
| 4. Shipping Cost Optimization | Analyze shipping costs, identify the most expensive shipping method, and evaluate the effectiveness of shipping cost allocation based on order priority. |


## Key Insights

| Insights | Descriptions |
| --- | --- |
| 1. Product Category | Identification of the product category with the highest sales and analysis of sales trends. |
| 2. Regional Sales | Top 3 and bottom 3 regions in terms of sales, with recommendations for improvement. |
| 3. Customer Segmentation | Identification of the most valuable customers, small business customers with high sales, and corporate customers with the most orders. |
| 4. Shipping Cost | Analysis of shipping costs, identification of the most expensive shipping method, and evaluation of shipping cost allocation. |


## Visual analysis and Inference

![image alt](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/6c66f8f5fb974bd7fc160d66fb60c9280b9fd628/Q1.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/186a86332abca4317cfe5b62d98fec8eaa10514d/Q2.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/caec0a92fb736b60f14bf4b0edbcc9e8bcb799a0/Q3.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/83b895108b90280c0992d332e6170622abdabe24/Q4.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/21b346049ced75f2304d850e3ce1fc52e80cfe4f/Q4-1.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/536e8d573de90e22a03cad17450fce02ad6a00b0/Q4-2.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/e2fcce86428c6eb7825fa74a41e3bf80afb8f484/Q5.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/6acc41f16a8acde0620033b9a4272b7d9fef81c4/Q6.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/373f75baad42df363155b4ef091a9ee3b9261114/Q7.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/220482f7c0676baab3cf4ddce4808e2cfec83033/Q8.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/0696e3ae001de4f9ed5989aa151960a8006bd03c/Q9.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/8a8ad7bd1a501dea1cb203074ca75aec65c96f86/Q10.png)

![image](https://github.com/isaacayeni225/Kultra-Maga-Stores-Inventory-Analysis/blob/d8bf8e160b452d84afa603acad5d4a5ad095cf8e/11.png)


## SQL Queries Used

Question 1
----------------Product with the highest sales---------------
SELECT TOP 3
Product_Category,
Sum(Sales) As [Total Sales]
From [dbo].[KMS_STATUS]
Group By
Product_Category
Order By
[Total Sales] DESC

Question 2
---------------Top 3 and Bottom 3 regions in terms of Sales--------------- 
SELECT TOP 3
Region, Sum(Sales) As [Total Sales] 
From [dbo].[KMS_STATUS]
GROUP BY 
Region
ORDER BY 
[Total Sales] DESC

---------------Bottom 3---------------
ELECT TOP 3
Region, Sum(Sales) As [Total Sales] 
From [dbo].[KMS_STATUS]
GROUP BY 
Region
ORDER BY 
[Total Sales] ASC

Question 3
---------------Total Sales of appliances in Ontario---------------
SELECT
Region,
Sum(Sales) As [Total Sales]
From [dbo].[KMS_STATUS]
WHERE
Product_Sub_Category = 'Appliances'
AND Region = 'Ontario'
Group By Region

Question 4
--------Advice for management of KMS on what to do to increase the revenue from the bottom 10 customers--------
SELECT top 10 
	customer_name, region, discount, customer_segment, product_category,province,
	count(OrderID) as totalorders,
	sum(sales) as totalsales
	from [dbo].[KMS_STATUS]
	 group by customer_name, region, discount, customer_segment, product_category, province
	 order by totalsales asc

	```SELECT 
'Potential Advice for Bottom 10 Customers' AS Advice,
'1. Personalized Marketing' AS Strategy,
'Offer targeted promotions, discounts, or loyalty programs' AS Description
UNION ALL
SELECT
'Potential Advice for Bottom 10 Customers' AS Advice,
'2. Customer feedback' AS Strategy,
'Collect feedback from customers to understand their needs and preferences' AS Description
UNION ALL
SELECT
'Potential Advice for Bottom 10 Customers' AS advice,
'3. Product Recommendations' AS strategy,
'Analyze purchase history and recommend products that might interest them' AS description
UNION ALL
SELECT
'Potential Advice for Bottom 10 Customers' AS Advice,
'4. Improved Customer Service' AS Strategy,
'Provide exceptional customer service to build trust and loyalty' AS Description
UNION ALL
SELECT
'Potential Advice for Bottom 10 Customers' AS Advice,
'5. Loyalty Programs' AS Strategy,
'Implement loyalty programs that reward repeat customers and encourage retention' AS Description
UNION ALL
SELECT
'Potential Advice for Bottom 10 Customers' As Advice,
'6. Targeted Communication' AS Strategy,
'Regularly communicate with customers through email, phone, or social media' AS Description```

Question 5
---------------The most shipping method cost incurred by KMS---------------
  ```SELECT TOP 1 
  [Ship_Mode], 
  SUM([Shipping_Cost]) AS [Total Shipping Cost]
FROM 
  [dbo].[KMS_STATUS] 
GROUP BY 
  [Ship_Mode] 
ORDER BY 
  [Total Shipping Cost] DESC```

 Question 6
 -------------The most valuable customers, and what products or services do they typically purchase------------
  ```SELECT TOP 10
  [dbo].[KMS_STATUS].Customer_Name, 
  [dbo].[KMS_STATUS].Product_Name, 
  SUM([dbo].[KMS_STATUS].Sales) AS Total_Sales
FROM 
  [dbo].[KMS_STATUS] 
WHERE 
 [dbo].[KMS_STATUS].Customer_Name IN (
    SELECT TOP 10 
      Customer_Name 
    FROM 
      [dbo].[KMS_STATUS] 
    GROUP BY 
      Customer_Name 
    ORDER BY 
      SUM(Sales) DESC
  )
GROUP BY 
 [dbo].[KMS_STATUS].Customer_Name, 
 [dbo].[KMS_STATUS].Product_Name 
ORDER BY 
 [dbo].[KMS_STATUS].Customer_Name, 
  Total_Sales DESC```

 Question 7
 ---------------The small business customer with the highest sales---------------
  ```SELECT TOP 10
  Customer_Name, SUM(Sales) As Total_Sales
  From [dbo].[KMS_STATUS] 
  WHERE 
  Customer_Segment = 'Small Business'
  GROUP BY 
  Customer_Name
  ORDER BY 
  Total_Sales DESC```

Question 8
--------------Corporate Customer who placed the most number of orders in 2009 - 2012---------------
```SELECT TOP 10 
    Customer_Name, 
    COUNT(Sales) AS Total_Sales 
FROM 
    [dbo].[KMS_STATUS] 
WHERE 
    Customer_Segment = 'Corporate' 
    AND Order_Date BETWEEN '2009-01-01' AND '2012-12-31' 
GROUP BY 
    Customer_Name 
ORDER BY 
    Total_Sales DESC```
	
  Question 9
  ---------------The most profitable consumer customer---------------
  ```SELECT TOP 10
  Customer_Name, SUM(Sales) As Total_Sales
  From KMS
  WHERE 
  Customer_Segment = 'Consumer'
  GROUP BY 
  Customer_Name
  ORDER BY 
  Total_Sales DESC```

  Question 10
  ---------------The customers who returned items, and their segment---------------
    ```SELECT DISTINCT 
    Customer_Name,  
    Customer_Segment
FROM 
    [dbo].[KMS_STATUS]
WHERE 
    Status = 'Returned'```

  Question 11
  ---------------The company Shipping methods and shipping costs---------------
```SELECT order_priority, ship_mode,
		count(distinct OrderID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
from [dbo].[KMS_STATUS] 
group by  order_priority, ship_mode
order by   order_priority, ship_mode desc```






