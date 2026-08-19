# Introduction to SQL (PostgreSQL)

## SELECT, FROM, WHERE

Structured Query Language (SQL) is used to retrieve, filter, and work with data stored in a database. In PostgreSQL, one of the most common tasks is querying data using the **SELECT**, **FROM**, and **WHERE** clauses.

By the end of this topic, you will be able to:

- Retrieve data from a table using `SELECT`
- Specify which table to query using `FROM`
- Filter records using `WHERE`
- Combine multiple conditions to refine query results

## Sample Table

Throughout these examples, we'll use a simple `students` table.

| student_id | first_name | last_name | course | age |
|------------|------------|------------|------------|-----|
| 1 | Alice | Brown | Cyber Security | 19 |
| 2 | Ben | Smith | Data Analytics | 22 |
| 3 | Chloe | Jones | Cyber Security | 21 |
| 4 | Daniel | White | Software Development | 18 |
| 5 | Emily | Green | Data Analytics | 25 |

## SELECT

The `SELECT` statement is used to choose which columns you want to retrieve.

**Retrieve All Columns**

```sql
SELECT *
FROM students;
```

**Result**

| student_id | first_name | last_name | course | age |
|------------|------------|------------|------------|-----|
| 1 | Alice | Brown | Cyber Security | 19 |
| 2 | Ben | Smith | Data Analytics | 22 |
| 3 | Chloe | Jones | Cyber Security | 21 |
| 4 | Daniel | White | Software Development | 18 |
| 5 | Emily | Green | Data Analytics | 25 |

The `*` symbol means all columns.

**Retrieve Specific Columns**

```sql
SELECT first_name, last_name
FROM students;
```

**Result**

| first_name | last_name |
|------------|------------|
| Alice | Brown |
| Ben | Smith |
| Chloe | Jones |
| Daniel | White |
| Emily | Green |

## FROM

The `FROM` clause specifies which table to query.

```sql
SELECT first_name, course
FROM students;
```

Here:

- `SELECT` specifies the columns to display.
- `FROM students` specifies the table containing the data.

## WHERE

The `WHERE` clause filters records so that only matching rows are returned.

**Find Students in Data Analytics**

```sql
SELECT *
FROM students
WHERE course = 'Data Analytics';
```

**Result**

| student_id | first_name | last_name | course | age |
|------------|------------|------------|------------|-----|
| 2 | Ben | Smith | Data Analytics | 22 |
| 5 | Emily | Green | Data Analytics | 25 |

**Find Students Older Than 20**

```sql
SELECT *
FROM students
WHERE age > 20;
```

**Result**

| student_id | first_name | last_name | course | age |
|------------|------------|------------|------------|-----|
| 2 | Ben | Smith | Data Analytics | 22 |
| 3 | Chloe | Jones | Cyber Security | 21 |
| 5 | Emily | Green | Data Analytics | 25 |

## Comparison Operators

| Operator | Meaning |
|-----------|----------|
| = | Equal to |
| <> | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

**Example**

```sql
SELECT *
FROM students
WHERE age >= 21;
```

## Multiple Conditions with AND

Return students studying Data Analytics who are older than 20.

```sql
SELECT *
FROM students
WHERE course = 'Data Analytics'
  AND age > 20;
```

**Result**

| student_id | first_name | last_name | course | age |
|------------|------------|------------|------------|-----|
| 2 | Ben | Smith | Data Analytics | 22 |
| 5 | Emily | Green | Data Analytics | 25 |

## Multiple Conditions with OR

Return students in either Data Analytics or Cyber Security.

```sql
SELECT *
FROM students
WHERE course = 'Data Analytics'
   OR course = 'Cyber Security';
```

## Using WHERE with Text

Find a specific student.

```sql
SELECT *
FROM students
WHERE first_name = 'Alice';
```

Text values must be enclosed in single quotes.
# Introduction to SQL Joins (PostgreSQL)

## Understanding Joins

As databases grow, information is often stored across multiple tables rather than in a single large table. This reduces duplication and keeps the database organised.

A **JOIN** allows data from multiple tables to be combined into a single result set.

In PostgreSQL, when people refer to a **JOIN**, they are usually referring to an **INNER JOIN**.

## Example Tables

**students**

| student_id | first_name | course_id |
|------------|------------|------------|
| 1 | Alice | 1 |
| 2 | Ben | 2 |
| 3 | Chloe | 1 |
| 4 | Daniel | 3 |

**courses**

| course_id | course_name |
|------------|------------|
| 1 | Cyber Security |
| 2 | Data Analytics |
| 3 | Software Development |

Notice that both tables contain a `course_id` column.

This column links the tables together.

## Why Use a Join?

If we query the students table on its own:

```sql
SELECT *
FROM students;
```

**Result**

| student_id | first_name | course_id |
|------------|------------|------------|
| 1 | Alice | 1 |
| 2 | Ben | 2 |
| 3 | Chloe | 1 |
| 4 | Daniel | 3 |

The course IDs are not very meaningful on their own.

A join allows us to retrieve the course names from the courses table.

