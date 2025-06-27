# Kultra-Mega-Stores-Inventory-PROJECT
This is my one of Case Study (Project) to work on as a Data Analyst during Incubator Hub Program

# $${\color{blue}INTRODUCTION}$$
Kultra Mega Stores (KMS) is a Lagos-based retail company specializing in office supplies and furniture. The company serves a diverse customer base comprising individual consumers, small businesses (retail), and large corporate clients (wholesale) throughout Lagos, Nigeria. As part of KMS’s expansion and performance tracking efforts in the Abuja division, I have been engaged as a Business Intelligence Analyst to support data-driven decision-making. My role involves analyzing historical order data provided, which spans the period from 2009 to 2012. Using SQL skills, I will examine this dataset to uncover key business insights. These insights aim to support the Abuja division’s strategy in areas such as customer segmentation, sales performance, product demand, and operational efficiency. The analysis will be guided by some given case scenarios, and the final output will include actionable findings, visualizations, and recommendations based on trends and patterns observed in the data.

# $${\color{blue}OBJECTIVE \space \space STATEMENT}$$

The objective of this analysis is to evaluate historical sales and order data for Kultra Mega Stores (KMS) with the goal of identifying key business insights that can inform strategic decisions for the Abuja division. Specifically, the analysis aims to:
- Understand sales trends and performance across customer segments (individual, retail, and wholesale)
- Identify high-performing products and underperforming categories
- Analyze customer behavior and purchasing patterns
- Uncover operational inefficiencies or opportunities for process improvement
- Provide data-driven recommendations to support the Abuja division’s business growth

This will be achieved through structured SQL queries and data modeling techniques, as acquired during the DSA Class, applied to the (KMS)  2009–2012 order dataset.

# $${\color{blue}PROJECT \space METHODOLOGY}$$

The methodology for this project follows a structured approach to ensure accurate, actionable, and insightful analysis of Kultra Mega Stores’ (KMS) order data from 2009 to 2012. The steps below outline the process used to address both case scenarios shared by the Business Manager, using SQL and business analysis techniques:

  1.  ## **$${\color{Lightblue}Business \space Context}$$**
      - **Company:** Kultra Mega Stores (KMS)
      - **Division of Interest:** Abuja
      - **Products:** Office supplies and furniture
      - **Customer Segments:** Individual, Retail (small businesses), Wholesale (large corporate clients)
      - **Goal:** Provide key insights based on sales data (2009–2012) to support decision-making for the Abuja branch.

  2. ## **$${\color{Lightblue}Analysis \space \space Objectives \space Case \space Scenario \space I}$$**
     - Which product category had the highest sales?

     - What are the Top 3 and Bottom 3 regions in terms of sales?

     - What were the total sales of appliances in Ontario?

     - Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers

     - KMS incurred the most shipping cost using which shipping method?

  3. ## **$${\color{Lightblue}Case \space Scenario \space II}$$**
     - Who are the most valuable customers, and what products or services do they typically purchase?

     - Which small business customer had the highest sales?

     - Which Corporate Customer placed the most number of orders in 2009 – 2012?

     - Which consumer customer was the most profitable one?

     - Which customer returned items, and what segment do they belong to?

     - If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer.
    
  4. ## **$${\color{Lightblue}Data \space Preparation(ETL \space Process)}$$**
 - **Extraction**
   - Extraction was done by using excel tools and the file was saved in Csv format in other to be loaded in to SQL Properly

 - **Transformation** 
(Data cleaning and Structured):
     - Removal of duplicates

     - Standardize column names

     - Data types are appropriate Ensured (e.g., dates, numeric)
 - **Loading**
     - Cleaned data was loaded into SQL Database

  5. ## **$${\color{Lightblue}SQL \space Queries \space Design \space to \space solve \space the \space given \space Case \space Scenarios}$$**
  ### **Case Scenario 1** *Approach & SQL Logic*

1. $${\color{red}Which \space product \space category \space had \space the \space highest \space sales?}$$

Below are the Queries for the Question;
```` SQL
SELECT TOP 1 product_category, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
GROUP BY product_category
ORDER BY Total_Sales DESC
````
RESULT

