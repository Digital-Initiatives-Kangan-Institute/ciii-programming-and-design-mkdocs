# Aggregates

## SwiftParcel 

**Scenario**

SwiftParcel operates delivery depots across several regions. Each row records a completed delivery, including the depot, driver, parcel type, delivery distance and delivery fee.

This dataset is separate from the examples in the PostgreSQL aggregates learning material. Use it to practise:

- `MIN()`
- `MAX()`
- `AVG()`
- `GROUP BY`
- `HAVING`
- Combining `WHERE` and `HAVING`

**Create the table**

```sql
CREATE TABLE parcel_deliveries (
    delivery_id SERIAL PRIMARY KEY,
    driver_name VARCHAR(50) NOT NULL,
    depot VARCHAR(50) NOT NULL,
    parcel_type VARCHAR(30) NOT NULL,
    distance_km NUMERIC(6,2) NOT NULL,
    delivery_fee NUMERIC(8,2) NOT NULL
);
```

**Insert the data**

```sql
INSERT INTO parcel_deliveries
    (driver_name, depot, parcel_type, distance_km, delivery_fee)
VALUES
    ('Amir',   'Broadmeadows', 'Standard',  12.50, 18.00),
    ('Amir',   'Broadmeadows', 'Express',   34.20, 42.00),
    ('Amir',   'Broadmeadows', 'Oversized', 18.40, 55.00),

    ('Bella',  'Sunshine',     'Standard',   8.30, 15.00),
    ('Bella',  'Sunshine',     'Express',    22.70, 35.00),
    ('Bella',  'Sunshine',     'Standard',   16.80, 21.00),

    ('Chen',   'Dandenong',    'Oversized', 45.60, 78.00),
    ('Chen',   'Dandenong',    'Express',   31.20, 47.00),
    ('Chen',   'Dandenong',    'Standard',  14.90, 20.00),

    ('Deepa',  'Broadmeadows', 'Express',   28.50, 39.00),
    ('Deepa',  'Broadmeadows', 'Standard',   9.60, 16.00),
    ('Deepa',  'Broadmeadows', 'Oversized', 52.30, 85.00),

    ('Ethan',  'Sunshine',     'Oversized', 38.10, 68.00),
    ('Ethan',  'Sunshine',     'Express',   19.70, 31.00),
    ('Ethan',  'Sunshine',     'Standard',  11.40, 17.00),

    ('Fatima', 'Dandenong',    'Standard',  24.80, 29.00),
    ('Fatima', 'Dandenong',    'Express',   41.50, 56.00),
    ('Fatima', 'Dandenong',    'Oversized', 63.20, 95.00),

    ('Grace',  'Geelong',      'Standard',  17.60, 23.00),
    ('Grace',  'Geelong',      'Express',   36.90, 49.00),
    ('Grace',  'Geelong',      'Oversized', 47.40, 76.00),

    ('Hassan', 'Geelong',      'Standard',  10.20, 16.00),
    ('Hassan', 'Geelong',      'Express',   25.50, 37.00),
    ('Hassan', 'Geelong',      'Standard',  14.30, 19.00);
```

**Review the dataset**

Before using aggregate functions, examine the records:

```sql
SELECT *
FROM parcel_deliveries
ORDER BY delivery_id;
```

Confirm the number of records imported:

```sql
SELECT COUNT(*) AS delivery_count
FROM parcel_deliveries;
```

Expected record count:

```text
24
```

**Activity 1: Basic aggregates**

Write PostgreSQL queries to answer the following questions:

1. What was the shortest delivery distance?
2. What was the longest delivery distance?
3. What was the average delivery distance?
4. What was the lowest delivery fee?
5. What was the highest delivery fee?
6. What was the average delivery fee?

Requirements:

- Give every calculated column a meaningful alias.
- Round averages to two decimal places.

---

## GROUP BY

Write queries to answer the following questions:

1. What was the average delivery fee for each depot?
2. What was the longest delivery distance recorded by each depot?
3. What was the shortest delivery distance recorded by each depot?
4. What was the average delivery fee for each parcel type?
5. What was the highest delivery fee charged for each parcel type?
6. What was the average delivery distance completed by each driver?
7. What were the minimum, maximum and average fees for each depot?

Requirements:

- Give every aggregate column a meaningful alias.
- Round averages to two decimal places.
- Sort each result in a logical order.

---

## Multi columns

Write queries to answer the following questions:

1. What was the average delivery fee for each parcel type at each depot?
2. What was the longest delivery distance for each driver and parcel type?
3. What was the average distance for each depot and parcel type?
4. What were the minimum, maximum and average fees for each depot and parcel type?

Requirements:

- Group using both required columns.
- Sort the results by depot and then by parcel type where relevant.
- Round averages to two decimal places.

---

## HAVING

Write queries to answer the following questions:

1. Which depots had an average delivery fee greater than $40?
2. Which parcel types had an average delivery distance greater than 25 km?
3. Which drivers had an average delivery fee greater than $35?
4. Which depots recorded a maximum delivery distance greater than 50 km?
5. Which parcel types had a minimum delivery fee greater than $20?

Remember that `HAVING` filters grouped results after aggregation.

---

## WHERE and HAVING

Write queries to answer the following questions:

1. For Express parcels only, which depots had an average delivery fee greater than $40?
2. For deliveries longer than 15 km, which depots had an average fee greater than $45?
3. Excluding Standard parcels, which drivers had an average delivery distance greater than 30 km?
4. For deliveries costing at least $20, which parcel types had an average distance greater than 25 km?

In these queries:

- Use `WHERE` to filter individual delivery rows.
- Use `GROUP BY` to create the required groups.
- Use `HAVING` to filter the grouped results.

---

## Challenge

SwiftParcel wants a summary report containing:

- Depot
- Parcel type
- Shortest delivery distance
- Longest delivery distance
- Average delivery distance
- Lowest delivery fee
- Highest delivery fee
- Average delivery fee

Only include depot and parcel-type combinations where:

- The average delivery fee is greater than $30.
- The longest delivery distance is greater than 30 km.

Requirements:

- Round all averages to two decimal places.
- Use meaningful aliases.
- Sort the output by depot and parcel type.

