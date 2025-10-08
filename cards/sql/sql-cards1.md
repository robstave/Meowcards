# SQL Interview Flashcards

<!-- Card Start -->
### Front
What is the difference between `!=` and `<>` operators in SQL?

- A. They are identical  
- B. `!=` is faster  
- C. `<>` is the standard SQL operator  
- D. They are not supported in all databases

### Back
**Correct Answer**: C

**Explanation**: Both operators mean "not equal to" in SQL, but `<>` is the standard SQL operator. Most databases support both.

```sql
-- Both work the same way
SELECT * FROM users WHERE age != 25;
SELECT * FROM users WHERE age <> 25;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between `CHAR_LENGTH()` and `LENGTH()` functions?

### Back
**CHAR_LENGTH()** counts **characters**, **LENGTH()** counts **bytes**.

- `CHAR_LENGTH(name)` → counts characters (recommended)
- `LENGTH(name)` → counts bytes (can differ for multi-byte characters)

```sql
SELECT 
    name,
    CHAR_LENGTH(name) as char_count,
    LENGTH(name) as byte_count
FROM users;
```

*Important*: For emojis or non-ASCII characters, byte count may be higher than character count.
<!-- Card End -->

<!-- Card Start -->
### Front
What is a scalar subquery? Provide an example.

### Back
A **scalar subquery** returns exactly one value (single row, single column).

```sql
-- Find products with price above average
SELECT * FROM Products  
WHERE price > (SELECT AVG(price) FROM Products);
```

The subquery `(SELECT AVG(price) FROM Products)` returns one value that can be used in comparisons.
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between scalar and correlated subqueries?

### Back
| Type | Description | Independence |
|------|-------------|--------------|
| **Scalar subquery** | Returns single value, runs once | Independent of outer query |
| **Correlated subquery** | References outer query columns, runs for each row | Dependent on outer query |

```sql
-- Scalar: runs once
WHERE price > (SELECT AVG(price) FROM Products)

-- Correlated: runs for each row
WHERE price > (SELECT AVG(p2.price) FROM Products p2 WHERE p2.category = p1.category)
```
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between `GROUP BY` and `DISTINCT`?

### Back
**GROUP BY** enables aggregate functions, **DISTINCT** only removes duplicates.

```sql
-- DISTINCT: removes duplicates
SELECT DISTINCT category FROM products;

-- GROUP BY: allows aggregation
SELECT category, COUNT(*), AVG(price) 
FROM products 
GROUP BY category;
```

*Key point*: `GROUP BY` lets you use `AVG`, `MAX`, `MIN`, `SUM`, and `COUNT`.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you compare strings in SQL? Does `<> "boring"` work?

### Back
**Yes!** String comparisons work with all comparison operators:

```sql
-- All of these work for strings
SELECT * FROM movies WHERE title <> 'boring';
SELECT * FROM movies WHERE title != 'boring';
SELECT * FROM movies WHERE title = 'exciting';
SELECT * FROM movies WHERE title LIKE 'action%';
```

*Note*: Use single quotes `'` for string literals in standard SQL.
<!-- Card End -->

<!-- Card Start -->
### Front
Which SQL clause is used to filter groups created by GROUP BY?

A) WHERE  
B) HAVING  
C) FILTER  
D) GROUP_FILTER

### Back
**Correct Answer**: B

**Explanation**: `HAVING` filters groups after `GROUP BY` is applied.

```sql
SELECT category, COUNT(*) 
FROM products 
GROUP BY category 
HAVING COUNT(*) > 5;  -- Filter groups with more than 5 items
```

*Remember*: `WHERE` filters individual rows, `HAVING` filters groups.
<!-- Card End -->

<!-- Card Start -->
### Front
What does an INNER JOIN return?

### Back
**INNER JOIN** returns only rows that have matching values in both tables.

```sql
SELECT customers.name, orders.order_date
FROM customers
INNER JOIN orders ON customers.id = orders.customer_id;
```

*Result*: Only customers who have placed orders will appear in the result set.
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between LEFT JOIN and RIGHT JOIN?

### Back
**LEFT JOIN** keeps all rows from the left table, **RIGHT JOIN** keeps all rows from the right table.

```sql
-- LEFT JOIN: all customers, even without orders
SELECT c.name, o.order_date
FROM customers c
LEFT JOIN orders o ON c.id = o.customer_id;

-- RIGHT JOIN: all orders, even with invalid customer_id
SELECT c.name, o.order_date
FROM customers c
RIGHT JOIN orders o ON c.id = o.customer_id;
```
<!-- Card End -->

<!-- Card Start -->
### Front
Which JOIN type returns all rows from both tables?

A) INNER JOIN  
B) LEFT JOIN  
C) RIGHT JOIN  
D) FULL OUTER JOIN

### Back
**Correct Answer**: D

**Explanation**: `FULL OUTER JOIN` returns all rows from both tables, with NULLs where there's no match.

```sql
SELECT c.name, o.order_date
FROM customers c
FULL OUTER JOIN orders o ON c.id = o.customer_id;
```

*Result*: Customers without orders AND orders without valid customers.
<!-- Card End -->

<!-- Card Start -->
### Front
What does the SQL aggregate function COUNT(*) do?

### Back
**COUNT(*)** counts the total number of rows in a result set, including rows with NULL values.

```sql
SELECT COUNT(*) FROM employees;  -- Total employees
SELECT COUNT(phone) FROM employees;  -- Employees with phone numbers
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

*Key difference*: `COUNT(column)` ignores NULL values, `COUNT(*)` counts all rows.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you find the second highest salary in an employees table?

### Back
Multiple approaches:

**Method 1: Using LIMIT/TOP**
```sql
SELECT DISTINCT salary 
FROM employees 
ORDER BY salary DESC 
LIMIT 1 OFFSET 1;
```

**Method 2: Using subquery**
```sql
SELECT MAX(salary) 
FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);
```
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the ORDER BY clause?

### Back
**ORDER BY** sorts the result set by one or more columns.

```sql
-- Ascending order (default)
SELECT * FROM products ORDER BY price;

-- Descending order
SELECT * FROM products ORDER BY price DESC;