| product_category | Total_Sales |
| --- | --- |
| *Technology* | *5,984,248.17547321* |

$${\color{green}The \space result \space above \space gives \space the \space top-selling \space product \space category \space by \space total \space sales \space value}$$

2. $${\color{red}What \space are \space the \space Top \space 3 \space and \space Bottom \space 3 \space regions \space in \space terms \space of \space sales?}$$

TOP 3 Queries;
```` SQL
SELECT TOP 3 region, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
GROUP BY region
ORDER BY Total_Sales DESC
````
RESULT

| Region | Total_Sales |
| --- | --- |
| *West* |	*3,597,549.269871* |
| *Ontario* |	*3,063,212.47638369* |
| *Prarie* |	*2,837,304.60503292* |

BOTTOM 3 Queries;
```` SQL
SELECT TOP 3 region, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
GROUP BY region
ORDER BY Total_Sales ASC
````
RESULT

| Region | Total_Sales |
| --- | --- |
| *Nunavut* |	*116,376.48383522* |
| *Northwest Territories* |	*800,847.330903053* |
| *Yukon* |	*975,867.375723362* |

$${\color{green}The \space result \space above \space Shows \space the \space highest \space and \space lowest \space performing \space regions}$$

3. $${\color{red}What \space were \space the \space total \space sales \space of \space appliances \space in \space Ontario?}$$

Below are the Queries for the Question;
```` SQL
SELECT Region, SUM(sales) as Total_Appliances
FROM [Kultra Mega Store]
WHERE Region = 'ontario'
GROUP BY Region
ORDER BY Total_Appliances ASC
````
RESULT

| Region | Total_Appliances |
| --- | --- |
| *Ontario* | *3,063,212.47638369* |

