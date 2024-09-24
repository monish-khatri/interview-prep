### **SQL Fundamentals**

1. **What is SQL?**
   - SQL (Structured Query Language) is a domain-specific language used to manage and manipulate relational databases. It is used for querying, updating, inserting, and managing data.

2. **What is a primary key?**
   - A primary key is a column (or set of columns) that uniquely identifies each row in a table. It ensures that no two rows have the same value in the primary key column(s), and it cannot contain `NULL` values.

3. **What is a foreign key?**
   - A foreign key is a column or group of columns in one table that is used to reference the primary key in another table. It is used to establish and enforce a relationship between the data in two tables.

4. **What is the difference between `INNER JOIN` and `OUTER JOIN`?**
   - `INNER JOIN` returns only the rows that have matching values in both tables.
   - `OUTER JOIN` can return all rows from one table and the matching rows from the other table. It can be further classified into `LEFT JOIN`, `RIGHT JOIN`, and `FULL OUTER JOIN`.

5. **What are indexes in SQL and why are they used?**
   - An index is a database object that improves the speed of data retrieval operations on a table. Indexes are created on columns that are often used in `WHERE` clauses or joins to make searches faster. However, they also slow down `INSERT` and `UPDATE` operations due to the need to maintain the index.

6. **What is a `UNION` and when would you use it?**
   - `UNION` combines the result sets of two or more `SELECT` queries into a single result set, removing duplicates. You use it when you need to combine results from multiple queries with the same number of columns and corresponding data types.

7. **What is normalization?**
   - Normalization is the process of organizing the data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller, more efficient tables and defining relationships between them using foreign keys. Common normal forms include 1NF, 2NF, 3NF, and BCNF.

8. **What is denormalization?**
   - Denormalization is the process of combining tables or data to improve query performance by reducing the number of joins needed. This usually introduces some redundancy but can lead to faster read performance in specific use cases.

9. **What is a `CHECK` constraint?**
   - A `CHECK` constraint is used to limit the value range that can be placed in a column. It ensures that all values in a column satisfy a specific condition.

---

### **Advanced SQL Concepts**

10. **What is a stored procedure?**
    - A stored procedure is a group of SQL statements that are stored in the database and can be executed as a single unit. They are used to encapsulate logic, improve performance, and ensure security by restricting direct access to data.

11. **What is the difference between a stored procedure and a function?**
    - A stored procedure can perform operations like modifying data, whereas a function is designed to return a single value or table but cannot modify data. Stored procedures can also return multiple results, while functions return only one.

12. **What is a trigger in SQL?**
    - A trigger is a special type of stored procedure that is automatically invoked in response to specific events on a table, such as `INSERT`, `UPDATE`, or `DELETE`. Triggers are used to enforce business rules, data integrity, and automatic auditing.

13. **Explain the concept of ACID properties in a database.**
    - ACID stands for Atomicity, Consistency, Isolation, and Durability, which are properties that ensure reliable database transactions.
      - **Atomicity**: Ensures that all parts of a transaction are completed, or none are.
      - **Consistency**: Ensures that the database remains in a consistent state before and after the transaction.
      - **Isolation**: Ensures that transactions do not interfere with each other.
      - **Durability**: Ensures that once a transaction is committed, it remains permanent even in the case of a system failure.

14. **What are the different types of joins in SQL?**
    - **INNER JOIN**: Returns only the rows where there is a match in both tables.
    - **LEFT JOIN (LEFT OUTER JOIN)**: Returns all rows from the left table and the matching rows from the right table. If no match is found, `NULL` values are returned for columns from the right table.
    - **RIGHT JOIN (RIGHT OUTER JOIN)**: Returns all rows from the right table and the matching rows from the left table. If no match is found, `NULL` values are returned for columns from the left table.
    - **FULL OUTER JOIN**: Returns all rows when there is a match in either table, and `NULL` for unmatched rows.
    - **CROSS JOIN**: Returns the Cartesian product of two tables, meaning all combinations of rows.

15. **What is a subquery, and what are the different types?**
    - A subquery is a query within another query. There are two types:
      - **Correlated subquery**: A subquery that depends on the outer query for its values.
      - **Non-correlated subquery**: A subquery that is independent of the outer query and can be run on its own.

