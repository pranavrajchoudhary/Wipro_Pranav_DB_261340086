# Restricting and Sorting Data – Hands-on Assignment

## Aim

To understand and implement SQL statements for **restricting**, **sorting**, **filtering**, and **formatting** data using clauses such as **WHERE, ORDER BY, DISTINCT, BETWEEN, IN, LIKE, IS NULL**, and **column aliases** on the **EMP** table.

---

# Question 1

## Display the ENAME, SAL, and COMM of employees who earn commission. Sort the records in descending order of Salary and Commission using the column's numeric position in the ORDER BY clause.

### Explanation

The **WHERE** clause filters employees who receive commission, while **ORDER BY** sorts the records using the column positions.

### SQL Query

```sql
SELECT ENAME, SAL, COMM
FROM EMP
WHERE COMM IS NOT NULL
ORDER BY 2 DESC, 3 DESC;
```

### Result

Displays employees receiving commission sorted by salary and commission in descending order.

---

# Question 2

## Display all unique job codes from the EMP table.

### Explanation

The **DISTINCT** keyword removes duplicate job values and displays only unique job codes.

### SQL Query

```sql
SELECT DISTINCT JOB
FROM EMP;
```

### Result

Displays all unique job titles available in the EMP table.

---

# Question 3

## Display employee number, employee name, job, and hire date with column aliases.

### Explanation

Column aliases make the output easier to understand by assigning meaningful column headings.

### SQL Query

```sql
SELECT EMPNO AS "Emp #",
       ENAME AS "Employee",
       JOB AS "Job",
       HIREDATE AS "Hire Date"
FROM EMP;
```

### Result

Displays employee details with customized column headings.

---

# Question 4

## Display the employee name concatenated with the job title. Name the column "Employee and Title".

### Explanation

The concatenation operator (`||`) combines employee name and job title into a single column.

### SQL Query

```sql
SELECT ENAME || ', ' || JOB AS "Employee and Title"
FROM EMP;
```

### Result

Displays the employee name and job title together in one column.

---

# Question 5

## Display ENAME, JOB, HIREDATE, and MGR in a single output column separated by commas. Name the column THE_OUTPUT.

### Explanation

Multiple columns are concatenated into one output string using commas as separators.

### SQL Query

```sql
SELECT ENAME || ',' || JOB || ',' || HIREDATE || ',' || MGR AS THE_OUTPUT
FROM EMP;
```

### Result

Displays all selected employee information in a single formatted column.

---

# Question 6

## Display the ENAME, JOB, and HIREDATE of employees named SCOTT or TURNER. Sort the records by hire date in ascending order.

### Explanation

The **IN** operator selects multiple employee names, while **ORDER BY** sorts the results by hire date.

### SQL Query

```sql
SELECT ENAME, JOB, HIREDATE
FROM EMP
WHERE ENAME IN ('SCOTT', 'TURNER')
ORDER BY HIREDATE ASC;
```

### Result

Displays employee details for SCOTT and TURNER sorted by hire date.

---

# Question 7

## Display the ENAME and DEPTNO of employees working in departments 20 or 30. Sort the records alphabetically by employee name.

### Explanation

The **IN** clause filters employees belonging to departments 20 and 30.

### SQL Query

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE DEPTNO IN (20, 30)
ORDER BY ENAME;
```

### Result

Displays employees from departments 20 and 30 in alphabetical order.

---

# Question 8

## Display the employee name and salary of employees earning between 2000 and 3000 and working in departments 20 or 30. Use the aliases Employee and Monthly Salary.

### Explanation

The **BETWEEN** operator filters salaries within a range, while **IN** restricts departments.

### SQL Query

```sql
SELECT ENAME AS "Employee",
       SAL AS "Monthly Salary"
