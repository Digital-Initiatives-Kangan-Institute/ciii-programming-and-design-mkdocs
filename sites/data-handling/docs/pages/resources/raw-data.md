# Understanding Raw Data

## Introduction

Before we can clean or transform data, we first need to understand what we are working with.

In real projects, data rarely arrives in a perfect format.

A common mistake is to start cleaning data immediately without first examining:

- The structure of the data
- Missing values
- Duplicates
- Data types
- Inconsistencies

Understanding the data comes before transforming the data.

---

## What is Raw Data?

Raw data is data in its original state before it has been cleaned, standardised, or transformed.

Examples include:

- Survey responses
- Excel exports
- CSV files
- Transaction records
- Sensor readings
- Customer databases

Raw data often contains errors and inconsistencies.

---

## Types of Data

Not all data looks the same.

Understanding the type of data helps us decide how it should be handled.

---

### Structured Data

Structured data is organised into rows and columns.

**Example**

| StudentID | Name | Course |
|------------|----------|----------|
| 1001 | Sarah Lee | Cyber |
| 1002 | David Tran | Programming |
| 1003 | Priya Sharma | Networking |

Structured data is easy to analyse and is commonly stored in databases.

---

### Semi-Structured Data

Semi-structured data contains some organisation but is not perfectly arranged in rows and columns.

**Example**

```text
Youth Survey Results

Collected March 2026

Student Information

Name      Age      Suburb
Sarah     15       Broadmeadows
David     16       Glenroy
```

Common characteristics:

- Multiple header rows
- Blank rows
- Notes mixed into data
- Report layouts
- Merged cells

---

### Unstructured Data

Unstructured data has little or no predefined structure.

Examples:

- Survey comments
- Emails
- Support tickets
- Reports
- Social media posts

**Example**

```text
I would like more buses available after youth activities.
```

Although useful, this data is much harder for computers to analyse.

---

## Why Understanding Data Matters

Poor understanding often leads to:

- Incorrect transformations
- Data loss
- Incorrect reporting
- Misleading dashboards

Before making changes we should understand:

- What the data represents
- How it was collected
- What quality issues exist

---

## Data Profiling

Data profiling is the process of examining a dataset to understand its content, structure, and quality.

Think of profiling as investigating the data before attempting to fix it.

---

## Questions to Ask

When reviewing a dataset ask:

- What does each column mean?
- Are there blank values?
- Are there duplicate records?
- Are the values consistent?
- Are there invalid values?
- Do all rows represent the same thing?

---

## Profiling Example

Consider the following data:

| CustomerID | State |
|------------|--------|
| 1001 | VIC |
| 1002 | Victoria |
| 1003 | vic |
| 1004 | VIC |

Questions:

- How many unique values exist?
- Are all values referring to the same state?
- Should they be standardised?

---

## Understanding Columns

Every column should have a clear meaning.

**Good Example**

| Name | Age | Suburb |
|--------|------|---------|

Each column stores a single type of information.

---

**Poor Example**

| Student Details |
|------------------|
| Sarah, 15, Broadmeadows |

Multiple pieces of information are combined into a single column.

This makes analysis more difficult.

---

## Understanding Rows

Each row should represent a single observation.

**Good Example**

| ResponseID | Rating |
|------------|--------|
| 1 | 4 |
| 2 | 5 |
| 3 | 3 |

Each row represents one survey response.


**Poor Example**

```text
Student Information

Sarah
David
Priya

Survey Responses

...
```

Multiple data structures are mixed together.

---

## Data Types

Data often falls into several categories.

---

### Text

Examples:

```text
Sarah
Broadmeadows
Programming
```

---

### Numbers

Examples:

```text
12
45
1050
```

---

### Dates

Examples:

```text
2026-03-01
2026-04-15
```

---

### Boolean Values

Values with only two possible outcomes.

Examples:

```text
Yes / No
True / False
Y / N
```

---

## Common Checks on Data

**Missing Values**: Missing values are one of the most common data quality issues.

**Example**

| Student | Email |
|----------|---------|
| Sarah | sarah@email.com |
| David | |
| Minh | minh@email.com |

Questions:

- How many values are missing?
- Can the missing information be recovered?
- Should records be removed?

---

**Duplicate Records**: Duplicate records can create incorrect reports and statistics.

**Example**

| StudentID | Name |
|-----------|----------|
| 1001 | Sarah |
| 1001 | Sarah |
| 1002 | David |

Questions:

- Are these accidental duplicates?
- Are they valid multiple records?
- Should they be merged or removed?

---

**Inconsistent Values**: Different values may represent the same thing.

**Example**

| State |
|---------|
| VIC |
| Victoria |
| vic |
| V.I.C |

Humans understand these are the same.

Computers often see them as different values.

---

**Invalid Values**: Data may contain values that are impossible or unlikely.

**Example**

| Age |
|------|
| 15 |
| 17 |
| 250 |

Questions:

- Is the value realistic?
- Is it a data entry error?
- Does it meet business rules?

---

## Common Spreadsheet Warning Signs

Be cautious when you see:

- Blank rows
- Blank columns
- Merged cells
- Multiple tables on one sheet
- Totals inside datasets
- Notes mixed with records
- Different date formats
- Inconsistent naming conventions

These often indicate additional transformation work will be required.

---

## Activity: Profile a Dataset

Review the supplied workbook.

For each worksheet identify:

- Missing values
- Duplicate records
- Inconsistent values
- Invalid values
- Mixed data types
- Blank rows
- Merged cells
- Unstructured data

Record findings in the Issue Log worksheet.

---

## Discussion Questions

1. Which issues would prevent successful analysis?
2. Which issues would prevent a Power Query import?
3. Which issues could be fixed automatically?
4. Which issues require human review?
5. Which issues present the highest risk?

---

## Key Takeaways

Before transforming data, we should understand:

- The structure of the dataset
- The meaning of each row
- The meaning of each column
- The quality issues present
- The types of data stored
