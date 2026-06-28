# Built-in Functions – Hands-on Assignment

## Aim

To understand and implement SQL **Built-in Functions** such as **Single Row Functions**, **Character Functions**, **Number Functions**, **Date Functions**, **Conversion Functions**, and **Conditional Functions** using the **EMPLOYEES** table.

---

# Question 1

## Write a query to display the current date. Label the column as Date.

### Explanation

The **SYSDATE** function returns the current system date and time from the database server.

### SQL Query

```sql
SELECT SYSDATE AS "Date"
FROM dual;
```

### Result

Displays the current system date.

---

# Question 2

## Display the employee number, last name, salary, and salary increased by 15.5%. Label the increased salary as New Salary.

### Explanation

The salary is increased by **15.5%**, and the **ROUND()** function converts the result to the nearest whole number.

### SQL Query

```sql
SELECT employee_id,
       last_name,
       salary,
       ROUND(salary * 1.155) AS "New Salary"
FROM employees;
```

### Result

Displays each employee's current salary and the revised salary after a 15.5% increase.

---

# Question 3

## Modify the previous query to display the salary increase amount. Label the column Increase.

### Explanation

The increase is calculated by subtracting the original salary from the new salary.

### SQL Query

```sql
SELECT employee_id,
       last_name,
       salary,
       ROUND(salary * 1.155) AS "New Salary",
       ROUND(salary * 1.155) - salary AS "Increase"
FROM employees;
```

### Result

Displays the original salary, new salary, and the salary increment.

---

# Question 4

## Display the employee names with the first letter in uppercase and remaining letters in lowercase. Also display the length of each name for employees whose names begin with J, A, or M.

### Explanation

The **INITCAP()** function formats names, **LENGTH()** returns the number of characters, and **SUBSTR()** extracts the first letter for filtering.

### SQL Query

```sql
SELECT INITCAP(last_name) AS Name,
       LENGTH(last_name) AS Length
FROM employees
WHERE UPPER(SUBSTR(last_name,1,1)) IN ('J','A','M')
ORDER BY last_name;
```

### Result

Displays formatted employee names and their lengths.

---

# Question 5

## Rewrite the previous query so that the user is prompted to enter the starting letter of the employee's last name.

### Explanation

The **ACCEPT** variable allows the user to provide the starting character at runtime.

### SQL Query

```sql
SELECT last_name
FROM employees
WHERE UPPER(last_name) LIKE UPPER('&letter') || '%';
```

### Result

Displays employee names beginning with the letter entered by the user.

---

# Question 6

## Display the length of employment for each employee.

### Explanation

The **MONTHS_BETWEEN()** function calculates the total number of months between the hire date and the current date.

### SQL Query

```sql
SELECT last_name,
       MONTHS_BETWEEN(SYSDATE, hire_date) AS MONTHS_WORKED
FROM employees
ORDER BY MONTHS_WORKED;
```

### Result

Displays the total months worked by each employee.

---

# Question 7

## Create a report showing each employee's monthly salary and desired salary (Salary × 3). Label the column Dream Salaries.

### Explanation

The query concatenates text with salary values to produce a readable sentence.

### SQL Query

```sql
SELECT last_name || ' earns ' || salary ||
       ' monthly but wants ' || salary*3 AS "Dream Salaries"
FROM employees;
```

### Result

Displays a sentence showing the employee's current and desired salary.

---

# Question 8

## Display the last name and salary. Format the salary to be 15 characters long and left-padded with the '$' symbol.

### Explanation

The **LPAD()** function pads the salary value with dollar symbols until it reaches a length of 15 characters.

### SQL Query

```sql
SELECT last_name,
       LPAD(salary,15,'$') AS SALARY
FROM employees;
```

### Result

Displays formatted salary values with left padding.

---

# Question 9

## Display each employee's last name, hire date, and salary review date (the first Monday after six months of service).

### Explanation

The **ADD_MONTHS()** function adds six months to the hire date, and **NEXT_DAY()** finds the first Monday after that date.

### SQL Query

```sql
SELECT last_name,
       hire_date,
       NEXT_DAY(ADD_MONTHS(hire_date,6),'MONDAY') AS REVIEW
FROM employees;
```

### Result

Displays the employee's next salary review date.

---

# Question 10

## Display the last name, hire date, and the day of the week on which the employee joined.

### Explanation

The **TO_CHAR()** function formats the hire date to display the day name.

### SQL Query

```sql
SELECT last_name,
       hire_date,
       TO_CHAR(hire_date,'Day') AS DAY
FROM employees
ORDER BY TO_CHAR(hire_date,'D');
```

### Result

Displays the employee's joining day of the week.

---

# Question 11

## Display employee names and commission amounts. If an employee does not receive commission, display "No Commission."

### Explanation

The **NVL()** function replaces NULL values with the specified text.

### SQL Query

```sql
SELECT last_name,
       NVL(TO_CHAR(commission_pct),'No Commission') AS COMM
FROM employees;
```

### Result

Displays employee commission values or "No Commission" where applicable.

---

# Question 12

## Display the first eight characters of employee names and represent their salaries using asterisks.

### Explanation

The **SUBSTR()** function extracts the first eight characters, while **RPAD()** creates a visual salary representation using asterisks.

### SQL Query

```sql
SELECT RPAD(SUBSTR(last_name,1,8),8,' ') AS LAST_NAME,
       RPAD('*',TRUNC(salary/1000),'*') AS EMPLOYEES_AND_THEIR_SALARIES
FROM employees
ORDER BY salary DESC;
```

### Result

Displays employee names and a graphical representation of salary.

---

# Question 13

## Using the DECODE function, display the grade of employees based on their JOB_ID.

### Explanation

The **DECODE()** function compares the job ID with predefined values and assigns a corresponding grade.

### SQL Query

```sql
SELECT last_name,
       job_id,
       DECODE(job_id,
              'AD_PRES','A',
              'ST_MAN','B',
              'SA_REP','C',
              'ST_CLERK','D',
              '0') AS GRADE
FROM employees;
```

### Result

Displays employee grades based on their job IDs.

---

# Question 14

## Rewrite the previous query using the CASE statement.

### Explanation

The **CASE** expression performs the same conditional evaluation as **DECODE**, but is more flexible and easier to read.

### SQL Query

```sql
SELECT last_name,
       job_id,
       CASE job_id
           WHEN 'AD_PRES' THEN 'A'
           WHEN 'ST_MAN' THEN 'B'
           WHEN 'SA_REP' THEN 'C'
           WHEN 'ST_CLERK' THEN 'D'
           ELSE '0'
       END AS GRADE
FROM employees;
```

### Result

Displays employee grades using the CASE expression.

---

# Conclusion

This hands-on assignment demonstrates the practical use of SQL **Built-in Functions**.

- **Character Functions** (INITCAP, LENGTH, SUBSTR, LPAD, RPAD)
- **Number Functions** (ROUND)
- **Date Functions** (SYSDATE, ADD_MONTHS, NEXT_DAY, MONTHS_BETWEEN)
- **Conversion Functions** (TO_CHAR)
- **Null Handling Functions** (NVL)
- **Conditional Functions** (DECODE, CASE)

These built-in functions simplify data formatting, calculations, and reporting, making SQL queries more efficient and user-friendly.