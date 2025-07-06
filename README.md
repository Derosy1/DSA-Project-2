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

### Gender Distribution (Overall)

•	Visual: Donut chart 

•	Axis: Gender

•	Value: Count of Employee ID

### Gender by Region

•	Visual: Stacked Column Chart 

•	Axis: Region

•	Legend: Gender

•	Value: Count of Employee ID

### Gender by Department

•	Visual: Stacked Bar Chart 

•	Axis: Department

•	Legend: Gender

•	Value: Count of Employee ID

### Matrix Table (Gender by Region and Department)

•	Visual: Matrix

•	Rows: Region

•	Columns: Department

•	Values: Count of Employee ID, with Gender as a slicer or small multiples

### To create a measure for % Female:
Dax

CopyEdit

% Female = 

DIVIDE(

    CALCULATE(COUNT(Employee[Employee ID]), Employee[Gender] = "Female"),
    
    COUNT(Employee[Employee ID])

2. Show insights on ratings based on gender

  
  A. Bar Chart: Count of Ratings by Gender
     
•	Axis: Rating

•	Legend: Gender

•	Value: Count of Employee ID

 Shows how many males vs. females received each rating.
 
 B. Stacked Column Chart: % of Each Gender by Rating
    
•	Axis: Rating

•	Legend: Gender

•	Value: Count of Employees

•	Turn on "Data label" and "Percent of total"

Helps highlight whether a specific gender is more likely to receive a higher/lower rating.

C. Matrix Table: Gender vs Rating

•	Rows: Gender

•	Columns: Rating

•	Values: Count of Employee ID

Offers a compact view of how ratings are distributed across genders.

 D. Average Rating by Gender (if rating is numeric)
 
You can create a DAX measure:

dax

Average Rating = AVERAGE(Employee[Rating])

Then use:
•	Visual: Bar

•	Axis: Gender

•	Value: Average Rating

Shows if one gender receives consistently higher or lower ratings.


3. Analyse the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management

A. Average Salary by Gender (DAX)

dax

Avg Salary = AVERAGE(Employee[Salary])

B. Gender Pay Gap (as % Difference)

dax

Gender Pay Gap % = 

VAR FemaleAvg = CALCULATE([Avg Salary], Employee[Gender] = "Female")

VAR MaleAvg = CALCULATE([Avg Salary], Employee[Gender] = "Male")

RETURN

DIVIDE(MaleAvg - FemaleAvg, MaleAvg)

C. Bar Chart: Average Salary by Gender

•	Axis: Gender

•	Value: Avg Salary

Shows overall pay gap.

D. Matrix Table: Average Salary by Gender + Department/Region

•	Rows: Department or Region

•	Columns: Gender

•	Values: Avg Salary

 Compare salary across gender and function/location.

E. Scatter or Column Chart: Gender Pay Gap by Department

•	Axis: Department

•	Value: Gender Pay Gap %

 Helps identify which departments have the widest gap.

   
4. A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000
● Does Palmoria meet this requirement?
● Show the pay distribution of employees grouped by a band of $10,000. For example:
● How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000, etc.?
● Also visualize this by regions

To filter Non-Compliant Records

dax

NonCompliant Employees = 

FILTER(

    Employee,
    
    Employee[Department] = "Manufacturing" && Employee[Salary] < 90000
    
)

A. Bar Chart: Number of Non-Compliant Employees by Region

•	Axis: Region

•	Values: Count of employees

•	Filter: Salary Compliance = "Below Minimum"

B. Bar/Column Chart: Non-Compliant Count by Gender

•	Show gender distribution of those below $90,000 in Manufacturing.

C. Matrix or Table: Full List of Non-Compliant Employees

•	Columns: Name, Region, Gender, Salary

•	Apply conditional formatting for easy flagging (e.g., red for < $90k)

D. KPI Card: Total Number of Non-Compliant Employees

•	Value:

dax

CopyEdit

NonCompliant Count = 

CALCULATE(COUNT(Employee[Employee ID]), 

    Employee[Department] = "Manufacturing" && Employee[Salary] < 90000
    
)


Case Questions
6. Mr Gamma thought to himself that since you were already working on the employee data, you could help out with allocating the annual bonus pay to employees based on the
performance rating. He handed you another data set that contains rules for making bonus payments and asked you to:
● Calculate the amount to be paid as a bonus to individual employees
● Calculate the total amount to be paid to individual employees (salary inclusive of bonus)
● Total amount to be paid out per region and company-wide



# Analysis

![Dashboard 1](https://github.com/user-attachments/assets/31d76444-4c2c-4a94-9dc1-9b92f5a3072f)
![Dashboard 2](https://github.com/user-attachments/assets/89d39dfb-f8e2-4719-bc98-96c42448ae92)
![PowerBi Dashboard](https://github.com/user-attachments/assets/ceca10cf-2663-4191-9bae-08a8deb15e93)


