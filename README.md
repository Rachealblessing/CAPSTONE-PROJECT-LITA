# CAPSTONE-PROJECT-LITA

### project title: Sales Transaction Data and Customer Subscription Data
---
[project overview for sales data](#project-overview-for-sales-data)

[project overview for customer data](#project-overview-for-customer-data)

[Data field for sales data](#Data-field-for-sales-data)

[Data field for customers data](#Data-field-for-customers-data)

[Data source](#Data-source)

[Tools used](#Tools-used)

[Data cleaning and preparation](#Data-cleaning-and-preparation)

[Explanatory data analysis](#Explabatory-data-analysis)

[Sales data](#Sales-data)

[Customer data](#Customer-data)

[Data Analysis](#Data-Analysis)

[Data Visualization](#Data-Visualization)

[My Result](#My-result)

[Sales data](#Sales-data)

[Customer data](#Customer-data)

### Project overview for sales data
---
This project focuses on analyzing sales data to uncover trends,product performances and customer insights. it involves data collection, cleaning and analyzing using tools like excel,SQL and power BI. The goal is to provide actionable recommendations to enhance sake strategies and improve overall performance 

### Project overview for customer data
---
This contain data related to customer subscription including subscription plans, user demographics and retention metrics. The goal is to analyze trends in subscription usage and identify factors affecting customer retention 

### Data field for sales data
---
 1. OrderID: Unique order identifier
 2. CustomerID: Unique customer identifier 
 3. Product: product purchase by customer 
 4. Region: Order location
 5. Orderdate: Date of the order
 6. Quantity: Units purchased 
 7. Unit price: price per unit
 8. Total sales:Total value ( unit price * quantity )

### Data field for customer data
---
 1. CustomerID: unique customer identifier
 2. Customer name: The namd of the customer that purchased product 
 3. Region: customer location 
 4. SubscriptionType: The type of subscription made by customer 
 5. SubscriptionStart: The start date of the subscription 
 6. SubscriptionEnd: The ebd date of the subscription 
 7. Canceled: The subscription status
 8. Revenue: The revenue for the subscription 
 9. Subscriptions duration: The period the subscriptions last for

### Data source
---
The data sources for this analysis are '' sales data .csv'' and '' customers data .csv'', which can be gotten from online source like kaggle

### Tools used 
---
.Microsoft excel
for data cleaning 
for data analysis 
for data visualization 

.SQL- structured query language 
for querying data

.PowerBI 
for data visualization 
.Github 
for portfolio building 

### Data cleaning and preparation 
---
data loading and inspection 

handling of missing variables 

data cleaning and formatting 

### Exploratory data analysis 
---
### For sales data
1. retrieve the total sales for each product category 
2. find the number of sales transactions in each region
3. find the highest selling product by total sales value
4. Calculate total revenue per product 
5. find the 5 top customers by total purchase amount
6. calculate the percentage of total sales contributed by each region
7. identify product with no sales in the last quarter 

### For customer data
1. retrieve the total number of customer from each region
2. find the most popular subscription type by the number of customers
3. find the customer who cancelled their subscription within 6 month
4. calculate the average subscription duration by all customers 
5. find customer with subscription longer than 12 month
6. calculate total revenue by subscription type
7. find the top 3 region by subscription cancellation 
8. find the total number of active and cancelled subscriptions 

### Data Analysis 
---

### for sales data

- Total sales by product category : Retrieve the total sales for each product category

  ```sql
  select product,
  sum(quantity*unitprice)as totalsales
  from table
  group by product
  order by totalsales
  ```

- Sales transactions by region: find the number of sales transactions in each region

  ```sql
  select region, count(orderid) as transaction_count
  from table
  group by region
  order by transaction_count desc
  ```

- highest selling product: find the highest selling product by sales value

  ```sql
  select top 1 product,
  sum(quantity*unitprice) as totalsales
  from table
  group by product
  ```
  

- Total revenue per product: Calculate total revenue per product

  ```sql
  select orderid,sum(quantity*unitprice) as totalrevenue
  from table
  group by orderid
  order by totalrevenue desc
  ```

- Top 5 customer by purchase Amount: find the 5 top customer by total purchase amount

  ```sql
  select top 5 customerid '
  sum(quantity*unitprice) as totalpurchaseamount
  from table
  group by customerid
  order by totalpurchaseamount
  ```
  
- sales contribution by region:Calculate the percentage of total sales contributed by each region

  ```sql
  select region,
  sum(quantity*unitprice) as totalsales,
  sum(quantity*unitprice)*100.0/(select
  sum(quantity*unitprice)
  from table as percentageoftotalsales
  from table
  group by region
  order by percentageoftotalsales
  ```
  
- Products with no sales in last quarter: identify products with no sales in the last quarter

  ```sql
  select distinct product
  from table
  where product not in(
  select product
  from table
  where orderdate>=
  dateadd(quarter,-1,getdate()) and
   orderdate<getdatw())
  ```

### for customer data

- Total customer by region: retrieve the total number of customer from each region

  ```sql
  select region,count(customerid) as totalcustomers
  from table
  group by region
  order by totalcustomers asc
  ```
  
- Most popular subscription type: find the most popular subscription type by the number of customers

  ```sql
  select top 1 subscriptiontype,
  count(customerid) as totalcustomer
  from tsble
  group by subscriptiontype
  order by totalcustomers desc
  ```

- Customer who canceled within 6 months: find the customer who canceled their subscription within 6 month

  ```sql
  update table
  set canceled = 1
  where cancelled = true
  update table
  set canceled = 0
  where canceled = false
  select count(customerid) as canceledcustomerin6mnth
  from table
  where cancelled = 1
  and
  subscriptionend>=dateadd(month,-6,getdate())
  ```

- Average subscription duration: calculate the average subscription duration for all customers

  ```sql
  select avg(datediff(day,subscriptionstart,subscriptionend))
  as avg_sub_duration
  from table
  ```
  
- Customer with subscription longer than 12 months: find customer with subscription longer than 12 months

  ```sql
  select count(customerid) as
  sub_12_mnth
  from table
  where
  subscriptionstart<=dateadd(monyh,-12,getdate())
  ```
  
- Total revenue by subscription type: calculate total revenue by subscription type

  ```sql
  select subscriptiontype,
  sum(revenue) as totalrevenue
  from table
  group by subscriptiontype
  ```

- Top 3 region by subscription cancellation: find the top 3 region by subscription cancellation

  ```sql
  select top 3 region,
  count(Customerid) as cancellation_count_top3
  from table
  where cancelled = 1
  group by region
  ```

- Total active and cancelled subscription: find the total number of active and cancelled subscription

  ```sql
  select
  sum(case when canceled = 1 then 1 else 0 end) as totalcanceled,
  sum(case when canceled = 0 then 1 else 0 end) as totalactive
  from table
  ```
