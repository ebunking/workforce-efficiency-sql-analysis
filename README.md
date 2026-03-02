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

•	One-to-many relationships (employees - salaries)

•	Many-to-many relationships (employees - departments via dept_emp)

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

1. Workforce Size	

SELECT COUNT(emp_no) AS total_employees 
FROM employees

Insight:

Determined the total number of employees in the organization, providing a baseline for workforce analysis.

2. Average Salary Across Organization

SELECT ROUND(AVG(salary), 2) AS average_salary 
FROM salaries

Insight:

Identified overall compensation trends, useful for salary benchmarking and planning.

3. Average Salary by Department

SELECT departments.dept_name,
       ROUND(AVG(salaries.salary), 2) AS avg_salary
FROM salaries
JOIN dept_emp ON salaries.emp_no = dept_emp.emp_no
JOIN departments ON dept_emp.dept_no = departments.dept_no
GROUP BY dept_name

Insight:

Highlighted salary disparities across departments, enabling leadership to evaluate compensation equity.

4. Current Managers

SELECT employees.emp_no,
       employees.first_name,
       employees.last_name,
       employee_titles.title
FROM employees
JOIN employee_titles 
     ON employees.emp_no = employee_titles.emp_no
WHERE title = 'Manager'
AND to_date = '9999-01-01'

Insight:

Identified active leadership personnel within the organization.

5. Employees in Finance Department

SELECT employees.emp_no,
       employees.first_name,
       employees.last_name,
       departments.dept_name
FROM employees
JOIN dept_emp 
     ON employees.emp_no = dept_emp.emp_no
JOIN departments 
     ON dept_emp.dept_no = departments.dept_no
WHERE dept_name = 'Finance'
AND dept_emp.to_date = '9999-01-01'

Insight:

Determined active workforce distribution within the Finance department.

6. Employees Earning Above 60,000

SELECT employees.emp_no,
       employees.first_name,
       employees.last_name,
       salaries.salary
FROM employees
JOIN salaries 
     ON employees.emp_no = salaries.emp_no
WHERE salary > 60000

Insight:

Identified high-income earners, useful for performance and compensation strategy analysis.

Key Findings
	
•	Salary distribution varies significantly across departments.
	
•	Leadership roles represent a small percentage of the total workforce.
	
•	Certain departments show higher average salary concentration.
	
•	Workforce data requires continuous updates to maintain data integrity.

Recommendations
	
•	Integrate employee performance metrics for deeper analysis.
	
•	Conduct regular data audits to improve data accuracy.
	
•	Implement role-based access control for data security.
	
•	Monitor departmental salary trends for equitable compensation planning.

Limitations
	
•	Static dataset (no real-time updates)

•	No performance or productivity metrics included
	
•	Some departments lacked complete salary records

•	Historical changes not fully Limitations
	•	Static dataset (no real-time updates)
	•	No performance or productivity metrics included
	•	Some departments lacked complete salary records
	•	Historical changes not fully analyzed

Skills Demonstrated
	
•	SQL Joins
	
•	Aggregation Functions

•	Data Cleaning

•	Relational Database Design
	
•	Business Insight Generation

•	Analytical Thinking


