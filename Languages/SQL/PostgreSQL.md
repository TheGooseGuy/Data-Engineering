# Basic SQL
## `SELECT`
```SQL
SELECT column1, column2, ...
FROM table_name;
```

```SQL
-- Select each and every column in a table
SELECT *
FROM table_name;
```
## `WHERE`
```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition1
	AND/OR condition2
	AND/OR condition3
```

**Logical Operators**

| Operator   | Definition                                   |
| ---------- | -------------------------------------------- |
| `=`        | Equals to                                    |
| `!=`, `<>` | Not Equals to                                |
| `<`, `>`   | Less than, more than                         |
| `<=`, `>=` | Less than or equal to, more than or equal to |
## `AND, OR, NOT`
```SQL
--Combine AND and OR operator
SELECT column1, column2, ...
FROM table_name
WHERE (condition1 OR condition 2)
	AND/OR condition 3;
```

```SQL
...
WHERE NOT condition
...
```
## `BETWEEN`
```SQL
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2
```
`BETWEEN` is inclusive, both the start and end values of the range are included.
## `IN`
```SQL
SELECT ...
FROM ...
WHERE column IN (...);
```
## `LIKE`
```SQL
SELECT ...
FROM ...
WHERE column LIKE ...
	AND/OR column NOT LIKE ...;
```
`%`: zero or multiple characters
`_`: a single character
## `ORDER BY`
Rows in relational database such as Postgres, MySQL, SQL Server, etc. aren't stored in particular order. Executing an identical `SELECT *` query twice doesn't produce same result.
```SQL
SELECT column1, column2
FROM table_name
WHERE condition(s)
ORDER BY column1, column2
-- ORDER BY column DESC (if descend)
-- ORDER BY 1, 2 DESC (order by column 1 and 2 (index))
OFFSET number -- Skip the first \number results
LIMIT number; -- Output first \number results
```
By default, `ORDER BY` sorts the result in ascending order (`ASC`)
# Intermediate SQL
## 5 SQL Aggregate Function

`COUNT()`, `SUM()`, `AVG()`, `MIN`, `MAX`

## `GROUP BY`
```SQL
SELECT ticker, 
       EXTRACT(YEAR FROM date) AS year, 
       ROUND(AVG(open),2) AS avg_open 
FROM stock_prices 
GROUP BY 1, 2 
ORDER BY year DESC;
```
`GROUP BY` can also be use to get rid of duplicates for certain columns

## `HAVING`
_aggregate functions are not allowed in WHERE_
`HAVING` can filter data based on values from aggregate functions
```SQL
SELECT ticker, AVG(open) 
FROM stock_prices
GROUP BY ticker 
HAVING AVG(open) > 200;
```
Difference between `WHERE` and `HAVING`: 

|                       | `WHERE`                | `HAVING`                               |
| --------------------- | ---------------------- | ------------------------------------- |
| When it filters       | Values before grouping | Values after groupi                    |
| Operates On Data From | Individual Rows       Aggregated Values from Groups of Rows om  |

## `DISTINCT`
`DISTINCT` is used in conjunction with the `SELECT` statement to return only distinct values.
(If there are multiple columns chosen, only include `DISTINCT` once)
```SQL
SELECT COUNT(DISTINCT column)
FROM table_name
```
## Arithmetic
`+`, `-`, `*`, `/`
`%` returns remainder
```SQL
SELECT 23 % 6; -- Returns 5
```
`^`: exponentiation
Order of operations: Parentheses, Exponents, Multiplication and Division, Addition and Subtraction
```SQL
SELECT column1 - column2 AS some_result
FROM table_name
```
## MATH FUNCTIONS
`ABS()`: absolute difference
```SQL
SELECT ABS(column1 - column2) AS abs_difference
FROM table_name
```

`ROUND()`: rounding numbers
```SQL
--round column1 to 2 decimal places
SELECT ROUND(column1, 2) AS rounded_col
FROM table_name
```

`CEIL()`: Round up

`FLOOR()`: Round down

`POWER()`: Raise a number to a specific power
```SQL
SELECT POWER(column, 2) AS squared_col
FROM table_name
```
`MOD()` or `%`: remainder of division

## Division
In SQL, integer division discards the remainder from the output, providing only the integer part of the result.

Three methods to return decimal/float output:

