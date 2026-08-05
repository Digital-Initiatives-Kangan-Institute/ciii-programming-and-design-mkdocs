# Redundancy in Databases

## Introduction

One of the primary purposes of database design is to remove/reduce to amount of **data redundancy**. **Redundancy** is the unnecessary repetition of data within a database.

While a small amount of duplication may not seem like a problem, excessive redundancy can lead to wasted storage, inconsistent data, and increased maintenance effort.

Keep in mind that what in the first instance may seem like a small amount of duplication can quickly grow into a large problem as the database grows.  We need to be thinking in large tems when designing databases (millions of records) and not just in terms of the small number of records we may be working with at the start.

---

## What is Redundancy?

Redundancy is the unnecessary repetition of data within a database.

Consider a training organisation that stores student enrolment information.

| StudentID | StudentName | Course | Teacher |
|------------|-------------|----------|----------|
| 1001 | Sarah Lee | Excel Basics | John Smith |
| 1002 | David Brown | Excel Basics | John Smith |
| 1003 | Emma Green | Excel Basics | John Smith |

Notice that the teacher's name appears repeatedly for every student enrolled in the course.

Although this information is correct, the course and teacher's name only needs to be stored once.

This repeated storage of the same information is an example of redundancy.

---

## Why is Redundancy a Problem?

In database design there are four main redundacy problems that we are addressing:

  1. Increased storage requirements
  2. Data Inconsistency
  3. Update Anomalies
  4. Insertion and Deletion Errors

### Increased Storage Requirements

Repeatedly storing the same data consumes additional storage space.

For a small table this may not matter, but large organisations can store millions of records.

If information is repeated thousands of times, storage requirements increase significantly.

### Data Inconsistency

When duplicated information exists in multiple locations, updates may not be applied consistently.

Imagine John Smith changes their name to John Wilson.

| StudentID | StudentName | Course | Teacher |
|------------|-------------|----------|----------|
| 1001 | Sarah Lee | Excel Basics | John Wilson |
| 1002 | David Brown | Excel Basics | John Smith |
| 1003 | Emma Green | Excel Basics | John Smith |

Now the database contains conflicting information.

Which teacher name is correct?

This issue is known as a *data inconsistency*.

### Update Anomalies

When information changes, every occurrence must be updated.

The more redundant data that exists, the more work is required to maintain the database.

### Insertion and Deletion Errors

Manually updating multiple records increases the likelihood of mistakes.

Some records may be missed, entered incorrectly, or accidentally deleted.

---

## Further issues with Redundancy


| StudentID | StudentName | Course | Teacher |
|------------|-------------|----------|----------|
| 1001 | Sarah Lee | Excel Basics | John Smith |
| 1002 | David Brown | Excel Basics | John Smith |
| 1003 | Emma Green | Excel Basics | John Smith |

Taking the example used before, there is another issue that crops up when we add additional courses and teachers to the database.  Let's add extra course that a student may undertake and a different teacher for that course.


| StudentID | StudentName | Course | Teacher |
|------------|-------------|----------|----------|
| 1001 | Sarah Lee | Excel Basics | John Smith |
| 1002 | David Brown | Excel Basics | John Smith |
| 1003 | Emma Green | Excel Basics | John Smith |
| 1001 | Sarah Lee | Word Basics | Karen Jones |
| 1002 | David Brown | Word Basics | Karen Jones |
| 1001 | Sarah Lee | PowerPoint Basics | John Smith |
| 1003 | Emma Green | PowerPoint Basics | John Smith |

Now alongside the duplication of the teacher's name, we also have duplication of the student's name.  This can have a multiplicative effect if we add further data/information to the database.  For example, if we add a new column for the student's date of birth, this will also be duplicated for each course that the student undertakes.  Or if we add the location of the course, this will also be duplicated for each student that undertakes the course.

---

## Reducing Redundancy

A common solution is to split the data into separate tables.

**Teachers Table**

| TeacherID | TeacherName |
|------------|-------------|
| T01 | John Smith |
| T02 | Karen Jones |


**Students Table**

| StudentID | StudentName | Course | TeacherID |
|------------|-------------|----------|----------|
| 1001 | Sarah Lee | Excel Basics | T01 |
| 1002 | David Brown | Excel Basics | T01 |
| 1003 | Emma Green | Excel Basics | T01 |
| 1001 | Sarah Lee | Word Basics | T02 |
| 1002 | David Brown | Word Basics | T02 |
| 1001 | Sarah Lee | PowerPoint Basics | T01 |
| 1003 | Emma Green | PowerPoint Basics | T01 |

Now each teacher's information is stored only once.

Students simply reference the teacher using the TeacherID.  The same can be done with the Course.  We can seperate the Course into its own table with a CourseID and then reference that in the Students table.  We can also reference the teacher in the Course table rather than the Students table.  We can then even further reduce duplication by having a Student table that gets referenced. 

??? notes "Final Tables"
    *Teachers Table*
    
    | TeacherID | TeacherName |
    |------------|-------------|
    | T01 | John Smith |
    | T02 | Karen Jones |
    
    
    *Course Table*
    
    |CourseID | CourseName | TeacherID |
    |---------|------------|-----------|
    | Ex01 | Excel Basics | T01 |
    | W01 | Word Basics | T02 |
    | P01 | PowerPoint Basics | T01 |
    
    
    *Students Table*

    | StudentID | StudentName | 
    |------------|-------------|
    | 1001 | Sarah Lee |
    | 1002 | David Brown |
    | 1003 | Emma Green |
    
    
    *Enrolments Table*

    | studentID | CourseID |
    |------------|---------|
    | 1001 | Ex01 |
    | 1002 | Ex01 |
    | 1003 | Ex01 |
    | 1001 | W01 |
    | 1002 | W01 |
    | 1001 | P01 |
    | 1003 | P01 |
    

This approach:

- Reduces storage requirements
- Improves data consistency
- Makes updates easier
- Reduces errors

---

## Activity: Identify Redundancy

Examine the table below.

| CustomerID | CustomerName | Product | Salesperson |
|------------|-------------|----------|-------------|
| C001 | Alice Brown | Laptop | David Chen |
| C002 | Michael Jones | Laptop | David Chen |
| C003 | Sarah Wilson | Laptop | David Chen |
| C004 | James Smith | Printer | Emma White |

**Questions**

1. Which information appears to be repeated?
2. What problems could occur if David Chen changes departments?
3. How could the table be redesigned to reduce redundancy?

---

## Knowledge Check

1. What is redundancy?
2. Why can redundancy lead to inconsistent data?
3. What is an update anomaly?
4. What is an insert anomaly?
5. What is a delete anomaly?
6. What are two benefits of reducing redundancy?

---

## Summary

Redundancy occurs when the same data is stored multiple times unnecessarily.

Poorly designed databases with high levels of redundancy can lead to:

- Increased storage requirements
- Data inconsistencies
- Update, insert, and delete anomalies
- Increased maintenance effort
- Higher risk of errors

Good database design reduces redundancy by separating information into related tables and storing each piece of information only once wherever possible.
