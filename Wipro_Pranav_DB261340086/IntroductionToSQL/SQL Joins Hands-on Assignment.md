# SQL Joins - Hands-on Assignment

## Aim

To understand and perform different types of SQL Joins such as **Natural Join, Equi Join, Self Join, Outer Join, Non-Equi Join, USING Clause, and ON Clause** using the EMP, DEPT, and SALGRADE tables.

---

# Question 1

## Natural Join

### Question

Write a query for the HR department to produce the addresses of all the departments. Use the **EMP** and **DEPT** tables. Display **EMPNO, ENAME, SAL, DNAME, and LOC** using a **NATURAL JOIN**.

### Explanation

A **Natural Join** automatically joins two tables using the common column (`DEPTNO`) present in both tables.

### SQL Query

```sql
SELECT EMPNO, ENAME, SAL, DNAME, LOC
FROM EMP
NATURAL JOIN DEPT;
```

### Result

Displays employee details along with their department name and location.

---

# Question 2

## Equi Join

### Question

Display the **JOB, MGR, SAL, COMM, and DNAME** of employees whose job is **SALESMAN**.

### Explanation

An **Equi Join** matches rows from two tables based on equal values of the common column (`DEPTNO`).

### SQL Query

```sql
SELECT E.JOB, E.MGR, E.SAL, E.COMM, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND E.JOB = 'SALESMAN';
```

### Result

Shows all employees working as Salesman along with their department name.

---

# Question 3

## Equi Join

### Question

Display the **ENAME, JOB, DEPTNO, and DNAME** of employees who work in **DALLAS**.

### Explanation

The EMP and DEPT tables are joined using the common department number, and only employees belonging to departments located in Dallas are displayed.

### SQL Query

```sql
SELECT E.ENAME, E.JOB, E.DEPTNO, D.DNAME
FROM EMP E, DEPT D
WHERE E.DEPTNO = D.DEPTNO
AND D.LOC = 'DALLAS';
```

### Result

Displays employee information for departments located in Dallas.

---

# Question 4

## Self Join

### Question

Create a report to display employees' name and employee number along with their manager's name and manager number.

### Explanation

A **Self Join** joins the EMP table with itself because managers are also employees in the same table.

### SQL Query

```sql
SELECT
    E.ENAME AS Employee,
    E.EMPNO AS "Emp#",
    M.ENAME AS Manager,
    M.EMPNO AS "Mgr#"
FROM EMP E
JOIN EMP M
ON E.MGR = M.EMPNO;
```

### Result

Displays every employee together with their reporting manager.

---

# Question 5

## Left Outer Join

### Question

Modify the previous query to display all employees including **KING**, who has no manager. Order the results by employee number.

### Explanation

A **LEFT OUTER JOIN** returns all employees even if they do not have a matching manager.

### SQL Query

```sql
SELECT
    E.ENAME AS Employee,
    E.EMPNO AS "Emp#",
    M.ENAME AS Manager,
    M.EMPNO AS "Mgr#"
FROM EMP E
LEFT OUTER JOIN EMP M
ON E.MGR = M.EMPNO
ORDER BY E.EMPNO;
```

### Result

Displays every employee, including those who do not report to anyone.

---

# Question 6

## Non-Equi Join

### Question

First display the structure of the **SALGRADE** table. Then display the employee name, job, department name, salary, and salary grade.

### SQL Query

```sql
DESC SALGRADE;
```

### Explanation

A **Non-Equi Join** compares values using a range instead of an equality condition.

### SQL Query

```sql
SELECT
    E.ENAME,
    E.JOB,
    D.DNAME,
    E.SAL,
    S.GRADE
FROM EMP E
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO
JOIN SALGRADE S
ON E.SAL BETWEEN S.LOSAL AND S.HISAL;
```

### Result

Displays employee details along with their salary grade.

---

# Question 7

## Right Outer Join

### Question

