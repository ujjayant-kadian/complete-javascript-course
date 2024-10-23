### 1. **Introduction to SQL**

SQL (Structured Query Language) is used to manage and manipulate relational databases. It allows for querying, updating, and managing databases. Most relational database management systems (RDBMS) like MySQL, PostgreSQL, SQL Server, and SQLite use SQL.

---

### 2. **Basic SQL Commands**

#### a. **Creating a Database**

```sql
CREATE DATABASE my_database;
```

This creates a new database. To use the database, you must select it:

```sql
USE my_database;
```

#### b. **Creating a Table**

A table holds data in rows and columns. Here’s an example of creating a table:

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    birth_date DATE,
    hire_date DATE
);
```

- `INT` is an integer type.
- `VARCHAR(50)` defines a variable-length string.
- `AUTO_INCREMENT` ensures the `employee_id` is automatically incremented.

#### c. **Inserting Data**

To insert records into a table:

```sql
INSERT INTO employees (first_name, last_name, birth_date, hire_date)
VALUES ('John', 'Doe', '1980-05-15', '2005-06-10');
```

#### d. **Querying Data**

To retrieve data from a table, use `SELECT`:

```sql
SELECT first_name, last_name FROM employees;
```

You can retrieve all columns using `*`:

```sql
SELECT * FROM employees;
```

#### e. **Updating Data**

To update existing records:

```sql
UPDATE employees
SET first_name = 'Jane'
WHERE employee_id = 1;
```

#### f. **Deleting Data**

To delete records:

```sql
DELETE FROM employees
WHERE employee_id = 1;
```

---

### 3. **Filtering Data with `WHERE` Clause**

The `WHERE` clause allows you to filter results based on specific conditions.

#### a. **Comparison Operators**

- `=` : Equal
- `!=` or `<>` : Not equal
- `>` : Greater than
- `<` : Less than
- `>=` : Greater than or equal
- `<=` : Less than or equal

Example:

```sql
SELECT * FROM employees
WHERE hire_date > '2010-01-01';
```

#### b. **Logical Operators**

- `AND`: Combines conditions, all must be true.
- `OR`: Combines conditions, at least one must be true.
- `NOT`: Negates a condition.

Example:

```sql
SELECT * FROM employees
WHERE hire_date > '2010-01-01' AND birth_date < '1985-01-01';
```

#### c. **Using `LIKE` and Wildcards**

`LIKE` is used for pattern matching with wildcards:

- `%`: Represents zero or more characters.
- `_`: Represents a single character.

Example:

```sql
SELECT * FROM employees
WHERE last_name LIKE 'D%'; -- Finds all last names starting with "D"
```

#### d. **Using `IN` and `BETWEEN`**

- `IN`: Matches values in a list.
- `BETWEEN`: Matches a range of values.

Example:

```sql
SELECT * FROM employees
WHERE last_name IN ('Doe', 'Smith');

SELECT * FROM employees
WHERE birth_date BETWEEN '1970-01-01' AND '1980-12-31';
```

---

### 4. **Aggregate Functions**

SQL offers several aggregate functions to perform calculations on data.

#### a. **Common Aggregate Functions**

- `COUNT()`: Returns the number of rows.
- `SUM()`: Returns the total sum of a numeric column.
- `AVG()`: Returns the average value of a numeric column.
- `MIN()`: Returns the minimum value.
- `MAX()`: Returns the maximum value.

Example:

```sql
SELECT COUNT(*) AS employee_count FROM employees;
SELECT AVG(salary) AS average_salary FROM employees;
```

#### b. **Grouping Data with `GROUP BY`**

`GROUP BY` is used with aggregate functions to group data based on one or more columns.

Example:

```sql
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
```

You can filter grouped data using `HAVING` (instead of `WHERE` for individual records):

```sql
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id
HAVING employee_count > 5;
```

---

### 5. **Sorting Data with `ORDER BY`**

The `ORDER BY` clause is used to sort the results of a query in ascending (`ASC`, default) or descending (`DESC`) order.

```sql
SELECT * FROM employees
ORDER BY last_name ASC, hire_date DESC;
```

---

### 6. **Joins**

A **join** allows you to combine rows from two or more tables based on a related column.

#### a. **Inner Join**

Returns only matching rows between two tables.

```sql
SELECT employees.first_name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```

#### b. **Left Join (or Left Outer Join)**

Returns all rows from the left table and the matched rows from the right table.

```sql
SELECT employees.first_name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```

#### c. **Right Join (or Right Outer Join)**

Returns all rows from the right table and the matched rows from the left table.

```sql
SELECT employees.first_name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

