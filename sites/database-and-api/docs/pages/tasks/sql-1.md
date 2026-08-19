# Intro SQL Single Table Exercises

These exercises are designed for introductory PostgreSQL practice using a single table. They focus on:

- `SELECT`
- `FROM`
- `WHERE`
- Comparison operators
- `AND`
- `OR`

**CSV Downloads** - [intro_sql_csv.zip](../../assets/intro_sql_csv.zip)

---

## Customers

**Table name**

```sql
customers
```

**Columns**

- `customer_id`
- `customer_name`
- `suburb`
- `age`
- `membership_level`

**Tasks**

1. Display all customer records.
2. Display only customer names and suburbs.
3. Find customers older than 50.
4. Find customers who live in Broadmeadows.
5. Find customers with a Gold membership.
6. Find customers aged between 25 and 40.
7. Find customers who do not have a Silver membership.
8. Display only customer names for customers living in Craigieburn.
9. Find customers older than 30 with a Platinum membership.
10. Display all customers from Glenroy or Fawkner.

---

## Products

**Table name**

```sql
products
```

**Columns**

- `product_id`
- `product_name`
- `category`
- `price`
- `stock_quantity`

**Tasks**

1. Display all products.
2. Display product names and prices.
3. Find products costing more than 500.
4. Find products in the Laptop category.
5. Find products with less than 10 units in stock.
6. Find products costing between 100 and 500.
7. Find products that are not Printers.
8. Display product names and stock quantities only.
9. Find products with more than 50 units in stock.
10. Find Monitors that cost more than 300.

---

## Employees

**Table name**

```sql
employees
```

**Columns**

- `employee_id`
- `employee_name`
- `department`
- `salary`
- `years_service`

**Tasks**

1. Display all employee records.
2. Display employee names and departments.
3. Find employees in the IT department.
4. Find employees earning more than 80000.
5. Find employees with more than 10 years of service.
6. Find employees in Marketing.
7. Find employees earning less than 60000.
8. Display employee names and salaries only.
9. Find employees in Finance earning more than 70000.
10. Find employees with between 5 and 15 years of service.

---

## Students

**Table name**

```sql
students
```

**Columns**

- `student_id`
- `student_name`
- `course`
- `age`
- `status`

**Tasks**

1. Display all student records.
2. Display student names and courses.
3. Find students enrolled in Cyber Security.
4. Find students enrolled in Data Analytics.
5. Find students older than 25.
6. Find students whose status is Active.
7. Find students whose status is Completed.
8. Display names of students enrolled in Cloud Computing.
9. Find active students older than 21.
10. Find students not enrolled in Software Development.

---

## Movies

**Table name**

```sql
movies
```

**Columns**

- `movie_id`
- `title`
- `genre`
- `release_year`
- `rating`

**Tasks**

1. Display all movies.
2. Display movie titles and ratings.
3. Find Action movies.
4. Find movies released after 2015.
5. Find movies with ratings greater than 8.
6. Find Comedy movies with ratings above 7.
7. Find movies released before 2000.
8. Display titles of Sci-Fi movies.
9. Find Horror movies released after 2010.
10. Find movies with ratings between 6 and 9.

---

## Operators to Practise

```sql
=
<>
>
<
>=
<=
AND
OR
```

## Example Query Structure

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

**Example**

```sql
SELECT customer_name, suburb
FROM customers
WHERE suburb = 'Broadmeadows';
```