## Performing a Join

```sql
SELECT
    students.first_name,
    courses.course_name
FROM students
JOIN courses
    ON students.course_id = courses.course_id;
```

**Result**

| first_name | course_name |
|------------|------------|
| Alice | Cyber Security |
| Ben | Data Analytics |
| Chloe | Cyber Security |
| Daniel | Software Development |

This query combines information from both tables.

## Understanding the Parts of the Query

```sql
SELECT
    students.first_name,
    courses.course_name
FROM students
JOIN courses
    ON students.course_id = courses.course_id;
```

**SELECT**

Specifies the columns we want to display.

```sql
SELECT
    students.first_name,
    courses.course_name
```

**FROM**

Specifies the first table.

```sql
FROM students
```

**JOIN**

Specifies the second table.

```sql
JOIN courses
```

**ON**

Defines how the tables are related.

```sql
ON students.course_id = courses.course_id
```

This tells PostgreSQL to match rows where the `course_id` values are equal.

## Using Table Aliases

Aliases provide short names for tables.

```sql
SELECT
    s.first_name,
    c.course_name
FROM students s
JOIN courses c
    ON s.course_id = c.course_id;
```

Here:

- `s` represents the `students` table.
- `c` represents the `courses` table.

The result is exactly the same, but the query is easier to write.

## Joining Three Tables

Joins become even more useful when working with multiple tables.

Consider the following example.

**students**

| student_id | first_name |
|------------|------------|
| 1 | Alice |
| 2 | Ben |

**enrolments**

| enrolment_id | student_id | course_id |
|------------|------------|------------|
| 1 | 1 | 1 |
| 2 | 1 | 2 |
| 3 | 2 | 2 |

**courses**

| course_id | course_name |
|------------|------------|
| 1 | Cyber Security |
| 2 | Data Analytics |

A student can enrol in multiple courses.

To display student names and course names:

```sql
SELECT
    s.first_name,
    c.course_name
FROM students s
JOIN enrolments e
    ON s.student_id = e.student_id
JOIN courses c
    ON e.course_id = c.course_id;
```

**Result**

| first_name | course_name |
|------------|------------|
| Alice | Cyber Security |
| Alice | Data Analytics |
| Ben | Data Analytics |

## Combining JOIN and WHERE

Display only Cyber Security students.

```sql
SELECT
    s.first_name,
    c.course_name
FROM students s
JOIN courses c
    ON s.course_id = c.course_id
WHERE c.course_name = 'Cyber Security';
```

**Result**

| first_name | course_name |
|------------|------------|
| Alice | Cyber Security |
| Chloe | Cyber Security |

## General Structure

A typical join follows this structure:

```sql
SELECT columns
FROM table1
JOIN table2
    ON table1.key = table2.key;
```

## Practice Tasks

Using the `students` and `courses` tables:

1. Display all student names and course names.
2. Display only first names and course names.
3. Display students enrolled in Data Analytics.
4. Display students enrolled in Software Development.
5. Sort the results by student name.

Using the `students`, `enrolments`, and `courses` tables:

6. Display all student-course enrolments.
7. Find all courses taken by Alice.
8. Find all students enrolled in Data Analytics.
9. Display all student names and course names sorted alphabetically.
10. Display only students enrolled in Cyber Security.

## Key Points

- A JOIN combines data from multiple tables.
- Tables are linked using related columns.
- The `ON` clause defines how records are matched.
- A JOIN returns rows where matching values exist in both tables.
- Table aliases make queries easier to read.
- Multiple JOIN statements can be used to combine three or more tables.
✅ Correct

```sql
WHERE first_name = 'Alice'
```

❌ Incorrect

```sql
WHERE first_name = Alice
```

## SQL Query Structure

A basic query follows this structure:

```sql
SELECT column_names
FROM table_name
WHERE condition;
```

**Example**

```sql
SELECT first_name, course
FROM students
WHERE age > 20;
```

Read this query as:

> Select the student's first name and course from the students table where the student's age is greater than 20.

## Practical Examples

**Example 1**

Display all courses.

```sql
SELECT course
FROM students;
```

**Example 2**

Display student names only.

```sql
SELECT first_name, last_name
FROM students;
```

**Example 3**

Display students under 21.

```sql
SELECT *
FROM students
WHERE age < 21;
```

**Example 4**

Display students not enrolled in Data Analytics.

```sql
SELECT *
FROM students
WHERE course <> 'Data Analytics';
```

## Practice Tasks

Using the `students` table, write SQL queries to:

1. Display all students.
2. Display only first names and courses.
3. Find students older than 21.
4. Find students enrolled in Cyber Security.
5. Find students who are not enrolled in Software Development.
6. Find students aged 18 or 19.
7. Display first and last names of students in Data Analytics.
8. Find students older than 20 who study Cyber Security.

## Key Points

- `SELECT` chooses which columns to display.
- `FROM` specifies which table contains the data.
- `WHERE` filters rows based on conditions.
- Text values use single quotes.
- Conditions can be combined using `AND` and `OR`.
- `SELECT *` returns all columns from a table.