FROM EMP
WHERE SAL BETWEEN 2000 AND 3000
AND DEPTNO IN (20, 30);
```

### Result

Displays employees whose salary falls between 2000 and 3000 and who belong to departments 20 or 30.

---

# Question 9

## Display the employee name and hire date of all employees hired in 1981.

### Explanation

The **BETWEEN** operator filters employees hired within the specified date range.

### SQL Query

```sql
SELECT ENAME, HIREDATE
FROM EMP
WHERE HIREDATE BETWEEN '01-JAN-81' AND '31-DEC-81';
```

### Result

Displays all employees hired during the year 1981.

---

# Question 10

## Display the ENAME and SAL of employees whose salary is greater than a user-specified value.

### Explanation

The **ACCEPT** command prompts the user to enter a salary value, which is then used in the query.

### SQL Query

```sql
ACCEPT AMT PROMPT 'Enter Salary : '

SELECT ENAME, SAL
FROM EMP
WHERE SAL > &AMT;
```

### Result

Displays employees whose salary is greater than the entered amount.

---

# Question 11

## Display the employee name and job title of employees who do not have a manager.

### Explanation

The **IS NULL** condition identifies employees whose manager ID is not assigned.

### SQL Query

```sql
SELECT ENAME, JOB
FROM EMP
WHERE MGR IS NULL;
```

### Result

Displays employees who do not report to any manager.

---

# Question 12

## Prompt the user for a Manager ID and display EMPNO, ENAME, SAL, and DEPTNO. Allow the user to sort the result by any selected column.

### Explanation

The **ACCEPT** command collects user input for the manager ID and the column name used for sorting.

### SQL Query

```sql
ACCEPT MID PROMPT 'Enter Manager ID : '
ACCEPT COL PROMPT 'Enter Column Name : '

SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MID
ORDER BY &COL;
```

### Result

Displays employees reporting to the specified manager and sorts the output according to the selected column.

---

# Question 13

## Prompt the user for a Manager ID and generate EMPNO, ENAME, SAL, and DEPTNO for employees working under that manager. Allow sorting by a selected column.

### Explanation

This query works similarly to the previous one by accepting user input for filtering and sorting.

### SQL Query

```sql
ACCEPT MID PROMPT 'Enter Manager ID : '
ACCEPT COL PROMPT 'Enter Column Name : '

SELECT EMPNO, ENAME, SAL, DEPTNO
FROM EMP
WHERE MGR = &MID
ORDER BY &COL;
```

### Result

Displays employees under the selected manager in the preferred sorting order.

---

# Question 14

## Display all employee names in which the third letter is 'A'.

### Explanation

The **LIKE** operator with underscores (`_`) is used to match a character at a specific position.

### SQL Query

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '__A%';
```

### Result

Displays employee names whose third character is A.

---

# Question 15

## Display the names of employees who have both 'A' and 'S' in their names.

### Explanation

Two **LIKE** conditions are used together to find names containing both letters.

### SQL Query

```sql
SELECT ENAME
FROM EMP
WHERE ENAME LIKE '%A%'
AND ENAME LIKE '%S%';
```

### Result

Displays employee names containing both the letters A and S.

---

# Question 16

## Display the ENAME, JOB, and SAL of employees whose job is CLERK and whose salary is either 800, 950, or 1300.

### Explanation

The **IN** operator checks whether the salary matches any one of the specified values.

### SQL Query

```sql
SELECT ENAME, JOB, SAL
FROM EMP
WHERE JOB = 'CLERK'
AND SAL IN (800, 950, 1300);
```

### Result

Displays clerks whose salary matches the specified salary values.

---

# Conclusion

This hands-on assignment demonstrates the use of SQL statements for restricting and sorting records.

- **WHERE** filters records based on conditions.
- **ORDER BY** sorts query results.
- **DISTINCT** removes duplicate values.
- **BETWEEN** filters values within a range.
- **IN** checks multiple values.
- **LIKE** performs pattern matching.
- **IS NULL** identifies missing values.
- **Column Aliases** improve report readability.
- **ACCEPT** allows user input for dynamic queries.

These SQL features are essential for retrieving accurate and organized data from relational databases.