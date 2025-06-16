# SQL String Functions - LEFT, RIGHT, SUBSTRING

<!-- Card Start -->
### Front
What do the LEFT(), RIGHT(), and SUBSTRING() functions do in SQL?

### Back
**String extraction functions** that return portions of a string:

- **LEFT(string, length)** → Returns leftmost characters
- **RIGHT(string, length)** → Returns rightmost characters  
- **SUBSTRING(string, start, length)** → Returns characters from a specific position

```sql
-- Examples with 'Hello World'
SELECT 
    LEFT('Hello World', 5) as left_part,      -- 'Hello'
    RIGHT('Hello World', 5) as right_part,    -- 'World'
    SUBSTRING('Hello World', 7, 5) as mid_part -- 'World'
FROM dual;
```

**Note**: Syntax may vary slightly between database systems (SUBSTR vs SUBSTRING).
<!-- Card End -->

<!-- Card Start -->
### Front
How do you sort employees by the last digit of their employee ID?

### Back
**Use RIGHT() to extract the last character** and convert to number for proper sorting:

```sql
-- Sort by last digit of employee_id
SELECT employee_id, name, department
FROM employees
ORDER BY CAST(RIGHT(employee_id, 1) AS INT);

-- Alternative using SUBSTRING
SELECT employee_id, name, department  
FROM employees
ORDER BY CAST(SUBSTRING(employee_id, LEN(employee_id), 1) AS INT);

-- Example results:
-- employee_id='1001' → last digit = 1
-- employee_id='2002' → last digit = 2
-- employee_id='1003' → last digit = 3
```

**Use case**: Distributing workload, creating balanced groups based on ID patterns.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you filter records based on the first 3 characters of a postal code?

### Back
**Use LEFT() to extract prefix characters** for filtering:

```sql
-- Find all customers in postal codes starting with specific prefixes
SELECT customer_name, postal_code, city
FROM customers
WHERE LEFT(postal_code, 3) IN ('902', '904', '906');

-- Filter by geographic regions using postal code patterns
SELECT *
FROM addresses
WHERE LEFT(postal_code, 3) BETWEEN '100' AND '199';  -- Manhattan zip codes

-- Combine with other conditions
SELECT customer_id, address, postal_code
FROM customers
WHERE LEFT(postal_code, 2) = '90'  -- California area codes
  AND city = 'Los Angeles';
```

**Use case**: Geographic filtering, regional analysis, postal code validation.
<!-- Card End -->

<!-- Card Start -->
### Front
Which function would you use to sort product codes like 'PROD-2023-001' by the year portion?

A) LEFT(product_code, 4)  
B) RIGHT(product_code, 3)  
C) SUBSTRING(product_code, 6, 4)  
D) MID(product_code, 6, 4)

### Back
**Correct Answer**: C (and D in some databases)

**Explanation**: For 'PROD-2023-001', the year '2023' starts at position 6 and is 4 characters long.

```sql
-- Extract year from product code for sorting
SELECT product_code, product_name
FROM products
WHERE SUBSTRING(product_code, 6, 4) = '2023'
ORDER BY SUBSTRING(product_code, 6, 4) DESC,  -- Year descending
         RIGHT(product_code, 3) ASC;          -- Sequence ascending

-- Breaking down 'PROD-2023-001':
-- Position: 123456789...
-- SUBSTRING(product_code, 6, 4) → '2023'
-- RIGHT(product_code, 3) → '001'
```

**Note**: MID() is an alias for SUBSTRING() in some databases like MySQL.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you create a custom sort order using SUBSTRING() for phone numbers?

### Back
**Extract area code and exchange using SUBSTRING()** for hierarchical sorting:

