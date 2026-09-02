
# Aggregates

## Introduction

**What are aggregate functions?**

Aggregate functions perform calculations across multiple rows and return a single result.

Common PostgreSQL aggregate functions include:

| Function | Description |
|---|---|
| `COUNT()` | Counts rows or non-null values |
| `SUM()` | Adds numeric values |
| `AVG()` | Calculates the arithmetic mean |
| `MIN()` | Returns the smallest value |
| `MAX()` | Returns the largest value |

For example, consider the following product prices:

| product | price |
|---|---:|
| Mouse | 25 |
| Keyboard | 80 |
| Monitor | 350 |

The following query returns the lowest price:

```sql
SELECT MIN(price)
FROM products;
```

Result:

```text
25
```

**Example dataset**

Throughout this lesson, you will use a `sales` table.

```sql
CREATE TABLE sales (
    sale_id SERIAL PRIMARY KEY,
    salesperson VARCHAR(50),
    region VARCHAR(50),
    product VARCHAR(50),
    amount NUMERIC(10,2)
);
```

Add the sample records:

```sql
INSERT INTO sales
    (salesperson, region, product, amount)
VALUES
    ('Alice', 'North', 'Laptop', 1200),
    ('Alice', 'North', 'Monitor', 400),
    ('Bob', 'South', 'Monitor', 350),
    ('Bob', 'South', 'Laptop', 1400),
    ('Charlie', 'North', 'Keyboard', 100),
    ('Charlie', 'East', 'Laptop', 1300),
    ('Diana', 'East', 'Monitor', 450);
```

Review the dataset:

```sql
SELECT *
FROM sales
ORDER BY sale_id;
```

---

## COUNT()

COUNT() returns the number of rows or non-null values in a column.

Find how many sales were recorded:

```sql
SELECT COUNT(*) AS total_sales
FROM sales;
```

Result:

```text
7
```

---
## MIN()

`MIN()` returns the smallest non-null value in a column.

Find the lowest sale amount:

```sql
SELECT MIN(amount) AS lowest_sale
FROM sales;
```

Result:

```text
100.00
```

`MIN()` can also operate on text values. With text, PostgreSQL returns the value that appears first according to the applicable sort order.

```sql
SELECT MIN(salesperson) AS first_salesperson
FROM sales;
```

Result:

```text
Alice
```

---

## MAX()

`MAX()` returns the largest non-null value in a column.

Find the highest sale amount:

```sql
SELECT MAX(amount) AS highest_sale
FROM sales;
```

Result:

```text
1400.00
```

An aggregate such as `MAX(amount)` returns the maximum value, but it does not automatically return the rest of the row containing that value. To retrieve the salesperson and amount for the highest sale, the results can instead be sorted:

```sql
SELECT
    salesperson,
    amount
FROM sales
ORDER BY amount DESC
LIMIT 1;
```

---

## Using AVG()

`AVG()` calculates the arithmetic mean of the non-null numeric values in a column.

```sql
SELECT AVG(amount) AS average_sale
FROM sales;
```

The result may contain several decimal places. Use `ROUND()` to make the output easier to read:

```sql
SELECT ROUND(AVG(amount), 2) AS average_sale
FROM sales;
```

Result:

```text
742.86
```

## Using GROUP BY

*GROUP BY* is used to group rows that have the same values in specified columns into summary rows.  In other words, it allows results to be grouped by unique values in a particular column.

*Without* `GROUP BY`, an aggregate calculation applies to all qualifying rows in the table.

```sql
SELECT ROUND(AVG(amount), 2) AS average_sale
FROM sales;
```

This produces one average for the entire table.

`GROUP BY` divides rows into categories before the aggregate function is applied.

For example, management may ask:

> What is the average sale amount in each region?

```sql
SELECT
    region,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY region;
```

Result:

| region | average_sale |
|---|---:|
| East | 875.00 |
| North | 566.67 |
| South | 875.00 |

Each distinct region forms a group. PostgreSQL calculates a separate average for each group.

??? "Activity"
    Create a query to group number of sales for each sales rep

---

## Selecting columns with GROUP BY

When a query contains `GROUP BY`, each selected column generally needs to be either:

- Included in the `GROUP BY` clause, or
- Used inside an aggregate function.

Correct:

```sql
SELECT
    region,
    AVG(amount) AS average_sale
FROM sales
GROUP BY region;
```

Incorrect:

```sql
SELECT
    region,
    salesperson,
    AVG(amount) AS average_sale
FROM sales
GROUP BY region;
```

The incorrect query selects `salesperson` without grouping or aggregating it. A region may contain several salespeople, so PostgreSQL cannot determine which salesperson should represent the group.

---

## Using multiple aggregate functions

Several aggregates can be calculated in the same query.

```sql
SELECT
    region,
    MIN(amount) AS lowest_sale,
    MAX(amount) AS highest_sale,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY region
ORDER BY region;
```

Result:

| region | lowest_sale | highest_sale | average_sale |
|---|---:|---:|---:|
| East | 450.00 | 1300.00 | 875.00 |
| North | 100.00 | 1200.00 | 566.67 |
| South | 350.00 | 1400.00 | 875.00 |

