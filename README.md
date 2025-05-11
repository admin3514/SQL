# SQL

✅ **1. Introduction to SQL**  <br>

SQL (Structured Query Language) is used to store, retrieve, update, and manage data in a relational database. <br>
 - SQL works with RDBMS (Relational Database Management System) like MySQL, PostgreSQL, Oracle, SQL Server, etc. <br>
 - It uses tables (rows and columns) to store data. <br>

<hr>

🕰️ **History of SQL**  <br>
 1. 1970 – The Birth of Relational Databases <br>
  - E.F. Codd, a British computer scientist at IBM, published a groundbreaking paper titled  <br>
    "A Relational Model of Data for Large Shared Data Banks".  <br>
  - This introduced the concept of relational databases, where data is stored in tables.  <br>

<hr>

✅ **SQL Data Types (Summary)** <br>

🔹 *1. Numeric Types : Used to store numbers.* <br>

```ssh
| Type             | Description              | Example    |
| ---------------- | ------------------------ | ---------- |
|  INT             | Whole numbers            | 100, -25   |
|  BIGINT          | Very large whole numbers | 1234567890 |
|  DECIMAL(p,s)    | Exact decimal values     | 99.99      |
|  FLOAT` /  REAL  | Approximate decimals     | 12.345     |
```

🔹 *2. String (Text) Types : Used to store characters and text.* <br>

```ssh
| Type         | Description            | Example         |
| ------------ | ---------------------- | --------------- |
|  CHAR(n)     | Fixed-length string    | 'abc   '        |
|  VARCHAR(n)  | Variable-length string | 'Hello'         |
|  TEXT        | Long text              | Notes, articles |
```

🔹 *3. Date & Time Types : Used to store dates and times.* <br>

```ssh
| Type        | Description            | Example               |
| ----------- | ---------------------- | --------------------- |
|  DATE       | Only date              | '2025-05-11'          |
|  TIME       | Only time              | '14:30:00'            |
|  DATETIME   | Date and time          | '2025-05-11 14:30:00' |
|  TIMESTAMP  | Auto-recorded datetime | (current timestamp)   |
```

🔹 *4. Boolean Type : Stores true/false values.*  <br>

```ssh
| Type      | Description   | Example |
| --------- | ------------- | ------- |
|  BOOLEAN  | TRUE or FALSE | TRUE    |
```

🔹 *5. Binary Types : Used to store binary files like images, audio.*  <br>

```ssh
| Type        | Description                  |
| ----------- | ---------------------------- |
|  BLOB      | Binary Large Object (images)  |
|  VARBINARY | Variable binary data          |
```

<hr>

✅ **2. SQL Categories** <br>

```ssh
| Category | Commands                              |
| -------- | ------------------------------------- |
|  DDL     | `CREATE`, `ALTER`, `DROP`, `TRUNCATE` |
|  DML     | `INSERT`, `UPDATE`, `DELETE`          |
|  DQL     | `SELECT`                              |
|  DCL     | `GRANT`, `REVOKE`                     |
|  TCL     | `COMMIT`, `ROLLBACK`, `SAVEPOINT`     |

```

<hr>

✅ **3. DDL (Data Definition Language)** <br>

🔹 *CREATE :* Create database objects <br>
```ssh
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  salary DECIMAL(10, 2)
);
```

🔹 *ALTER :* Modify structure of a table <br>
```ssh
ALTER TABLE employees ADD department VARCHAR(30);
```

🔹 *DROP :* Delete a table or database permanently <br>
```ssh
DROP TABLE employees;
```

🔹 *TRUNCATE :* Delete all rows (faster than DELETE, no rollback) <br>
```ssh
TRUNCATE TABLE employees;
```

<hr>

✅ **4. DML (Data Manipulation Language)**  <br>

🔹 *INSERT :* Add new data
```ssh
INSERT INTO employees (id, name, salary) VALUES (1, 'Alice', 50000);
```

🔹 *UPDATE :* Modify existing data
```ssh
UPDATE employees SET salary = 55000 WHERE id = 1;
```

🔹 *DELETE :* Remove rows from a table
```ssh
DELETE FROM employees WHERE id = 1;
```

<hr>

✅ **5. DQL (Data Query Language)** <br>

🔹 *SELECT :* Retrieve data
```ssh
SELECT * FROM employees;
SELECT name, salary FROM employees WHERE salary > 50000;
```

🔸 **Clauses :**  <br>
 - WHERE: Filter records  <br>
 - ORDER BY: Sort results  <br>
 - GROUP BY: Group rows based on a column  <br>
 - HAVING: Filter groups (used with GROUP BY)  <br>
 - DISTINCT: Remove duplicates  <br>
 - LIMIT: Restrict the number of rows  <br>

<hr>

✅ **6. DCL (Data Control Language)** 

🔹 *GRANT :* Give privileges
```ssh
GRANT SELECT, INSERT ON employees TO 'user1';
```

🔹 *REVOKE :* Take back privileges
```ssh
REVOKE SELECT ON employees FROM 'user1';
```

<hr>

✅ **7. TCL (Transaction Control Language)**

Used to manage transactions in SQL. <br>
 - COMMIT: Save changes permanently  <br>
 - ROLLBACK: Undo changes since last COMMIT  <br>
 - SAVEPOINT: Mark a point to roll back to  <br>

```ssh
BEGIN;
UPDATE employees SET salary = 60000 WHERE id = 2;
SAVEPOINT s1;
DELETE FROM employees WHERE id = 3;
ROLLBACK TO s1;
COMMIT;
```

<hr>

✅ **8. SQL Constraints**

```ssh
| Constraint    | Description                                 |
| ------------- | ------------------------------------------- |
|  PRIMARY KEY  | Uniquely identifies each row                |
|  FOREIGN KEY  | Links two tables                            |
|  UNIQUE       | Ensures all values are different            |
|  NOT NULL     | Disallows NULL values                       |
|  CHECK        | Limits values in a column                   |
|  DEFAULT      | Assigns a default value if none is provided |
```

<hr>

✅ **9. SQL Joins**

Used to combine rows from two or more tables based on related columns. <br>

```ssh
| Join Type      | Description                                         |
| -------------- | --------------------------------------------------- |
|   INNER JOIN   | Returns records with matching values in both tables |
|   LEFT JOIN    | All records from left, matching from right          |
|   RIGHT JOIN   | All records from right, matching from left          |
|   FULL JOIN    | All records from both tables                        |
```

```ssh
SELECT e.name, d.dept_name 
FROM employees e
INNER JOIN departments d ON e.dept_id = d.id;
```

<hr>


✅ **10. Subqueries**

A query inside another query. Can be used in SELECT, FROM, or WHERE clauses.  <br>
```ssh
SELECT name
FROM employees
WHERE salary > (SELECT AVG(salary)
FROM employees);
```

<hr>

✅ **What is a Nested Subquery?**

A nested subquery (also called an inner query) is a query within another query. It is placed inside a WHERE, HAVING, or FROM clause of another SQL statement. <br>
Nested subqueries are used when you want to use the result of one query to filter or process another. <br>

<hr>

✅ **12. Indexes**

Indexes improve the speed of data retrieval. <br>
```ssh
CREATE INDEX idx_name ON employees(name);
```

<hr>

✅ **13. Views**

A virtual table based on the result of a query.  <br>
```ssh
CREATE VIEW high_salary AS
SELECT name, salary FROM employees WHERE salary > 50000;
```
