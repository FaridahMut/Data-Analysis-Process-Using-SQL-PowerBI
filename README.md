# Data-Analysis of a Bike Share dataset

## Introduction
The aim of the project is to develop a Dashboard for T-Bike Share that displays the key performance metrics for an informed decision-making.
The dataset is provided and we need to provide recommendation on raising prices for the next year.

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
* First step is to create a databse and import the data from the threee tables: bike_share_yr_0, bike_share_yr_0, cost_table into it.
  
### Develop SQL Queries
Append the bike data from 2021 and 2022 using a *UNION so I could work with it in one table. **NOTE:** **Union all**, puts all the data including duplicated values in the tables.
* I then join the data in the the tables with the cost_table using a **left join** to join the years.
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
riders*price - COGS as profit
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
  * Transformed the hr to whole number and applier a filter to display values within working hours i.e, 0700hrs to 2100 hrs
*A visualization of the sum of revenue vs Season using a bar chart.
A combined chart to display the sum of revenue, riders per month.
An a doughurt chart to display the sum of the rider types i., registered vs casual riders

<img width="589" alt="image" src="https://github.com/FaridahMut/Data-Analysis-Process-Using-SQL-PowerBI/assets/160776452/d02c31b9-06dc-4790-9b72-a37e96d281eb">

## Analysis Questions and Recommendations

   
