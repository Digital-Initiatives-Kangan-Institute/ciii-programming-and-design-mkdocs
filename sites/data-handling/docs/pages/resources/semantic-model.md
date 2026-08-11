# Module 3: Data Models and Semantic Models

## Module Overview

Power BI is most effective when data is organised into a clear and reliable model. A data model defines how tables relate to each other and allows users to analyse information across multiple datasets.

In this module, students will learn what a data model is, how semantic models support reporting, and how relationships are created between tables in Power BI. Students will use customer, product, and sales data to build a basic model that supports business reporting.

---

## Learning Outcomes

By the end of this module, students will be able to:

- Explain the purpose of a data model in Power BI.
- Describe what a semantic model is.
- Identify tables, fields, primary keys, and foreign keys.
- Explain one-to-many relationships.
- Create relationships between tables in Power BI.
- Identify fact tables and dimension tables.
- Build a simple model using customer, product, and sales data.

---

## What is a Data Model?

A data model is a structured way of organising data so that it can be analysed effectively.

In Power BI, a data model usually contains:

- Tables
- Columns
- Relationships
- Keys
- Data types
- Business-friendly field names

A well-designed data model helps users create accurate reports and visualisations.

---

## Why Data Models Matter

When data is imported into Power BI, it may come from multiple files or systems. For example, sales information may be stored separately from customer and product information.

Instead of keeping all information in one large table, Power BI allows related information to be stored in separate tables and connected through relationships.

This approach helps to:

- Reduce repeated data.
- Improve report performance.
- Make reports easier to maintain.
- Support more flexible analysis.
- Create consistent reporting across different pages and visuals.

---

## Example Business Scenario

A retail business may have three separate datasets:

- A customer list
- A product list
- A sales transaction table

Each dataset contains different information.

### Customers Table

The Customers table may contain:

- Customer ID
- First name
- Last name
- Email
- Suburb
- State
- Customer segment

### Products Table

The Products table may contain:

- Product ID
- Product name
- Category
- Unit price
- Product tier

### Sales Table

The Sales table may contain:

- Sale ID
- Order date
- Customer ID
- Product ID
- Quantity
- Discount

The Sales table contains references to the Customers and Products tables using ID fields.

---

## Tables in a Data Model

A table stores related information in rows and columns.

### Rows

Each row represents a single record.

Examples:

- One customer
- One product
- One sale

### Columns

Each column represents a specific field or attribute.

Examples:

- Customer ID
- Product name
- Order date
- Quantity

---

## Fact Tables and Dimension Tables

Power BI models often use fact tables and dimension tables.

---

## Fact Tables

A fact table contains measurable business events or transactions.

Examples:

- Sales transactions
- Orders
- Bookings
- Payments
- Attendance records

Fact tables usually contain:

- Transaction IDs
- Dates
- Quantity values
- Amount values
- Foreign keys that connect to other tables

### Example

The Sales table is a fact table because it records individual sales transactions.

Each row in the Sales table represents one sale.

---

## Dimension Tables

A dimension table contains descriptive information used to filter, group, or explain data.

Examples:

- Customers
- Products
- Stores
- Staff
- Locations
- Dates

Dimension tables usually contain:

- A unique ID
- Descriptive fields
- Categories or grouping fields

### Example

The Customers table is a dimension table because it describes the customers involved in sales.

The Products table is also a dimension table because it describes the products being sold.

---

## Primary Keys

A primary key is a field that uniquely identifies each record in a table.

Each value in a primary key column should be unique.

### Examples

| Table | Primary Key |
|---|---|
| Customers | CustomerID |
| Products | ProductID |
| Sales | SaleID |

### Why Primary Keys Matter

Primary keys help Power BI identify individual records.

They also allow tables to be connected correctly through relationships.

---

## Foreign Keys

A foreign key is a field in one table that refers to the primary key in another table.

Foreign keys are used to create relationships between tables.

### Example

The Sales table contains:

- CustomerID
- ProductID

These fields are foreign keys because they link each sale to a customer and a product.

---

## Relationships

Relationships connect tables together in a data model.

A relationship allows Power BI to understand how records in one table relate to records in another table.

### Example

A customer can have many sales.

This means:

- One record in the Customers table may connect to many records in the Sales table.
- Each sale belongs to one customer.

---

## One-to-Many Relationships

A one-to-many relationship is one of the most common relationship types in Power BI.

It means that one record in a table can relate to many records in another table.

### Example 1: Customers and Sales

One customer can make many purchases.

Relationship:

- Customers[CustomerID] connects to Sales[CustomerID]

This is a one-to-many relationship.

### Example 2: Products and Sales

One product can appear in many sales transactions.

Relationship:

- Products[ProductID] connects to Sales[ProductID]

This is also a one-to-many relationship.

---

## Cardinality

Cardinality describes the type of relationship between tables.

Common relationship types include:

- One-to-many
- Many-to-one
- One-to-one
- Many-to-many

For beginner Power BI modelling, one-to-many relationships are the most important to understand.

---

## Relationship Direction

Relationships in Power BI have a filter direction.

The filter direction controls how filters flow between tables.

In a basic model:

- Dimension tables filter fact tables.
- Customers can filter Sales.
- Products can filter Sales.

### Example

If a report is filtered to show only customers from Victoria, Power BI uses the relationship between Customers and Sales to show only the sales linked to Victorian customers.

---

## Semantic Models

