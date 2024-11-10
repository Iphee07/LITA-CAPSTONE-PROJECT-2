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
My analysis reveals that the Capstone Subscription Service from the 31st of January, 2022 to the 31st of August, 2023 made a total revenue of %67.5 million with a total number of 20 customers cutting across four regions( North, South, East and West). My analysis reveals that the 20 customers are shared within the four regions as we have 5 customers in each of the region.

The revenue analysis revealed that Basic subscription type generated the highest revenue, generating $33.8 million which is 50% of the total revenue while the Premium and Standard subscription types both generated $16.9 million each , making it 25% each of total revenue. Basic subscription type being the most popular among customers was subscribed by 10 customers from two regions (North and East) while the Premium and the standard subscription plans were both subscribed by 5 customers in South and West Region respectively.

The average subscription duration stands at approximately 365 days, indicating a moderate level of customer commitment. I identified a high cancellation rate of 44.9% within the first 6 months of subscription; 9 customers out of 20 cancelled their subscription ( 3 customers for each subscription type), highlighting the need for enhancedcustomer support and engagement during this critical period.

For the region by revenue analysis, all the regions did well as the revenue generated by each were close and highly competitve. East, South, West and North regions making 25.1%, 25.0%, 25.0% and 24.9% of total revenue respectively. East region was the only region with no subscription cancellation while there were subscription cancellations in the other regions.

### Recommendation
- Diversification Strategy

  - Offer Premium and Standard plans in North and East regions to increase Average Revenue per User (ARPU)
  - Promote Basic plan in South and West Regions to attract price-sensitive customers.
- Regional Specialisation

  - Develop targeted marketing campaigns to maintain South's loyalty to Premium subscription plan even if Basic and Standard plans will be offered to the region
  - Develop targeted marketing campaigns to maintain West"s loyalty to Standard subscription plan even if Basic and Premium plans will be introduced to the region
  - Develop targeted marketing campaigns to maintain North's and East's loyalty to Basic plan even if Premium and Standard plans will be offered to the region.
- Retention and Growth

  - Investigate cancellations reasons in North, South and West regions
  - Implement retention strategies to minimize cancellations.
