# Good Data Practices

## Why Data Quality Matters

Before we can analyse, visualise, or report on data, we need to ensure the data is accurate and usable.

A common saying in data analytics is:

If poor quality data is entered into a system, poor quality information will be produced.

Poor quality data can lead to:
- Incorrect reports
- Poor business decisions
- Failed automation
- Duplicate records
- Inaccurate dashboards
- Wasted time cleaning data

## Data vs Information
In addition to poor data quality, we also need to consider the difference between data and information.
**Data** has no context or meaning.  **Information** is data that has been processed and given context.

For example, an address on *85 Smith St, Cremorne, Vic, 3121* is **information**.  This information is made up of **data** such as the street number, street name, suburb, state, and postcode - (85 | Smith St | Cremorne | Vic | 3121).

!!! note
    Data transformation is often less about analysing data and more about fixing problems created by how humans enter and store information.

---

## What Does Good Data Look Like?

Good data should have several important characteristics.

### Accurate

Data should reflect reality.


| Bad Data | Good Data |
|-----------|-----------|
| Customer age = 250 | Customer age = 25 |
| Quantity sold = -100 | Quantity sold = 100 |

---

### Complete

Required information should be present.


| CustomerID | Name | Email |
|------------|--------|--------|
| 1001 | Anh Nguyen | <anh@example.com> |
| 1002 | Sarah Smith | |

The second record is incomplete because the email address is missing.

---

### Consistent

Data should use the same format throughout the dataset.

**Bad Example**

| State |
|---------|
| VIC |
| Victoria |
| vic |
| V.I.C |


**Good Example**

| State |
|---------|
| VIC |
| VIC |
| VIC |
| VIC |

---

### Unique

Duplicate records should be avoided.

**Bad Example**

| CustomerID | Name |
|------------|---------|
| 1001 | Jane Doe |
| 1001 | Jane Doe |

Duplicate records can lead to incorrect reporting and calculations.

---

### Timely

Data should be current and up to date.

Old information may no longer be useful for decision making.

**Example**

A customer's address from 10 years ago may no longer be valid.

---

### Valid

Data should follow agreed business rules.

**Examples**

- Postcodes must have four digits.
- Ages cannot be negative.
- Dates must be valid calendar dates.

---

## Data and Computers

Humans can understand messy information surprisingly well.

Computers cannot.

Consider the following values:

```text
VIC
Victoria
vic
Vict.
```

A person understands these all refer to Victoria.

A computer sees four completely different values.

---

## Tabular Data

Most systems work best when data is organised into rows and columns.

**Example** of Good Tabular Data

| StudentID | FirstName | LastName | Course |
|------------|------------|------------|---------|
| 1001 | Sarah | Lee | Cyber |
| 1002 | David | Tran | Networking |
| 1003 | Priya | Sharma | Programming |

Each row represents one record.

Each column represents one attribute.

---

## One Observation Per Row

Each row should represent a single thing.

**Good Example**

| OrderID | Customer | Product |
|----------|-----------|----------|
| 101 | Sarah | Laptop |
| 102 | David | Keyboard |

---

## One Attribute Per Column

Each column should contain one piece of information.

**Bad Example**

| Customer Details |
|-------------------|
| Sarah, VIC, 0400000000 |

**Good Example**

| Name | State | Phone |
|--------|--------|---------|
| Sarah | VIC | 0400000000 |

---

## Common Spreadsheet Problems

Many Excel files are designed for people to read, not for computers to process.

These files often contain problems that make transformation difficult.

### Multiple Tables on One Sheet

```text
Customer Table

(blank rows)

Sales Table

(blank rows)

Inventory Table
```

Computers generally expect a single table of data.

---

### Blank Rows and Columns

Blank rows often break imports and calculations.

**Bad Example**

```text
Name
Sarah
David

Priya
Minh
```

---

### Merged Cells

Merged cells look nice in reports but make processing difficult.

**Example**

```text
Sales Report 2025
```

Merged across ten columns.

This may look good for humans but creates issues for data tools.

---

### Totals Inside the Data

**Bad Example**

| Product | Sales |
|-----------|---------|
| Laptop | 100 |
| Mouse | 50 |
| Total | 150 |
| Keyboard | 30 |

The Total row is not actual data and can cause problems during analysis.

??? example "Why are things such as totals, averages and maximum/minimum values not considered data?"
    Because they are not observations of a single thing.  They are calculations based on the data.

---

## Data Profiling
 
Before cleaning data we should investigate it.
 
Ask the following questions:

- What does each column represent?
- Are there missing values?
- Are there duplicate rows?
- Are formats consistent?
- Are there invalid values?
- Is every row describing the same thing?
 
This process is known as **data profiling**.

---

## Class Activity
In the Excel file found [here](../../assets/Module1_Data_Quality_Activity.xlsx)

Identify:

- Missing values
- Duplicate records
- Inconsistent values
- Invalid values
- Blank rows
- Multiple tables
- Merged cells

---

## Key Takeaways

Good data is:

- Accurate
- Complete
- Consistent
- Unique
- Timely
- Valid

Data should:

- Have one observation per row
- Have one attribute per column
- Avoid merged cells
- Avoid blank rows
- Avoid report formatting
- Be easy for computers to process
