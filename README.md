
# SQL Fundamentals & Reference Guide
This repository contains SQL exercises and scripts focused on data retrieval, filtering, and conditional logic.
Below is a breakdown of the core commands and best practices used throughout these files.
## 🛠 Core SQL Statement Order
SQL requires a specific order of statements to execute correctly. Writing them in the wrong order will cause a syntax error.
 1. **SELECT**: Specifies which columns to retrieve.
 2. **FROM**: Specifies the table (or schema) containing the data.
 3. **WHERE**: Filters rows based on specific conditions.
 4. **GROUP BY**: Organizes data into categorical groups (e.g., department, city).
 5. **ORDER BY**: Sorts the final results.
## 🔍 Basic Commands
### 1. SELECT & FROM
 * **SELECT ***: Use the asterisk wildcard to return every column in a table.
 * **SELECT DISTINCT**: Returns only unique values, removing any duplicates.
 * **Aliases (AS)**: Renames a column or table temporarily for better readability (e.g., SELECT product_id AS barcode).
 * **Commas**: Must be placed between column names but **never** after the last column.
### 2. WHERE (Filtering Rows)
The WHERE clause is used to narrow down results.
 * **Text Values**: Must be wrapped in single quotes (e.g., WHERE city = 'Chicago').
 * **AND/OR**: AND requires both conditions to be true simultaneously, while OR requires at least one to be true.
 * **BETWEEN**: This operator is inclusive, meaning it includes both the minimum and maximum boundary values.
 * **IN**: Used to check if a value matches any value in a list (e.g., WHERE city IN ('JHB', 'PTA')).
### 3. ORDER BY (Sorting)
 * **ASC**: Sorts data from smallest to biggest (default).
 * **DESC**: Sorts data from biggest to smallest (useful for "most expensive" or "newest").
### 4. GROUP BY & Aggregations
To summarize data, use aggregate functions with GROUP BY on a categorical column.
 * **SUM()**: Adds all values in a column together.
 * **COUNT(DISTINCT)**: Returns the number of unique/different values in a column.
 * **AVG()**: Calculates the average of the values.
## ⚖️ Conditional Logic (CASE Statement)
The CASE statement creates a **new column** in your result set based on conditional logic. It is evaluated from top to bottom and stops at the first match.
**Syntax Example:**
```sql
SELECT product_name,
    CASE 
        WHEN price > 1000 THEN 'Expensive'
        WHEN price BETWEEN 100 AND 1000 THEN 'Mid-range'
        ELSE 'Budget'
    END AS price_category 
FROM products;

```
## 📅 Date Functions Quick Reference
The following functions allow for precise time-based analysis:
 * **YEAR() / MONTH() / DAY()**: Extracts specific parts of a date.
 * **DATEADD / DATE_ADD**: Adds a specific time interval to a date (e.g., adding 2 years).
 * **DATEDIFF**: Calculates the difference (e.g., number of years or days) between two dates.
 * **NOW() / GETDATE() / CURRENT_DATE**: Retrieves the current date or timestamp from the server.
## 💡 Pro-Tips
 * **Case Sensitivity**: SQL keywords (like SELECT) are not case-sensitive, but the **data** inside the tables often is
 * (e.g., 'Johannesburg' ≠ 'johannesburg').
 * **Semi-colons (;)**: Used to end a SQL query; it is a best practice and required by many platforms.
 * **Indexing**: Avoid wrapping indexed date columns in functions (like WHERE YEAR(date) = 2026) as it can slow down your query.
 *  Use range conditions
 *  (e.g., WHERE date >= '2026-01-01') instead.
