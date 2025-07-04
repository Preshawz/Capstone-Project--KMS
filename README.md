# Capstone-Project--KMS
This is my  first Data Analysis project under DSA, supervised by the Incubator Hub.


## KMS PROJECT 
### Project Overview
This project aims to ananlyse the data provided by KMS company from 2009 to 2012 and present key insights and findings. 
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
 BE FOCUSED ON TECHNOLOGY AND FURNITURE DESPITE THIER REGION AND SEGMENT

7 ------TOP SHIPPING COST WITH WHAT SHIPPING MODE-----
 ``` sql
 SELECT TOP 1 * FROM 
 (SELECT SHIPPING_COST, SHIP_MODE FROM KMS) AS KMS
 ORDER BY SHIPPING_COST DESC
```
