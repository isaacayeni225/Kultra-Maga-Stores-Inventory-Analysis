# Kultra-Maga-Stores-Inventory-Analysis
## Kultra Mega Stores Inventory Analysis Project

## Overview
Kultra Mega Stores (KMS), a leading office supplies and furniture retailer in Nigeria, has engaged me as a Business Intelligence Analyst to analyze their order data from 2009 to 2012. The analysis aims to provide key insights and findings to inform business decisions and drive growth. And will also provide a clear and concise representation of the data, facilitating informed decision-making by the KMS management team.

## Data Collected
The dataset includes the following key columns:
1. Order ID: Unique identifier for each order
2. Order Date: The date the order was placed
3. Order Priority: The priority level assigned to the order
4. Sales: Total sales revenue generated
5. Discount: The discount amount offered to customers
6. Shipping Mode: The shipping method used for the order
7. Profit: The revenue remaining after deducting expenses from sales
8. Unit Price: The price of a single unit of the product
9. Shipping Cost: The cost of shipping the order
10. Customer Name: The name of the customer who placed the order
11. Province/Region: The province or region where the order was placed
12. Customer Segment: A group of customers with similar characteristics and needs
13. Product Category: A category of similar products or services
14. Product Name: The name of the product purchased
15. Status: The status of the order (e.g., returned, delivered, pending)


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


*Question 11* 


If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the order priority? Explain your answer

Based on the query ran here:

                SELECT order_priority, ship_mode,
		count(distinct OrderID) as TotalOrder,
		round(sum(sales - profit),2) as [Estimated shipping Cost],
		avg(datediff(day,[order_date],[ship_date])) as avgshipdays
                from [dbo].[KMS_STATUS] 
                group by  order_priority, ship_mode
                order by   order_priority, ship_mode desc```
                 

it appears that the company was not using the most cost-effective shipping methods for certain order priorities. Recommendations include:

- The company should review shipping policies to ensure alignment with business objectives.
- The company should also analyze data to identify opportunities for cost savings.
- And finally, the company should implement changes to shipping methods and policies as needed.
  
## Conclusion 
The Kultra Mega Stores Inventory Analysis provides a comprehensive understanding of the company's sales performance, customer behavior, and shipping costs. By leveraging data-driven insights, KMS can optimize product offerings, improve regional sales, enhance customer relationships, and streamline shipping operations. The analysis serves as a foundation for informed decision-making, enabling KMS to drive business growth, improve customer satisfaction, and maintain its position as a leading office supplies and furniture retailer in Nigeria. With actionable recommendations and compelling visualizations, this analysis empowers KMS to take strategic steps towards a more efficient, customer-centric, and profitable business model.



















