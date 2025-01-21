# Bike Shop Sales Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Recommended Strategies](#recommended-strategies)
- [Limitations](#limitations)

### Project Overview
---
This data analysis project aim to provide insight into the sales performance of a bike store over the past years. By analyzing various aspects of the sales data.The Stakeholder requirements are( Hourly Revenue Analysis, Profit and Revenue Trends, Seasonal Revenue). We seek to identify trends, make data-driven recommmendations, and gain a deeper understanding of the shop's performance.

![dashboard](https://github.com/user-attachments/assets/5d38b2b1-6f6f-403c-a8c4-5953f5402d65)


### Data Sources

The datasets used for this analysis are "bike_share_yr_0.csv" file, "bike_share_yr_1.csv" file, "cost_table.csv" file, containing detailed information about each sales made by the company.

### Tools 

- Microsoft SQL - Data cleaning,transformations. 
- Power BI - Dax Functions,Creating reports.

### Data Cleaning and Preparation

In the initial data preparation phase, I performed the following tasks:

 1. Data loading and inspection
 2. Handling missing values (But we had none).
 3. Data cleaning and formatting.
 
### Exploratory Data Analysis

EDA invovled exploring the sales data to answer key questions asked by the shareholders, which are:

- The hourly revenue analysis?
- The profit and revenue trends?
- The seasonal revenue?
- The riders demgographics?

### Data Analysis

``` sql
with cte as(
select * from bike_share_yr_0
union all
select * from bike_share_yr_1)

select 
dteday,
season,
a.yr,
weekday,
hr,
rider_type,
riders,
price,
COGS,
riders*price as revenue,
riders*price -COGS as profit
from cte a
left join cost_table b
on a.yr = b.yr
```

### Results and Findings

#### Question 1

25% increase in price

Difference in price = 4.99 – 3.99 = 1

New price – Old Price/ Old Price

4.99 – 3.99/3.99 = 0.25%

#### Question 2

64% increase in demand

Difference in demand = 2,049,576 – 1,243,103 = 806,473

New Riders – Old Riders/Old Riders

2,049,576 – 1,243,103/1,243,103

#### Question 3

Using price elasticity of demand, to deduce that an additional increase in price here will not affect the demand for riders

Price elasticity = increase in demand/increase in price = 64%/25% = 2.56%

2.56% price elasticity, in this case if price increases, demand increases let’s say other factors play crucial roles in this case.

### Recommendations

**Moderate Increase:** the increase in price between 2021 and 2022 is 25%, which is significantly high, a moderate increase should be considered to avoid instances where demand starts plunging. A suggestion of an increase between the range of 10 – 15% could be a safe ground without emerging in significant loss of customers.

#### Assumption of the 10-15% increase in price setting:

•	The current price in 2022 is $4.99, an increase of 10% would be $5.49.

•	An increase of 15% would set the new price at approximately $5.74

### Recommended Strategies

- **Long Term Performance Monitoring:** The KPI trend shows consistent growth in riders and profits over time. Maintain efforts on customer acquisition while monitoring profit margins to ensure sustainability.
- **Segmented Pricing Strategy:** putting into consideration different pricing for casuals as against registered users. Also, since profit peaks on Wednesday and Fridays, plan campaigns or events to further boost sales on these days.
- **Conduct Market Analysis:** conducting in-depth market research to further understand the customers’ satisfaction, the current market competitors, threats and the economic environment at large. This will aid in determining whether to adhere to the suggested recommendations on price increments.
#### Continuous Monitoring and Adjustments through data driven decision:

•	**Expand Data Analysis:** Integrate customer feedback, weather data, and local events into your analysis to further understand revenue patterns.

•	**Real-Time Adjustments:** Use daily performance metrics to adjust marketing efforts dynamically.

### Limitations

 I had no need to remove any values from the dataset, however I added two new columns (revenue and profit), because they are need for the accuracy of my conclusions for this project.

### Author
[Lawan Opeyemi Mercy](https://www.linkedin.com/in/opeyemi-mercy-lawan-81a048276/)
