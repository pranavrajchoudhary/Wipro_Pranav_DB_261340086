# Retrieving Data Using the SQL SELECT Statement – Hands-on Assignment

## Aim

To understand the basic SQL **SELECT** statement and retrieve data from database tables using commands such as **DESC**, **SELECT**, and **WHERE**.

---

# Question 1

## Determine the Structure of the DEPT Table and its Contents.

### Explanation

The **DESC** command is used to view the structure of a table, including column names, data types, and constraints. The **SELECT** statement retrieves all records stored in the table.

### SQL Query

#### Display the Structure of the DEPT Table

```sql
DESC DEPT;
```

#### Display the Contents of the DEPT Table

```sql
SELECT * FROM DEPT;
```

### Result

- The `DESC` command displays the structure of the **DEPT** table.
- The `SELECT` statement displays all records available in the **DEPT** table.

---

# Question 2

## Determine the Structure of the EMP Table and its Contents.

### Explanation

The structure of the **EMP** table is displayed using the **DESC** command, while all employee records are retrieved using the **SELECT** statement.

### SQL Query

#### Display the Structure of the EMP Table

```sql
DESC EMP;
```

#### Display the Contents of the EMP Table

```sql
SELECT * FROM EMP;
```

### Result

- The table structure shows all columns and their data types.
- The query retrieves every record stored in the **EMP** table.

---

# Question 3

## Display the ENAME and DEPTNO from the EMP table whose EMPNO is 7788.

### Explanation

The **WHERE** clause is used to filter records based on a specified condition. Here, only the employee whose employee number is **7788** is selected.

### SQL Query

```sql
SELECT ENAME, DEPTNO
FROM EMP
WHERE EMPNO = 7788;
```

### Result

Displays the **Employee Name (ENAME)** and **Department Number (DEPTNO)** of the employee whose **EMPNO** is **7788**.

---

# Conclusion

This hands-on assignment introduces the basic SQL **SELECT** statement and demonstrates how to retrieve information from database tables.

- **DESC** is used to view the table structure.
- **SELECT** retrieves records from a table.
- **SELECT *** displays all columns.
- **WHERE** filters records based on a specified condition.

These commands form the foundation of SQL and are essential for querying data in relational database systems.