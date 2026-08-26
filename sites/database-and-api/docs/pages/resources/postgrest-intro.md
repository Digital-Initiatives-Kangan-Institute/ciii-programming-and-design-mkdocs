# Introduction to PostgREST: Reading Data with GET Requests

## What is PostgREST?

PostgREST is a tool that automatically creates a REST API from a PostgreSQL database. Tables, views, and functions in your database become web endpoints that can be accessed using standard HTTP requests. 

This means that instead of writing a custom backend application, you can interact directly with your PostgreSQL database through a REST API. 

---

## Why Use PostgREST?

Benefits include:

- Automatic API generation
- No need to create controllers or routes
- Standard REST interface
- Built-in support for filtering and sorting
- Support for database relationships
- Integration with PostgreSQL security features such as Row Level Security (RLS) 

For learners, it provides a simple way to retrieve data from a PostgreSQL database without needing to build a backend application.

---

## Basic GET Requests

Assume we have the following table:

```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    first_name TEXT,
    last_name TEXT,
    email TEXT
);
```

PostgREST automatically creates an endpoint:

```http
/students
```

---

## Retrieve All Records

Request:

```http
GET /students
```

Response:

```json
[
  {
    "student_id": 1,
    "first_name": "Jane",
    "last_name": "Smith",
    "email": "jane@example.com"
  },
  {
    "student_id": 2,
    "first_name": "John",
    "last_name": "Brown",
    "email": "john@example.com"
  }
]
```

The request returns all rows from the table. 

---

## Selecting Specific Columns

You may not need every field.

Request:

```http
GET /students?select=first_name,last_name
```

Response:

```json
[
  {
    "first_name": "Jane",
    "last_name": "Smith"
  }
]
```

This is similar to:

```sql
SELECT first_name, last_name
FROM students;
```



---

## Filtering Results

Filtering allows you to return only matching rows.

## Equal To

Request:

```http
GET /students?last_name=eq.Smith
```

Equivalent SQL:

```sql
SELECT *
FROM students
WHERE last_name = 'Smith';
```

---

## Greater Than

Request:

```http
GET /students?student_id=gt.10
```

Equivalent SQL:

```sql
SELECT *
FROM students
WHERE student_id > 10;
```

---

## Less Than

Request:

```http
GET /students?student_id=lt.50
```

Equivalent SQL:

```sql
SELECT *
FROM students
WHERE student_id < 50;
```

---

## Common Operators

| Operator | Meaning |
|-----------|----------|
| eq | Equals |
| neq | Not equal |
| gt | Greater than |
| gte | Greater than or equal |
| lt | Less than |
| lte | Less than or equal |
| like | Pattern matching |



---

## Sorting Results

## Ascending Order

Request:

```http
GET /students?order=last_name
```

Equivalent SQL:

```sql
SELECT *
FROM students
ORDER BY last_name ASC;
```

---

## Descending Order

Request:

```http
GET /students?order=last_name.desc
```

Equivalent SQL:

```sql
SELECT *
FROM students
ORDER BY last_name DESC;
```

---

## Limiting Results

Request:

```http
GET /students?limit=5
```

Equivalent SQL:

```sql
SELECT *
FROM students
LIMIT 5;
```

---

## PostgREST in Supabase

Supabase uses PostgREST to generate its REST API automatically. Every table you create in Supabase becomes available through a REST endpoint. 

For example, if you create a table called `students`, Supabase automatically exposes:

```http
https://your-project.supabase.co/rest/v1/students
```

To retrieve data:

```http
GET https://your-project.supabase.co/rest/v1/students
```

Required headers:

```http
apikey: YOUR_API_KEY
Authorization: Bearer YOUR_API_KEY
```

Behind the scenes, this request is processed by PostgREST and translated into a PostgreSQL query. 

---

## Querying Related Data (Joins)

One of the most powerful features of PostgREST is its ability to automatically understand foreign key relationships and perform joins between tables. 

Consider the following database:

