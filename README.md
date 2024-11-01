# Project Title: Subscription Service Analysis


## Project Overview
This project involves analyzing customer data for a Subscription Servive to identify segments and trends. The aim is to understand customer behaviour, track subcription types and renewals.

## Data Source
The primary data used is Customer data.CSV file. This is an open source data that can be freely downloaded online.

## Tools Used
- Microsoft Excel
- MYSQL Workbench
- Power BI

## Microsoft Analysis
- Analyze customer data using Pivot Tables to find subscription patterns.
- Using Excel function to calculate the average subscription duration.
- Using Excel function to identify the most popular subscription types.
- Interesting reports using visualization


 ## SQL Analysis
 - The total number of customers from each region
  
  ```SQL
  SELECT Region, COUNT(Distinct customerid) AS Customers_Per_Region FROM customersegmentation
  GROUP BY Region
  ORDER BY 2 DESC;
 ```
 - The most popular subscription type by the number of customers
```SQL
 SELECT subscriptiontype, COUNT(customerid) AS Top_Subscription_Type FROM customersegmentation
 GROUP BY subscriptiontype
 ORDER BY 2 DESC
 LIMIT 1;
```
 - Customers who cancelled their subscrition within 6 months
```SQL
 SELECT COUNT(*) AS Canceled_Subscription FROM customersegmentation
 WHERE subscriptionend IS NOT NULL AND subscriptionstart IS NOT NULL
 AND subscriptionend <= DATE_ADD(subscriptionstart, INTERVAL 6 MONTH)
```
 - The average subscription duration for all customers
```SQL



```
 - Customers with subscription longer than 12 months
```SQL


```
 - Total revenue by subscription type
```SQL
 SELECT Subscriptiontype, SUM(Revenue) AS Total_Revenue_Subscription_Type
 FROM customersegmentation
 GROUP BY Subscriptiontype
 ORDER BY 2 DESC;
```
 - Top 3 region by subscription cancellations
```SQL
 SELECT Region, COUNT(*) AS Subscription_Cancelation_By_Region FROM customersegmentation
 WHERE Canceled = 'TRUE'
 GROUP BY Region
 ORDER BY 2 DESC
 LIMIT 3;
```
 - Total number of active and cancelled subcriptions
```SQL
 

```

## Pivot Table
