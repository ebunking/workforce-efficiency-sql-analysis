# workforce-efficiency-sql-analysis
Workforce efficiency analysis using PostgreSQL and SQL queries to generate HR insights.
Project Overview

This project analyzes employee workforce data using PostgreSQL to extract actionable insights that support HR decision-making.

The objective was to:
•	Analyze employee demographics
•	Evaluate salary distribution
•	Identify departmental workforce trends
•	Examine leadership roles and managerial structure
•	Generate insights for workforce optimization

The dataset consisted of structured CSV files imported into PostgreSQL and organized into relational tables.

Database Schema

The database follows a relational HR structure:
	•	employees
	•	departments
	•	dept_emp
	•	salaries
	•	employee_titles

Entity Relationship Structure![IMG_7874](https://github.com/user-attachments/assets/8b04e7e7-80ce-4a9f-824e-117687451681)

The schema demonstrates:
	•	One-to-many relationships (employees → salaries)
	•	Many-to-many relationships (employees ↔ departments via dept_emp)
	•	Historical tracking using to_date = '9999-01-01' for current records

Tools & Technologies
	•	PostgreSQL
	•	CSV Data Files
	•	SQL (JOIN, GROUP BY, COUNT, AVG, ORDER BY, WHERE)
	•	Excel (Data Cleaning)
	
Project Workflow
	1.	Converted Excel files to CSV format
	2.	Created PostgreSQL database
	3.	Defined tables with appropriate data types
	4.	Imported CSV data into PostgreSQL
	5.	Performed SQL querying and analysis
	6.	Generated workforce insights and recommendations

Key Business Questions & SQL Analysis

Workforce Size	
SELECT COUNT(emp_no) AS total_employees 
FROM employees;
Insight:
Determined the total number of employees in the organization, providing a baseline for workforce analysis.