16. **Explain the difference between `HAVING` and `WHERE` clauses.**
    - The `WHERE` clause is used to filter rows before grouping or aggregation, while the `HAVING` clause is used to filter groups or aggregates after the `GROUP BY` clause.

17. **What are `CROSS APPLY` and `OUTER APPLY` in SQL?**
    - `CROSS APPLY` is like an inner join, where the right-side table function is evaluated for each row of the left-side table, and only rows with matching results are returned. `OUTER APPLY` is like a left join, returning all rows from the left-side table and `NULL` values from the right-side table if no match is found.

18. **What is a Common Table Expression (CTE)?**
    - A Common Table Expression (CTE) is a temporary result set that you can reference within a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement. It is defined using the `WITH` clause and can be recursive or non-recursive.

---

### **Performance Optimization and Indexing**

19. **What are the types of indexes in SQL?**
    - **Clustered Index**: Determines the physical order of data in the table and can only have one per table.
    - **Non-clustered Index**: Does not alter the physical order of data, and a table can have multiple non-clustered indexes.

20. **What is the `EXPLAIN` command used for?**
    - The `EXPLAIN` command is used to analyze and display the execution plan of a query. It helps in understanding how the SQL engine processes the query, which can be useful for performance optimization.

21. **What are the best practices for writing efficient SQL queries?**
    - Use indexes wisely.
    - Avoid using `SELECT *`—only retrieve the necessary columns.
    - Use joins instead of subqueries when possible.
    - Avoid excessive use of `DISTINCT`, as it adds overhead.
    - Use `EXISTS` instead of `IN` for large datasets.
    - Normalize your database to remove redundancy.
    - Analyze query execution plans with `EXPLAIN`.

22. **What is query optimization, and how would you approach it?**
    - Query optimization is the process of enhancing the performance of an SQL query. Some common approaches include:
      - Creating proper indexes.
      - Using `EXPLAIN` to analyze query performance.
      - Reducing the use of `SELECT *` by fetching only necessary columns.
      - Applying proper indexing and partitioning.
      - Minimizing the use of functions in `WHERE` clauses.
      - Avoiding correlated subqueries if possible.

23. **What is database partitioning, and when would you use it?**
    - Partitioning is the process of dividing a large table into smaller, more manageable pieces while maintaining a logical whole. It improves query performance and manageability, especially for large datasets. It’s often used in data warehousing and large transactional systems.

24. **What is a materialized view?**
    - A materialized view is a view where the query results are stored and periodically refreshed. It can improve performance for complex queries because the result set is precomputed and stored in the database.

25. **What are the advantages of using an index, and when might it not be beneficial?**
    - Indexes improve query performance by allowing the database to quickly locate rows. However, indexes can slow down `INSERT`, `UPDATE`, and `DELETE` operations due to the overhead of maintaining the index. They also consume additional storage space.

---

### **SQL Functions**

26. **What is a window function in SQL?**
    - A window function performs calculations across a set of table rows that are related to the current row. It is often used in analytics and reporting. Examples include `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, and `LEAD()`.

27. **What is the difference between `RANK()` and `DENSE_RANK()`?**
    - `RANK()` assigns a unique rank to each row, but it leaves gaps in the ranking if there are ties. `DENSE_RANK()` assigns a rank without gaps, even if there are ties.

28

. **What is the purpose of the `COALESCE()` function in SQL?**
    - The `COALESCE()` function returns the first non-`NULL` value in a list of expressions. It’s commonly used to handle `NULL` values.

29. **What is the difference between `COUNT(*)`, `COUNT(column)`, and `COUNT(DISTINCT column)`?**
    - `COUNT(*)` counts all rows in the table.
    - `COUNT(column)` counts the number of non-`NULL` values in the column.
    - `COUNT(DISTINCT column)` counts the number of unique, non-`NULL` values in the column.

30. **How does the `GROUP BY` clause work?**
    - The `GROUP BY` clause is used to group rows that have the same values in specified columns into summary rows. It’s commonly used with aggregate functions like `SUM()`, `COUNT()`, and `AVG()` to perform calculations on each group.