-- Multiple columns
SELECT * FROM products ORDER BY category, price DESC;
```

*Note*: `ASC` is default, `DESC` for descending order.
<!-- Card End -->

<!-- Card Start -->
### Front
Which SQL function would you use to get the current date?

A) NOW()  
B) CURRENT_DATE  
C) TODAY()  
D) Both A and B

### Back
**Correct Answer**: D

**Explanation**: Both work, but syntax varies by database:

```sql
-- Standard SQL
SELECT CURRENT_DATE;        -- Date only
SELECT CURRENT_TIMESTAMP;   -- Date and time

-- MySQL/PostgreSQL
SELECT NOW();               -- Date and time
SELECT CURDATE();           -- Date only (MySQL)
```
<!-- Card End -->

<!-- Card Start -->
### Front
What does the LIKE operator do? Provide examples with wildcards.

### Back
**LIKE** is used for pattern matching with wildcards:

- `%` → matches zero or more characters
- `_` → matches exactly one character

```sql
-- Names starting with 'A'
SELECT * FROM customers WHERE name LIKE 'A%';

-- Names ending with 'son'
SELECT * FROM customers WHERE name LIKE '%son';

-- Names with 'a' as second character
SELECT * FROM customers WHERE name LIKE '_a%';
```
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between WHERE and HAVING clauses?

### Back
**WHERE** filters individual rows before grouping, **HAVING** filters groups after GROUP BY.

```sql
SELECT category, COUNT(*), AVG(price)
FROM products 
WHERE price > 10          -- Filter rows first
GROUP BY category 
HAVING COUNT(*) > 5;      -- Then filter groups
```

*Order*: WHERE → GROUP BY → HAVING → ORDER BY
<!-- Card End -->

<!-- Card Start -->
### Front
How do you handle NULL values in SQL comparisons?

### Back
**NULL comparisons require special operators:**

```sql
-- Wrong: returns no results even if name is NULL
SELECT * FROM users WHERE name = NULL;

-- Correct: use IS NULL / IS NOT NULL
SELECT * FROM users WHERE name IS NULL;
SELECT * FROM users WHERE name IS NOT NULL;

-- COALESCE for default values
SELECT COALESCE(phone, 'No phone') FROM users;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What does the UNION operator do? How is it different from UNION ALL?

### Back
**UNION** combines results from multiple SELECT statements:

- `UNION` → removes duplicates
- `UNION ALL` → keeps all rows including duplicates

```sql
-- Removes duplicates
SELECT city FROM customers 
UNION 
SELECT city FROM suppliers;

-- Keeps duplicates (faster)
SELECT city FROM customers 
UNION ALL 
SELECT city FROM suppliers;
```
<!-- Card End -->

<!-- Card Start -->
### Front
Which aggregate function would you use to find the total sum of values?

A) COUNT()  
B) AVG()  
C) SUM()  
D) TOTAL()

### Back
**Correct Answer**: C

**Explanation**: `SUM()` calculates the total of numeric values.

```sql
-- Total sales
SELECT SUM(amount) FROM sales;

-- Sum by category
SELECT category, SUM(price) 
FROM products 
GROUP BY category;
```

*Note*: `SUM()` ignores NULL values.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you limit the number of rows returned in a query?

### Back
**Depends on the database system:**

