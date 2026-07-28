# Transforming Data Across Multiple Sheets and Workbooks

## Introduction

In many organisations, data is not stored in a single table.

It is common to find information spread across:

- Multiple worksheets
- Multiple workbooks
- Monthly reports
- Department exports
- Shared folders

Power Query provides tools for combining and consolidating these sources into a single dataset.

By the end of this module, you will be able to:

- Work with multiple worksheets
- Combine data from multiple workbooks
- Use Append Queries
- Use Merge Queries
- Import data from folders
- Build automated consolidation workflows

---

## Why Multiple Data Sources Create Problems

Many organisations store data like this:

```text
January.xlsx
February.xlsx
March.xlsx
April.xlsx
```

Or:

```text
January Sheet
February Sheet
March Sheet
```

Although useful for humans, this structure is difficult for reporting and analysis.

To analyse the full dataset we first need to combine the data.

---

## Working with Multiple Worksheets

A workbook may contain multiple worksheets holding similar data.

**Example**

```text
January
February
March
April
```

Each worksheet contains:

- Customer data
- Survey responses
- Transactions
- Attendance information

Rather than analysing each worksheet separately, we can combine them into a single table.

---

## Importing Multiple Worksheets

Power Query can import:

- Individual worksheets
- Multiple worksheets
- Entire workbooks

When importing a workbook, Power Query allows you to choose which sheets to use.

---

## Consistent Structures

Combining worksheets works best when structures are consistent.

**Good Example**

### January

| Date | Customer | Sales |
|--------|--------|--------|

### February

| Date | Customer | Sales |
|--------|--------|--------|

### March

| Date | Customer | Sales |
|--------|--------|--------|

---

## Inconsistent Structures

Different column names often create issues.

**January**

| CustomerID | Name |
|------------|--------|

**February**

| CustID | Customer Name |
|---------|---------|

These must often be standardised before combining.

---

## Appending Queries

Append combines datasets vertically.

Think of append as stacking tables on top of each other.

**Example**

January:

| Customer |
|-----------|
| Sarah |
| David |

February:

| Customer |
|-----------|
| Minh |
| Priya |

Result:

| Customer |
|-----------|
| Sarah |
| David |
| Minh |
| Priya |

---

## When to Use Append

Use Append when:

- Columns are similar
- Data represents the same thing
- New records need to be added

Common examples:

- Monthly reports
- Survey responses
- Attendance records
- Transaction histories

---

## Append Example

Monthly youth survey responses:

### January

| ResponseID | Rating |
|------------|---------|
| R001 | 4 |
| R002 | 5 |

### February

| ResponseID | Rating |
|------------|---------|
| R003 | 3 |
| R004 | 5 |

### Combined

| ResponseID | Rating |
|------------|---------|
| R001 | 4 |
| R002 | 5 |
| R003 | 3 |
| R004 | 5 |

---

## Merging Queries

Merge combines data horizontally.

Think of merge as joining tables together using a matching field.

---

## Example

### Orders

| CustomerID | Order |
|------------|--------|
| 1001 | Laptop |
| 1002 | Mouse |

### Customers

| CustomerID | Name |
|------------|--------|
| 1001 | Sarah |
| 1002 | David |

### Merged Result

| CustomerID | Name | Order |
|------------|--------|--------|
| 1001 | Sarah | Laptop |
| 1002 | David | Mouse |

---

## Keys

Merges require a common field.

Common keys include:

- CustomerID
- StudentID
- OrderID
- EmployeeID
- Survey ResponseID

Good keys should be:

- Unique
- Consistent
- Complete

---

## Common Merge Problems

Problems often occur when:

- IDs are missing
- IDs are duplicated
- Different formats are used

**Example**

```text
001
```

versus

```text
1
```

These may not match correctly.

---

## Standardising Before Combining

Before combining data:

- Standardise column names
- Standardise formats
- Standardise dates
- Standardise categories

This reduces errors during append and merge operations.

---

## Best Practices

When combining datasets:

- Standardise structure first
- Check keys carefully
- Remove duplicates
- Review unmatched records
- Document your queries

---

## Activity: Combine Monthly Worksheets

Using the transformed `namesX` datasets used previously.  Join the datasets together to create a single dataset containing all records.
[names.xlsx](../../assets/names.xlsx)
[names2.xlsx](../../assets/names2.xlsx)
[names3.xlsx](../../assets/names3.xlsx)
