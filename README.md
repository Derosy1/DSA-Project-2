# DSA-Project 2
My PowerBi project with DSA Incubator in Data Analysis
# Project Overview: Gender Equality & Compensation Analysis for Palmoria Group
The Palmoria Group, a manufacturing company in Nigeria, is facing reputational damage due to reported gender inequality across its three operational regions. To address this, the CEO has engaged an HR Analytics expert to analyze the company's employee data, focusing on gender distribution, performance ratings, salary structures, and compliance with the newly mandated $90,000 minimum wage. The project involves cleaning the dataset, identifying gender disparities by region and department, detecting gender-based pay gaps, visualizing salary bands, and calculating performance-based bonuses. The goal is to generate actionable insights that will help management promote fairness, improve gender equality, ensure regulatory compliance, and restore public trust ahead of planned business expansion.
# Data Source
The primary data source for this project is the internal HR dataset provided by Palmoria Group. This dataset contains employee-level information including:

Employee demographics (e.g., gender, region, department)

Salary details

Performance ratings

Employment status (active or exited)

Additionally, a bonus rule dataset was provided, outlining how annual bonuses should be allocated based on employee performance ratings. These datasets are assumed to be extracted from Palmoria’s internal HR Information System (HRIS), such as SAP SuccessFactors, BambooHR, or a custom enterprise solution.
# Tools Used
Power BI Desktop - [Download Here](https://www.bing.com/search?q=powerbi+link&cvid=9eb952e08617473f8456dd58f6fb4a2a&gs_lcrp=EgRlZGdlKgYIABBFGDkyBggAEEUYOTIGCAEQABhAMgYIAhAAGEAyBggDEAAYQDIGCAQQABhAMgYIBRAAGEAyBggGEAAYQDIGCAcQABhAMgYICBAAGEDSAQg1NDk5ajBqNKgCCLACAQ&FORM=ANAB01&PC=U531) - For data import cleaning, analysis, and visualization 

Power Query Editor (within Power BI) – For data transformation and cleaning

DAX (Data Analysis Expressions) – For creating calculated columns, measures, and KPIs

# Data Cleaning/Preparation 
* I loaded the palmoria group bonus table and employee data 
* I removed the exited employees by unchecking all blank salaries
* Removed employees with NULL department by unchecking NUL
* Removed ubrelated rating by unchecking them
* Replaced missing genders byfilling ramdomely
* Ensure correct data type
* checked data quality all = 100%
* Rename fact tanle as employee table

Observed the supplimentary table is yet to be uploaded which is the rating table, thus i uploaded it from get data

# Unpivot Values
I highlighted all the rating columns, right clicked, unpivot all columns.
Rename from attribute table to rating table and from vales table to bonus table

# Combining the main table and supplimentary table
I selected the main table, from Home i merged queries
Using department as the merging columns
Selected left outer join
A bonus table was created, clicked to expand and unchecked others, selected bonus, ok
Close & Apply

# Exploratory Data Analysis




# Analysis
  
