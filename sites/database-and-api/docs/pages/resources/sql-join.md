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

## ON

The `ON` clause defines how the tables are related.

```sql
ON students.course_id = courses.course_id
```

This tells PostgreSQL to match rows where the `course_id` values are equal.

The columns used in the `ON` clause are typically:

- A **Primary Key (PK)** in one table.
- A **Foreign Key (FK)** in another table.

In our example:

**courses**

| course_id (PK) | course_name |
|------------|------------|
| 1 | Cyber Security |
| 2 | Data Analytics |
| 3 | Software Development |

**students**

| student_id (PK) | first_name | course_id (FK) |
|------------|------------|------------|
| 1 | Alice | 1 |
| 2 | Ben | 2 |
| 3 | Chloe | 1 |
| 4 | Daniel | 3 |

The `course_id` in the `courses` table is the **Primary Key**.

```text
courses.course_id
```

The `course_id` in the `students` table is the **Foreign Key**.

```text
students.course_id
```

The Foreign Key stores a value that refers to a record in another table.

When PostgreSQL processes the join:

```sql
ON students.course_id = courses.course_id
```

it matches:

```text
students.course_id (FK)
          =
courses.course_id (PK)
```

For example:

```text
Alice → course_id 1
```

matches

```text
course_id 1 → Cyber Security
```

and PostgreSQL combines the data into a single row:

| first_name | course_name |
|------------|------------|
| Alice | Cyber Security |

When designing databases, the columns used in the `ON` clause will often be the same columns used to create relationships in your ERD.

A useful rule to remember is:

> JOIN tables by matching a Foreign Key to its related Primary Key.

## Table Aliases

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
