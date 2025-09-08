# SQL How to
SQL tips & tricks

* [The following pattern represents P(5): ``` * * *  * * *  * * * *  * * * * *  ``` Write a query to print the pattern P(20).](#The-following-pattern-represents-P-5-Write-a-query-to-print-the-pattern-P-20)
* [Query to calculate median value](#Query-to-calculate-median-value)
* [How to pivot a table in SQL Server?](#How-to-pivot-a-table-in-SQL-Server)
* [How to pivot a table in MySQL?](#How-to-pivot-a-table-in-MySQL)

## The following pattern represents P(5): ``` * * *  * * *  * * * *  * * * * *  ``` Write a query to print the pattern P(20).
Sample query using recursive cte
```sql
with recursive cte as
(
    select 1 as n
    union all
    select n + 1 from cte where n < 20
)
select repeat('* ', n) from cte;
```

[Top](#top)

## Query to calculate median value
```sql
SELECT x.value from table x, table y
GROUP BY x.value
HAVING SUM(SIGN(1 - SIGN(y.value - x.value))) = (COUNT(*) + 1) / 2
```

[Top](#top)

## How to pivot a table in SQL Server?
SQL Server provides a built-in `PIVOT` function, which makes pivoting quite easy.

### Example:
Assume you have a table `Sales` with columns `Year`, `Product` and `Revenue`. You want to pivot this data to show the revenue for each product across different years.

```sql
SELECT *
FROM (
    SELECT Year, Product, Revenue
    FROM Sales
) AS SourceTable
PIVOT (
    SUM(Revenue) 
    FOR Year IN ([2018], [2019], [2020])
) AS PivotTable;
```

### Explanation:
- The inner query selects the data.
- The `PIVOT` function is applied to transform the `Year` column into separate columns.
- The `SUM(Revenue)` aggregates the revenue values for each year.

[Top](#top)

## How to pivot a table in MySQL?
MySQL does not have a built-in `PIVOT` function, but you can simulate it using `CASE` statements and `GROUP BY`.

### Example:
Pivot a table `Sales` with columns `Year`, `Product` and `Revenue`, showing revenue for each year.

```sql
SELECT 
    Product,
    SUM(CASE WHEN Year = 2018 THEN Revenue ELSE 0 END) AS `2018`,
    SUM(CASE WHEN Year = 2019 THEN Revenue ELSE 0 END) AS `2019`,
    SUM(CASE WHEN Year = 2020 THEN Revenue ELSE 0 END) AS `2020`
FROM Sales
GROUP BY Product;
```

### Explanation:
- The `CASE` statement checks for each year and sums the revenue for each product accordingly.

- The `GROUP BY` groups by the product to create a row for each product with columns representing each year.

[Top](#top)
