# Reporting Aggregated Data Using Group Functions – Hands-on Assignment

## Aim

To understand and implement SQL **Group Functions** such as **MAX(), MIN(), SUM(), AVG(), COUNT(), GROUP BY, HAVING, ORDER BY**, and aggregate calculations using the **EMPLOYEES** table.

---

# Question 1

## Find the highest, lowest, total, and average salary of all employees. Label the columns as Maximum, Minimum, Sum, and Average.

### Explanation

Aggregate functions are used to perform calculations on multiple rows and return a single result. This query calculates the maximum salary, minimum salary, total salary, and average salary of all employees.

### SQL Query

```sql
SELECT MAX(salary) AS Maximum,
       MIN(salary) AS Minimum,
       SUM(salary) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees;
```

### Result

Displays the highest, lowest, total, and average salary of all employees.

---

# Question 2

## Round the results to the nearest whole number.

### Explanation

The **ROUND()** function is used to remove decimal values and display rounded results.

### SQL Query

```sql
SELECT ROUND(MAX(salary)) AS Maximum,
       ROUND(MIN(salary)) AS Minimum,
       ROUND(SUM(salary)) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees;
```

### Result

Displays all salary calculations rounded to the nearest whole number.

---

# Question 3

## Display the minimum, maximum, total, and average salary for each job type.

### Explanation

The **GROUP BY** clause groups employees according to their job type, allowing aggregate functions to calculate values for each group.

### SQL Query

```sql
SELECT job_id,
       MIN(salary) AS Minimum,
       MAX(salary) AS Maximum,
       SUM(salary) AS Sum,
       ROUND(AVG(salary)) AS Average
FROM employees
GROUP BY job_id;
```

### Result

Displays salary statistics separately for each job.

---

# Question 4

## Display the number of employees having the same job.

### Explanation

The **COUNT()** function counts the number of employees in each job category.

### SQL Query

```sql
SELECT job_id,
       COUNT(*) AS Number_of_People
FROM employees
GROUP BY job_id;
```

### Result

Displays the total number of employees for each job role.

---

# Question 5

## Determine the number of managers without listing them. Label the column as Number of Managers.

### Explanation

The **COUNT(DISTINCT)** function counts only unique manager IDs and ignores duplicate values.

### SQL Query

```sql
SELECT COUNT(DISTINCT manager_id) AS "Number of Managers"
FROM employees;
```

### Result

Displays the total number of unique managers.

---

# Question 6

## Find the difference between the highest and lowest salaries. Label the column as DIFFERENCE.

### Explanation

The difference is calculated by subtracting the minimum salary from the maximum salary.

### SQL Query

```sql
SELECT MAX(salary) - MIN(salary) AS DIFFERENCE
FROM employees;
```

### Result

Displays the salary difference between the highest-paid and lowest-paid employee.

---

# Question 7

## Display the manager number and the salary of the lowest-paid employee for each manager. Exclude employees without managers and groups whose minimum salary is 2000 or less. Sort the result in descending order of salary.

### Explanation

This query groups employees by manager, finds the lowest salary under each manager, filters groups using the **HAVING** clause, and sorts the output in descending order.

### SQL Query

```sql
SELECT manager_id,
       MIN(salary) AS Lowest_Salary
FROM employees
WHERE manager_id IS NOT NULL
GROUP BY manager_id
HAVING MIN(salary) > 2000
ORDER BY Lowest_Salary DESC;
```

### Result

Displays managers whose lowest-paid employee earns more than 2000, sorted by salary.

---

# Question 8

## Display the total number of employees and the number of employees hired in 1980, 1981, and 1982.

### Explanation

The query uses **CASE** statements with aggregate functions to count employees hired in different years.

### SQL Query

```sql
SELECT COUNT(*) AS Total_Employees,
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1980 THEN 1 ELSE 0 END) AS "1980",
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1981 THEN 1 ELSE 0 END) AS "1981",
       SUM(CASE WHEN EXTRACT(YEAR FROM hire_date) = 1982 THEN 1 ELSE 0 END) AS "1982"
FROM employees;
```

### Result

Displays the total number of employees along with the number of employees hired in the years 1980, 1981, and 1982.

---

# Conclusion

This hands-on assignment demonstrates the use of SQL **Aggregate Functions** for analyzing and summarizing data.

- **MAX()** returns the highest value.
- **MIN()** returns the lowest value.
- **SUM()** calculates the total value.
- **AVG()** computes the average value.
- **COUNT()** counts records.
- **GROUP BY** organizes data into groups.
- **HAVING** filters grouped records.
- **ORDER BY** sorts the final output.

These functions are essential for generating reports and performing data analysis in SQL databases.