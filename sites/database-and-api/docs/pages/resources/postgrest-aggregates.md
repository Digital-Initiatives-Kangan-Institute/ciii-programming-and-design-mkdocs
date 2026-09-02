# PostgREST Aggregate Functions

https://docs.postgrest.org/en/latest/references/api/aggregate_functions.html

---

## The Parcel Deliveries Dataset

```sql
CREATE TABLE parcel_deliveries (
    delivery_id SERIAL PRIMARY KEY,
    driver_name VARCHAR(50),
    depot VARCHAR(50),
    parcel_type VARCHAR(30),
    distance_km NUMERIC(6,2),
    delivery_fee NUMERIC(8,2)
);
```

Example data:

```text
Amir      Broadmeadows   Standard    12.50   18.00
Amir      Broadmeadows   Express     34.20   42.00
Bella     Sunshine       Standard     8.30   15.00
Chen      Dandenong      Oversized   45.60   78.00
...
```

---

## How Aggregate Functions Work in PostgREST

In PostgreSQL we would write:

```sql
SELECT SUM(delivery_fee)
FROM parcel_deliveries;
```

In PostgREST, aggregates are placed directly inside the `select` parameter.

Example:

```http
GET /parcel_deliveries?select=delivery_fee.sum()
```

PostgREST returns:

```json
[
    {
        "sum": 1027.00
    }
]
```

Aggregate functions are applied directly to the selected column. 【1-581ed3】

---

## COUNT()

### Count All Deliveries

```http
GET /parcel_deliveries?select=count()
```

Example response:

```json
[
    {
        "count": 24
    }
]
```

### What Does count() Mean?

`count()` counts rows.

Equivalent PostgreSQL:

```sql
SELECT COUNT(*)
FROM parcel_deliveries;
```

---

## COUNT(column)

### Count Non-Null Values

```http
GET /parcel_deliveries?select=driver_count:driver_name.count()
```

Example response:

```json
[
    {
        "driver_count": 24
    }
]
```

PostgREST documentation highlights an important distinction:

```text
count()
```

counts rows.

Whereas:

```text
column.count()
```

counts non-null values in the specified column. 【1-581ed3】

---

## SUM()

### Total Delivery Revenue

```http
GET /parcel_deliveries?select=delivery_fee.sum()
```

Example response:

```json
[
    {
        "sum": 1027.00
    }
]
```

Equivalent PostgreSQL:

```sql
SELECT SUM(delivery_fee)
*ROM parcel_deliveries;
```

### To*al Distance Travelled

```http
GET*/parcel_deliveries?select=distance*km.sum()
```

Example response:

`*`json
[
    {
        "sum": 685.4*
    }
]
```

---

## MIN()

### L*west Delivery Fee

```http*GET /parcel_deliveries?select=deli*ery_fee.min()
```

Example respons*:

```json
[
    {
        "min": 15.00
    }
]
```

Equivalent Postg*eSQL:

```sql
SELECT MIN(delivery_*ee)
FROM parcel_deliveries;
```

#*# Shortest Delivery Distance

```h*tp
GET /parcel_deliveries?select=d*stance_km.min()
```

---

## MAX()*
### Highest Delivery Fee

```http*GET /parcel_deliveries?select=deli*ery_fee.max()
```

Example respons*:

```json
[
    {
        "max": 95.00
    }
]
```

Equivalent Postg*eSQL:

```sql
SELECT MAX(delivery_*ee)
FROM parcel_deliveries;
```

#*# Longest Delivery Distance

```ht*p
GET /parcel_deliveries?select=di*tance_km.max()
```

---

## AVG()
*### Average Delivery Fee

```http
*ET /parcel_deliveries?select=deliv*ry_fee.avg()
```

Example response*

```json
[
    {
        "avg": 42.79
    }
]
```

Equivalent Postgr*SQL:

```sql
SELECT AVG(delivery_f*e)
FROM parcel_deliveries;
```

##* Average Delivery Distance

```htt*
GET /parcel_deliveries?select=dis*ance_km.avg()
```

---

## Multipl* Aggregates in One Request

PostgR*ST allows multiple aggregates in t*e same request. Aggregates can be *enamed using aliases. 【1-581ed3】

*``http
GET /parcel_deliveries?
sel*ct=
total_revenue:delivery_fee.sum*),
average_fee:delivery_fee.avg(),*highest_fee:delivery_fee.max(),
lo*est_fee:delivery_fee.min(),
delive*y_count:count()
```