$${\color{green}The \space result \space above \space gives \space Targeted \space insight \space into \space Ontario's \space appliances \space performance}$$

4. $${\color{red}Advise \space KMS \space on \space what \space to \space do \space to \space increase \space the \space revenue \space from \space the \space bottom \space 10 \space customers \space Recommendations \space based \space on \space analysis}$$

Below are the Queries for the Question;
```` SQL
SELECT TOP 10 Customer_name, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
GROUP BY Customer_name
ORDER BY Total_Sales ASC
````
RESULT

| Customer_name | Total_Sales |
| --- | --- |
| *Jeremy Farry* |	*85.7200021743774* |
| *Natalie DeCherney* |	*125.900001525879* |
| *Nicole Fjeld* |	*153.030006408691* |
| *Katrina Edelman* |	*180.760005950928* |
| *Dorothy Dickinson* |	*198.080001831055* |
| *Christine Kargatis* |	*293.2200050354* |
| *Eric Murdock* |	*343.32799911499* |
| *Chris McAfee* |	*350.180004119873* |
| *Rick Huthwaite* |	*415.819980621338* |
| *Mark Hamilton* |	*450.990005493164* |

✅  $${\color{green}Base \space on \space the \space analysis, \space The \space customers \space above \space contribute \space very\space little \space to \space total \space sales \space volume.}$$ $${\color{green}and \space My \space Advise \space for \space KMS \space Organisation, \space in \space other \space to \space increase \space the \space revenue \space from \space this \space bottom \space 10 \space customers \space are \space to;}$$
   - $${\color{green}Analyze \space purchasing \space behavior \space of \space these \space 10 \space customers;}$$
   - $${\color{green}Which \space products \space do \space they \space buy \space (if \space any)?}$$
   - $${\color{green}Are \space their \space orders \space in \space frequent \space or \space low \space in \space value?}$$


     📌 $${\color{green}And \space my \space Recommendations \space are \space to;}$$
   - $${\color{green}Offer \space them \space personalized \space discounts \space or \space targeted \space email \space follow-ups.}$$
   - $${\color{green}Analyze \space their \space order \space history \space and \space recommend \space frequently \space bought \space items.}$$
   - $${\color{green}Bundle \space offers \space to \space encourage \space higher-value \space purchases.}$$
   - $${\color{green}Survey \space to \space find \space out \space if \space they \space faced \space service/product \space issues.}$$


5. $${\color{red}KMS \space incurred \space the \space most \space shipping \space cost \space using \space which \space shipping \space method?}$$

Below are the Queries for the Question;
```` SQL
SELECT TOP 1 ship_mode, SUM(Shipping_Cost) as Total_Shipping_Cost
FROM [Kultra Mega Store]
GROUP BY Ship_mode
ORDER BY Total_Shipping_Cost DESC
````
RESULT

| Ship_mode | Total_Shipping_Cost |
| --- | --- |
| *Delivery Truck* | *51,971.9397373199* |

✅  $${\color{green}Base \space on \space the \space abve \space analysis, \space The \space Shipping \space mode \space that \space costs \space most \space is \space DELIVERY-TRUCK}$$ 

📌  $${\color{green}and \space I \space Suggest \space if \space the \space company \space can \space renegotiate \space with \space couriers \space or \space shift \space to \space more \space cost-effective \space options}$$

### **Case Scenario 2**
6. $${\color{red}Who \space are \space the \space most \space valuable \space customers, \space and \space what \space products \space or \space services \space do \space they \space typically \space purchase?}$$

Below are the Queries for the most valuable customers by total sales;
``` SQL
SELECT TOP 5 Customer_Name, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
GROUP BY Customer_Name
ORDER BY Total_Sales DESC
```
RESULT

| Customer_Name | Total_Sales |
| --- | --- |
| *Emily Phan* | *117,124.435264587* |
| *Deborah Brumfield* | *97,433.1346206665* |
| *Roy Skaria* | 92,542.1531906128* |
| *Sylvia Foulston* | *88,875.7581214905* |
| *Grant Carroll* | *88,417.0006103516* |

Below are the Queries for the Product/Services they purchase;
```` SQL
SELECT Customer_Name, Product_Category, SUM(sales) as Category_Sales
FROM [Kultra Mega Store]
WHERE Customer_Name	IN (
	SELECT TOP 5 Customer_Name
	FROM [Kultra Mega Store]
	GROUP BY Customer_Name
	ORDER BY SUM(sales) DESC
````

RESULT

| Customer_Name |	Product_Category | Category_Sales |
| :--- | :---: | ---: |
| Deborah Brumfield |	Technology | 76,795.7947387695 |
| Deborah Brumfield |	Furniture |	12,809.6198730469 |
| Deborah Brumfield |	Office Supplies |	7,827.7200088501 |
| Emily Phan |	Technology |	110,481.965362549 |
| Emily Phan |	Furniture |	4,011.64990234375 |
| Emily Phan |	Office Supplies |	2,630.81999969482 |
| Grant Carroll |	Office Supplies |	50,837.2688293457 |
| Grant Carroll |	Furniture |	29,826.8493652344 |
| Grant Carroll |	Technology |	7,752.88241577148 |
| Roy Skaria |	Furniture |	50,177.2399902344 |
| Roy Skaria |	Technology |	30,349.3932495117 |
| Roy Skaria |	Office Supplies |	12,015.5199508667 |
| Sylvia Foulston |	Furniture |	48,173.3799133301 |
| Sylvia Foulston |	Technology |	29,669.0381469727 |
| Sylvia Foulston |	Office Supplies |	11,033.3400611877 |

✅  $${\color{green}Above \space Result \space is \space the \space Top \space customers \space generate \space the \space majority \space of \space revenue \space and \space usually \space purchase \space from \space specific \space categories.}$$

📌 $${\color{green}And \space I \space Recommended \space to;}$$
- $${\color{green}Offer \space them \space loyalty \space rewards, \space custom \space offers, \space and \space premium \space services}$$
- $${\color{green}Use \space their \space purchase \space behavior \space to \space design \space future \space promotions}$$


7. $${\color{red}Which \space small \space business \space customer \space had \space the \space highest \space sales?}$$

Below are the Queries for small business customer that has the highest sales 
```` SQL
SELECT TOP 1 Customer_Name, SUM(sales) as Total_Sales
FROM [Kultra Mega Store]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY Total_Sales DESC
````
RESULT

| Customer_Name | Total_Sales |
| --- | --- |
| *Dennis Kane* | *75,967.5932159424 |
