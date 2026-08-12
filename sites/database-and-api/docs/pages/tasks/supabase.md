# Supabase Relationship Scenarios

## Overview

For the below scenarios find sample data at [sample data](../../assets/supabase_relationship_scenarios_csv.zip)
 
    - create the required tables and relationships in Supabase
    - upload the data from the CSV files into the database tables

---

## Scenario 1: Departments and Employees

A training organisation stores information about departments and employees.

Each department can have many employees. Each employee belongs to one department.

**Relationship type:** One-to-many

**Tables:**

- departments
- employees

**Relationship:**

```text
departments.department_id 1 ---- many employees.department_id
```

**CSV files:**

- scenario_01_departments.csv
- scenario_01_employees.csv

**Possible keys:**

- departments.department_id = Primary Key
- employees.employee_id = Primary Key
- employees.department_id = Foreign Key

**Student task:**

1. Identify the parent table.
2. Identify the child table.
3. Identify the primary key in each table.
4. Identify the foreign key.
5. Explain why this is a one-to-many relationship.

---

## Scenario 2: Libraries and Books

A small education provider manages several libraries.

Each library contains many books. Each book is stored at one library.

**Relationship type:** One-to-many

**Tables:**

- libraries
- books

**Relationship:**

```text
libraries.library_id 1 ---- many books.library_id
```

**CSV files:**

- scenario_02_libraries.csv
- scenario_02_books.csv

**Possible keys:**

- libraries.library_id = Primary Key
- books.book_id = Primary Key
- books.library_id = Foreign Key

**Student task:**

1. Identify the parent table.
2. Identify the child table.
3. Identify the primary key in each table.
4. Identify the foreign key.
5. Explain why this is a one-to-many relationship.

---

## Scenario 3: Students and Courses

A training organisation offers several courses.

A student can enrol in multiple courses, and each course can have multiple students.

This requires an enrolments table to connect students and courses.

**Relationship type:** Many-to-many

**Tables:**

- students
- courses
- enrolments

**Relationship:**

```text
students 1 ---- many enrolments many ---- 1 courses
```

**CSV files:**

- scenario_03_students.csv
- scenario_03_courses.csv
- scenario_03_enrolments.csv

**Possible keys:**

- students.student_id = Primary Key
- courses.course_id = Primary Key
- enrolments.student_id = Foreign Key
- enrolments.course_id = Foreign Key
- enrolments composite key option = student_id + course_id

**Student task:**

1. Identify the two main tables.
2. Identify the junction table.
3. Identify the primary keys in the main tables.
4. Identify the foreign keys in the junction table.
5. Explain why this is a many-to-many relationship.
6. Explain how the junction table resolves the many-to-many relationship.

---

## Scenario 4: Movies and Actors

A movie database stores movies and actors.

An actor can appear in multiple movies. A movie can include multiple actors.

This requires a movie_cast table to connect movies and actors.

**Relationship type:** Many-to-many

**Tables:**

- movies
- actors
- movie_cast

**Relationship:**

```text
movies 1 ---- many movie_cast many ---- 1 actors
```

**CSV files:**

- scenario_04_movies.csv
- scenario_04_actors.csv
- scenario_04_movie_cast.csv

**Possible keys:**

- movies.movie_id = Primary Key
- actors.actor_id = Primary Key
- movie_cast.movie_id = Foreign Key
- movie_cast.actor_id = Foreign Key
- movie_cast composite key option = movie_id + actor_id

**Student task:**

1. Identify the two main tables.
2. Identify the junction table.
3. Identify the primary keys in the main tables.
4. Identify the foreign keys in the junction table.
5. Explain why this is a many-to-many relationship.
6. Suggest one extra field that could be stored in the junction table.

---

## Scenario 5: Members and Events

A community centre runs events.

A member can register for many events. Each event can have many members registered.

This requires a registrations table to connect members and events.

**Relationship type:** Many-to-many

**Tables:**

- members
- events
- registrations

**Relationship:**

```text
members 1 ---- many registrations many ---- 1 events
```

**CSV files:**

- scenario_05_members.csv
- scenario_05_events.csv
- scenario_05_registrations.csv

**Possible keys:**

- members.member_id = Primary Key
- events.event_id = Primary Key
- registrations.member_id = Foreign Key
- registrations.event_id = Foreign Key
- registrations composite key option = member_id + event_id

**Student task:**

1. Identify the two main tables.
2. Identify the junction table.
3. Identify the primary keys in the main tables.
4. Identify the foreign keys in the junction table.
5. Explain why this is a many-to-many relationship.
6. Suggest one extra field that could be stored in the junction table.

---

## Overall Student Task

For each scenario:

1. Identify the tables.
2. Identify whether the relationship is one-to-many or many-to-many.
3. Identify the primary key in each main table.
4. Identify the foreign key fields.
5. For many-to-many scenarios, identify the junction table.
6. Upload the CSV files into Supabase.
7. Create the primary keys and foreign keys.
8. Create a simple ERD using the Supabase Schema Visualizer.

---

## Relationship Summary

| Scenario | Main Tables | Relationship Type | Junction Table Required? |
|---|---|---|---|
| 1 | departments, employees | One-to-many | No |
| 2 | libraries, books | One-to-many | No |
| 3 | students, courses | Many-to-many | Yes, enrolments |
| 4 | movies, actors | Many-to-many | Yes, movie_cast |
| 5 | members, events | Many-to-many | Yes, registrations |

---

## Key Reminder

A one-to-many relationship means:

```text
One record in Table A can relate to many records in Table B.
Each record in Table B relates back to one record in Table A.
```

A many-to-many relationship means:

```text
Many records in Table A can relate to many records in Table B.
```

In a relational database, a many-to-many relationship should be resolved using a junction table.

```text
Many-to-Many
     ↓
Create Junction Table
     ↓
Becomes Two One-to-Many Relationships
```