```sql
-- MySQL, PostgreSQL
SELECT * FROM products LIMIT 10;

-- SQL Server
SELECT TOP 10 * FROM products;

-- Oracle
SELECT * FROM products WHERE ROWNUM <= 10;

-- Standard SQL (newer versions)
SELECT * FROM products FETCH FIRST 10 ROWS ONLY;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What is a foreign key and what does it ensure?

### Back
A **foreign key** is a column that references the primary key of another table, ensuring **referential integrity**.

```sql
CREATE TABLE orders (
    id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```

**Benefits**:
- Prevents invalid references
- Maintains data consistency
- Enables proper joins between tables
<!-- Card End -->

<!-- Card Start -->
### Front
How do you find duplicate records in a table?

### Back
**Use GROUP BY with HAVING COUNT(*) > 1:**

```sql
-- Find duplicate emails
SELECT email, COUNT(*) 
FROM users 
GROUP BY email 
HAVING COUNT(*) > 1;

-- Get full records of duplicates
SELECT * FROM users 
WHERE email IN (
    SELECT email FROM users 
    GROUP BY email 
    HAVING COUNT(*) > 1
);
```
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between DELETE, DROP, and TRUNCATE?

### Back
| Command | Action | Rollback | Speed |
|---------|--------|----------|-------|
| **DELETE** | Removes specific rows | Yes | Slow |
| **TRUNCATE** | Removes all rows | Limited | Fast |
| **DROP** | Removes entire table | Yes | Fast |

```sql
DELETE FROM users WHERE age < 18;  -- Remove specific rows
TRUNCATE TABLE temp_data;          -- Remove all rows, keep structure
DROP TABLE old_table;              -- Remove table completely
```
<!-- Card End -->

<!-- Card Start -->
### Front
How do you update data in SQL? Provide a safe example.

### Back
**Always use WHERE clause to avoid updating all rows:**

```sql
-- Safe update with WHERE
UPDATE products 
SET price = price * 1.1 
WHERE category = 'electronics';

-- Update multiple columns
UPDATE users 
SET last_login = NOW(), status = 'active' 
WHERE id = 123;
```

*Best practice*: Test with SELECT first to verify which rows will be affected.
<!-- Card End -->

<!-- Card Start -->
### Front
What does the INSERT statement do? Show different syntax options.

### Back
**INSERT** adds new rows to a table:

```sql
-- Specify columns (recommended)
INSERT INTO users (name, email, age) 
VALUES ('John Doe', 'john@email.com', 25);

-- Multiple rows
INSERT INTO users (name, email) 
VALUES 
    ('Alice', 'alice@email.com'),
    ('Bob', 'bob@email.com');

-- From another table
INSERT INTO archive_users SELECT * FROM users WHERE status = 'inactive';
```
<!-- Card End -->

<!-- Card Start -->
### Front
Which SQL clause is used to remove duplicate rows from query results?

A) UNIQUE  
B) DISTINCT  
C) REMOVE_DUPLICATES  
D) NO_DUPLICATES

### Back
**Correct Answer**: B

**Explanation**: `DISTINCT` removes duplicate rows from the result set.

```sql
-- Get unique cities
SELECT DISTINCT city FROM customers;

-- Distinct combination of columns
SELECT DISTINCT category, brand FROM products;
```

*Note*: DISTINCT applies to the entire row, not individual columns.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you create an index in SQL and why would you use one?

### Back
**CREATE INDEX** improves query performance by creating a data structure for faster lookups:

```sql
-- Create index on frequently searched column
CREATE INDEX idx_customer_email ON customers(email);

-- Composite index
CREATE INDEX idx_order_date_status ON orders(order_date, status);

-- Unique index
CREATE UNIQUE INDEX idx_product_sku ON products(sku);
```

**Benefits**: Faster SELECT, WHERE, ORDER BY, and JOIN operations.
**Cost**: Slower INSERT/UPDATE/DELETE operations.
<!-- Card End -->

<!-- Card Start -->
### Front
What is normalization in database design?

### Back
**Normalization** is organizing data to reduce redundancy and improve data integrity.

**Key Normal Forms**:
- **1NF**: Atomic values, no repeating groups
- **2NF**: 1NF + no partial dependencies
- **3NF**: 2NF + no transitive dependencies

**Benefits**:
- Eliminates data duplication
- Reduces storage space
- Improves data consistency
- Easier maintenance

*Trade-off*: May require more complex queries with joins.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you perform a CROSS JOIN and when would you use it?

### Back
**CROSS JOIN** returns the Cartesian product of two tables (every row from first table combined with every row from second table).

```sql
-- Explicit syntax
SELECT * FROM colors CROSS JOIN sizes;

-- Implicit syntax (same result)
SELECT * FROM colors, sizes;
```

**Use cases**:
- Generating all possible combinations
- Creating test data
- Mathematical operations requiring all pairs

*Warning*: Can produce very large result sets!
<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between a view and a table?

### Back
| Aspect | Table | View |
|--------|--------|------|
| **Storage** | Stores actual data | Stores query definition only |
| **Performance** | Direct access | Executes underlying query |
| **Updates** | Always updatable | Sometimes updatable |
| **Space** | Uses disk space | Minimal space |

```sql
-- Create a view
CREATE VIEW active_customers AS
SELECT * FROM customers WHERE status = 'active';

-- Use like a table
SELECT * FROM active_customers;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What is a Common Table Expression (CTE) and how do you use it?

### Back
A **CTE** is a temporary named result set that exists only during query execution.

```sql
-- Basic CTE
WITH high_earners AS (
    SELECT name, salary, department 
    FROM employees 
    WHERE salary > 50000
)
SELECT department, COUNT(*) as count
FROM high_earners
GROUP BY department;
```

**Benefits**:
- Improves readability
- Replaces complex subqueries
- Can be referenced multiple times
- Enables recursive queries
<!-- Card End -->

<!-- Card Start -->
### Front
How do you write a recursive CTE? Provide an example.

### Back
**Recursive CTEs** reference themselves to handle hierarchical data:

```sql
-- Find all employees and their management chain
WITH RECURSIVE employee_hierarchy AS (
    -- Base case: top-level managers
    SELECT id, name, manager_id, 1 as level
    FROM employees 
    WHERE manager_id IS NULL
    
    UNION ALL
    
    -- Recursive case
    SELECT e.id, e.name, e.manager_id, eh.level + 1
    FROM employees e
    JOIN employee_hierarchy eh ON e.manager_id = eh.id
)
SELECT * FROM employee_hierarchy ORDER BY level, name;
```

**Use case**: Organizational charts, bill of materials, any hierarchical data.
<!-- Card End -->

<!-- Card Start -->
### Front
What are window functions and how are they different from aggregate functions?

### Back
**Window functions** perform calculations across related rows without collapsing the result set.

| Aspect | Aggregate Functions | Window Functions |
|--------|-------------------|------------------|
| **Grouping** | Groups rows into single result | Keeps all individual rows |
| **Usage** | With GROUP BY | With OVER() clause |

```sql
-- Aggregate: collapses to groups
SELECT department, AVG(salary) FROM employees GROUP BY department;

-- Window: keeps all rows
SELECT name, salary, AVG(salary) OVER (PARTITION BY department) as dept_avg
FROM employees;
```

**Key point**: Window functions allow access to other rows in the result set without grouping.
<!-- Card End -->

<!-- Card Start -->
### Front
Which window function would you use to rank employees by salary within each department?

A) COUNT()  
B) RANK()  
C) SUM()  
D) AVG()

### Back
**Correct Answer**: B

**Explanation**: `RANK()` assigns rankings with gaps for ties.

```sql
SELECT 
    name, 
    department, 
    salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) as rank
FROM employees;
```

**Related functions**:
- `DENSE_RANK()` - no gaps in ranking
- `ROW_NUMBER()` - unique sequential numbers
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between RANK(), DENSE_RANK(), and ROW_NUMBER()?

### Back
| Function | Ties Handling | Example Results |
|----------|---------------|-----------------|
| **ROW_NUMBER()** | Unique numbers | 1, 2, 3, 4, 5 |
| **RANK()** | Gaps after ties | 1, 2, 2, 4, 5 |
| **DENSE_RANK()** | No gaps | 1, 2, 2, 3, 4 |

```sql
SELECT 
    name, 
    salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) as row_num,
    RANK() OVER (ORDER BY salary DESC) as rank,
    DENSE_RANK() OVER (ORDER BY salary DESC) as dense_rank
FROM employees;
```

*Note*: Use RANK when you want to allow ties and leave gaps, use DENSE_RANK to avoid gaps.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you use LAG() and LEAD() window functions?

### Back
**LAG()** accesses previous row, **LEAD()** accesses next row in the result set.

```sql
SELECT 
    date,
    revenue,
    LAG(revenue, 1) OVER (ORDER BY date) as prev_revenue,
    LEAD(revenue, 1) OVER (ORDER BY date) as next_revenue,
    revenue - LAG(revenue, 1) OVER (ORDER BY date) as growth
FROM monthly_sales
ORDER BY date;
```

**Parameters**: `LAG(column, offset, default_value)`
**Use cases**: Calculating differences, trends, comparisons with adjacent rows.
<!-- Card End -->

<!-- Card Start -->
### Front
What is a stored procedure and how do you create one?

### Back
A **stored procedure** is a precompiled set of SQL statements stored in the database.