```sql
-- Sort phone numbers by area code, then exchange
SELECT customer_name, phone_number
FROM customers
WHERE phone_number IS NOT NULL
ORDER BY 
    SUBSTRING(phone_number, 1, 3) ASC,    -- Area code (first 3 digits)
    SUBSTRING(phone_number, 4, 3) ASC,    -- Exchange (next 3 digits)
    SUBSTRING(phone_number, 7, 4) ASC;    -- Last 4 digits

-- For formatted numbers like '(555) 123-4567'
SELECT customer_name, phone_number
FROM customers
ORDER BY 
    SUBSTRING(phone_number, 2, 3),        -- Area code inside parentheses
    SUBSTRING(phone_number, 7, 3),        -- Exchange after space
    SUBSTRING(phone_number, 11, 4);       -- Last 4 digits after dash
```

**Use case**: Telecommunications data analysis, geographic customer distribution.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you filter email addresses by domain using RIGHT() and SUBSTRING()?

### Back
**Extract domain portion** using string functions for filtering:

```sql
-- Method 1: Using RIGHT() with calculated position
SELECT name, email
FROM users
WHERE RIGHT(email, LEN(email) - CHARINDEX('@', email)) = 'company.com';

-- Method 2: Using SUBSTRING() with CHARINDEX()
SELECT name, email  
FROM users
WHERE SUBSTRING(email, CHARINDEX('@', email) + 1, 50) IN ('gmail.com', 'yahoo.com');

-- Method 3: Simple approach for known domains
SELECT name, email
FROM users
WHERE email LIKE '%@company.com'
  AND RIGHT(email, 11) = 'company.com';  -- Ensures exact match

-- Get domain statistics
SELECT 
    SUBSTRING(email, CHARINDEX('@', email) + 1, 50) as domain,
    COUNT(*) as user_count
FROM users
WHERE email LIKE '%@%'
GROUP BY SUBSTRING(email, CHARINDEX('@', email) + 1, 50)
ORDER BY user_count DESC;
```
<!-- Card End -->

<!-- Card Start -->
### Front
How do you sort alphanumeric codes naturally (A1, A2, A10) instead of lexicographically?

### Back
**Split into alphabetic and numeric parts** for proper natural sorting:

```sql
-- Natural sort for codes like A1, A2, A10, B1, B2
SELECT product_code, description
FROM products
ORDER BY 
    LEFT(product_code, 1),                                    -- Letter part
    CAST(SUBSTRING(product_code, 2, 10) AS INT);             -- Number part as integer

-- For more complex patterns like 'ITEM-A-123'
SELECT item_code, item_name
FROM inventory
ORDER BY 
    SUBSTRING(item_code, 1, 4),                              -- 'ITEM'
    SUBSTRING(item_code, 6, 1),                              -- Letter after first dash
    CAST(SUBSTRING(item_code, 8, 10) AS INT);                -- Number part

-- Handle variable length prefixes
SELECT 
    product_id,
    LEFT(product_id, PATINDEX('%[0-9]%', product_id) - 1) as alpha_part,
    CAST(SUBSTRING(product_id, PATINDEX('%[0-9]%', product_id), 10) AS INT) as num_part
FROM products
ORDER BY alpha_part, num_part;
```

**Problem solved**: Prevents sorting A1, A10, A2 instead of A1, A2, A10.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you extract and filter by the file extension from a filename column?

### Back
**Use RIGHT() and SUBSTRING() with CHARINDEX()** to extract file extensions:

```sql
-- Extract file extension using RIGHT() and reverse search
SELECT 
    filename,
    RIGHT(filename, LEN(filename) - CHARINDEX('.', REVERSE(filename)) + 1) as extension
FROM documents;

-- Filter by specific file types
SELECT filename, file_size, upload_date
FROM documents
WHERE RIGHT(filename, 4) IN ('.pdf', '.doc', '.txt')
   OR RIGHT(filename, 5) = '.docx';

-- More robust approach handling multiple dots
SELECT filename, upload_date
FROM documents  
WHERE SUBSTRING(filename, 
    LEN(filename) - CHARINDEX('.', REVERSE(filename)) + 2, 
    CHARINDEX('.', REVERSE(filename)) - 1
) IN ('pdf', 'xlsx', 'png', 'jpg');

-- Group files by extension
SELECT 
    RIGHT(filename, LEN(filename) - CHARINDEX('.', REVERSE(filename)) + 1) as file_type,
    COUNT(*) as file_count,
    SUM(file_size) as total_size
FROM documents
GROUP BY RIGHT(filename, LEN(filename) - CHARINDEX('.', REVERSE(filename)) + 1)
ORDER BY file_count DESC;
```
<!-- Card End -->

