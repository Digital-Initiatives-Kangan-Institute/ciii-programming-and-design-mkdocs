# Common Data Transformation Patterns

## Introduction

Certain data problems appear repeatedly across organisations and industries.

Learning these common transformation patterns allows you to solve many real-world data issues quickly.

By the end of this module, you will be able to:

- Recognise common transformation patterns
- Convert report-style data into tabular data
- Unpivot columns
- Fill missing values
- Create conditional columns
- Extract useful information from text

---

## What is a Transformation Pattern?

A transformation pattern is a common technique used to convert data from one structure into another.

Examples include:

- Unpivoting
- Filling values
- Extracting text
- Categorising data
- Creating calculated fields

---

## Report Data vs Analysis Data

Data created for humans often differs from data required for analysis.

**Report Format**

| Product | Jan | Feb | Mar |
|-----------|------|------|------|

**Analysis Format**

| Product | Month | Sales |
|-----------|--------|--------|

This transformation is one of the most common in Power Query.

---

## Understanding Unpivot

Unpivot converts multiple columns into rows.

### Before

| Product | Jan | Feb | Mar |
|----------|------|------|------|
| Laptop | 100 | 120 | 130 |

### After

| Product | Month | Sales |
|----------|--------|--------|
| Laptop | Jan | 100 |
| Laptop | Feb | 120 |
| Laptop | Mar | 130 |

---

## Why Unpivot Matters

Many reporting tools expect data to be stored in:

```text
One row per observation
```

rather than:

```text
One column per period
```

Unpivoting helps satisfy this requirement.

---

## Fill Down

Some datasets place headings above groups of records.

### Before

| Category |
|-----------|
| Hardware |
| |
| |
| Software |
| |

### After

| Category |
|-----------|
| Hardware |
| Hardware |
| Hardware |
| Software |
| Software |

---

## Why Fill Down is Useful

Common uses include:

- Financial reports
- Survey exports
- Legacy systems
- Government reports

---

## Extracting Text

Text often contains useful information hidden inside larger values.

---

## Example

**Before**

```text
Customer-1047
```

**After**

```text
1047
```

---

## Extracting Postcodes

**Before**

```text
Broadmeadows VIC 3047
```

**After**

```text
3047
```

---

## Extracting Dates

**Before**

```text
Meeting held on 12 March 2026
```

**After**

```text
12 March 2026
```

---

## Conditional Columns

Conditional Columns allow us to create categories based on rules.

---

## Example

Sales:

```text
1500
```

New Column:

```text
High Value
```

---

## Another Example

Age:

```text
16
```

Age Group:

```text
15-17
```

---

## Categorising Data

Many datasets contain similar values that can be grouped together.

### Before

```text
Sports
Basketball
Football
Netball
```

### After

```text
Sport
Sport
Sport
```

---

## Standardising Survey Responses

### Before

```text
YES
Yes
Y
```

### After

```text
Yes
Yes
Yes
```

---

## Creating Business Rules

Business rules help standardise data.

**Examples**

- Ratings between 1 and 5 only
- Ages must be positive
- Postcodes must be four digits
- Dates must be valid

---

## Identifying Outliers

Transformation often reveals unusual values.

### Example

```text
12
15
16
250
```

The value:

```text
250
```

may require investigation.

---

## Working with Youth Survey Data

Common transformations include:

- Standardising suburb names
- Standardising program categories
- Creating age groups
- Categorising comments
- Extracting keywords

---

## Building a Transformation Pipeline

A typical workflow might be:

```text
Import Data
```

↓

```text
Remove Blank Rows
```

↓

```text
Standardise Values
```

↓

```text
Unpivot
```

↓

```text
Create Categories
```

↓

```text
Load Dataset
```

---

## Activity: Fixing Report-Style Data

Using the supplied workbook:

1. Identify report-style structures.
2. Remove unnecessary formatting.
3. Unpivot monthly columns.
4. Create an analysis-ready table.

---

## Activity: Youth Survey Transformation Patterns

1. Standardise program names.
2. Create age groups.
3. Extract keywords from comments.
4. Create categories.
5. Produce an analysis-ready dataset.

---

## Key Takeaways

Many transformation problems follow predictable patterns.

Common patterns include:

- Unpivot
- Fill Down
- Text Extraction
- Categorisation
- Conditional Columns

Remember:

> The more transformation patterns you recognise, the faster you can prepare data for analysis.
