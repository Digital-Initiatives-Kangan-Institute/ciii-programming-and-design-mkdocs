# Aggregates with Joins

## Scenario

Kanga Electronics sells products to customers through an online ordering system.

The database contains information about:

- Customers
- Orders

Management would like several reports showing purchasing behaviour and customer spending patterns.

You will use table joins together with aggregate functions to answer business questions.

---

## Create the Tables

**Customers**

```sql
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    customer_name VARCHAR(50) NOT NULL,
    suburb VARCHAR(50) NOT NULL
);
```

**Orders**

```sql
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    customer_id INT NOT NULL REFERENCES customers(customer_id),
    order_date DATE NOT NULL,
    order_total NUMERIC(10,2) NOT NULL
);
```

---

## Insert Sample Data

**Customers**

```sql
INSERT INTO customers
(customer_name, suburb)
VALUES
('Alice','Broadmeadows'),
('Ben','Craigieburn'),
('Chloe','Glenroy'),
('Daniel','Broadmeadows'),
('Ella','Sunbury');
```

**Orders**

```sql
INSERT INTO orders
(customer_id, order_date, order_total)
VALUES
(1,'2026-01-10',250),
(1,'2026-02-15',420),
(1,'2026-03-02',180),

(2,'2026-01-05',120),
(2,'2026-02-22',300),

(3,'2026-01-18',550),
(3,'2026-02-10',650),
(3,'2026-03-12',700),

(4,'2026-02-01',90),
(4,'2026-03-05',150),
(4,'2026-03-18',220),

(5,'2026-01-25',800),
(5,'2026-02-20',720);
```

---

## Inspect the Data

Write a query to display:

- Customer name
- Suburb
- Order date
- Order total

Using an `INNER JOIN`.

---

## Activity 1: COUNT() with JOIN

Write queries to answer:

1. How many orders has each customer placed?
2. How many customers are in each suburb?
3. How many orders were placed by customers from each suburb?

---

## Activity 2: MIN() with JOIN

Write queries to answer:

1. What is the smallest order placed by each customer?
2. What is the smallest order placed by customers in each suburb?
3. Which customer has the lowest single order?

---

## Activity 3: MAX() with JOIN

Write queries to answer:

1. What is the largest order placed by each customer?
2. What is the largest order placed by
