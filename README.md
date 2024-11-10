# LITA-CAPSTONE-PROJECT-2

### Project Title : Customer Segmentation Analysis

### Table of Contents
[Project Overview](#project-overview)

[Dataset](#dataset)

[Data Sources](#data-sources)

[Analytical Tools Used](#analytical-tools-used)

[Data Cleaning](#data-cleaning)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Insights](#insights)

[Recommendation](#recommendation)

### Project Overview
This analysis shows customers behaviour towards a subscription type and patterns in cancellation and renewals. Using MsExcel, SQL and Power BI tools, this analysis informs data driven decision and optimize subscription services

### Dataset
The dataset contains the following columns:
- CustomerID: Unique identifier foe each customer
- Customer Name: Name of each customer who subscribed
- Region: Geographical area where the subscription order was made
- Subscription Type: The subscription plan the customer is subscribed to
- Subscription Start: Start date of the customer's subscription
- Subscription End: End date pf the customer's subscription
- Cancelled: Shows if subscription was cancelled before subscription end
- Revenue: Revenue generated from each subscription that was purchased
- Subscription Duration: Duration of each subscription in days, calculated as Subscription End- Subscription Start

### Data Sources
The primary source of data used here is Customer Data.csv and this is an open source data that can be downloaded from an open source online such as Kaggle or FRED, though this dataset was given by the Incubator Hub(LITA).

### Analytical Tools Used
The analytical tools used were:
- MsExcel- this was used for data cleaning and analysis
- SQL (Structured Query Language)- this was used to query data
- Power BI- this business intelligence tool was used for data visualization

### Data Cleaning
In this phase of my analysis, the following actions were taken:
- Data Loading: Loaded the dataset
- Blank Value Check: Verified the dataset for blank values
- Data Type Conversion: Converted specified columns to text format for consistency
- Data Standardization: Reformatted date columns to YYYY-MM-DD for uniformity
- Duplicate Removal: Removed duplicate rows to ensure unique records. 41,213 duplicates were found and removed left with 33,787 unique values out of 75,000 records that was given in the dataset.

### Exploratory Data Analysis
In this phase of my analysis, the dataset was explored to show:
- Customer behavioural pattern
- Subscription types
- Trend in subscription cancellaions and renewals

### Data Analysis
- Excel Analysis
  - Average Subscription Duration
```Excel
=AVERAGE(I:I)
```
 - Most Popular Subscription Types
```Excel
=COUNTIF(D:D,"basic")
=COUNTIF(D:D,"premium")
=COUNTIF(D:D,"standard")
```
- SQL Queries
  - Total Customer by Region
  ```SQL
  Select Region, count(distinct CustomerID) as total_customers
  from [dbo].[Customer Data_Project]
  Group by Region;
  ```
  - Top Subscription Type by Customer
  ```SQL
  Select top 1 subscriptiontype,
  Count(CustomerID) as total_customers
  from [dbo].[Customer Data_Project]
  Group by subscriptiontype
  Order by total_customers desc;
  ```
  - Average Subscription by Customers
  ```SQL
  Select AVG(datediff(day,subscriptionstart,subscriptionend))as AVG_subscription_duration
  from [dbo].[Customer Data_Project]
  ```
  - Total Revenue by Subscription Type
  ```SQL
  Select subscriptiontype,
  Sum(revenue)as total_revenue
  from [dbo].[Customer Data_Project]
  group by subscriptiontype
  ```
  - Top 3 Region by Subscription Cancellation
  ```SQL
  Select top 3 region,
  Count(CustomerID) as cancellation_count_top3
  from [dbo].[Customer Data_Project]
  where Canceled = 1
  group by Region
  order by cancellation_count_top3
  ```
  - Total Active and Cancelled Subscription
  ```SQL
  Select
  Sum(case when canceled = 1 then 1
  else 0 end) as total_active
  from [dbo].[Customer Data_Project]
  ```
  ### Data Visualization
  ![CUSTOMER PIVOT TABLE](https://github.com/user-attachments/assets/f24ebcf9-6c63-42c4-8d5c-01be147aa905)

  
![CUSTOMER POWER BI](https://github.com/user-attachments/assets/42b6249b-5e4f-4130-b78f-bb2238638627)

### Insights
  
