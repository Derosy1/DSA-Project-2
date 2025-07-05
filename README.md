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


Required:
● Generally, there are two genders in the organization. However, some employees refused to disclose their gender. You would need to assign a generic gender status to these employees
● Some employees are without a salary because they are no longer with the company. You will need to take those employees out
● Lastly, some departments are indicated as “NULL”. These departments would also need to be taken out.
Pointers from Mr Gamma
1. What is the gender distribution in the organization? Distil to regions and departments
2. Show insights on ratings based on gender
3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management
4. A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000
● Does Palmoria meet this requirement?
● Show the pay distribution of employees grouped by a band of $10,000. For example:
● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, etc.?
● Also visualize this by regions
Case Questions
5. Mr Gamma thought to himself that since you were already working on the employee data, you could help out with allocating the annual bonus pay to employees based on the
performance rating. He handed you another data set that contains rules for making bonus payments and asked you to:
● Calculate the amount to be paid as a bonus to individual employees
● Calculate the total amount to be paid to individual employees (salary inclusive of bonus)
● Total amount to be paid out per region and company-wide



# Analysis
![Power BI 1](https://github.com/user-attachments/assets/7087d997-6741-4c08-ae51-b0c641893266)![Power Bi 2](https://github.com/user-attachments/assets/e70a0df2-33d5-4f4d-bed5-82f661a94f9b)


  ![Power BI 3](https://github.com/user-attachments/assets/64019612-b646-4702-9ec9-19df8a63aef6)![Power BI 4](https://github.com/user-attachments/assets/ee02acfb-d301-4254-9868-959f42b336e1)


![PowerBi Dashboard](https://github.com/user-attachments/assets/fa80a57c-3c7f-40b7-9d97-2f7266d9955a)
