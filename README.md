# DSA PROJECT - 2
# My PowerBi project with DSA Incubator in Data Analysis
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
* I assign a generic gender status to these employees
* I removed the exited employees by unchecking all blank salaries
* Removed departments with NULL department by unchecking NUL
* Removed unrelated rating by unchecking them
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


1. What is the gender distribution in the organization? Distil to regions and departments

### Count of name by gender

•	Visual: Donut chart 

•	Legend: Gender

•	Value: Count of Employee name

### Gender by Location

•	Visual: Stacked Column Chart 

•	X-Axis: Location

•	Legend: Gender

•	Y-Axis: Count of Employee name

### Count of name by department and gender

•	Visual: Stacked Bar Chart 

•	X-Axis: Department

•	Legend: Gender

•	Y-Axis: Count of Employee name


### To create a measure for % Female:
% Female = 
DIVIDE(
    CALCULATE(COUNT(EmployeeData[Name]), EmployeeData[Gender] = "Female"),
    COUNT(EmployeeData[Name])
)*100


2. Show insights on ratings based on gender

    A. Colunm Chart: Count of name by rating and gender
     
•	X-Axis: Rating

•	Legend: Gender

•	Y-Axis: Count of Employee name


 
 B. Stacked Column Chart: % GT count of location by Rating and gender
    
•	X-Axis: Rating

•	Legend: Gender

•	Y-Axis:  % GT count of location


C. Matrix Table: Rating

•	Field: Rating


3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management

  Gender Pay Gap % = 
VAR FemaleAvg = CALCULATE([Avg Salary], EmployeeData[Gender] = "Female")
VAR MaleAvg = CALCULATE([Avg Salary], EmployeeData[Gender] = "Male")
RETURN
DIVIDE(MaleAvg - FemaleAvg, MaleAvg) 

Avg Salary = AVERAGE(EmployeeData[Salary]) 


A. Average Salary by Gender 

•	X-Axis: Gender

•	Legend: Gender

•	Y-Axis:  Avg salary


B. Gender Pay Gap % depaertment and gender

•	X-Axis: Department

•	Legend: Gender

•	Y-Axis:  Gender pay gap %


C. Matrix Table: Average Salary by Gender and Department

•	Rows: Department 

•	Columns: Gender

•	Values: Avg Salary



 
4. A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000
● Does Palmoria meet this requirement?
● Show the pay distribution of employees grouped by a band of $10,000. For example:
● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, etc.?
● Also visualize this by regions

Salary Compliance = 
IF(
    EmployeeData[Department] = "Manufacturing" && EmployeeData[Salary] < 90000,
    "Below Minimum",
    "Compliant"
)


A. Bar Chart: Count of salary compliance by location and gender

•	Y-Axis: Location

•	Legend: Gender

•	X-Axis: Count of salary compliance


B. Column Chart: Count of gender by salary compliance and gender

•	Y-Axis: Salary compliance

•	Legend: Gender

•	X-Axis: Count of gender


C. Table: Nane and department

•	Columns: Name, department, Gender, Sum of Salary


D. Field: Department

•	Columns: Department


E. % Female

% Female = 
DIVIDE(
    CALCULATE(COUNT(EmployeeData[Name]), EmployeeData[Gender] = "Female"),
    COUNT(EmployeeData[Name])
)*100



## Case Questions
6. Mr Gamma thought to himself that since you were already working on the employee data, you could help out with allocating the annual bonus pay to employees based on the
performance rating. He handed you another data set that contains rules for making bonus payments and asked you to:
● Calculate the amount to be paid as a bonus to individual employees

Total Bonus Paid = SUM('EmployeeData'[Bonus Amount])


● Calculate the total amount to be paid to individual employees (salary inclusive of bonus)

Total Pay = 
'EmployeeData'[Salary] + 'EmployeeData'[Bonus Amount]

● Total amount to be paid out per region and company-wide

Total Bonus by Region = 
CALCULATE(SUM('EmployeeData'[Bonus Amount]), ALLEXCEPT('EmployeeData', 'EmployeeData'[Location]))



# Analysis

![Dashboard 1](https://github.com/user-attachments/assets/31d76444-4c2c-4a94-9dc1-9b92f5a3072f)
![Dashboard 2](https://github.com/user-attachments/assets/89d39dfb-f8e2-4719-bc98-96c42448ae92)
![PowerBi Dashboard](https://github.com/user-attachments/assets/ceca10cf-2663-4191-9bae-08a8deb15e93)