---

## Grouping by multiple columns

A query can group rows using more than one column.

```sql
SELECT
    region,
    product,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY region, product
ORDER BY region, product;
```

Each unique combination of `region` and `product` becomes a separate group.

Result:

| region | product | average_sale |
|---|---|---:|
| East | Laptop | 1300.00 |
| East | Monitor | 450.00 |
| North | Keyboard | 100.00 |
| North | Laptop | 1200.00 |
| North | Monitor | 400.00 |
| South | Laptop | 1400.00 |
| South | Monitor | 350.00 |


---

## Using HAVING

`HAVING` filters grouped results after aggregation.

A useful way to distinguish the clauses is:

- `WHERE` filters individual rows before grouping.
- `HAVING` filters groups after aggregation.

Show only regions with an average sale above $700:

```sql
SELECT
    region,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY region
HAVING AVG(amount) > 700;
```

Result:

| region | average_sale |
|---|---:|
| East | 875.00 |
| South | 875.00 |

**WHERE compared with HAVING**

Use `WHERE` when the condition applies to individual rows.

```sql
SELECT *
FROM sales
WHERE amount > 500;
```

Use `HAVING` when the condition applies to an aggregate result.

```sql
SELECT
    region,
    AVG(amount) AS average_sale
FROM sales
GROUP BY region
HAVING AVG(amount) > 700;
```

The following query is incorrect because an aggregate function cannot normally be used in `WHERE`:

```sql
SELECT
    region,
    AVG(amount) AS average_sale
FROM sales
WHERE AVG(amount) > 700
GROUP BY region;
```

---

## Combining WHERE, GROUP BY and HAVING

A query can use both `WHERE` and `HAVING` because they filter at different stages.

```sql
SELECT
    region,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
WHERE amount > 100
GROUP BY region
HAVING AVG(amount) > 500
ORDER BY average_sale DESC;
```

This query:

1. Reads rows from `sales`.
2. Removes individual sales of $100 or less.
3. Groups the remaining rows by region.
4. Calculates an average for each region.
5. Keeps groups with an average above $500.
6. Sorts the displayed results.

---

## Logical query-processing order

SQL is written beginning with `SELECT`, but its logical processing order is approximately:

```text
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
LIMIT
```

Understanding this order helps explain why:

- `WHERE` cannot normally filter an aggregate result.
- `HAVING` is evaluated after groups are created.
- A column alias created in `SELECT` may not be available to an earlier clause.

---

## Business reporting examples

Find the highest sale in each region:

```sql
SELECT
    region,
    MAX(amount) AS highest_sale
FROM sales
GROUP BY region
ORDER BY highest_sale DESC;
```

Find the lowest sale in each region:

```sql
SELECT
    region,
    MIN(amount) AS lowest_sale
FROM sales
GROUP BY region
ORDER BY lowest_sale;
```

Find the average sale for each salesperson:

```sql
SELECT
    salesperson,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY salesperson
ORDER BY average_sale DESC;
```

Find salespeople whose average sale is above $700:

```sql
SELECT
    salesperson,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY salesperson
HAVING AVG(amount) > 700
ORDER BY average_sale DESC;
```

## Practice

Write queries using the `sales` table to:

1. Find the highest sale amount.
2. Find the lowest sale amount.
3. Find the average sale amount.
4. Find the average sale amount by region.
5. Find the highest sale amount by region.
6. Find the minimum, maximum and average sale for each salesperson.
7. Show only regions with an average sale greater than $800.
8. Show only products with a maximum sale greater than $1,000.

**Worked challenge**

Create a report containing:

- Region
- Number of sales
- Lowest sale
- Highest sale
- Average sale

Only include regions where:

- The average sale is greater than $500.
- At least two sales were recorded.

```sql
SELECT
    region,
    COUNT(*) AS sales_count,
    MIN(amount) AS lowest_sale,
    MAX(amount) AS highest_sale,
    ROUND(AVG(amount), 2) AS average_sale
FROM sales
GROUP BY region
HAVING AVG(amount) > 500
   AND COUNT(*) >= 2
ORDER BY average_sale DESC;
```

**Common mistakes**

- Writing `GROUPBY` instead of the two-word clause `GROUP BY`.
- Using an aggregate function in `WHERE` instead of `HAVING`.
- Selecting columns that are neither grouped nor aggregated.
- Forgetting that aggregates normally ignore `NULL` values.
- Assuming `MAX(column)` returns the entire row containing the maximum value.
- Grouping by too many columns and accidentally creating overly specific groups.
- Forgetting to round an average when presenting financial or measurement data.

**Summary**

- `MIN()` returns the smallest non-null value.
- `MAX()` returns the largest non-null value.
- `AVG()` calculates the arithmetic mean of non-null numeric values.
- `GROUP BY` divides rows into groups before aggregates are calculated.
- Multiple columns can be used to create more detailed groups.
- `WHERE` filters individual rows before grouping.
- `HAVING` filters groups after aggregation.
- Multiple aggregate functions can appear in the same summary query.