#### d. **Full Outer Join**

Returns all rows when there is a match in either table.

```sql
SELECT employees.first_name, departments.department_name
FROM employees
FULL OUTER JOIN departments
ON employees.department_id = departments.department_id;
```

#### e. **Cross Join**

Returns the Cartesian product of two tables.

```sql
SELECT employees.first_name, departments.department_name
FROM employees
CROSS JOIN departments;
```

---

### 7. **Subqueries (Nested Queries)**

A subquery is a query within another query. It can be used in `SELECT`, `INSERT`, `UPDATE`, and `DELETE` statements.

Example:

```sql
SELECT first_name, last_name
FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Sales');
```

---

### 8. **Modifying Table Structures**

#### a. **Altering a Table**

To modify an existing table structure, use the `ALTER` statement:

```sql
ALTER TABLE employees ADD COLUMN salary DECIMAL(10, 2);
```

You can also drop columns:

```sql
ALTER TABLE employees DROP COLUMN salary;
```

#### b. **Dropping a Table**

To delete a table and all its data:

```sql
DROP TABLE employees;
```

---

### 9. **Views**

A view is a virtual table based on the result set of an SQL query.

#### a. **Creating a View**

```sql
CREATE VIEW employee_view AS
SELECT first_name, last_name, department_id
FROM employees
WHERE hire_date > '2010-01-01';
```

You can then query the view as if it were a table:

```sql
SELECT * FROM employee_view;
```

#### b. **Dropping a View**

```sql
DROP VIEW employee_view;
```

---

### 10. **Indexes**

Indexes improve the speed of data retrieval. However, they can slow down `INSERT` and `UPDATE` operations.

#### a. **Creating an Index**

```sql
CREATE INDEX idx_last_name ON employees(last_name);
```

#### b. **Dropping an Index**

```sql
DROP INDEX idx_last_name;
```

---

### 11. **Transactions**

Transactions allow you to execute multiple SQL statements as a single unit, ensuring that either all or none of the changes are committed.

#### a. **Starting a Transaction**

```sql
START TRANSACTION;
```

#### b. **Committing a Transaction**

```sql
COMMIT;
```

#### c. **Rolling Back a Transaction**

If something goes wrong, you can undo changes made during the transaction:

```sql
ROLLBACK;
```

---

### 12. **SQL Constraints**

Constraints are rules applied to table columns to enforce data integrity.

- `PRIMARY KEY`: Uniquely identifies each record in a table.
- `FOREIGN KEY`: Links two tables together.
- `UNIQUE`: Ensures that all values in a column are unique.
- `NOT NULL`: Ensures that a column cannot have a `NULL` value.
- `CHECK`: Ensures that all values in a column meet a specific condition.
- `DEFAULT`: Sets a default value for a column.

---

### 13. **Advanced SQL Topics**

#### a. **Window Functions**

Window functions allow performing calculations across a set of table rows related to the current row.

Example (Calculating a running total):

```sql
SELECT employee_id, salary,
SUM(salary) OVER (ORDER BY hire_date) AS running_total
FROM employees;
```

#### b. **Common Table Expressions (CTEs)**

A **CTE** is a temporary result set that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

```sql
WITH cte_example AS (
    SELECT department_id, COUNT(*)

 AS employee_count
    FROM employees
    GROUP BY department_id
)
SELECT * FROM cte_example WHERE employee_count > 5;
```

---

### 14. **SQL Best Practices**

- Use `JOIN` instead of subqueries for better performance when possible.
- Use `LIMIT` or `TOP` to reduce the result set size for large queries.
- Index columns that are frequently used in `WHERE` clauses.
- Avoid using `SELECT *`; select only necessary columns to improve performance.

---
