# DBMS Normalization - Hands-on Assignment Solution

## Question 1

### Observe the structure of the given EMPLOYEE table and suggest whether it can be further normalized.

**Table Structure**

`EMPNO, ENAME, SAL, DEPTNO, DNAME, LOC`

### Answer

### Current Normal Form: Second Normal Form (2NF)

### Explanation

- `EMPNO` is the **Primary Key** of the table.
- The attributes `ENAME`, `SAL`, and `DEPTNO` are directly dependent on `EMPNO`.
- However, `DNAME` and `LOC` are dependent on `DEPTNO` instead of `EMPNO`.
- This creates a **Transitive Dependency**, which means the table does not satisfy the requirements of Third Normal Form (3NF).

### Converting the Table into 3NF

To remove the transitive dependency, the department-related information should be stored in a separate table.

#### EMPLOYEE Table

| EMPNO | ENAME | SAL | DEPTNO |
|-------:|-------|----:|-------:|
| 101 | Ram | 30000 | 10 |

#### DEPARTMENT Table

| DEPTNO | DNAME | LOC |
|-------:|-------|------|
| 10 | Sales | Delhi |

### Result

After separating department details, every non-key attribute depends only on the primary key, and the database satisfies **Third Normal Form (3NF)**.

---

# Question 2

### Observe the structure of the given STUDENT table and suggest whether it can be further normalized.

**Table Structure**

`ROLLNO, NAME, AGE, EXAM, MARKS, GRADE`

### Answer

### Current Normal Form: Second Normal Form (2NF)

### Explanation

- `ROLLNO` acts as the **Primary Key**.
- The attributes `NAME`, `AGE`, `EXAM`, and `MARKS` are associated with `ROLLNO`.
- The attribute `GRADE` is determined by the value of `MARKS` rather than directly by `ROLLNO`.
- This introduces a **Transitive Dependency**, preventing the table from being in Third Normal Form.

### Converting the Table into 3NF

Separate the student, result, and grade information into different tables.

#### STUDENT Table

| ROLLNO | NAME | AGE |
|-------:|------|----:|
| 1 | Aaliya | 20 |

#### RESULT Table

| ROLLNO | EXAM | MARKS |
|-------:|------|------:|
| 1 | DBMS | 95 |

#### GRADE Table

| MARKS | GRADE |
|------:|-------|
| 95 | A+ |

### Result

This design removes the transitive dependency and ensures that each non-key attribute depends only on the primary key, achieving **Third Normal Form (3NF)**.

---

# Question 3

### Observe the structure of the given EMPLOYEE table and identify the problem. Also suggest how to solve it.

**Table Structure**

`EMPNO, PROJECT_NO, NO_OF_DAYS, CUSTOMERNAME`

**Note:** `EMPNO` and `PROJECT_NO` together form a **Composite Primary Key**.

### Answer

### Problem Identified: Partial Dependency

### Explanation

- The composite primary key consists of `EMPNO` and `PROJECT_NO`.
- `NO_OF_DAYS` depends on both attributes of the composite key.
- However, `CUSTOMERNAME` depends only on `PROJECT_NO` and not on the complete composite key.
- Since one non-key attribute depends on only a part of the primary key, the table contains a **Partial Dependency**.
- Therefore, the table is only in **First Normal Form (1NF)**.

### Converting the Table into 2NF

Split the table into two separate tables to eliminate the partial dependency.

#### EMPLOYEE_PROJECT Table

| EMPNO | PROJECT_NO | NO_OF_DAYS |
|-------:|------------|-----------:|
| 101 | P101 | 20 |

#### PROJECT Table

| PROJECT_NO | CUSTOMERNAME |
|------------|--------------|
| P101 | ABC Ltd |

### Result

By moving the customer information into a separate table, all non-key attributes become fully dependent on the complete composite key. This removes the partial dependency and converts the design into **Second Normal Form (2NF)**.

---

# Conclusion

The given tables contain either **Transitive Dependency** or **Partial Dependency**, which prevent them from reaching higher normal forms. By separating related data into appropriate tables, redundancy is reduced, data consistency is improved, and the database follows proper normalization principles.