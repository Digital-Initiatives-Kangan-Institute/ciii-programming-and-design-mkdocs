# PostgreSQL Aggregates with Joins

## Learning Outcomes

By the end of this mini-module, students will be able to:

- Join data from multiple tables.
- Use aggregate functions on joined data.
- Group results using `GROUP BY`.
- Filter aggregated results using `HAVING`.
- Create simple business reports from relational data.

---

## Why Use Aggregates with Joins?

In real-world databases, information is typically stored across multiple related tables.

For example:

- Customers are stored in a `customers` table.
- Orders are stored in an `orders` table.

To answer business questions such as:

> What is the average order value for each customer?

We need:

1. A `JOIN` to combine data from multiple tables.
2. Aggregate functions to summarise the combined data.

---

## Example Dataset

Create the customer table:

```sql
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    customer_name VARCHAR(50)
);
```

Create the orders table:

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    customer_id INT REFERENCES customers(customer_id),
    order_total NUMERIC(10,2)
);
```

Insert customers:

```sql
INSERT INTO customers
(customer_name)
VALUES
('Alice'),
('Bob'),
('Charlie'),
('Diana');
```

Insert orders:

```sql
INSERT INTO orders
(customer_id, order_total)
VALUES
(1, 250),
(1, 420),
(1, 180),
(2, 120),
(2, 300),
(3, 550),
(3, 650),
(3, 700),
(4, 90);
```

---

## Viewing Joined Data

Before using aggregates, verify the relationship between the tables.

```sql
SELECT
    c.customer_name,
    o.order_total
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id;
```

Result:

```text
Alice     250
Alice     420
Alice     180
Bob       120
Bob       300
Charlie   550
Charlie   650
Charlie   700
Diana      90
```

---

## COUNT() with JOIN

Count how many orders each customer has placed.

```sql
SELECT
    c.customer_name,
    COUNT(o.order_id) AS order_count
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

Result:

```text
Alice      3
Bob        2
Charlie    3
Diana      1
```

---

## MIN() with JOIN

Find the smallest order placed by each customer.

```sql
SELECT
    c.customer_name,
    MIN(o.order_total) AS smallest_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

Result:

```text
Alice      180
Bob        120
Charlie    550
Diana       90
```

---

## MAX() with JOIN

Find the largest order placed by each customer.

```sql
SELECT
    c.customer_name,
    MAX(o.order_total) AS largest_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

Result:

```text
Alice      420
Bob        300
Charlie    700
Diana       90
```

---

## AVG() with JOIN

Find the average order value for each customer.

```sql
SELECT
    c.customer_name,
    ROUND(AVG(o.order_total), 2) AS average_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
```

Result:

```text
Alice      283.33
Bob        210.00
Charlie    633.33
Diana       90.00
```

---

## Multiple Aggregates in a Single Query

Many business reports require several aggregate calculations at once.

```sql
SELECT
    c.customer_name,
    COUNT(*) AS order_count,
    MIN(o.order_total) AS smallest_order,
    MAX(o.order_total) AS largest_order,
    ROUND(AVG(o.order_total), 2) AS average_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name
ORDER BY c.customer_name;
```

Result:

```text
Alice      3     180     420     283.33
Bob        2     120     300     210.00
Charlie    3     550     700     633.33
Diana      1      90      90      90.00
```

---

## Using HAVING with Joins

`HAVING` filters groups after aggregate calculations have been performed.

Display customers whose average order value is greater than $250.

```sql
SELECT
    c.customer_name,
    ROUND(AVG(o.order_total), 2) AS average_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY c.customer_name
HAVING AVG(o.order_total) > 250;
```

Result:

```text
Alice      283.33
Charlie    633.33
```

---

## Using WHERE and HAVING Together

Find customers whose orders are greater than $100 and whose average remaining order value exceeds $300.

```sql
SELECT
    c.customer_name,
    ROUND(AVG(o.order_total), 2) AS average_order
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.order_total > 100
GROUP BY c.customer_name
HAVING AVG(o.order_total) > 300;
```

---

## Three-Table Example

Many databases contain multiple related tables.

```text
CUSTOMERS
    |
    |
    v
ORDERS
    |
    |
    v
ORDER_ITEMS
```

Example query:

```sql
SELECT
    c.customer_name,
    SUM(oi.quantity) AS total_items_purchased
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id
INNER JOIN order_items oi
    ON o.order_id = oi.order_id
GROUP BY c.customer_name;
```

This aggregates data across three related tables.

---

## Student Activity

Using the `customers` and `orders` tables, write queries to answer the following questions:

1. How many orders has each customer placed?
2. What is the smallest order for each customer?
3. What is the largest order for each customer?
4. What is the average order value for each customer?
5. Which customers have an average order value greater than $300?
6. Which customers have placed more than two orders?
7. Create a report showing:
   - Customer name
   - Number of orders
   - Minimum order
   - Maximum order
   - Average order

---

## Challenge Activity

Create a report showing:

- Customer name
- Number of orders
- Lowest order
- Highest order
- Average order

Only include customers where:

- The average order value is greater than $250
- The customer has made at least 2 orders

Sort the result by average order value descending.

---

## Summary

- `JOIN` combines related data from multiple tables.
- `COUNT()`, `MIN()`, `MAX()`, and `AVG()` can be used on joined data.
- `GROUP BY` creates groups before aggregate calculations occur.
- `HAVING` filters aggregated groups.
- Most reporting queries combine:
  - `JOIN`
  - `GROUP BY`
  - Aggregate functions
  - `HAVING`
- Business reporting often relies on aggregate functions across multiple related tables.