```sql
-- SQL Server/MySQL syntax
CREATE PROCEDURE GetEmployeesByDepartment
    @dept_name VARCHAR(50)
AS
BEGIN
    SELECT name, salary, hire_date
    FROM employees 
    WHERE department = @dept_name
    ORDER BY salary DESC;
END;

-- Execute procedure
EXEC GetEmployeesByDepartment 'Engineering';
```

**Benefits**: Performance, security, code reuse, centralized business logic.
<!-- Card End -->

<!-- Card Start -->
### Front
What is a database trigger and when would you use one?

### Back
A **trigger** is a special stored procedure that automatically executes in response to database events.

```sql
-- Audit trigger example
CREATE TRIGGER salary_audit_trigger
AFTER UPDATE ON employees
FOR EACH ROW
BEGIN
    IF OLD.salary != NEW.salary THEN
        INSERT INTO salary_audit (employee_id, old_salary, new_salary, changed_date)
        VALUES (NEW.id, OLD.salary, NEW.salary, NOW());
    END IF;
END;
```

**Use cases**: Auditing, logging, data validation, automatic calculations.
**Types**: BEFORE, AFTER, INSTEAD OF triggers.
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between a clustered and non-clustered index?

### Back
| Type | Data Storage | Table Limit | Performance |
|------|-------------|-------------|-------------|
| **Clustered** | Data rows stored in index order | One per table | Fastest for range queries |
| **Non-clustered** | Separate structure pointing to data | Multiple per table | Good for specific lookups |

```sql
-- Clustered index (usually primary key)
CREATE CLUSTERED INDEX idx_employee_id ON employees(id);

-- Non-clustered index
CREATE NONCLUSTERED INDEX idx_employee_email ON employees(email);
```

*Key point*: Clustered index determines physical storage order.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you optimize a slow SQL query? List key strategies.

### Back
**Query Optimization Strategies**:

1. **Add appropriate indexes**
   ```sql
   CREATE INDEX idx_order_date ON orders(order_date);
   ```

2. **Use EXPLAIN/EXPLAIN PLAN**
   ```sql
   EXPLAIN SELECT * FROM orders WHERE order_date > '2023-01-01';
   ```

3. **Avoid SELECT **
4. **Use WHERE clauses effectively**
5. **Optimize JOIN conditions**
6. **Consider query rewriting**
7. **Update table statistics**
8. **Partition large tables**

*Tools*: Database-specific query analyzers, execution plans.
<!-- Card End -->

<!-- Card Start -->
### Front
What is database partitioning and why is it useful?

### Back
**Partitioning** divides large tables into smaller, manageable pieces based on specific criteria.

```sql
-- Range partitioning example (PostgreSQL)
CREATE TABLE sales (
    id INT,
    sale_date DATE,
    amount DECIMAL
) PARTITION BY RANGE (sale_date);

CREATE TABLE sales_2023 PARTITION OF sales
FOR VALUES FROM ('2023-01-01') TO ('2024-01-01');
```

**Benefits**:
- Improved query performance
- Easier maintenance
- Parallel processing
- Better backup/recovery

**Types**: Range, List, Hash, Composite partitioning.
<!-- Card End -->

<!-- Card Start -->
### Front
Which isolation level prevents dirty reads but allows phantom reads?

A) READ UNCOMMITTED  
B) READ COMMITTED  
C) REPEATABLE READ  
D) SERIALIZABLE

### Back
**Correct Answer**: B

**Explanation**: READ COMMITTED prevents dirty reads but allows non-repeatable reads and phantom reads.

| Isolation Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|----------------|------------|-------------------|--------------|
| READ UNCOMMITTED | ✓ | ✓ | ✓ |
| READ COMMITTED | ✗ | ✓ | ✓ |
| REPEATABLE READ | ✗ | ✗ | ✓ |
| SERIALIZABLE | ✗ | ✗ | ✗ |

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What is the MERGE statement and when would you use it?

### Back
**MERGE** performs INSERT, UPDATE, or DELETE operations in a single statement based on matching conditions.

```sql
MERGE target_table AS target
USING source_table AS source
ON target.id = source.id
WHEN MATCHED THEN 
    UPDATE SET target.name = source.name, target.salary = source.salary
WHEN NOT MATCHED BY TARGET THEN
    INSERT (id, name, salary) VALUES (source.id, source.name, source.salary)
WHEN NOT MATCHED BY SOURCE THEN
    DELETE;
```

**Use cases**: Data synchronization, upsert operations, ETL processes.
**Also known as**: UPSERT in some databases.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you handle transactions in SQL? Provide an example.

### Back
**Transactions** ensure data consistency using ACID properties:

```sql
BEGIN TRANSACTION;

-- Transfer money between accounts
UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

-- Check if both updates succeeded
IF @@ERROR = 0
    COMMIT TRANSACTION;
ELSE
    ROLLBACK TRANSACTION;
```

**Key commands**:
- `BEGIN/START TRANSACTION` - Start transaction
- `COMMIT` - Save changes
- `ROLLBACK` - Undo changes
- `SAVEPOINT` - Create checkpoint
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the COALESCE function?

### Back
**COALESCE** returns the first non-NULL value from a list of expressions.

```sql
-- Handle NULL values with defaults
SELECT 
    name,
    COALESCE(phone, email, 'No contact') as contact_method,
    COALESCE(salary, 0) as salary
FROM employees;

-- Equivalent to nested CASE statements
SELECT 
    name,
    CASE 
        WHEN phone IS NOT NULL THEN phone
        WHEN email IS NOT NULL THEN email
        ELSE 'No contact'
    END as contact_method
FROM employees;
```

**Use cases**: Providing default values, handling NULL data gracefully.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you pivot data in SQL? Show an example.

### Back
**PIVOT** transforms rows into columns:

```sql
-- Manual pivot using CASE statements
SELECT 
    year,
    SUM(CASE WHEN quarter = 'Q1' THEN sales ELSE 0 END) as Q1,
    SUM(CASE WHEN quarter = 'Q2' THEN sales ELSE 0 END) as Q2,
    SUM(CASE WHEN quarter = 'Q3' THEN sales ELSE 0 END) as Q3,
    SUM(CASE WHEN quarter = 'Q4' THEN sales ELSE 0 END) as Q4
FROM quarterly_sales
GROUP BY year;

-- SQL Server PIVOT syntax
SELECT year, Q1, Q2, Q3, Q4
FROM (SELECT year, quarter, sales FROM quarterly_sales) as src
PIVOT (SUM(sales) FOR quarter IN (Q1, Q2, Q3, Q4)) as pvt;
```

