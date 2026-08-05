# Data vs Information, Business Rules, ETL and Power Query

## Learning Outcomes

By the end of this topic, students should be able to:

- Explain the difference between data and information.
- Describe how information supports decision-making.
- Identify business rules from a business scenario.
- Explain the purpose of ETL (Extract, Transform, Load).
- Describe common data transformation activities.
- Explain how Power Query can be used as a data transformation tool.

---

## Why This Matters

Organisations collect large amounts of data every day.

Examples include:

- Customer records
- Student enrolments
- Survey responses
- Purchase transactions
- Sensor readings

Before this data can be used effectively, it must be understood, cleaned and transformed into useful information.

Understanding data, information, business rules and ETL helps ensure that reporting and analysis are based on accurate and reliable data.

---

## Data vs Information

### What is Data?

Data consists of raw facts, values or observations that have little meaning on their own.

Examples:

| Student ID | Name | Survey Score |
|-----------|----------|-------------|
| 1001 | Sarah Lee | 8 |
| 1002 | Tom Brown | 9 |
| 1003 | Priya Singh | 10 |

This table contains data, but it does not yet provide insights or answer business questions.

### Characteristics of Data

- Raw and unprocessed
- May contain errors
- May lack context
- Stored in databases, spreadsheets and systems
- Used as input for analysis

Examples:

- Postcode
- Date of birth
- Email address
- Survey response
- Number of residents

---

### What is Information?

Information is data that has been processed, organised or analysed to provide meaning.

Using the previous example:

- Average survey score = 9
- Highest score = 10
- All students scored above 7

These results are information because they help support decisions.

### Characteristics of Information

- Meaningful
- Organised
- Contextual
- Useful for decision-making
- Often presented in reports or dashboards

---

### From Data to Information

Raw Data

↓

Cleaning

↓

Transformation

↓

Analysis

↓

Information

↓

Decision Making

**Example**

Raw survey responses:

| Response |
|----------|
| Yes |
| Yes |
| No |
| Yes |

After analysis:

- 75% of respondents answered "Yes"

The percentage is information because it provides meaning.

---

## Activity: Data or Information?

Classify each example.

| Example | Data or Information? |
|----------|----------|
| Student age = 18 | Data |
| Average student age = 24 | Information |
| Survey response = "Satisfied" | Data |
| Satisfaction rate = 85% | Information |
| Postcode = 3047 | Data |
| Most respondents live in Broadmeadows | Information |

---

## Case Study: Youth Council Survey

A local council surveys young people across several suburbs.

Data collected:

- Age
- Gender
- Suburb
- Preferred activity
- Satisfaction rating

After analysis, the council discovers:

- 72% prefer sporting activities
- Craigieburn has the highest participation rate
- Average satisfaction score is 4.5 out of 5

These findings are information because they support planning and funding decisions.

---

## Business Rules

### What Are Business Rules?

Business rules are statements that define or constrain how an organisation operates.

They describe requirements, restrictions and expectations for data.

Business rules help ensure that data remains accurate, consistent and meaningful.

---

### Why Are Business Rules Important?

Business rules help organisations:

- Maintain data quality
- Reduce errors
- Standardise data entry
- Improve reporting accuracy
- Ensure systems operate consistently

---

### Examples of Business Rules

**School Scenario**

- Every student must have a unique student ID.
- A student may enrol in many units.
- A student cannot enrol in the same unit more than once.

**Library Scenario**

- Each book must have a unique ISBN.
- Members can borrow a maximum of 10 books.
- Only registered members may borrow books.

**Solar Property Scenario**

- Every property must have at least one owner.
- An owner may own multiple properties.
- Solar panel counts cannot be negative.
- Resident counts must be between 1 and 16.

---

### Identifying Business Rules

Business rules often contain words such as:

- Must
- Cannot
- Always
- Only
- Maximum
- Minimum
- At least

Example:

"Customers can make orders, but every order has to be attached to a customer."

Possible business rules:

1. A customer may place many orders.
2. An order must belong to one customer.
3. An order cannot exist without a customer.

---

## Activity: Extract Business Rules

Scenario:

A recreation centre offers activities to members.

- Members can attend many activities.
- Activities can have many members.
- Each activity has one instructor.
- Instructors may run multiple activities.

Task:

Identify:

1. The business rules.
2. Any constraints.
3. Data that would need to be collected.

---

## Understanding ETL

### What is ETL?

ETL stands for:

- Extract
- Transform
- Load