<!-- Card Start -->
### Front
How do you create a search filter that matches partial matches at word boundaries using SUBSTRING()?

### Back
**Combine SUBSTRING() with CHARINDEX()** to find word boundary matches:

```sql
-- Find products where search term appears at word boundaries
DECLARE @search VARCHAR(50) = 'phone';

SELECT product_name, category
FROM products
WHERE 
    -- Match at beginning of string
    LEFT(LOWER(product_name), LEN(@search)) = LOWER(@search)
    OR
    -- Match after a space (word boundary)
    CHARINDEX(' ' + LOWER(@search), ' ' + LOWER(product_name)) > 0
    OR  
    -- Match with specific delimiters
    product_name LIKE '%[- ]' + @search + '%'
    OR
    product_name LIKE '%[- ]' + @search;

-- More sophisticated word boundary search
SELECT product_id, product_name
FROM products
WHERE EXISTS (
    SELECT 1 
    FROM (
        SELECT value as word
        FROM STRING_SPLIT(LOWER(product_name), ' ')
    ) words
    WHERE words.word LIKE LOWER(@search) + '%'
);

-- Extract first word for categorization
SELECT 
    LEFT(product_name, CHARINDEX(' ', product_name + ' ') - 1) as first_word,
    COUNT(*) as product_count
FROM products
GROUP BY LEFT(product_name, CHARINDEX(' ', product_name + ' ') - 1)
ORDER BY product_count DESC;
```
<!-- Card End -->

<!-- Card Start -->
### Front
What is the basic syntax of a CASE statement in SQL?

### Back
**CASE statement** provides conditional logic within SQL queries with two forms:

**Simple CASE:**
```sql
CASE column_name
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ELSE default_result
END
```

**Searched CASE:**
```sql
CASE 
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE default_result
END
```

**Example:**
```sql
SELECT 
    name,
    CASE department
        WHEN 'Engineering' THEN 'Tech'
        WHEN 'Marketing' THEN 'Business'
        ELSE 'Other'
    END as division
FROM employees;
```
<!-- Card End -->

<!-- Card Start -->
### Front
How do you use CASE to categorize numeric values into ranges?

### Back
**Use searched CASE with comparison operators** to create value ranges:

```sql
-- Categorize employees by salary ranges
SELECT 
    name,
    salary,
    CASE 
        WHEN salary < 30000 THEN 'Entry Level'
        WHEN salary BETWEEN 30000 AND 60000 THEN 'Mid Level'
        WHEN salary BETWEEN 60001 AND 100000 THEN 'Senior Level'
        WHEN salary > 100000 THEN 'Executive'
        ELSE 'Not Classified'
    END as salary_grade
FROM employees;

-- Age groups with CASE
SELECT 
    customer_name,
    age,
    CASE 
        WHEN age < 18 THEN 'Minor'
        WHEN age BETWEEN 18 AND 34 THEN 'Young Adult'
        WHEN age BETWEEN 35 AND 54 THEN 'Middle Age'
        WHEN age >= 55 THEN 'Senior'
        ELSE 'Unknown'
    END as age_group
FROM customers;
```

**Key point**: Use BETWEEN for inclusive ranges, or explicit comparisons for more control.
<!-- Card End -->

<!-- Card Start -->
### Front
How can you use CASE in aggregate functions for conditional counting?

### Back
**Combine CASE with aggregate functions** to perform conditional aggregation:

