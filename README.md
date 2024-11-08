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

[pivot table](#pivot-table)

[Data Analysis](#Data-Analysis)

[for sales data](for-sales-data)

[for customer data](#for-customer-data)

[Data Visualization](#Data-Visualization)

[My Results](#My-results)

[for Sales data 2](#for-Sales-data-2)

[for Customer data 2](#for-Customer-data-2)

[Recommendations](#Recommendations)

[for sales data 3](#for-sales-data-3)

[for customer data 3](#for-customer-data-3)

### Project overview for sales data
---
This project focuses on analyzing sales data to uncover trends,product performances and customer insights. it involves data collection, cleaning and analyzing using tools like excel,SQL and power BI. The goal is to provide actionable recommendations to enhance sales strategies and improve overall performance 

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
 6. SubscriptionEnd: The end date of the subscription 
 7. Canceled: The subscription status
 8. Revenue: The revenue for the subscription 
 9. Subscriptions duration: The period the subscriptions last for

### Basic Statistics of Sales data
---
Total sales: 2 million

Total number of transactions: 9,921

Number of product: 6

### Basic Statistics of Customer data
---
Sum of revenue: 68 million 

Number of renewed subscription: 18,612

Number of cancelled subscription: 15,175

Total number of customers: 33,787

Number of subscription type: 3

### Data source
---
The data sources for this analysis are '' sales data .csv'' and '' customers data .csv'', which can be gotten from online source like kaggle

### Tools used 
---
- Microsoft excel

for data cleaning 

for data analysis 

for data visualization 

- SQL- structured query language 

for querying data

- PowerBI 

for data visualization 
- Github 

for portfolio building 

### Data cleaning and preparation 
---
data loading and inspection 

handling of missing variables 

data cleaning and formatting 

### Exploratory data analysis 
---
### sales data
1. retrieve the total sales for each product category 
2. find the number of sales transactions in each region
3. find the highest selling product by total sales value
4. Calculate total revenue per product 
5. find the 5 top customers by total purchase amount
6. calculate the percentage of total sales contributed by each region
7. identify product with no sales in the last quarter 

### customer data
1. retrieve the total number of customer from each region
2. find the most popular subscription type by the number of customers
3. find the customer who cancelled their subscription within 6 month
4. calculate the average subscription duration by all customers 
5. find customer with subscription longer than 12 month
6. calculate total revenue by subscription type
7. find the top 3 region by subscription cancellation 
8. find the total number of active and cancelled subscriptions

### pivot table
pivot table is use to summarize,analyze and present large set of data quickly and efficiently

- summary of my customer data with pivot table

![pivottttt](https://github.com/user-attachments/assets/ef8f1188-36e5-439b-af92-e3d5cfb3cf26)

- summary of my sales data with pivot table

![pivot 22](https://github.com/user-attachments/assets/d59c4a1c-0765-4298-bacc-d64ca9f982f5)



### Data Analysis 
---

### for sales data

create table
![sql 1](https://github.com/user-attachments/assets/2cd53e9d-1de7-4c9c-a2df-9cc9086bc1d7)


- Total sales by product category : Retrieve the total sales for each product category

  ```sql
  select product,
  sum(quantity*unitprice)as totalsales
  from table
  group by product
  order by totalsales
  ```
  ![sql 2](https://github.com/user-attachments/assets/a08327c5-cb8f-4d17-8827-79e6fe312f91)




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
  select top 5 customerid,
  sum(quantity*unitprice) as totalpurchaseamount
  from table
  group by customerid
  order by totalpurchaseamount
  ```
  ![sql 3](https://github.com/user-attachments/assets/1fcf1068-05cc-413c-8198-6870f7de90b4)

  
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
   orderdate<getdate())
  ```
  ![sql 4](https://github.com/user-attachments/assets/dc5a566c-d344-44c3-bd38-c03c7a07b2f2)


### for customer data

create table
![sql table](https://github.com/user-attachments/assets/b89ad94b-d8cd-4bbb-8670-1db1b42315e5)


- Total customer by region: retrieve the total number of customer from each region

  ```sql
  select region,count(customerid) as totalcustomers
  from table
  group by region
  order by totalcustomers asc
  ```
  ![sql iii](https://github.com/user-attachments/assets/0e2c96b4-7ff3-40ac-8bf6-78759382267f)

  
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
  ![sql ii](https://github.com/user-attachments/assets/e976b779-c1f9-45fe-b42d-21dd38efe40b)


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
  ![lastt](https://github.com/user-attachments/assets/533c4197-3bf6-4b64-ba36-9b8f7f50db16)


### DATA VISUALIZATION
---
Data visualization of customer data
![new 2 visualization cust](https://github.com/user-attachments/assets/767e654d-a258-422d-8276-3a95465e1c51)



map visualization of customer data
![CUSTOMER DATA VISUALLLL](https://github.com/user-attachments/assets/cfde7bf4-d102-480f-85de-f27760e3091d)

Data visualization of sales data
![sales data 2222](https://github.com/user-attachments/assets/fd967c31-cc16-4c55-a31c-269fb2cb2b7a)



map visualization of sales data
![MAP SALES DATA](https://github.com/user-attachments/assets/054046e9-e0e2-45e1-b54e-2ab3787bffb2)

### My Results 
---
### for sales data 2
The sales data analysis highlights key insights :total sales for gloves were 296,900.00, hats at 316,295.00,jackets at 208,230.00,shirt at 485,600.00, and sock at 180,785.00. Shoes led with impressive sales of 613,380.00, indicating a strong demand.

Regionally, the east achieved 485,925.00,the north 387,000.00, and west 300,345.00,but the south stood out with 927,820.00 in sales, making it a vital market.

Focusing on shoe products and tailoring strategies for the south could enhance overall sales and growth 

### for customer data 2
The subscription analysis shows a total of 33,787 subscription with the basic plan being the most favored at 16,921 subscriptions. Renewals totaled 18,612, with basic plan having a high renewal rate of 70% while both premium and standard plans lagged behind at 40%.Cancellations reached 15,715, with the basic plan seeing 29.9% cancellations compared to the mych higher rates for premium and standard plans, which were around 59%. 

This indicates that while the Basic plan is well-received, there are significant concerns regarding the value of the premium and standard options,suggesting a need for improvement in those areas.

### Recommendations 
### for sales data 3
Recommendation for high performing products, since shoe are the best selling product, consider expanding the shoe line with new styles or promotions to capitalize on this demand. highlighting shoes in marketing campaigns can attract more customers. target the south region,with the south showing the highest sales,tailor marketing strategies specifically for this region.consider localized promotions, partnerships with local influencers, or events to engage customer more effectively.Ensure that inventory levels for shoes and popular items in the south are optimized to meet demand. This could involve increasing stock levels or introducing exclusive items for this market.

for the low performing products create targeted promotions or discounts for thse products to increase visibility and attract customers,consider bundling them with popular items to encourage sales. showcase these items prominently in-store or online to draw attention to them,highlight their unique features or benefit to entice customer to make a purchase.
engage with customers through social media or email marketing to educate them about the benefit of these products. consider introducing new design or variations of these products to generate renewed interest, customer feedback can provide valuable insights for product improvements.

### for customer data 3
Improve premiuk and standard plans with better features and support, conduct survey to gather feedback from cancelled subscriptions.
Offer promotional discounts to attract new subscribers,clearly communicate the benefits of premium and standard plans.
introduce a loyalty program fir long term subscribers , probide free trail periods for premium and standard plans.
Continuously monitor trends and adjust strategies accordingly 
