# Pewlett-Hackard-Analysis
## Overview of Pewlett Hackard Analysis

### Purpose
The purpose of this analysis was to:
1. determine the number of retiring employees per title.
2. identify employees who are eligible to participate in a mentorship program.


The purpose of our project is to determine the number of retiring employees by title and identify which employees are eligible to to participate in the mentorship program. Our retiring employees by title information will show the titles of all employees born between January, 1 1952 and December, 31 1955. First we created a query that retrieved the emp_no, first_name and last_name columns from the employees table and retrieved the title,from_date and to_date columns of the titles table in our pewlett-hackard query. We joined both of these table on the primary key,filtered the data by birth_date and put the information into a new table. For the next two parts of deliverable 1 we created a unique_titles table to find the first occurance of the emp_no in our new table by using the DISTINCT ON function and for the last part of the deliverable we did ORDER BY COUNT to show us the total number of each title from our unique_titles table that we created. The second deliverable we wrote a query that retrieved columns from our employees and dept_emp table, filtered data on current employees born in 1965 then ordered the table by emp_no.


## Results

- With the retirment_titles table we are able to see every eligible for retirement employee and how long they have worked at each position over the course of their career.

- The unique titles table that we created is showing the most recent title for employees of retirment age.

- Our retiring_titles shows us the a majority of the employees of retirment age (57,668/90,398 = 64%) have senior titles.
![retiring_titles](https://github.com/nayanbarhate/Pewlett-Hackard-Analysis/blob/main/retiring_titles.png)

-  The final part of our project shows mentorship eligibility, if you look at the head of the new csv - you can see that most of these employees have senior titles.
![mentorship](https://github.com/nayanbarhate/Pewlett-Hackard-Analysis/blob/main/mentorship.png)

Note: This table only shows the first 10 rows. The full table is 1,940 rows.


## Pewlett Hackard Analysis Summary

90,398 roles will need to be filled as the employees begin to hit retirement age. However, we can provide additional queries to understand the impact of this more deeply. By finding the total number of employees at Pewlett Hackard, we can see the impact on the company by a percentage of how many jobs will remain filled and how many need to be filled.

We can create a query which creates a table holding all the employees at the company while also removing duplicate values by using the DISTINCT ON function and ordering the table so that it shows an employee's most recent job title. We can then write a simple query to count the number of employee IDs to get the number of total employees.

```
SELECT DISTINCT ON (employees.emp_no) employees.emp_no,
    employees.first_name,
    employees.last_name,
    titles.title,
    titles.from_date,
    titles.to_date
INTO all_employees
FROM employees
LEFT JOIN titles
ON employees.emp_no = titles.emp_no
ORDER BY employees.emp_no, titles.to_date DESC

SELECT COUNT (emp_no)
FROM all_employees
```

The query results show that there are 300,024 total employees. With this new information, we can now see that almost a third of Pewlett Hackard employees are going to be retiring, with a percentage of 30.1%.

In terms of whether there are enough employees to mentor the next generation of employees, there is approximately 2 mentors for every 90 new employees coming into Pewlett Hackard. There are not enough mentors to effectively train the next generation and I would recommend expanding the eligibilty date for mentors in order to increase the amount of mentors.

