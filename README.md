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

_Total sales by product category : Retrieve the total sales for each product category 

Sales transactions by region: find the number of sales transactions in each region

highest selling product: find the highest selling product by sales value

Total revenue per product: Calculate total revenue per product

Top 5 customer by purchase Amount: find the 5 top customer by total purchase amount

sales contribution by region:Calculate the percentage of total sales contributed by each region

Products with no sales in last quarter: identify products with no sales in the last quarter 

### for customer data

Total customer by region: retrieve the total number of customer from each region 

Most popular subscription type: find the most popular subscription type by the number of customers 

Customer who canceled within 6 months: find the customer who canceled their subscription within 6 month

Average subscription duration: calculate the average subscription duration for all customers 

Customer with subscription longer than 12 months: find customer with subscription longer than 12 months

Total revenue by subscription type: calculate total revenue by subscription type

Top 3 region by subscription cancellation: find the top 3 region by subscription cancellation

Total active and cancelled subscription: find the total number of active and cancelled subscription 
