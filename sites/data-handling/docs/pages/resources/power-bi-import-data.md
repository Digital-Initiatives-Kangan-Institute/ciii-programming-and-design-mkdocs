# Module 2: Importing and Preparing Data

## Module Overview

Before data can be analysed and visualised, it must first be imported into Power BI and prepared for reporting. Data often comes from multiple sources and may contain inconsistencies, errors, or formatting issues that need to be addressed.

In this module, students will learn how to connect Power BI to common data sources, load data into a report, and perform basic data preparation tasks using Power Query.

Some files that we'll need for the next few modules:

- [powerbi_customers](../../assets/powerbi_customers.csv)
- [powerbi_products](../../assets/powerbi_products.csv)
- [powerbi_sales](../../assets/powerbi_sales.csv)

---

## Learning Outcomes

By the end of this module, students will be able to:

- Connect Power BI to common data sources.
- Import data from Excel and CSV files.
- Navigate the Power Query Editor.
- Apply basic data transformations.
- Identify and correct common data quality issues.
- Configure appropriate data types.
- Prepare datasets for reporting and analysis.

---

## Understanding Data Sources

Power BI can connect to a wide variety of data sources. This flexibility allows organisations to combine information from multiple systems into a single reporting environment.

### Common Data Sources

#### Excel Workbooks

Excel is one of the most commonly used data sources in Power BI.

Examples include:

- Sales reports
- Budgets
- Customer lists
- Inventory records

Benefits:

- Easy to access
- Widely used in business
- Supports multiple worksheets and tables

---

#### CSV Files

CSV (Comma Separated Values) files are simple text files that store tabular data.

Examples include:

- Exported reports
- Transaction records
- System-generated data

Benefits:

- Lightweight format
- Compatible with many systems
- Easy to transfer and share

---

#### Databases

Many organisations store data in relational databases.

Examples:

- SQL Server
- MySQL
- PostgreSQL
- Oracle

Benefits:

- Large data volumes
- Centralised storage
- Real-time reporting potential

---

#### Online Services

Power BI can connect directly to cloud-based services.

Examples:

- SharePoint
- Salesforce
- Microsoft Dynamics
- Azure Services

Benefits:

- Automated updates
- Cloud integration
- Reduced manual processing

---

## Connecting to Data

Connecting to a data source is the first step in building a Power BI report.

### The Get Data Process

Power BI uses the **Get Data** feature to establish connections with external data sources.

Typical process:

1. Select **Get Data**.
2. Choose a data source.
3. Browse or connect to the source.
4. Preview available data.
5. Load or transform the data.

---

## Previewing Data

Before importing data, Power BI provides a preview of the available information.

Previewing allows users to:

- Verify the correct dataset has been selected.
- Review column names.
- Check data quality.
- Identify missing or incorrect values.
- Confirm expected records are present.

Data should always be reviewed before loading into a report.

---

## Loading Data

Once data has been reviewed, it can be loaded into Power BI.

### Load Option

The Load option imports data directly into the Power BI model.

This approach is suitable when:

- Data is already clean.
- Minimal transformation is required.
- Rapid reporting is needed.

---

### Transform Data Option

The Transform Data option opens Power Query Editor before loading.

This approach is suitable when:

- Data requires cleaning.
- Data types need adjustment.
- Columns need to be removed or renamed.
- Multiple datasets are being prepared.

In most professional reporting environments, some level of transformation is required before data is loaded.

---

## Introduction to Power Query

Power Query is the data preparation component of Power BI.

It provides tools for:

- Cleaning data
- Transforming data
- Combining data sources
- Improving data quality

Power Query records each transformation step, allowing processes to be repeated automatically whenever data is refreshed.

---

## Power Query Interface

The Power Query Editor contains several important areas.

### Queries Pane

Located on the left side of the screen.

Purpose:

- Displays imported queries.
- Allows navigation between datasets.
- Organises multiple data sources.

---

### Data Preview Area

Located in the centre of the screen.

Purpose:

- Displays dataset contents.
- Allows inspection of rows and columns.
- Supports transformation activities.

---

### Applied Steps

Located on the right side of the screen.

Purpose:

- Displays all transformation steps.
- Allows modification of previous actions.
- Provides an audit trail of changes.

Examples:

- Removed Columns
- Changed Type
- Renamed Columns
- Filtered Rows

---

## Data Quality Concepts

Effective reporting depends on high-quality data.

### Common Data Quality Issues