```text
STUDENT
--------
student_id
first_name
last_name

ENROLMENT
---------
student_id
course_id

COURSE
-------
course_id
course_name
```

Foreign keys:

```sql
enrolment.student_id → student.student_id
enrolment.course_id  → course.course_id
```

---

## Example 1: Student with Their Enrolments

SQL:

```sql
SELECT *
FROM student s
JOIN enrolment e
    ON s.student_id = e.student_id;
```

PostgREST:

```http
GET /student?select=*,enrolment(*)
```

Example Response:

```json
[
  {
    "student_id": 1,
    "first_name": "Jane",
    "last_name": "Smith",
    "enrolment": [
      {
        "course_id": 101
      },
      {
        "course_id": 102
      }
    ]
  }
]
```



---

## Example 2: Course with Enrolled Students

SQL:

```sql
SELECT *
FROM course c
JOIN enrolment e
    ON c.course_id = e.course_id
JOIN student s
    ON e.student_id = s.student_id;
```

PostgREST:

```http
GET /course?select=course_name,enrolment(student(*))
```

This returns each*course together with the students *nrolled in it. *2-042e4d】

*--

*# Example 3: Student with Course D*tails

SQL:

```sql
SELECT**   s*first*name,
    s.last_name,
    c*course*name
FROM student s
JOIN enrolment*e
    ON s.student_id = e.student_id
JOIN course c
    ON e.course_id = c.course_id;
```

PostgREST:

```http
GET /student?select=first_name,last_name,enrolment(course(*))
```

Example Response:

```json
[
  {
    "first_name": "Jane",
    "last_name": "Smith",
    "enrolment": [
      {
        "course": {
          "course_id": 101,
          "course_name": "Database Fundamentals"
        }
      }
    ]
  }
]
```

---

## Example 4: Many-to-Many Relationship

The relationship between students and courses is many-to-many.

```text
STUDENT
    |
    |
    |
ENROLMENT
    |
    |
    |
COURSE
```

A student can enrol in many courses.

A course can contain many students.

PostgREST automatically follows the foreign keys through the junction table and returns nested data structures. 

Example:

```http
GET /student?select=first_name,last_name,enrolment(course_name:course(course_name))
```

This returns each student and the names of courses they are enrolled in.

---

## Comparing SQL Joins and PostgREST

| SQL Concept | PostgREST Equivalent |
|-------------|----------------------|
| SELECT | select= |
| WHERE | field=eq.value |
| ORDER BY | order= |
| LIMIT | limit= |
| INNER JOIN | Embedded resources |
| Foreign Key Relationships | Automatic discovery |
| Many-to-Many Joins | Junction table embedding |



---

## Common Read Examples

**Get all students**

```http
GET /students
```

**Get only names**

```http
GET /students?select=first_name,last_name
```

**Get students named Smith**

```http
GET /students?last_name=eq.Smith
```

**Get students sorted by surname**

```http
GET /students?order=last_name
```

**Get the first five students**

```http
GET /students?limit=5
```

**Get students with ID greater than 100**

```http
GET /students?student_id=gt.100
```

**Get students and their enrolments**

```http
GET /student?select=*,enrolment(*)
```

**Get courses and enrolled students**

```http
GET /course?select=course_name,enrolment(student(*))
```

**Get students and their courses**

```http
GET /student?select=first_name,last_name,enrolment(course(*))
```

---

## Key Takeaways

✅ PostgREST automatically creates a REST API from PostgreSQL.

✅ GET requests are used to retrieve data.

✅ The `select` parameter chooses columns to return.

✅ Filters use operators such as `eq`, `gt`, and `lt`.

✅ Results can be sorted with `order`.

✅ Results can be limited with `limit`.

✅ Pagination uses `limit` and `offset`.

✅ Foreign key relationships are automatically detected.

✅ Related data can be embedded to perform joins.

✅ Supabase uses PostgREST to power its auto-generated REST API. 

## Further Reading

- PostgREST Documentation: https://postgrest.org/en/stable/
- Supabase Data API Documentation: https://supabase.com/docs/guides/api
