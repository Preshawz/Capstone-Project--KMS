# Capstone-Project--KMS
This is my  first Data Analysis project under DSA, supervised by the Incubator Hub.


## KMS PROJECT 
### Project Overview
This project aims to ananlyse the data provided by KMS company from 2009 to 2012 to present key insights and findings. 
The KMS company specialises in office supplies and furniture. Its customer base includes individual consumers, small businesses (retail),
and large corporate clients (wholesale) across Lagos, Nigeria. 

### Data Source
The source is a cvs file presumly give by the KMS business manager.

### Data Tools
- SQL Server (For Query & Analysis)

### Data Preparation
This stage inlvolved;
1. Data Importing as CVS file
2. Selecting appropriate Data Type
3. Selecting 'Allow Nulls' column
4. Loading of Data

### Exploratory Data Analysis
EDA involved exploring data to answer questions like;
1. Which product category had the highest sales? 
2. What are the Top 3 and Bottom 3 regions in terms of sales? 
3. What were the total sales of appliances in Ontario? etc.

### Data Analysis
This include the queries used for analysis.
1. Table was visulaized
  
   ```  sql
    SELECT * FROM KMS

2  ----HIGHEST SALES BY PRODECT CATEGORY----
``` sql
 SELECT SALES, Product_Category FROM KMS
ORDER BY SALES DESC

  ```

3 ---TOP 3 REGIONS BY SALES---
 ``` sql
SELECT TOP 3 * FROM
(SELECT REGION, SALES FROM KMS) AS KMS
ORDER BY SALES DESC

 ```
4 -----BOTTOM 3 REGIONS BY SALES----
``` sql
SELECT TOP 3 * FROM
(SELECT REGION, SALES FROM KMS) AS KMS
ORDER BY SALES ASC
```
5 -----total sales of appliances in Ontario----

``` sql
SELECT SUM(SALES) AS TOTAL_SALES FROM KMS
WHERE REGION ='ONTARIO' AND PRODUCT_SUB_CATEGORY='APPLIANCES'
```
6 -----REVENUE/SALES OF bottom 10 customers----- 
 ``` sql
 SELECT TOP 10 CUSTOMER_NAME, SALES,REGION,Customer_Segment,Product_Category 
 FROM KMS 
 ORDER BY SALES ASC

  SELECT * FROM
 (SELECT SALES,REGION,Customer_Segment,Product_Category FROM KMS)AS KMS
 WHERE Region='QUEBEC'
 ORDER BY SALES DESC
```
 - ADVICE, THE REVENUE OF THE BOTTOM 10 CUSTOMERS CAN BE INCREASED IF PRODUCT CATEGORY CAN
 BE FOCUSED ON TECHNOLOGY AND FURNITURE IRRESPECTIVE OF THE REGION AND SEGMENT

7 ------TOP SHIPPING COST WITH WHAT SHIPPING MODE-----
 ``` sql
 SELECT TOP 1 * FROM 
 (SELECT SHIPPING_COST, SHIP_MODE FROM KMS) AS KMS
 ORDER BY SHIPPING_COST DESC
```

8-----MOST VALUABLE CUSTOMERS AND PRODUCT THEY PURCHASE----
``` sql 
 SELECT TOP 3 CUSTOMER_NAME,SUM(SALES)AS TOTAL_SALES,PRODUCT_CATEGORY
 FROM KMS
 GROUP BY Customer_Name,PRODUCT_CATEGORY
 ORDER BY TOTAL_SALES DESC
```
9---- small business customer WITH the highest sales----
``` sql 
 SELECT Customer_Segment,CUSTOMER_NAME, Sales
 FROM KMS
 WHERE Customer_Segment = 'SMALL BUSINESS'
 ORDER BY SALES DESC
```

10 -----Corporate Customer WITH the most number of orders in 2009 � 2012----
``` sql 
 SELECT Customer_Segment,CUSTOMER_NAME, SUM(ORDER_QUANTITY) AS [TOTAL ORDER_QUANTITY]
 FROM KMS
 WHERE Customer_Segment = 'CORPORATE'
 GROUP BY Customer_Segment,CUSTOMER_NAME
 ORDER BY [TOTAL ORDER_QUANTITY] DESC
```
11------most profitable consumer customer----
``` sql 
SELECT TOP 1 Customer_Segment,CUSTOMER_NAME, SUM(PROFIT) AS [TOTAL_PROFIT] 
FROM KMS
WHERE Customer_Segment ='CONSUMER'
GROUP BY Customer_Segment,Customer_Name
ORDER BY [TOTAL_PROFIT] DESC
```

12---SHIPPING METHOD-DELIVERY TRUCK-SLOW-ECONOMICAL-ORDER PRIORITY
``` sql 
SELECT COUNT(ORDER_ID)AS [C.ORDER_ID],SHIP_MODE,SUM(SALES-PROFIT) AS [ESTIMATED SHIPPING COST], ORDER_PRIORITY, 
AVG(DATEDIFF(DAY,[ORDER_DATE],[SHIP_DATE])) AS AVGSHIP_DATE
FROM KMS
GROUP BY ORDER_PRIORITY,SHIP_MODE
ORDER BY [ESTIMATED SHIPPING COST] DESC
```
### Insights
1. Technology drives revenue: Technology products have the highest revenue turnover, while office supplies have significantly lower turnovers.
   - Focus on technology products to maximize sales.
   - Investigate reasons for office supplies underperformance  (e.g., low demand, competition).

2. High-value customers prioritize tech: The most valuable customers are purchasing more technology products, indicating a strong demand in this category.
   - Tailor marketing to high-value customers.
   - The revenue of the bottom 10 customers can be increased if office supplies can be focused on tech-inclined varieties. 

3. Shipping strategy review needed: Despite Express Air being the fastest and most expensive shipping option, its cost doesn't align with the order priority, suggesting a need to reassess the shipping strategy.
   - Reevaluate shipping strategies to balance cost and priority.