#### Missing Values

Some records may contain blank or null values.

Examples:

- Missing customer names
- Missing sale amounts
- Missing dates

Potential impacts:

- Incorrect calculations
- Incomplete analysis
- Reduced confidence in reporting

---

#### Duplicate Records

A dataset may contain multiple copies of the same record.

Examples:

- Duplicate customers
- Repeated transactions
- Re-imported data

Potential impacts:

- Inflated totals
- Inaccurate metrics
- Misleading visualisations

---

#### Inconsistent Formatting

Data may be entered using different formats.

Examples:

- VIC
- Vic
- Victoria
- victoria

Potential impacts:

- Incorrect grouping
- Fragmented categories
- Reporting inaccuracies

---

#### Incorrect Data Types

Values may be stored as the wrong type.

Examples:

| Value | Incorrect Type | Correct Type |
|---------|---------|---------|
| 500 | Text | Whole Number |
| 15/05/2026 | Text | Date |
| 125.75 | Text | Decimal Number |

Potential impacts:

- Calculation errors
- Visualisation issues
- Reduced analytical capability

---

## Basic Transformations

Power Query provides tools for correcting common data issues.

---

### Renaming Columns

Clear column names improve report readability.

Examples:

| Original Name | Improved Name |
|--------------|--------------|
| Cust_ID | Customer ID |
| ProdName | Product Name |
| Qty | Quantity |

Benefits:

- Easier understanding
- Improved report maintenance
- Better collaboration

---

### Removing Columns

Datasets often contain unnecessary information.

Examples:

- Internal system identifiers
- Temporary fields
- Obsolete attributes

Removing unused columns:

- Simplifies reports
- Improves performance
- Reduces clutter

---

### Reordering Columns

Columns can be rearranged to improve organisation.

Benefits:

- Easier data review
- Improved navigation
- Better dataset structure

---

### Filtering Rows

Power Query can remove unwanted records before data is loaded.

Examples:

- Remove inactive customers
- Exclude cancelled orders
- Remove test data

Benefits:

- Cleaner reports
- Improved performance
- More reliable analysis

---

### Sorting Data

Rows can be sorted to assist with data inspection.

Examples:

- Highest sales first
- Newest dates first
- Alphabetical order

Sorting allows users to quickly identify anomalies or trends during preparation.

---

## Working with Data Types

Selecting the correct data type is essential for accurate reporting.

### Common Data Types

#### Text

Used for:

- Names
- Categories
- Email addresses
- Locations

Examples:

- Melbourne
- Electronics
- Customer Name

---

#### Whole Number

Used for:

- Quantities
- Counts
- Identifiers

Examples:

- 5
- 120
- 1000

---

#### Decimal Number

Used for:

- Revenue
- Profit
- Prices

Examples:

- 10.50
- 125.75
- 999.99

---

#### Date

Used for:

- Transactions
- Customer registration dates
- Appointment dates

Examples:

- 01/01/2026
- 15/05/2026

---

#### Date/Time

Used when both date and time are required.

Examples:

- 01/01/2026 10:30 AM
- 15/05/2026 4:45 PM

---

## Refreshing Data

One of Power BI's strengths is the ability to refresh imported data.

When data is refreshed:

- New records are imported.
- Existing transformations are reapplied.
- Reports update automatically.
- Visualisations reflect current information.

Benefits include:

- Reduced manual effort
- Consistent reporting
- More up-to-date insights

---

## Best Practices for Data Importing

When preparing data in Power BI:

- Verify data before loading.
- Use meaningful column names.
- Remove unnecessary columns.
- Correct data types early.
- Check for missing values.
- Address duplicate records.
- Apply transformations in Power Query rather than manually editing source data.
- Keep datasets as clean and simple as possible.

---

## Knowledge Check

1. What types of data sources can Power BI connect to?
2. What is the purpose of the Get Data feature?
3. What is the difference between Load and Transform Data?
4. What is Power Query used for?
5. Why are correct data types important?
6. What problems can duplicate records cause?
7. Why should unnecessary columns be removed?
8. What happens when a dataset is refreshed?

---

## Module Summary

In this module, you learned how to:

- Connect to common data sources.
- Import data into Power BI.
- Use Power Query Editor.
- Identify common data quality issues.
- Apply basic transformations.
- Configure appropriate data types.
- Prepare data for reporting and analysis.

In the next module, you will explore data modelling and semantic models, including creating relationships between tables and developing measures for reporting.
