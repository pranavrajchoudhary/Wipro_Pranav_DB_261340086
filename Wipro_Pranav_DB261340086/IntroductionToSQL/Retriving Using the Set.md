# Using the Set Operators – Hands-on Assignment

## Aim

To understand and implement SQL **Set Operators** such as **UNION** and **UNION ALL** for combining the results of multiple SQL queries. This assignment also demonstrates the use of aggregate functions and matrix reports using the **EMPLOYEES** table.

---

# Question 1

## Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job, for departments 10, 20, and 30. Give each column an appropriate heading.

### Explanation

This query creates a **matrix report** by using the **DECODE()** function. It displays the total salary for each job in departments **10**, **20**, and **30**, along with the overall salary for that job.

### SQL Query

```sql
SELECT job,
       SUM(DECODE(department_id,10,salary)) AS Dept10,
       SUM(DECODE(department_id,20,salary)) AS Dept20,
       SUM(DECODE(department_id,30,salary)) AS Dept30,
       SUM(salary) AS Total
FROM employees
WHERE department_id IN (10,20,30)
GROUP BY job;
```

### Result

Displays a matrix showing department-wise salary totals and the overall salary for each job.

---

# Question 2

## Using the SET operator, display the DEPTNO and total salary for each department, the JOB and total salary for each job, and the overall total salary.

### Explanation

The **UNION** operator combines the results of multiple SELECT statements into a single result set. Each query returns similar columns, allowing department totals, job totals, and the grand total to be displayed together.

### SQL Query

```sql
SELECT TO_CHAR(department_id) AS Department,
       NULL AS Job,
       SUM(salary) AS Total_Salary
FROM employees
GROUP BY department_id

UNION

SELECT NULL,
       job_id,
       SUM(salary)
FROM employees
GROUP BY job_id

UNION

SELECT 'TOTAL',
       NULL,
       SUM(salary)
FROM employees;
```

### Result

Displays department-wise salary totals, job-wise salary totals, and the overall salary in one combined report.

---

# Question 3

## Using the SET operator, display the JOB and DEPTNO of employees working in departments 20, 10, and 30 in the same order.

### Explanation

The **UNION ALL** operator combines the results of multiple queries without removing duplicate records. It also preserves the order of each SELECT statement, displaying departments in the required sequence.

### SQL Query

```sql
SELECT job_id, department_id
FROM employees
WHERE department_id = 20

UNION ALL

SELECT job_id, department_id
FROM employees
WHERE department_id = 10

UNION ALL

SELECT job_id, department_id
FROM employees
WHERE department_id = 30;
```

### Result

Displays the job IDs and department numbers of employees from departments **20**, **10**, and **30** in the specified order.

---

# Conclusion

This hands-on assignment demonstrates the use of SQL **Set Operators** for combining data from multiple queries.

- **UNION** combines result sets while removing duplicate rows.
- **UNION ALL** combines result sets and retains duplicate rows.
- **DECODE()** is useful for creating matrix-style reports.
- Aggregate functions such as **SUM()** help generate summarized reports.

These SQL techniques are widely used in report generation and data analysis within relational database systems.