*Note*: Not all databases support PIVOT syntax, manual methods may be required.
<!-- Card End -->

<!-- Card Start -->
### Front
What are the different types of SQL constraints?

### Back
**SQL Constraints** enforce rules on data:

| Constraint | Purpose | Example |
|------------|---------|---------|
| **PRIMARY KEY** | Unique identifier | `id INT PRIMARY KEY` |
| **FOREIGN KEY** | Referential integrity | `FOREIGN KEY (dept_id) REFERENCES departments(id)` |
| **UNIQUE** | Prevent duplicates | `email VARCHAR(100) UNIQUE` |
| **NOT NULL** | Require values | `name VARCHAR(50) NOT NULL` |
| **CHECK** | Validate data | `CHECK (age >= 18)` |
| **DEFAULT** | Default values | `status VARCHAR(20) DEFAULT 'active'` |

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE NOT NULL,
    age INT CHECK (age >= 18),
    status VARCHAR(20) DEFAULT 'active'
);
```
<!-- Card End -->

<!-- Card Start -->
### Front
How do you find the Nth highest value in a column?

### Back
**Multiple approaches for finding Nth highest value:**

```sql
-- Method 1: Using LIMIT with OFFSET
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET (N-1);

-- Method 2: Using window functions
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) as rank
    FROM employees
) ranked
WHERE rank = N;

-- Method 3: Using subquery
SELECT MAX(salary)
FROM employees
WHERE salary < (
    SELECT MAX(salary) FROM employees
    WHERE salary < (SELECT MAX(salary) FROM employees)
); -- For 3rd highest
```

*Note*: Replace `N` with the desired rank number.
<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between UNION and JOIN operations?

### Back
**UNION** combines rows vertically, **JOIN** combines columns horizontally:

```sql
-- UNION: combines rows from similar tables
SELECT name, city FROM customers
UNION
SELECT name, city FROM suppliers;
-- Result: All names and cities from both tables

-- JOIN: combines columns from related tables
SELECT c.name, c.city, o.order_date
FROM customers c
JOIN orders o ON c.id = o.customer_id;
-- Result: Customer info with their order dates
```

**Key differences**:
- UNION requires same column structure
- JOIN requires relationship between tables
- UNION stacks data, JOIN expands data width
<!-- Card End -->

<!-- Card Start -->
### Front
How do you calculate running totals in SQL?

### Back
**Running totals** using window functions:

```sql
-- Running total of sales
SELECT 
    date,
    daily_sales,
    SUM(daily_sales) OVER (ORDER BY date) as running_total,
    AVG(daily_sales) OVER (ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) as seven_day_avg
FROM daily_sales
ORDER BY date;

-- Running total by category
SELECT 
    category,
    date,
    sales,
    SUM(sales) OVER (PARTITION BY category ORDER BY date) as category_running_total
FROM sales_data;
```

**Frame clause options**: ROWS, RANGE, UNBOUNDED PRECEDING/FOLLOWING
<!-- Card End -->

<!-- Card Start -->
### Front
What is a materialized view and how is it different from a regular view?

### Back
**Materialized views** store actual data, unlike regular views which store only queries:

| Aspect | Regular View | Materialized View |
|--------|-------------|-------------------|
| **Storage** | Query definition only | Actual result data |
| **Performance** | Executes query each time | Fast access to pre-computed data |
| **Freshness** | Always current | Needs manual/scheduled refresh |
| **Space** | Minimal | Uses storage space |

```sql
-- Create materialized view
CREATE MATERIALIZED VIEW sales_summary AS
SELECT 
    category,
    SUM(amount) as total_sales,
    COUNT(*) as order_count
FROM orders
GROUP BY category;

-- Refresh materialized view
REFRESH MATERIALIZED VIEW sales_summary;
```

*Note*: Materialized views require storage and need to be refreshed to stay updated.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you handle hierarchical data in SQL without recursive CTEs?

### Back
**Alternative approaches for hierarchical data:**

**1. Path Enumeration Model:**
```sql
-- Store complete path in each node
CREATE TABLE categories (
    id INT,
    name VARCHAR(50),
    path VARCHAR(255)  -- e.g., '1/5/12/'
);
```

**2. Nested Set Model:**
```sql
-- Store left and right boundaries
CREATE TABLE categories (
    id INT,
    name VARCHAR(50),
    lft INT,
    rgt INT
);

-- Find all descendants
SELECT * FROM categories 
WHERE lft > parent_lft AND rgt < parent_rgt;
```

**3. Closure Table:**
```sql
-- Separate table storing all ancestor-descendant pairs
CREATE TABLE category_closure (
    ancestor_id INT,
    descendant_id INT,
    depth INT
);
```

*Note*: Choose the model based on use case, query patterns, and data modification frequency.
<!-- Card End -->

<!-- Card Start -->
### Front
What are the different ways to concatenate strings in SQL?

### Back
**String concatenation methods vary by database:**

```sql
-- Standard SQL
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM users;

-- SQL Server
SELECT first_name + ' ' + last_name as full_name FROM users;

-- MySQL
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM users;
-- or
SELECT first_name + ' ' + last_name as full_name FROM users;

-- PostgreSQL
SELECT first_name || ' ' || last_name as full_name FROM users;
-- or
SELECT CONCAT(first_name, ' ', last_name) as full_name FROM users;

-- Handle NULLs with COALESCE
SELECT CONCAT(COALESCE(first_name, ''), ' ', COALESCE(last_name, ''));
```

*Note*: Use the method appropriate for your database system, and handle NULLs to avoid unexpected results.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you implement pagination in SQL?

### Back
**Pagination techniques for different databases:**

```sql
-- MySQL/PostgreSQL: LIMIT and OFFSET
SELECT * FROM products
ORDER BY id
LIMIT 20 OFFSET 40;  -- Page 3, 20 items per page

