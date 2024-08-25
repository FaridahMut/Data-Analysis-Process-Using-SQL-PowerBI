# Data-Analysis of a Bike Share dataset

## Introduction
The project aims to develop a Dashboard for T-Bike Share that displays the key performance metrics for informed decision-making.
The dataset is provided and we need to provide recommendations on raising prices for the next year.

The questions that need to be addressed are;
1. An hourly revenue analysis
2. Profit and Revenue Trends
3. Seasonal Revenue
4. Rider Demographics

## Data Analysis Workflow
1. Create a Database
2. Develop SQL Queries
3. Connect PowerBI to DataBase
4. Build a Dashboard in PowerBI
5. Answer the Analysis Questions

### Create a database
* The first step is to create a database and import the data from the three tables: bike_share_yr_0, bike_share_yr_0, and cost_table.
  
### Develop SQL Queries
Append the bike data from 2021 and 2022 using a *UNION so I could work with it in one table. **NOTE:** **Union all**, puts all the data including duplicated values in the tables.
* I then join the data in the tables with the cost_table using a **left join** to join the years.
* Select the columns that are relevant for the analysis
* Add other calculations like **revenue**=riders x price and **profit**=riders x price-COGSx riders
```SQL
with cte as (
SELECT *
FROM bike_share_yr_0
UNION
SELECT *
FROM bike_share_yr_1)

SELECT 
dteday,
hr,
season,weekday
cte.yr,
rider_type,
riders,
price, 
COGS,
riders*price AS revenue,
riders*price - COGS*riders as profit
FROM cte
left join cost_table
on cte.yr= cost_table.yr
```
### Connect PowerBI to DataBase
* I then Opened PowerBI and connected to the database I had created and copied the SQL queries and loaded the data
  
### Build a Dashboard in PowerBI
* After importing the data, I began to build the dashboard.
* I divided the dashboard into three sections with some cards
* Added a table to **analysis the hourly revenue**
  * Transformed the hr to a whole number and applier a filter to display values within working hours i.e, 0700hrs to 2100 hrs
* A visualization of the sum of revenue vs Season using a bar chart.
* A combined chart to display the sum of revenue, and riders per month.
* A doughurt chart to display the sum of the rider types i., registered vs casual riders

<img width="589" alt="image" src="https://github.com/FaridahMut/Data-Analysis-Process-Using-SQL-PowerBI/assets/160776452/d02c31b9-06dc-4790-9b72-a37e96d281eb">

## Analysis Questions and Recommendations
Comparing the data from the two years that is the revenue, profit and the number of riders, it can be seen that there was an increase in these values as the average price was increased from 3.99$ to 4.99$. The number of riders increased by 64% despite the price increase, i.e., a 25% increase.

<img width="402" alt="image" src="https://github.com/FaridahMut/Data-Analysis-Process-Using-SQL-PowerBI/assets/160776452/ff51eab9-b533-47db-bf58-3e1eb329fe22">

Calculating the price elasticity brings 2.56, which means an increase in price by 2,5 reduces the demand by 2.56. However, in our case, the demand increased.

## Recommendation
1. Price Setting
The company to do a conservative price increase between 10-15% to test the market response without risking a significant loss of customers.
  1. First price option set at 10% i.e, 10% of $4.99 gives $5.49
  2. Second price option is set at 15% i.e., 15% of $4.99 gives $5.74
2. A Strategy
   * The company to **monitor and adjust**. Should be prepared to implement the new prices and ready to adjust them based on the customer feedback and the sales data.
   * **Segment the prices**. The company can consider offering two prices for their customer types i.e., the casual and the registered riders
   * **A market analysis**. To conduct a market analysis to understand their customers, know their satisfaction levels, potential competitors, where they can improve and the economic environment.
  



   