A semantic model is a business-friendly layer that sits on top of the data.

It helps users interact with data using meaningful names and logical relationships.

A semantic model can include:

- Tables
- Relationships
- Field names
- Data types
- Hierarchies
- Business rules
- Measures

In this introductory course, the focus is on tables, relationships, keys, and business-friendly structure.

---

## Why Semantic Models Are Useful

Semantic models make reporting easier because they organise data in a way that users can understand.

Instead of working with raw system data, users can work with meaningful business concepts.

### Example

A source system might use technical field names such as:

- Cust_ID
- Prod_SKU
- Txn_Date

A semantic model can present these as:

- Customer ID
- Product ID
- Order Date

This makes the report easier for business users to understand.

---

## Star Schema

A star schema is a common way to organise data for reporting.

It contains:

- One central fact table
- Multiple surrounding dimension tables

### Example

In this module:

- Sales is the central fact table.
- Customers is a dimension table.
- Products is a dimension table.

The model looks like a star because the Sales table sits in the middle and connects to the surrounding tables.

---

## Benefits of a Star Schema

A star schema helps to:

- Keep data organised.
- Reduce duplication.
- Improve report performance.
- Make relationships easier to understand.
- Support clearer reporting.

---

## Practical Activity: Build a Basic Data Model

### Scenario

You work for a retail business that wants to analyse sales performance.

You have been provided with three Excel files:

- powerbi_customers.xlsx
- powerbi_products.xlsx
- powerbi_sales.xlsx

Your task is to import the data into Power BI and create a simple data model.

---

## Supplied Files

### Customers File

Contains customer details.

Important field:

- CustomerID

### Products File

Contains product details.

Important field:

- ProductID

### Sales File

Contains sales transactions.

Important fields:

- SaleID
- CustomerID
- ProductID
- OrderDate
- Quantity
- Discount

---

## Activity Instructions

### Step 1: Import the Data

Import all three Excel files into Power BI Desktop:

- Customers
- Products
- Sales

Check that each table has loaded correctly.

---

### Step 2: Review the Tables

Review each table and identify:

- The purpose of the table.
- The primary key.
- Any foreign keys.
- Which table is the fact table.
- Which tables are dimension tables.

---

### Step 3: Check Data Types

Check that fields have appropriate data types.

Suggested data types:

| Field | Suggested Data Type |
|---|---|
| CustomerID | Text |
| ProductID | Text |
| SaleID | Text |
| OrderDate | Date |
| Quantity | Whole Number |
| Discount | Percentage |
| UnitPrice | Decimal Number or Currency |

---

### Step 4: Create Relationships

Create the following relationships:

| From Table | Field | To Table | Field | Relationship Type |
|---|---|---|---|---|
| Customers | CustomerID | Sales | CustomerID | One-to-many |
| Products | ProductID | Sales | ProductID | One-to-many |

---

### Step 5: Review the Model View

Open Model View and check that:

- Customers connects to Sales.
- Products connects to Sales.
- Sales is positioned as the central fact table.
- Customers and Products act as dimension tables.
- The relationships use the correct fields.

---

## Questions for Students

1. Which table is the fact table?
2. Which tables are dimension tables?
3. What is the primary key in the Customers table?
4. What is the primary key in the Products table?
5. Which fields in the Sales table are foreign keys?
6. Why is the Sales table connected to both Customers and Products?
7. What does a one-to-many relationship mean?
8. Why is this model similar to a star schema?

---

## Common Modelling Issues

When creating relationships, students should watch for the following issues.

### Incorrect Fields Selected

A relationship should connect matching ID fields.

Correct:

- Customers[CustomerID] to Sales[CustomerID]

Incorrect:

- Customers[FirstName] to Sales[CustomerID]

---

### Duplicate Values in Dimension Tables

Primary key fields in dimension tables should contain unique values.

For example:

- Each CustomerID should appear once in the Customers table.
- Each ProductID should appear once in the Products table.

---

### Missing Matching Values

Foreign key values in the Sales table should match values in the related dimension tables.

For example:

- Every Sales[CustomerID] should exist in Customers[CustomerID].
- Every Sales[ProductID] should exist in Products[ProductID].

---

### Incorrect Data Types

Relationship fields should use compatible data types.

For example:

- Customers[CustomerID] should be Text.
- Sales[CustomerID] should also be Text.

---

## Best Practices for Basic Data Models

When building data models in Power BI:

- Use clear table names.
- Use clear column names.
- Keep fact and dimension tables separate.
- Use unique primary keys in dimension tables.
- Check that relationship fields match.
- Avoid unnecessary columns where possible.
- Use a simple star schema where appropriate.
- Review Model View before building visuals.

---

## Knowledge Check

1. What is a data model?
2. What is a semantic model?
3. What is the difference between a fact table and a dimension table?
4. What is a primary key?
5. What is a foreign key?
6. What is a one-to-many relationship?
7. Why is the Sales table considered a fact table?
8. Why are Customers and Products considered dimension tables?
9. What is the purpose of Model View in Power BI?
10. Why is a star schema useful for reporting?

---

## Module Summary

In this module, you learned how Power BI uses data models to organise and connect data.

You explored:

- Tables
- Fact tables
- Dimension tables
- Primary keys
- Foreign keys
- One-to-many relationships
- Semantic models
- Star schemas

You also created a basic model using Customers, Products, and Sales data.

In the next module, you will use this model to begin creating visualisations in Power BI.