-- SQL Server: OFFSET and FETCH
SELECT * FROM products
ORDER BY id
OFFSET 40 ROWS
FETCH NEXT 20 ROWS ONLY;

-- Oracle: ROWNUM (older versions)
SELECT * FROM (
    SELECT ROWNUM as rn, p.* FROM products p
    WHERE ROWNUM <= 60
) WHERE rn > 40;

-- Performance tip: Use cursor-based pagination for large datasets
SELECT * FROM products
WHERE id > 1000  -- Last ID from previous page
ORDER BY id
LIMIT 20;
```

*Note*: Choose the method that best fits your database system and performance requirements.
<!-- Card End -->

<!-- Card Start -->
### Front
What is a deadlock and how can you prevent it?

### Back
A **deadlock** occurs when two or more transactions wait for each other to release locks, creating a circular dependency.

**Prevention strategies:**
1. **Consistent lock ordering**
   ```sql
   -- Always access tables in same order
   -- Transaction 1 & 2: users first, then orders
   ```

2. **Keep transactions short**
3. **Use appropriate isolation levels**
4. **Set lock timeouts**
   ```sql
   SET LOCK_TIMEOUT 5000;  -- 5 seconds
   ```

5. **Use NOLOCK hint (read uncommitted)**
   ```sql
   SELECT * FROM products WITH (NOLOCK);
   ```

**Detection**: Most databases automatically detect and resolve deadlocks by rolling back one transaction.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you find gaps in sequential data?

### Back
**Finding missing values in sequences:**

```sql
-- Find missing IDs in a sequence
WITH expected_sequence AS (
    SELECT generate_series(1, (SELECT MAX(id) FROM orders)) as expected_id
)
SELECT expected_id as missing_id
FROM expected_sequence
WHERE expected_id NOT IN (SELECT id FROM orders);

-- Alternative: using LAG
SELECT 
    prev_id + 1 as gap_start,
    current_id - 1 as gap_end
FROM (
    SELECT 
        id as current_id,
        LAG(id) OVER (ORDER BY id) as prev_id
    FROM orders
) gaps
WHERE current_id - prev_id > 1;
```

**Use cases**: Finding missing invoice numbers, detecting data import issues.
<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between CASE and IIF functions?

### Back
**CASE** is standard SQL for conditional logic, **IIF** is a shorthand for simple conditions:

```sql
-- CASE: full conditional logic
SELECT 
    name,
    CASE 
        WHEN salary < 30000 THEN 'Low'
        WHEN salary < 60000 THEN 'Medium'
        WHEN salary < 100000 THEN 'High'
        ELSE 'Executive'
    END as salary_band
FROM employees;

-- IIF: simple true/false conditions (SQL Server, Access)
SELECT 
    name,
    IIF(salary > 50000, 'High', 'Low') as salary_level
FROM employees;

-- IIF equivalent using CASE
SELECT 
    name,
    CASE WHEN salary > 50000 THEN 'High' ELSE 'Low' END as salary_level
FROM employees;
```

*Note*: IIF is not available in all database systems. Prefer CASE for portability.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you perform bulk insert operations efficiently?

### Back
**Efficient bulk insert strategies:**

```sql
-- Method 1: Multi-row VALUES
INSERT INTO products (name, price, category)
VALUES 
    ('Product 1', 10.99, 'Electronics'),
    ('Product 2', 15.99, 'Electronics'),
    ('Product 3', 25.99, 'Books');

-- Method 2: INSERT FROM SELECT
INSERT INTO archive_orders
SELECT * FROM orders WHERE order_date < '2023-01-01';

-- Method 3: Bulk insert from file (SQL Server)
BULK INSERT products
FROM 'C:\data\products.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);

-- Method 4: Disable constraints temporarily
ALTER TABLE products NOCHECK CONSTRAINT ALL;
-- Insert data
ALTER TABLE products CHECK CONSTRAINT ALL;
```

**Performance tips**: Use transactions, disable indexes during insert, increase batch size.
<!-- Card End -->

<!-- Card Start -->
### Front
What are table-valued parameters and how do you use them?

### Back
**Table-valued parameters** (SQL Server) allow passing table data to stored procedures:

```sql
-- 1. Create user-defined table type
CREATE TYPE ProductTableType AS TABLE (
    ProductName VARCHAR(50),
    Price DECIMAL(10,2),
    Category VARCHAR(30)
);

-- 2. Create procedure accepting table parameter
CREATE PROCEDURE InsertProducts
    @ProductTable ProductTableType READONLY
AS
BEGIN
    INSERT INTO Products (name, price, category)
    SELECT ProductName, Price, Category
    FROM @ProductTable;
END;

-- 3. Use from application code
DECLARE @Products ProductTableType;
INSERT INTO @Products VALUES ('Laptop', 999.99, 'Electronics');
INSERT INTO @Products VALUES ('Book', 19.99, 'Education');
EXEC InsertProducts @Products;
```

**Benefits**: Type safety, better performance than multiple individual calls.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you implement audit trails in SQL?

### Back
**Audit trail implementation strategies:**

**1. Trigger-based auditing:**
```sql
CREATE TABLE audit_log (
    table_name VARCHAR(50),
    operation VARCHAR(10),
    old_values TEXT,
    new_values TEXT,
    changed_by VARCHAR(50),
    changed_date DATETIME
);

CREATE TRIGGER products_audit
AFTER UPDATE ON products
FOR EACH ROW
BEGIN
    INSERT INTO audit_log VALUES (
        'products', 'UPDATE', 
        CONCAT('price:', OLD.price), 
        CONCAT('price:', NEW.price),
        USER(), NOW()
    );
END;
```

**2. Shadow table approach:**
```sql
-- Create identical table with audit columns
CREATE TABLE products_audit AS 
SELECT *, 'INSERT' as operation, NOW() as audit_date
FROM products WHERE 1=0;
```

**3. Application-level logging**
**4. Database-specific features** (CDC, temporal tables)
<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between a function and a stored procedure?

### Back
| Aspect | Function | Stored Procedure |
|--------|----------|------------------|
| **Return value** | Must return a value | Optional return value |
| **Usage** | In SELECT statements | Standalone execution |
| **Side effects** | Should be pure | Can modify data |
| **Transaction** | Cannot control | Can use transactions |
| **Performance** | Can be inlined | Compiled and cached |

```sql
-- Function example
CREATE FUNCTION CalculateAge(@BirthDate DATE)
RETURNS INT
AS
BEGIN
    RETURN DATEDIFF(YEAR, @BirthDate, GETDATE());
