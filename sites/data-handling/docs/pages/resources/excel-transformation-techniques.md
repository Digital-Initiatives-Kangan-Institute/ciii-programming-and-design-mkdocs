# Core Transformation Techniques in Excel

## Introduction

Once we understand the structure and quality of our data, we can begin transforming it into a format suitable for analysis.

Data transformation is the process of modifying data so that it becomes:

- Consistent
- Accurate
- Complete
- Analysis-ready

In this module, we will use standard Excel tools to clean and transform messy datasets.

---

## The Transformation Process

Data transformation typically follows a series of steps:

1. Inspect the data
2. Remove unnecessary information
3. Standardise formats
4. Correct inconsistencies
5. Handle missing values
6. Remove duplicates
7. Restructure columns where necessary
8. Validate the final dataset

---

## Removing Unnecessary Data

One of the first tasks is removing information that does not belong in the dataset.

### Blank Rows

Blank rows often cause problems when:

- Filtering
- Sorting
- Importing into Power Query
- Creating Pivot Tables

**Before**

| Student |
|----------|
| Sarah |
| David |
| |
| Minh |

**After**

| Student |
|----------|
| Sarah |
| David |
| Minh |


### Blank Columns

Blank columns can make datasets difficult to work with and should generally be removed.

### Totals Rows

Report-style totals should not exist within raw data.

**Before**

| Product | Sales |
|----------|--------|
| Laptop | 100 |
| Mouse | 50 |
| Total | 150 |
| Keyboard | 40 |

**After**

| Product | Sales |
|----------|--------|
| Laptop | 100 |
| Mouse | 50 |
| Keyboard | 40 |

### Notes and Comments

Notes intended for humans should usually be separated from the dataset.

**Example**

```text
Data exported from old system.
Need to verify records before reporting.
```

These notes are useful but should not be mixed into the data table.

---

## Standardising Text Values

Computers treat different text values as different categories.

### Inconsistent Categories

**Before**

```text
VIC
Victoria
vic
V.I.C
```

**After**

```text
VIC
VIC
VIC
VIC
```

### Find and Replace

Excel's Find and Replace tool can quickly standardise data.

Example:

Find:

```text
Victoria
```

Replace with:

```text
VIC
```

---

## Cleaning Text

Text values often contain unwanted spaces or formatting.

### Removing Extra Spaces

**Before**

```text
 Sarah
Sarah
Sarah
```

Although these may look identical, they are actually different values.

**After**

```text
Sarah
Sarah
Sarah
```

### Consistent Capitalisation

**Before**

```text
SARAH
sarah
Sarah
```

**After**

```text
Sarah
Sarah
Sarah
```

---

## Standardising Dates

Dates commonly appear in different formats.

**Before**
```text
01/02/2026
1 Feb 2026
2026-02-01
```


**After**
```text
2026-02-01
2026-02-01
2026-02-01
```


**Why This Matters**
Dates stored inconsistently can cause problems when:

- Sorting
- Filtering
- Reporting
- Creating timelines

---

## Standardising Numbers

Numbers must be stored as numbers rather than text.

**Example**

**Text**

```text
"100"
```

**Number**

```text
100
```

A text value may look like a number but cannot always be used in calculations.

### Common Number Problems

**Currency Symbols**

```text
$1,200
```

**Commas**

```text
1,200
```

**Text Mixed with Numbers**

```text
1200 dollars
```

These may need cleaning before analysis.

---

## Working with Missing Values

Missing values are common in real-world data.

**Example**

| Name | Email |
|--------|---------|
| Sarah | sarah@email.com |
| David | |
| Minh | minh@email.com |

### Options for Handling Missing Values

**Keep the Record**

If the missing data is not important.

**Remove the Record**

If the record cannot be used without the missing value.

**Replace the Value**

Examples:

```text
Unknown
Not Provided
N/A
```

!!! note
    There is no single correct approach. The appropriate solution depends on the business requirements.

---

## Splitting Columns

Sometimes data contains multiple pieces of information in a single field.

**Example**

**Before**

| Full Name |
|------------|
| Sarah Lee |

**After**

| First Name | Last Name |
|------------|-----------|
| Sarah | Lee |

### Other Examples

**Before**

```text
Broadmeadows, VIC
```

**After**

| Suburb | State |
|---------|-------|
| Broadmeadows | VIC |

---

## Combining Columns

Sometimes separate columns should be joined together.

**Example**

**Before**

| First Name | Last Name |
|------------|-----------|
| Sarah | Lee |

**After**

| Full Name |
|-----------|
| Sarah Lee |

---

## Standardising Yes/No Values

Survey data often contains inconsistent responses.

### Before

```text
Yes
YES
yes
Y
True
```

### After

```text
Yes
Yes
Yes
Yes
Yes
```

### Another Example

**Before**

```text
No
NO
N
False
```

**After**

```text
No
No
No
No
```

---

## Removing Duplicates

Duplicate records can distort reporting and analysis.

**Example**

**Before**

| ResponseID |
|------------|
| R001 |
| R001 |
| R002 |

**After**

| ResponseID |
|------------|
| R001 |
| R002 |

### Important Question

Are the records actually duplicates?

Sometimes two records look similar but represent different events.

Always review duplicates before removing them.

---

## Checking for Invalid Values

Transformation is also an opportunity to identify invalid data.

**Example: Age**

**Before**

| Age |
|------|
| 15 |
| 17 |
| 250 |

The value 250 is likely incorrect.

**Example: Rating**

Survey scale:

```text
1 to 5
```

Values such as:

```text
0
6
10
```

may indicate data entry issues.

---

## Working with Survey Data

Survey datasets contain many common transformation challenges.

### Standardising Program Names

**Before**

```text
Sports
Sport
sports
SPORTS
```

**After**

```text
Sports
Sports
Sports
Sports
```

### Standardising School Year Levels

**Before**

```text
Year 10
Y10
Yr 10
10
```

**After**

```text
Year 10
Year 10
Year 10
Year 10
```

---

## Preparing Data for Analysis

Before analysis begins, check:

- Are column names meaningful?
- Are rows complete?
- Are formats consistent?
- Are duplicates removed?
- Are invalid values addressed?
- Are categories standardised?

---

## Transformation Checklist

Before finishing your work:

✅ Blank rows removed

✅ Blank columns removed

✅ Totals rows removed

✅ Dates standardised

✅ Text values standardised

✅ Categories standardised

✅ Missing values reviewed

✅ Duplicates reviewed

✅ Invalid values investigated

✅ Dataset ready for analysis

---

## Activity: Clean a Customer Dataset

Using Excel tools only:

1. Remove blank rows.
2. Remove unnecessary columns.
3. Standardise state values.
4. Standardise dates.
5. Remove duplicates.
6. Fix inconsistent text.
7. Investigate invalid values.
8. Produce a clean dataset.

---

## Activity: Clean a Youth Survey Dataset

Using the supplied workbook:

1. Standardise Yes/No responses.
2. Standardise program names.
3. Standardise year level values.
4. Remove duplicate responses.
5. Identify invalid ages.
6. Identify missing values.
7. Produce an analysis-ready table.

---

## Key Takeaways

Data transformation is the process of converting messy data into reliable information.

Good transformation results in data that is:

- Consistent
- Accurate
- Complete
- Easy to analyse

Remember:

> The goal is not simply to clean data. The goal is to create a dataset that can be trusted for decision making.
