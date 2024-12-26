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