END;

-- Usage in query
SELECT name, dbo.CalculateAge(birth_date) as age FROM employees;

-- Stored procedure
CREATE PROCEDURE UpdateSalary(@EmployeeID INT, @NewSalary DECIMAL)
AS
BEGIN
    UPDATE employees SET salary = @NewSalary WHERE id = @EmployeeID;
END;
```

*Note*: Functions are generally used for computations, stored procedures for actions.
<!-- Card End -->

<!-- Card Start -->
### Front
What is the difference between MAX() and GREATEST() functions?

### Back
**MAX()** is an aggregate function that works across rows, **GREATEST()** compares values within a single row.

```sql
-- MAX: finds highest value across all rows
SELECT MAX(salary) FROM employees;

-- GREATEST: finds highest value within a row
SELECT name, GREATEST(salary, bonus, commission) as highest_pay
FROM employees;

-- Example with multiple columns
SELECT 
    product_name,
    GREATEST(price_jan, price_feb, price_mar) as highest_monthly_price
FROM product_prices;
```

**Key difference**: MAX aggregates data, GREATEST compares column values in the same row.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you use GREATEST() and LEAST() functions? What databases support them?

### Back
**GREATEST()** returns the largest value, **LEAST()** returns the smallest value from a list of expressions.

```sql
-- Find highest and lowest values across columns
SELECT 
    student_name,
    GREATEST(math_score, english_score, science_score) as best_score,
    LEAST(math_score, english_score, science_score) as worst_score
FROM student_grades;

-- Handle NULL values with COALESCE
SELECT GREATEST(COALESCE(score1, 0), COALESCE(score2, 0), COALESCE(score3, 0));
```

**Database Support**:
- ✅ MySQL, PostgreSQL, Oracle
- ❌ SQL Server (use CASE statements instead)

*Note*: If any argument is NULL, the result is NULL.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you implement GREATEST() and LEAST() functionality in SQL Server?

### Back
**SQL Server doesn't have GREATEST/LEAST**, but you can use CASE statements or VALUES with MAX/MIN:

```sql
-- Method 1: Using CASE statements
SELECT 
    name,
    CASE 
        WHEN salary >= bonus AND salary >= commission THEN salary
        WHEN bonus >= commission THEN bonus
        ELSE commission
    END as greatest_value;

-- Method 2: Using VALUES with MAX/MIN (SQL Server 2008+)
SELECT 
    name,
    (SELECT MAX(value) FROM (VALUES (salary), (bonus), (commission)) AS temp(value)) as greatest_value,
    (SELECT MIN(value) FROM (VALUES (salary), (bonus), (commission)) AS temp(value)) as least_value
FROM employees;

-- Method 3: Using IIF for simple cases
SELECT name, IIF(salary > bonus, salary, bonus) as higher_amount
FROM employees;
```
<!-- Card End -->

<!-- Card Start -->
### Front
Which function would you use to find the maximum salary across all employees vs. the highest of three salary components for each employee?

A) MAX() for both cases  
B) GREATEST() for both cases  
C) MAX() for all employees, GREATEST() for each employee  
D) GREATEST() for all employees, MAX() for each employee

### Back
**Correct Answer**: C

**Explanation**: 
- **MAX()** aggregates across rows (all employees)
- **GREATEST()** compares values within a row (per employee)

```sql
-- MAX: across all employees
SELECT MAX(salary) as company_highest_salary FROM employees;

-- GREATEST: within each employee's row
SELECT 
    name,
    GREATEST(base_salary, overtime_pay, bonus) as employee_highest_component
FROM employees;
```

*Remember*: MAX works vertically (across rows), GREATEST works horizontally (across columns).
<!-- Card End -->

<!-- Card Start -->
### Front
How do you handle NULL values when using GREATEST() and LEAST()?

### Back
**GREATEST/LEAST return NULL if any argument is NULL**. Use COALESCE or ISNULL to handle this:

```sql
-- Problem: NULL kills the result
SELECT GREATEST(10, 20, NULL);  -- Returns NULL

-- Solution 1: Use COALESCE with default values
SELECT 
    name,
    GREATEST(
        COALESCE(score1, 0), 
        COALESCE(score2, 0), 
        COALESCE(score3, 0)
    ) as best_score
FROM test_results;

-- Solution 2: Filter out NULLs first
SELECT 
    name,
    CASE 
        WHEN score1 IS NULL AND score2 IS NULL THEN score3
        WHEN score1 IS NULL THEN GREATEST(score2, score3)
        WHEN score2 IS NULL THEN GREATEST(score1, score3)
        ELSE GREATEST(score1, score2, score3)
    END as best_score
FROM test_results;
```

**Best practice**: Decide whether NULL should be treated as 0, ignored, or preserved.
<!-- Card End -->

<!-- Card Start -->
### Front
Show how to find the date closest to today using LEAST() with ABS().

### Back
**Use LEAST() with ABS() and date differences** to find the closest date:

```sql
-- Find the appointment date closest to today
SELECT 
    patient_name,
    appointment_date,
    ABS(DATEDIFF(DAY, appointment_date, GETDATE())) as days_difference
FROM appointments
WHERE appointment_date = (
    SELECT appointment_date
    FROM appointments a2 
    WHERE a2.patient_id = appointments.patient_id
    ORDER BY ABS(DATEDIFF(DAY, a2.appointment_date, GETDATE()))
    LIMIT 1
);

-- Using LEAST for multiple date differences
SELECT 
    date,
    current_value,
    LEAST(current_value, LAG(running_max, 1, 0) OVER (ORDER BY date)) as running_max
FROM (
    SELECT 
        date,
        sales as current_value,
        MAX(sales) OVER (ORDER BY date ROWS UNBOUNDED PRECEDING) as running_max
    FROM sales_data
) subquery;

-- High water mark with reset conditions
SELECT 
    month,
    sales,
    CASE 
        WHEN month_num = 1 THEN sales  -- Reset in January
        ELSE GREATEST(sales, LAG(high_water_mark) OVER (ORDER BY month))
    END as high_water_mark