**`CAST()`**  
```SQL
SELECT 
  CAST(10 AS DECIMAL)/4, -- 2.5000000000000000
  CAST(10 AS FLOAT)/4,   -- 2.5
  10/CAST(6 AS DECIMAL), -- 1.6666666666666667
  10/CAST(6 AS FLOAT);   -- 1.6666666666666667
```

**Multiplication by 1.0**  
```SQL
SELECT 
  10/6,        -- 1
  10*1.0/6,    -- 1.6666666666666667
  10/6*1.0,    -- 1.0
  10/(6*1.0);  -- 1.6666666666666667
```

**::DECIMAL/::FLOAT**  
```SQL
SELECT 
  10::DECIMAL/4,  -- 2.5000000000000000
  10::FLOAT/4,    -- 2.5
  10/4::DECIMAL,  -- 2.5000000000000000
  10/4::FLOAT,    -- 2.5
  10::DECIMAL/6,  -- 1.6666666666666667
  10::FLOAT/6;    -- 1.6666666666666667
```
### Calculate Percentages

**Without rounding**  
`(Part / Total) * 100 AS percentage`

**With rounding**  
`((Part / Total) * 100, n) AS percentage`  
Here `n` specify the number of decimal places to round to.

### Different Ways of Representing Percentages
`0.50`: decimal, commonly used in mathematical calculations or when precision is important.

`50.0`: percentage with one decimal place, often used in reports or visualizations.

## NULL
```SQL
SELECT *
FROM table_name
WHERE column1 IS NULL
```

```SQL
SELECT *
FROM table_name
WHERE column1 IS NOT NULL
```

> In SQL's sorting order, `NULL` takes a special place as the smallest value. When a column containing `NULL` get's sorted, these `NULL` values ascend to the top of the result.

### `COALESCE()`
This function takes multiple inputs and returns the first non-null value.
```SQL
COALESCE(column_name, 'expression')
```
If `column_name` is NULL, it returns the specified expression. Otherwise, it returns the value of `column_name`.

### `IFNULL()`
Use `IFNULL()` function to fill in the gaps with default values.
```SQL
IFNULL(column_name, value_if_null)
```

## `CASE` Statement
### Use `CASE` Statement in `SELECT`
```SQL
SELECT
  column_1,
  column_2, 
  CASE 
    WHEN condition_1 THEN result_1
    WHEN condition_2 THEN result_2
    WHEN ... THEN ...
    ELSE result_3 -- If condition_1 and condition_2 are not met, return result_3 in ELSE clause
  END AS column_3_name -- Give your new column an alias
FROM table_1;  
```
### Use `CASE` in `WHERE`
```SQL
SELECT
  column_1,
  column_2
FROM table_1
WHERE CASE 
    WHEN condition_1 THEN result_1
    WHEN condition_2 THEN result_2
    WHEN ... THEN ...
    ELSE result_3 -- If condition_1 and condition_2 are not met, return result_3 in ELSE clause
  END; 
```
### Counting Results with `CASE` in `COUNT()`
```SQL
SELECT
  platform,
  COUNT(CASE 
    WHEN followers >= 500000 THEN 1
    ELSE NULL
  END) AS popular_actor_count,
  COUNT(CASE 
    WHEN followers < 500000 THEN 1
    ELSE NULL
  END) AS less_popular_actor_count
FROM marvel_avengers
GROUP BY platform;
```
### Adding Results with `CASE` in `SUM()`
```SQL
SELECT
  platform,
  SUM(CASE 
    WHEN engagement_rate >= 8.0 THEN followers
    ELSE 0
  END) AS high_engagement_followers_sum,
  SUM(CASE 
    WHEN engagement_rate < 8.0 THEN followers
    ELSE 0
  END) AS low_engagement_followers_sum
FROM marvel_avengers
GROUP BY platform;
```
### Averaging Results with `CASE` in `AVG()`
```SQL
SELECT
  platform,
  AVG(CASE 
    WHEN engagement_rate >= 8.0 THEN followers
    ELSE NULL
  END) AS avg_high_engagement_followers,
  AVG(CASE 
    WHEN engagement_rate < 8.0 THEN followers
    ELSE NULL
  END) AS avg_low_engagement_followers
FROM marvel_avengers
GROUP BY platform;
```
## `JOIN`
