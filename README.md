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
 '''  SELECT * FROM KMS ''''

3. HIGHEST SALES BY PRODECT CATEGORY

'''
 SELECT SALES, Product_Category FROM KMS
ORDER BY SALES DESC

''''



