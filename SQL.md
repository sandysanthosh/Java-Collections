Here are some common **SQL interview questions** along with brief answers:

### 1. **What is SQL?**
   - **SQL (Structured Query Language)** is a standard programming language used to manage and manipulate relational databases. It is used for querying, inserting, updating, and deleting data, as well as managing database objects like tables, indexes, and views.

### 2. **What are the different types of SQL statements?**
   SQL statements are broadly categorized into:
   - **DDL (Data Definition Language)**: Used to define the structure of the database objects (e.g., `CREATE`, `ALTER`, `DROP`).
   - **DML (Data Manipulation Language)**: Used for manipulating data in the database (e.g., `INSERT`, `UPDATE`, `DELETE`, `SELECT`).
   - **DCL (Data Control Language)**: Used to control access to data (e.g., `GRANT`, `REVOKE`).
   - **TCL (Transaction Control Language)**: Used to manage transactions in the database (e.g., `COMMIT`, `ROLLBACK`, `SAVEPOINT`).

### 3. **What is a primary key?**
   - A **primary key** is a column or a combination of columns in a table that uniquely identifies each row. It must contain unique values, and it cannot contain `NULL` values. Every table can have only one primary key.

### 4. **What is a foreign key?**
   - A **foreign key** is a column or set of columns in one table that references the primary key in another table. It is used to maintain referential integrity between the two tables.

### 5. **What is the difference between `JOIN` and `UNION`?**
   - **JOIN**: Combines rows from two or more tables based on a related column between them. It merges the columns.
   - **UNION**: Combines the results of two or more `SELECT` queries into a single result set, stacking the rows on top of each other (must have the same number of columns and compatible data types).

### 6. **What are the different types of `JOIN` in SQL?**
   - **INNER JOIN**: Returns only the matching rows between the tables.
   - **LEFT JOIN (or LEFT OUTER JOIN)**: Returns all rows from the left table, and the matching rows from the right table; returns `NULL` for non-matching rows from the right table.
   - **RIGHT JOIN (or RIGHT OUTER JOIN)**: Returns all rows from the right table, and the matching rows from the left table; returns `NULL` for non-matching rows from the left table.
   - **FULL JOIN (or FULL OUTER JOIN)**: Returns all rows when there is a match in either the left or right table; non-matching rows are filled with `NULL`.

### 7. **What is the difference between `WHERE` and `HAVING`?**
   - **WHERE**: Filters rows before any groupings are made. Used with `SELECT`, `UPDATE`, and `DELETE` queries.
   - **HAVING**: Filters groups after aggregation. It is used with `GROUP BY` to filter the result set after applying aggregate functions like `SUM()`, `COUNT()`, etc.

### 8. **What is an `INDEX`? Why is it used?**
   - An **INDEX** is a database object used to improve the speed of data retrieval operations on a table. It allows the database to find rows quickly without scanning the entire table.
   - However, indexes can slow down `INSERT`, `UPDATE`, and `DELETE` operations since the index must also be updated.

### 9. **What is `Normalization`?**
   - **Normalization** is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller ones and defining relationships between them. The main normal forms are:
     - **1NF**: Eliminate duplicate columns from the same table.
     - **2NF**: Remove subsets of data that apply to multiple rows and place them in separate tables.
     - **3NF**: Remove columns that do not depend on the primary key.

### 10. **What is `Denormalization`?**
   - **Denormalization** is the process of combining normalized tables to improve query performance by reducing the number of joins needed. It increases redundancy but can speed up data retrieval operations in read-heavy systems.

### 11. **What is a `View` in SQL?**
   - A **View** is a virtual table that is based on the result set of an SQL query. It can simplify complex queries, enhance security by restricting access to specific data, and provide a layer of abstraction over the actual tables.
     ```sql
     CREATE VIEW EmployeeView AS
     SELECT name, department FROM Employee WHERE department = 'Sales';
     ```

### 12. **What is a `Stored Procedure`?**
   - A **Stored Procedure** is a precompiled set of SQL statements that can be executed as a single unit. It helps in modular programming and allows for logic like loops and conditionals. It is stored in the database and can accept parameters.
     ```sql
     CREATE PROCEDURE GetEmployeeInfo (IN empId INT)
     BEGIN
        SELECT * FROM Employee WHERE id = empId;
     END;
     ```