```sql
-- Count different types of orders
SELECT 
    customer_id,
    COUNT(*) as total_orders,
    COUNT(CASE WHEN status = 'completed' THEN 1 END) as completed_orders,
    COUNT(CASE WHEN status = 'cancelled' THEN 1 END) as cancelled_orders,
    SUM(CASE WHEN status = 'completed' THEN amount ELSE 0 END) as completed_revenue
FROM orders
GROUP BY customer_id;

-- Pivot-style aggregation using CASE
SELECT 
    department,
    AVG(CASE WHEN gender = 'M' THEN salary END) as avg_male_salary,
    AVG(CASE WHEN gender = 'F' THEN salary END) as avg_female_salary,
    COUNT(CASE WHEN hire_date >= '2023-01-01' THEN 1 END) as new_hires_2023
FROM employees
GROUP BY department;
```

**Pattern**: `COUNT(CASE WHEN condition THEN 1 END)` counts matching rows, `SUM(CASE WHEN condition THEN value ELSE 0 END)` sums conditionally.
<!-- Card End -->

<!-- Card Start -->
### Front
Which CASE statement correctly handles NULL values?

A) `CASE WHEN column = NULL THEN 'Empty' ELSE 'Has Value' END`  
B) `CASE WHEN column IS NULL THEN 'Empty' ELSE 'Has Value' END`  
C) `CASE WHEN ISNULL(column) THEN 'Empty' ELSE 'Has Value' END`  
D) Both B and C

### Back
**Correct Answer**: B (and possibly D depending on database)

**Explanation**: NULL comparisons require `IS NULL` or `IS NOT NULL`, not `= NULL`.

```sql
-- Correct NULL handling
SELECT 
    customer_name,
    CASE 
        WHEN phone IS NULL THEN 'No Phone'
        WHEN phone = '' THEN 'Empty Phone'
        ELSE 'Has Phone'
    END as phone_status,
    CASE 
        WHEN email IS NOT NULL AND email <> '' THEN 'Contactable'
        ELSE 'No Email Contact'
    END as email_status
FROM customers;

-- Handle multiple NULL scenarios
SELECT 
    product_name,
    CASE 
        WHEN price IS NULL THEN 'Price TBD'
        WHEN price = 0 THEN 'Free'
        WHEN price < 10 THEN 'Budget'
        ELSE 'Premium'
    END as price_category
FROM products;
```

**Remember**: `= NULL` always returns NULL (false), use `IS NULL` instead.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you use nested CASE statements for complex conditional logic?

### Back
**Nest CASE statements** or use multiple conditions for complex business rules:

```sql
-- Nested CASE for complex shipping logic
SELECT 
    order_id,
    weight,
    destination,
    CASE 
        WHEN weight > 50 THEN 
            CASE destination
                WHEN 'Domestic' THEN 'Heavy Domestic'
                WHEN 'International' THEN 'Heavy International'
                ELSE 'Heavy Unknown'
            END
        WHEN weight <= 50 THEN
            CASE 
                WHEN destination = 'Domestic' AND weight <= 5 THEN 'Standard'
                WHEN destination = 'Domestic' THEN 'Medium Domestic'
                WHEN destination = 'International' THEN 'Light International'
                ELSE 'Standard International'
            END
        ELSE 'No Weight Data'
    END as shipping_type
FROM orders;

-- Alternative: Complex conditions in single CASE
SELECT 
    customer_id,
    order_count,
    total_spent,
    CASE 
        WHEN order_count >= 10 AND total_spent >= 1000 THEN 'VIP Gold'
        WHEN order_count >= 5 AND total_spent >= 500 THEN 'VIP Silver'
        WHEN order_count >= 3 OR total_spent >= 200 THEN 'Regular Plus'
        WHEN order_count >= 1 THEN 'Regular'
        ELSE 'New Customer'
    END as customer_tier
FROM customer_summary;
```

**Best practice**: Keep nesting to 2-3 levels maximum for readability.
<!-- Card End -->

# SQL Aggregate Functions - AVG()

