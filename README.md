# Employees' Dataset

## Table of Content

- [Project Overview](#project-overview)
- [Q&A](#Q&A)
- [References](#references)


### Project Overview 

This Data Analysis Project aims to extract actionable business intelligence from the AdventureWorks2022 dataset, which models the global operational, manufacturing, and commercial footprint of a multinational bicycle manufacturing enterprise. By querying multi-domain tables across sales history, product manufacturing, vendor purchasing, and human resource distributions, this project aims to uncover operational bottlenecks, isolate high-margin consumer trends, and reveal critical purchasing patterns required to optimize corporate supply chain and revenue channels.

### Data Import

Move the File to the SQL Server Backup DirectorySQL Server requires strict security permissions to view files. To prevent permission errors during import, move the file from your Downloads folder into SQL Server's default directory:Copy the downloaded AdventureWorks2022.bak file.Navigate to your local SQL Server instance backup folder. For standard default installations of SQL Server 2022, the path is:C:\Program Files\Microsoft SQL Server\MSSQL16.MSSQLSERVER\MSSQL\BackupPaste the file into this folder. Provide Administrator permission if prompted.


### Tools

The tool used for this analysis is Microsoft SQL Server Management Studio (SSMS), for querying the database, writing queries, creating views, and extracting insights; and Power BI, for data visualization (connected using views).


 ### Data Analysis
Queries Used

Before diving deep into our analysis, lets explore the database to get some information about it. 

<pre>
   SELECT TABLE_NAME 
FROM AdventureWorks2022.INFORMATION_SCHEMA.TABLES
WHERE table_type = 'BASE TABLE'
</pre>

<img width="691" height="174" alt="image" src="https://github.com/user-attachments/assets/ac22e2b1-2f8d-42ed-94ed-b2e265fc3cef" />

## Q&A
Exercise 1: Select the job titles of all single male employees 

<pre>
  SELECT JobTitle 
  FROM HumanResources.Employee 
  WHERE Gender = 'M' 
  AND MaritalStatus != 'M'; 
</pre>

<img width="247" height="277" alt="Screenshot 2026-08-19 011145" src="https://github.com/user-attachments/assets/9dd05c21-b4f4-432a-81c6-33739d4f5708" />


Exercise 2: Select employees whose pay rate is 50 or more 

<pre>
  SELECT BusinessEntityID, Rate, RateChangeDate 
  FROM HumanResources.EmployeePayHistory 
  WHERE Rate >= 50;
</pre>

<img width="303" height="227" alt="image" src="https://github.com/user-attachments/assets/5b99acfd-bfb4-4842-b447-eedc9f587bac" />


Exercise 3: Select employees with their departments and shifts 

<pre>
SELECT DISTINCT d.Name AS DepartmentName, s.Name AS ShiftName 
FROM HumanResources.EmployeeDepartmentHistory AS edh 
JOIN HumanResources.Department AS d 
ON edh.DepartmentID = d.DepartmentID 
JOIN HumanResources.Shift AS s 
ON edh.ShiftID = s.ShiftID; 
</pre>

<img width="261" height="274" alt="Screenshot 2026-08-19 012321" src="https://github.com/user-attachments/assets/6325ae73-f14e-4638-b71f-29def5777b59" />


Exercise 4: Select the highest and lowest sick leave hours 

<pre>
SELECT MIN(SickLeaveHours) AS MinSickLeaveHours, 
  MAX(SickLeaveHours) AS MaxSickLeaveHours 
  FROM HumanResources.Employee;
</pre>
<img width="285" height="96" alt="Screenshot 2026-08-19 012641" src="https://github.com/user-attachments/assets/0bd18283-944d-497c-a871-8d9fb9016f0f" />



### References

[AdventureWorks.bak Dataset](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-)ver17&tabs=ssms)usp=sharing&ouid=107969485968939728677&rtpof=true&sd=true)
 