### 13. **What is a `Trigger`?**
   - A **Trigger** is a database object that automatically executes a predefined action in response to certain events on a table (such as `INSERT`, `UPDATE`, or `DELETE`). It is used to enforce business rules, audit changes, or maintain logs.
     ```sql
     CREATE TRIGGER after_employee_insert
     AFTER INSERT ON Employee
     FOR EACH ROW
     BEGIN
         INSERT INTO Log (message) VALUES ('Employee added');
     END;
     ```

### 14. **What is a `Transaction` in SQL?**
   - A **Transaction** is a sequence of one or more SQL statements that are executed as a single unit of work. Transactions ensure data integrity by following ACID properties (Atomicity, Consistency, Isolation, Durability).
     - **COMMIT**: Saves the transaction changes permanently.
     - **ROLLBACK**: Undoes the changes made by the transaction.
     - **SAVEPOINT**: Marks a specific point in a transaction to which you can later roll back.

### 15. **What is the difference between `TRUNCATE` and `DELETE`?**
   - **DELETE**:
     - Removes rows from a table based on a `WHERE` clause.
     - Can be rolled back (part of a transaction).
     - Triggers are fired on delete.
   - **TRUNCATE**:
     - Removes all rows from a table without logging individual row deletions.
     - Cannot be rolled back.
     - Resets the identity of the table (if any).

### 16. **What are aggregate functions in SQL?**
   - Aggregate functions perform calculations on multiple rows and return a single value. Common aggregate functions include:
     - `COUNT()`: Returns the number of rows.
     - `SUM()`: Returns the sum of a numeric column.
     - `AVG()`: Returns the average value.
     - `MIN()`: Returns the smallest value.
     - `MAX()`: Returns the largest value.

### 17. **What is the `GROUP BY` clause in SQL?**
   - The **GROUP BY** clause is used to group rows that have the same values in specified columns into summary rows (e.g., summing or counting). It is often used with aggregate functions.
     ```sql
     SELECT department, COUNT(*) FROM Employee GROUP BY department;
     ```

### 18. **What is a `Subquery`?**
   - A **Subquery** is a query nested within another query. It is used to perform operations in multiple steps or to use the result of one query inside another.
     ```sql
     SELECT * FROM Employee WHERE salary > (SELECT AVG(salary) FROM Employee);
     ```

### 19. **What are the types of subqueries?**
   - **Single-row Subquery**: Returns a single row.
   - **Multi-row Subquery**: Returns multiple rows.
   - **Correlated Subquery**: A subquery that references columns from the outer query. It is evaluated once for each row processed by the outer query.
   - **Non-correlated Subquery**: A subquery that can be run independently of the outer query.

### 20. **What is `Indexing` and how does it improve performance?**
   - **Indexing** creates a data structure (usually a B-tree or hash index) that speeds up data retrieval operations. An index helps the database quickly locate the data without scanning the entire table. However, indexes can slow down `INSERT`, `UPDATE`, and `DELETE` operations because they need to be updated alongside the table.

### 21. **What is the difference between `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER()`?**
   - **RANK()**: Assigns a unique rank to rows, but skips ranks if there are ties.
     ```sql
     SELECT name, salary, RANK() OVER (ORDER BY salary DESC) FROM Employee;
     ```
   - **DENSE_RANK()**: Similar to `RANK()`, but does not skip ranks if there are ties.
   - **ROW_NUMBER()**: Assigns a unique number to each row, even if there are ties.

### 22. **What is `ACID` in databases?**
   - **ACID** stands for:
     - **Atomicity**: Transactions are all-or-nothing.
     - **

Consistency**: Transactions take the database from one valid state to another.
     - **Isolation**: Transactions are isolated from each other.
     - **Durability**: Once a transaction is committed, it remains in the system even if there is a failure.

### 23. **What is the `EXISTS` clause?**
   - The **EXISTS** clause is used to check whether a subquery returns any rows. It returns `TRUE` if the subquery returns one or more rows and `FALSE` otherwise.
     ```sql
     SELECT * FROM Employee WHERE EXISTS (SELECT * FROM Department WHERE department = 'Sales');
     ```

These SQL interview questions cover the essential concepts you need to know for interviews. If you'd like deeper insights into any of these questions or need help practicing queries, feel free to ask!