<!-- Card Start -->
### Front
What does the AVG() function do in SQL?

### Back
**AVG() calculates the average value** of a numeric column:

```sql
-- Calculate average salary from employees table
SELECT AVG(salary) as avg_salary
FROM employees;

-- Average order amount
SELECT AVG(amount) as avg_order_amount
FROM orders
WHERE order_date >= '2023-01-01';

-- Group by department with average salary
SELECT department, AVG(salary) as avg_salary
FROM employees
GROUP BY department
ORDER BY avg_salary DESC;
```

**Note**: AVG() ignores NULL values by default.
<!-- Card End -->

<!-- Card Start -->
### Front
How does the AVG() function handle NULL values?

### Back
**AVG() ignores NULL values** and calculates the average of non-NULL values only:

```sql
-- Sample data: scores = [85, 90, NULL, 95, NULL]
SELECT AVG(score) FROM test_results;  -- Result: 90 (270/3, not 270/5)

-- Compare with manual calculation
SELECT 
    AVG(score) as avg_excluding_nulls,
    SUM(score) / COUNT(*) as avg_including_nulls,
    COUNT(score) as non_null_count,
    COUNT(*) as total_count
FROM test_results;

-- Handle NULLs explicitly with COALESCE
SELECT AVG(COALESCE(score, 0)) as avg_with_zero_for_nulls
FROM test_results;
```

**Key point**: AVG() only considers rows where the column value is NOT NULL, which can affect your calculations if you expect NULLs to be treated as zeros.
<!-- Card End -->

<!-- Card Start -->
### Front
How do you calculate a weighted average using SQL?

### Back
**Use SUM() and division** to create weighted averages when each value has different importance:

```sql
-- Weighted average of course grades
SELECT 
    student_id,
    SUM(grade * credit_hours) / SUM(credit_hours) as weighted_gpa
FROM student_grades
GROUP BY student_id;

-- Weighted average with conditional weights
SELECT 
    product_category,
    SUM(rating * review_count) / SUM(review_count) as weighted_avg_rating
FROM product_reviews
WHERE review_count > 0
GROUP BY product_category;

-- Compare simple vs weighted average
SELECT 
    department,
    AVG(salary) as simple_average,
    SUM(salary * years_experience) / SUM(years_experience) as experience_weighted_avg
FROM employees
WHERE years_experience > 0
GROUP BY department;
```

**Formula**: `SUM(value * weight) / SUM(weight)` gives you the weighted average.
<!-- Card End -->

<!-- Card Start -->
### Front
Which query correctly calculates the average salary by department, excluding departments with fewer than 3 employees?

A) `SELECT department, AVG(salary) FROM employees GROUP BY department WHERE COUNT(*) >= 3;`  
B) `SELECT department, AVG(salary) FROM employees WHERE COUNT(*) >= 3 GROUP BY department;`  
C) `SELECT department, AVG(salary) FROM employees GROUP BY department HAVING COUNT(*) >= 3;`  
D) `SELECT department, AVG(salary) FROM employees HAVING COUNT(*) >= 3 GROUP BY department;`

### Back
**Correct Answer**: C

**Explanation**: Use HAVING to filter groups after GROUP BY, WHERE cannot use aggregate functions.

```sql
-- Correct: HAVING filters groups after aggregation
SELECT 
    department, 
    AVG(salary) as avg_salary,
    COUNT(*) as employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) >= 3
ORDER BY avg_salary DESC;

-- Additional examples with AVG and HAVING
SELECT 
    department,
    AVG(salary) as avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 50000;  -- Departments with high average salary

-- Multiple conditions in HAVING
SELECT 
    department,
    AVG(salary) as avg_salary,
    COUNT(*) as headcount
FROM employees
GROUP BY department
HAVING COUNT(*) >= 3 
   AND AVG(salary) BETWEEN 40000 AND 80000;
```

**Remember**: WHERE filters rows before grouping, HAVING filters groups after aggregation.
<!-- Card End -->
