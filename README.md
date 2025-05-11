# SQL

✅ **1. Introduction to SQL**  <br>

SQL (Structured Query Language) is used to store, retrieve, update, and manage data in a relational database. <br>
 - SQL works with RDBMS (Relational Database Management System) like MySQL, PostgreSQL, Oracle, SQL Server, etc. <br>
 - It uses tables (rows and columns) to store data. <br>

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