FROM monthly_sales;
```

**Use case**: Finding nearest dates, closest values, minimum distances.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you use GREATEST() to implement a "high water mark" or running maximum?

### Back
**Combine GREATEST() with window functions** for running maximums:

```sql
-- Running maximum using window function
SELECT 
    date,
    daily_sales,
    MAX(daily_sales) OVER (ORDER BY date ROWS UNBOUNDED PRECEDING) as running_max
FROM sales_data;

-- Using GREATEST for conditional maximums
SELECT 
    date,
    current_value,
    GREATEST(current_value, LAG(running_max, 1, 0) OVER (ORDER BY date)) as running_max
FROM (
    SELECT 
        date,
        sales as current_value,
        MAX(sales) OVER (ORDER BY date ROWS UNBOUNDED PRECEDING) as running_max
    FROM sales_data
) subquery;

-- High water mark with reset conditions
SELECT 
    month,
    sales,
    CASE 
        WHEN month_num = 1 THEN sales  -- Reset in January
        ELSE GREATEST(sales, LAG(high_water_mark) OVER (ORDER BY month))
    END as high_water_mark
FROM monthly_sales;
```

*Note*: Adjust partitioning and ordering based on your specific requirements.
<!-- Card End -->

<!-- Card Start -->
### Front
What does DISTINCT do when used with multiple columns?

### Back
**DISTINCT applies to the entire row combination**, not individual columns.

```sql
-- This finds unique combinations of category AND brand
SELECT DISTINCT category, brand FROM products;

-- Example data and results:
-- Input:  category='Electronics', brand='Sony'
--         category='Electronics', brand='Apple' 
--         category='Electronics', brand='Sony'
-- Output: category='Electronics', brand='Sony'
--         category='Electronics', brand='Apple'
```

**Key point**: DISTINCT removes rows where ALL specified columns have the same values.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you count distinct values in a column?

### Back
**Use COUNT(DISTINCT column_name)** to count unique values:

```sql
-- Count unique customers who placed orders
SELECT COUNT(DISTINCT customer_id) as unique_customers FROM orders;

-- Count unique products sold
SELECT COUNT(DISTINCT product_id) as products_sold FROM order_items;

-- Multiple distinct counts in one query
SELECT 
    COUNT(DISTINCT customer_id) as unique_customers,
    COUNT(DISTINCT product_id) as unique_products,
    COUNT(*) as total_orders
FROM orders;
```

**Note**: COUNT(DISTINCT) ignores NULL values, just like regular COUNT.
<!-- Card End -->

<!-- Card Start -->
### Front
What's the difference between these two queries?

```sql
SELECT DISTINCT department FROM employees;
SELECT department FROM employees GROUP BY department;
```

### Back
**Functionally identical** - both return unique department names, but with different approaches:

| Aspect | DISTINCT | GROUP BY |
|--------|----------|----------|
| **Purpose** | Remove duplicates | Group for aggregation |
| **Performance** | Usually faster for simple deduplication | Enables aggregate functions |
| **Extensibility** | Limited | Can add COUNT(), SUM(), etc. |

```sql
-- DISTINCT: simple deduplication
SELECT DISTINCT department FROM employees;

-- GROUP BY: enables aggregation
SELECT department, COUNT(*) as employee_count 
FROM employees 
GROUP BY department;
```

**When to use**: DISTINCT for simple deduplication, GROUP BY when you need aggregates.
<!-- Card End -->

<!-- Card Start -->
### Front
Can you use DISTINCT with aggregate functions? Show examples.

### Back
**Yes! DISTINCT can be used inside aggregate functions** to operate only on unique values:

```sql
-- Sum of distinct salaries (removes duplicate salary amounts)
SELECT SUM(DISTINCT salary) FROM employees;

-- Average of distinct prices
SELECT AVG(DISTINCT price) FROM products;

-- Count distinct vs total count
SELECT 
    COUNT(*) as total_orders,
    COUNT(DISTINCT customer_id) as unique_customers,
    COUNT(DISTINCT product_id) as unique_products
FROM orders;

-- Multiple aggregates with DISTINCT
SELECT 
    department,
    COUNT(*) as total_employees,
    COUNT(DISTINCT salary) as unique_salary_levels,
    AVG(DISTINCT salary) as avg_unique_salary
FROM employees 
GROUP BY department;
```

*Note*: Using DISTINCT inside aggregates can have performance implications, test as needed.
<!-- Card End -->

<!-- Card Start -->
### Front
What happens when you use DISTINCT with NULL values?

### Back
**DISTINCT treats all NULL values as identical** and keeps only one NULL in the result:

```sql
-- Sample data: names = ['John', 'Jane', NULL, 'John', NULL]
SELECT DISTINCT name FROM users;
-- Result: ['John', 'Jane', NULL]  -- Only one NULL

-- With multiple columns containing NULLs
SELECT DISTINCT first_name, last_name FROM users;
-- NULLs in the same positions are treated as duplicates

-- Count distinct including NULLs
SELECT COUNT(DISTINCT name) FROM users;  -- NULLs not counted
SELECT COUNT(*) FROM (SELECT DISTINCT name FROM users) t;  -- NULLs included

-- Handle NULLs explicitly
SELECT DISTINCT COALESCE(name, 'Unknown') as name FROM users;
```

**Key point**: DISTINCT keeps one instance of NULL, but COUNT(DISTINCT) ignores NULLs.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you find rows that appear exactly once (no duplicates) in a table?

### Back
**Use GROUP BY with HAVING COUNT(*) = 1** to find unique rows:

```sql
-- Find customers who placed exactly one order
SELECT customer_id 
FROM orders 
GROUP BY customer_id 
HAVING COUNT(*) = 1;

-- Find products that appear in only one order
SELECT product_id
FROM order_items
GROUP BY product_id
HAVING COUNT(DISTINCT order_id) = 1;

-- Find emails that appear exactly once
SELECT email
FROM users
GROUP BY email
HAVING COUNT(*) = 1;

-- Get full records of unique rows
SELECT u.*
FROM users u
JOIN (
    SELECT email 
    FROM users 
    GROUP BY email 
    HAVING COUNT(*) = 1
) unique_emails ON u.email = unique_emails.email;
```

**Use case**: Data quality checks, finding singleton records.
<!-- Card End -->
