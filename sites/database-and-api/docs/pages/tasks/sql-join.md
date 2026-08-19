
# Intro SQL Join Exercises PostgreSQL

These exercises practise `JOIN` queries using realistic table names and values. The focus is on the default PostgreSQL join style, which behaves as an inner join when written as `JOIN`.

```sql
SELECT columns
FROM table_a
JOIN table_b
    ON table_a.foreign_key = table_b.primary_key;
```

**CSV Files** - [sql_join_csv.zip](../../assets/sql_join_csv.zip)

---

## Metro Beans Cafe

This exercise uses two tables.

**Tables**

```sql
customers
orders
```

**Relationship**

```sql
orders.customer_id = customers.customer_id
```

`customers.customer_id` is the Primary Key.

`orders.customer_id` is the Foreign Key.

**Tasks**

1. Display each order with the customer name and item name.
2. Display customer name, suburb, order date, and order amount.
3. Find all orders made by Gold loyalty customers.
4. Find all orders from customers who live in Broadmeadows.
5. Display all orders where the order amount is greater than 15.
6. Display customer names and item names for all orders containing `Latte`.
7. Find all orders made by customers from Coburg or Glenroy.
8. Display all orders made after `2026-04-01`.
9. Find Gold loyalty customers who spent more than 12 on an order.
10. Display customer name, loyalty level, item name, and order amount.

**Starter Query**

```sql
SELECT
    c.customer_name,
    o.item_name,
    o.order_amount
FROM customers c
JOIN orders o
    ON c.customer_id = o.customer_id;
```

---

## BrightTech Store

This exercise uses two tables.

**Tables**

```sql
products
sales
```

**Relationship**

`sales.product_id` is the Foreign Key.

**Tasks**

1. Display each sale with the product name and quantity sold.
2. Display product name, category, store location, and sale date.
3. Find all sales for products in the Laptop category.
4. Find all sales from the Broadmeadows store.
5. Display sales where the quantity is greater than 3.
6. Display product names and store locations for Monitor sales.
7. Find products with a unit price greater than 1000 that have been sold.
8. Display product name, unit price, quantity, and store location.
9. Find sales made after `2026-05-01`.
10. Find sales for products that are not in the Mouse category.

**Starter Query**

```sql
SELECT
    p.product_name,
    p.category,
    s.store_location,
    s.quantity
FROM products p
JOIN sales s
    ON p.product_id = s.product_id;
```

---

## Northside Library

This exercise uses two tables.

**Tables**

```sql
books
borrowings
```

**Relationship**

`borrowings.book_id` is the Foreign Key.

**Tasks**

1. Display each borrowing with the book title and borrower name.
2. Display title, author, genre, borrow date, and due date.
3. Find all borrowings for Mystery books.
4. Find all books borrowed after `2026-05-01`.
5. Display borrowings for books published after 2015.
6. Find borrowings for Technology books.
7. Display borrower name and title only.
8. Find all borrowings where the author is `Mira Roberts`.
9. Display all Biography books that have been borrowed.
10. Find all borrowings due after `2026-07-01`.

**Starter Query**

```sql
SELECT
    b.title,
    b.author,
    br.borrower_name,
    br.borrow_date
FROM books b
JOIN borrowings br
    ON b.book_id = br.book_id;
```

---

## Skills Academy

This exercise uses three tables.

**Tables**

```sql
students
courses
enrolments
```

**Relationships**

`students.student_id` is the Primary Key for students.

`courses.course_id` is the Primary Key for courses.

`enrolments.student_id` and `enrolments.course_id` are Foreign Keys.

**Tasks**

1. Display each enrolment with the student name and course name.
2. Display student name, suburb, course name, and enrolment status.
3. Find all students enrolled in Intro to SQL.
4. Find all enrolments in the Data course area.
5. Display completed enrolments only.
6. Find active students enrolled in Power BI Basics.
7. Display all enrolments after `2026-04-01`.
8. Find students from Broadmeadows enrolled in any course.
9. Display student name, course area, and enrolment date.
10. Find withdrawn enrolments for Web or Cloud courses.

**Starter Query**

```sql
SELECT
    s.student_name,
    c.course_name,
    e.enrolment_status
FROM students s
JOIN enrolments e
    ON s.student_id = e.student_id
JOIN courses c
    ON e.course_id = c.course_id;
```

---

## Community Health Clinic

This exercise uses three tables.

**Tables**

```sql
patients
doctors
appointments
```

**Keys**

`patients.patient_id` is the Primary Key for patients.

`doctors.doctor_id` is the Primary Key for doctors.

**Tasks**

1. Display each appointment with patient name and doctor name.
2. Display patient name, suburb, doctor name, specialty, and appointment date.
3. Find appointments with doctors in General Practice.
4. Find completed appointments only.
5. Display appointments for patients older than 60.
6. Find appointments for patients from Broadmeadows.
7. Display appointments where the reason is Check-up.
8. Find appointments after `2026-06-01`.
9. Display patient name and doctor specialty for cancelled appointments.
10. Find appointments with Mental Health doctors where the status is Booked.

**Starter Query**

```sql
SELECT
    p.patient_name,
    d.doctor_name,
    d.specialty,
    a.appointment_date
FROM patients p
JOIN appointments a
    ON p.patient_id = a.patient_id
JOIN doctors d
    ON a.doctor_id = d.doctor_id;
```

## Key Reminder

When writing joins, look for the relationship between tables.

A useful rule is:

> Match the Foreign Key in one table to the related Primary Key in another table.