Example respo*se:

```json
[
    {
        "total_revenue": 1027.00,
        "average_fee": 42.79,
        "highest_fee": 95.00,
        "lowest_fee": 15.00,
        "delivery_count": 24
    }
]
```

---

## Automatic GROUP*BY

One of the most interesting Po*tgREST features is that grouping i* handled automatically.

Suppose m*nagement wants average fees by dep*t.

Instead of writing a SQL `GROU* BY`, include the grouping column *n the `select` statement.

```http*GET /parcel_deliveries?
select=dep*t,delivery_fee.avg()
```

PostgRES* automatically groups by `depot`. *1-581ed3】

Example response:

```j*on
[
    {
        "depot": "Broad*eadows",
        "avg": 42.50
    *,
    {
        "depot": "Dandenon*",
        "avg": 54.17
    },
   *{
        "depot": "Geelong",
    *   "avg": 36.67
    },
    {
     *  "depot": "Sunshine",
        "av*": 31.17
    }
]
```

Equivalent P*stgreSQL:

```sql
SELECT
    depot*
    AVG(delivery_fee)
FROM parcel*deliveries
GROUP BY depot;
```

--*

## Aggregates by Depot

### Numb*r of Deliveries by Depot

```http
*ET /parcel_deliveries?
select=depo*,count()
```

### Total Revenue by*Depot

```http
GET /parcel_deliver*es?
select=depot,delivery_fee.sum(*
```

### Maximum Fee by Depot

``*http
GET /parcel_deliveries?
selec*=depot,delivery_fee.max()
```

###*Average Fee by Depot

```http
GET *parcel_deliveries?
select=depot,de*ivery_fee.avg()
```

PostgREST aut*matically groups by `depot` becaus* it appears beside an aggregate. 【*-581ed3】

---

## Aggregates by Pa*cel Type

### Average Fee

```http*GET /parcel_deliveries?
select=par*el_type,delivery_fee.avg()
```

##* Total Revenue

```http
GET /parce*_deliveries?
select=parcel_type,de*ivery_fee.sum()
```

### Number of*Deliveries

```http
GET /parcel_de*iveries?
select=parcel_type,count(*
```

### Highest Fee

```http
GET*/parcel_deliveries?
select=parcel_*ype,delivery_fee.max()
```

---

#* Current Limitations

When using P*stgREST aggregates:

- Aggregates *ust be enabled.
- `HAVING` is not *urrently supported.
- Ordering by *ggregated columns is not currently*supported.
- Automatic grouping oc*urs when non-aggregated columns ar* included in the `select` paramete*. 【1-581ed3】

---

## Student Acti*ity 1

Write the PostgREST URLs re*uired to return:

1. Total deliver* count.
2. Total delivery revenue.*3. Lowest delivery fee.
4. Highest*delivery fee.
5. Average delivery fee.

---

## Student Activity 2

Write PostgREST URLs to return:

1. Delivery count by depot.
2. Average fee by depot.
3. Maximum fee by depot.
4. Total revenue by depot.
5. Minimum fee by depot.

---

## Student Activity 3

Write PostgREST URLs to return:

1. Average fee by parcel type.
2. Total revenue by parcel type.
3. Delivery count by parcel type.
4. Highest fee by parcel type.
5. Lowest fee by parcel type.

---

## Challenge Activity

Create a single PostgREST request that returns:

- Delivery count
- Total revenue
- Lowest fee
- Highest fee
- Average fee
- Minimum distance
- Maximum distance
- Average distance

Rename every aggregate using aliases.

Example structure:

```http
GET /parcel_deliveries?
select=
delivery_count:count(),
total_revenue:delivery_fee.sum(),
...
```

---

## Summary

- `count()` counts rows.
- `column.count()` counts non-null values.
- `sum()` adds values together.
- `min()` returns the smallest value.
- `max()` returns the largest value.
- `avg()` calculates the average value.
- Multiple aggregates can be used in a single request.
- Aggregates can be renamed using aliases.
- PostgREST automatically performs grouping when non-aggregated columns are included in the `select` parameter.
- Unlike standard SQL, no explicit `GROUP BY` is required in the API request. 【1-581ed3】