Display the **ENAME** and **DNAME** of all employees. Also display department names that do not have any employees.

### Explanation

A **RIGHT OUTER JOIN** returns all department records, even if no employee belongs to that department.

### SQL Query

```sql
SELECT E.ENAME, D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

### Result

Displays all departments along with available employee names.

---

# Question 8

## Self Join with Outer Join

### Question

Find the names and hire dates for employees who were hired before their managers, along with their managers' names and hire dates.

### Explanation

The EMP table is joined with itself to compare employee hire dates with manager hire dates.

### SQL Query

```sql
SELECT
    E.ENAME AS Employee,
    E.HIREDATE AS Employee_HireDate,
    M.ENAME AS Manager,
    M.HIREDATE AS Manager_HireDate
FROM EMP E
LEFT OUTER JOIN EMP M
ON E.MGR = M.EMPNO
WHERE M.HIREDATE > E.HIREDATE;
```

### Result

Displays employees who joined the organization before their managers.

---

# Question 9

## USING Clause

### Question

Display the **EMPNO, ENAME, DNAME, and LOC** of employees working as **CLERK** using the **USING** clause.

### Explanation

The **USING** clause joins two tables using the common column without repeating the column name.

### SQL Query

```sql
SELECT EMPNO, ENAME, DNAME, LOC
FROM EMP
JOIN DEPT
USING (DEPTNO)
WHERE JOB = 'CLERK';
```

### Result

Displays all clerks along with their department details.

---

# Question 10

## ON Clause

### Question

Display the **ENAME, SAL, MGR, and DNAME** of employees whose salary is greater than **2000**.

### Explanation

The **ON** clause explicitly specifies the join condition between two tables.

### SQL Query

```sql
SELECT E.ENAME, E.SAL, E.MGR, D.DNAME
FROM EMP E
JOIN DEPT D
ON E.DEPTNO = D.DEPTNO
WHERE E.SAL > 2000;
```

### Result

Displays employees earning more than 2000 with their department name.

---

# Question 11

## LEFT OUTER JOIN

### Question

Display the **EMPNO, ENAME, JOB, DEPTNO, DNAME, and LOC** using **LEFT OUTER JOIN**.

### Explanation

Returns all employee records and matching department information.

### SQL Query

```sql
SELECT
    E.EMPNO,
    E.ENAME,
    E.JOB,
    E.DEPTNO,
    D.DNAME,
    D.LOC
FROM EMP E
LEFT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

### Result

Displays all employees even if department information is unavailable.

---

# Question 12

## RIGHT OUTER JOIN

### Question

Display the **ENAME** and **DNAME** of employees using **RIGHT OUTER JOIN**.

### Explanation

Returns every department along with matching employee records.

### SQL Query

```sql
SELECT E.ENAME, D.DNAME
FROM EMP E
RIGHT OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

### Result

Displays department names including those without employees.

---

# Question 13

## FULL OUTER JOIN

### Question

Display the **EMPNO, DNAME, and LOC** using **FULL OUTER JOIN**.

### Explanation

A **FULL OUTER JOIN** returns all matching and non-matching records from both EMP and DEPT tables.

### SQL Query

```sql
SELECT
    E.EMPNO,
    D.DNAME,
    D.LOC
FROM EMP E
FULL OUTER JOIN DEPT D
ON E.DEPTNO = D.DEPTNO;
```

### Result

Displays all employees and all departments, including unmatched records from both tables.

---

# Conclusion

This practical assignment demonstrates the implementation of different SQL Join operations.

- **Natural Join** joins tables automatically using common columns.
- **Equi Join** matches rows based on equal values.
- **Self Join** relates records within the same table.
- **Outer Joins** return matched as well as unmatched records.
- **Non-Equi Join** joins records using a range condition.
- **USING** and **ON** clauses provide different ways to define join conditions.

These joins are essential for retrieving related data from multiple tables efficiently in relational database management systems.