ETL is a common process used to prepare data for reporting, analysis and business intelligence.

---

### Extract

Extracting means collecting data from source systems.

Examples:

- Excel spreadsheets
- CSV files
- Databases
- Online forms
- Business applications

At this stage, data is often incomplete, inconsistent or poorly structured.

---

### Transform

Transforming means cleaning, correcting and preparing data.

Common transformation tasks include:

- Removing duplicates
- Correcting errors
- Standardising formats
- Splitting columns
- Merging columns
- Remove calculated fields
- Fixing data types

This is often the most time-consuming stage of ETL.

---

### Load

Loading means placing transformed data into a destination system.

Examples:

- Excel reports
- Dashboards
- Data warehouses
- Business intelligence platforms
- Databases

The goal is to make the data available for business use.

---

### Example ETL Process

**Extract**

Monthly youth survey responses are collected from several community centres.

**Transform**

- Remove duplicate responses.
- Standardise suburb names.
- Correct date formats.
- Remove unnecessary columns.

**Load**

The cleaned data is loaded into a reporting workbook used by council staff.

---

## Introduction to Data Transformation

### What is Data Transformation?

Data transformation is the process of changing data into a format that is suitable for analysis.  Transformation is the process that we'll most be focusing on in this topic as it's where development tends to interface with data.

Raw data is rarely perfect.

Transformation improves:

- Accuracy
- Consistency
- Reliability
- Reporting quality

---

### Example: Raw Data

| Name | Suburb | Survey Score |
|--------|--------|--------|
| Sarah Lee | broadmeadows | 8 |
| TOM BROWN | Craigieburn | 9 |
| Priya Singh | CRAIGIEBURN | 10 |

Problems:

- Inconsistent capitalisation
- Inconsistent suburb names
- Poor presentation quality

---

### Example: Transformed Data

| Name | Suburb | Survey Score |
|--------|--------|--------|
| Sarah Lee | Broadmeadows | 8 |
| Tom Brown | Craigieburn | 9 |
| Priya Singh | Craigieburn | 10 |

The data is now more suitable for reporting and analysis.

---

### Common Transformations

**Remove Duplicates**

- Identify and remove repeated records.
- Fill or Manage Missing Values
- Split Columns
- Convert/Cast columns to the correct data type
- Removing unnecessary columns and rows
- Standardise Values

---

## Activity

Download and open the dataset [solar_data.csv](../../assets/solar_data.csv)

- Identify the data quality issues.

---

## Power Query

### What is Power Query?

Power Query is a data transformation and preparation tool included with Microsoft Excel.

It allows users to:

- Import data from different sources
- Clean data
- Transform data
- Combine datasets
- Automate repetitive tasks

---

### Why Use Power Query?

Manual spreadsheet cleaning can be:

- Slow
- Repetitive
- Error-prone

Power Query records each transformation step, allowing the same process to be repeated whenever new data arrives.

This makes it ideal for ETL processes.

---

### Typical Power Query Workflow

1. Connect to a data source.
2. Review data quality.
3. Remove unnecessary columns.
4. Correct data types.
5. Standardise values.
6. Create new columns if required.
7. Load the transformed data into Excel.

---

### Common Power Query Transformations

- Remove Duplicates
    - Removes repeated records.

- Split Columns
    - Break a column into multiple columns.

- Merge Queries
    - Combine data from multiple sources.

- Replace Values
    - Correct inconsistent values.

- Change Data Types
    - Ensure numbers, dates and text are stored correctly.

[*Power Query Documentation*](https://learn.microsoft.com/en-us/power-query/)

[https://youtu.be/0aeZX1l4JT4?si=HX5QNBssh3T2KPsO&t=420](https://youtu.be/0aeZX1l4JT4?si=HX5QNBssh3T2KPsO&t=420)

---

### Benefits of Power Query

- Reduces manual effort
- Improves consistency
- Creates repeatable processes
- Handles large datasets efficiently
- Supports ETL workflows
- Integrates directly with Excel

---

## Activity

Use power query to address the data quality issues identified in the solar_data.csv dataset.  [solar_data.csv](../../assets/solar_data.csv)

---

## Summary

Data provides raw facts.

Information provides meaning.

Business rules define requirements and constraints.

ETL extracts, transforms and loads data so it can be used effectively.

Power Query is a practical ETL tool that helps automate data cleaning and transformation tasks within Excel.

Together, these concepts form an important foundation for working with data analytics, reporting and business intelligence.
