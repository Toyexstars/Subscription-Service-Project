# Project Title: Subscription Service Analysis


## Project Overview
This project involves analyzing customer data for a Subscription Servive to identify segments and trends. The aim is to understand customer behaviour, track subcription types and renewals.

## Data Source
The primary data used is Capstone Dataset Customer data.CSV file. This is an open source data that can be freely downloaded online.

## Tools Used
- Microsoft Excel
- MYSQL Workbench
- Power BI

## Microsoft Analysis
- Analyze customer data using Pivot Tables to find subscription patterns.
- Using Excel function to calculate the average subscription duration.
  - Average Suscription Duration = AVERAGE( Table(SubcriptionEnd)-Table(SubscriptionStart))
- Using Excel function to identify the most popular subscription types.
  - Most Popular subscrition type = COUNTIF(Table( Subscription type), D2)
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
 SELECT AVG(DATEDIFF(subscriptionend,subscriptionstart)) AS Avg_Subscription_Duration 
 FROM customersegmentation;

```
 - Customers with subscription longer than 12 months
```SQL
 SELECT COUNT(*) AS Canceled_Subscription FROM customersegmentation
 WHERE subscriptionend IS NOT NULL AND subscriptionstart IS NOT NULL
 AND subscriptionend >= DATE_ADD(subscriptionstart, INTERVAL  12 MONTH);

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
 SELECT SUM(CASE WHEN canceled = false THEN 1
        ELSE 0 END) AS Active_subscriptions,
        SUM(CASE WHEN Canceled = true THEN 1
        ELSE 0 END) AS Cancelled_subscription
 FROM customersegmentation;
```

## Pivot Table
The Pivot table summarizes
- Number of customers by subscription type
- Number of Customers per region
- Total revenue by subscription type
- Total revenue by region


     <img width="616" alt="SubscriptionPivot" src="https://github.com/user-attachments/assets/f4bb25f0-b65b-45c9-bc30-2f7f47920489">

## Excel Report

<img width="593" alt="Excel Subscription Analysis" src="https://github.com/user-attachments/assets/1c6badd4-8847-4054-89c5-5fc34489fb76">


## Key Performance Indicators
- Total Customers: Count of customers that subscribe
- Attrition: Number of customers that cancelled their subscription
- Active Customers: Number of current customers
- Attrition Rate : Total attrition divided by number of customers multiply by 100
- Average Duration : Average of total subscription durations

## Chart Analysis
- Total Customers by Subscription Type and Cancelled (Bar Chart): To identify total customers that are active and inactive per subscription type.
- Total Customers by Region (Column Barchart) : To identify total customers in each region.
- Total Revenue by subscrition type (Donut Chat) : To determine total revenue and percentage of revenue generated by each subscription type.
- Total Customers by SubscriptionStart Monthname (Line Chart): To identify the month the customers subscribed most.
- Attrition by region (Area Chart): To determine top 3 region by cancellation
- Attrition by Subscription Type (Column Barchat) : To determine total attriotion by subscription type.


## Visualization using Power BI

<img width="497" alt="PowerBI Subscription" src="https://github.com/user-attachments/assets/f1d3f1da-08f4-4699-95bc-524f80ebccd2">

## Result/Findings
Based on the anslysis above, the following results are deduced:
1. East Region has the highest customers with Basic subscription type.
2. All customers are active in East region.
3. No customer cancelled their subscription within six months. They all have 365 or 366 days duration.
4. Top three region by attrition are South, West and North.

## Recommendation
1. The company should channel their resources in productive region and define carry out extensive research in other region to find out their taste.
2. Discounted rate for other subscription type to increase patronage.
3. Compare the strength of the competitors to their own weakness and develop strategy to improve in those area.

## Conclusion
This insight can help Subscription Service understand their customers segmentation and develop strategies aimed at reducing cancellation and increasing subscription duration.
