# Assessment Task: Global Economic Insights Database Project

## Scenario

You have been engaged as a Junior Data Analyst for **Global Economic Insights (GEI)**.

GEI has received a CSV file containing information about countries, regions, economic performance, population statistics, exports and industries.

The organisation would like to analyse this information using a relational database hosted in Supabase. Before this can occur, the data must be transformed, modelled and imported into an appropriately designed database.

You have been provided with the following file:

[countries_area_region_gdp_population_exports.csv](../../assets/countries_area_region_gdp_population_exports.csv)

Your task is to analyse the dataset, design and implement an appropriate database solution, and produce a series of SQL and PostgREST reports to support business decision-making.

## Part A: Data Preparation and Transformation and Database Design

Analyse the supplied CSV and identify any data modelling, structural and data quality issues.

- Transform the source data into a set of relational tables suitable for implementation in a PostgreSQL database.
- Design a relational database capable of storing the transformed data.
- Create an Entity Relationship Diagram (ERD) representing your proposed database.

Your transformed solution must support:

- Country information
- Regional classifications
- Annual GDP statistics
- Annual population statistics
- Country exports
- Country industries

Your database design must:

- Identify the required entities
- Identify appropriate attributes for each entity
- Identify primary keys
- Identify foreign keys
- Define relationships between entities
- Show relationship cardinalities
- Use appropriate data types
- Apply appropriate normalisation principles
- Prevent unnecessary duplication
- Support the required reports

Your transformed data must be provided as a collection of CSV files suitable for import into Supabase.

**Artifacts**

- Original CSV file
- Transformed CSV files
- Description of transformations performed
- Data quality findings
- Evidence that the transformed data has been validated


**ERD Checklist**

- Completed ERD
- Entity and attribute definitions
- Primary keys
- Foreign keys
- Data types
- Relationship cardinalities
- Description of database design decisions
- Explanation of the normalisation approach

## Part B: Supabase Database Implementation

Implement your database design in Supabase.

Your Supabase database must include:

- All required tables
- Primary keys
- Foreign keys
- Appropriate PostgreSQL data types
- Required fields
- Unique constraints where appropriate
- Relationships that match the ERD

Import all transformed data into the appropriate database tables.

After importing the data, validate that:

- All expected records have been imported
- Primary key values are unique
- Foreign key values reference valid records
- Numeric values have been imported using appropriate data types
- Annual statistics are associated with the correct country and year
- Exports are associated with the correct countries
- Industries are associated with the correct countries
- Duplicate relationship records have not been created


## Part C: SQL Reporting

Create SQL queries that satisfy the following business reporting requirements.

Your reports must demonstrate the use of:

- Single-table queries
- Selected columns
- Sorting
- Limiting results
- `WHERE` conditions
- Pattern matching
- Multiple conditions
- Two-table joins
- Multi-table joins
- Aggregate functions
- `GROUP BY`
- `HAVING`
- Calculated values

For each report, submit:

- Report number and title
- SQL query
- Screenshot or copy of the query results
- Number of records returned
- Brief explanation of the result

## Single-Table Reports

**Report 1: Country Directory**

Produce a directory containing:

- Country name
- ISO code
- Surface area

Sort the results alphabetically by country name.

**Report 2: Largest Countries**

Display the five countries with the largest surface area.

Include:

- Country name
- ISO code
- Surface area

Sort from the largest surface area to the smallest.

**Report 3: Region Directory**

Produce an alphabetical list of all regions stored in the database.

**Report 4: Annual Statistics**

Display all annual statistics.

Include:

- Country identifier
- Year
- GDP
- Population

Sort the records by country identifier and then by year.

## WHERE Reports

**Report 5: Countries Larger Than One Million Square Kilometres**

Display countries with a surface area greater than 1,000,000 square kilometres.

Include:

- Country name
- Surface area

Sort from largest to smallest.

**Report 6: Countries Containing "United"**

Display countries whose name contains the word:

`United`

Include:

- Country name
- ISO code

**Report 7: GDP Records Above USD $2 Trillion**

Display all annual GDP records where GDP exceeds USD $2 trillion.

The GDP values in the supplied dataset are measured in billions of US dollars.

Include:

- Country identifier
- Year
- GDP

Sort from the highest GDP to the lowest.

**Report 8: Population Range**

Display annual statistics records where the population is between 50 million and 100 million.

Include:

- Country identifier
- Year
- Population

**Report 9: Selected Years**

Display GDP and population statistics for 2020 and 2023 only.

Include:

- Country identifier
- Year
- GDP
- Population

## Join Reports

**Report 10: Countries by Region**

Display:

- Country name
- ISO code
- Region name

Sort by region and then by country.

**Report 11: East Asia and Pacific Countries**

Display all countries located within the East Asia and Pacific region.

Include:

- Country name
- ISO code
- Surface area
- Region name

**Report 12: Country GDP by Year**

Display:

- Country name
- Year
- GDP

Sort by country and then by year.

**Report 13: 2023 Population Report**

Display:

- Country name
- Region name
- Population

Use population data for 2023 only.

**Report 14: Country Export Directory**

Display one record for every country and export combination.

Include:

- Country name
- Export name

Sort by country name and then by export name.

**Report 15: Countries Exporting Cars**

Display all countries that have `Cars` recorded as a major export.

Include:

- Country name
- ISO code
- Export name

The query must use the normalised export data rather than searching the original semicolon-separated CSV field.

**Report 16: Country Industry Directory**

Display one record for every country and industry combination.

Include:

- Country name
- Industry name

Sort by country name and then by industry name.

**Report 17: Countries with a Technology Industry**

Display countries associated with the `Technology` industry.

Include:

- Country name
- Region name
- Industry name

## Aggregate Reports

**Report 18: Number of Countries**

Display the total number of countries stored in the database.

**Report 19: Surface Area Summary**

Produce a single summary containing:

- Smallest country surface area
- Largest country surface area
- Average country surface area

**Report 20: Countries per Region**

Display:

- Region name
- Number of countries

Sort from the region with the highest number of countries to the region with the lowest.

**Report 21: Average GDP by Year**

Display:

- Year
- Average GDP

Round the average GDP to two decimal places.

**Report 22: Total Population by Year**

Display:

- Year
- Total population

Sort the results by year.

**Report 23: Highest GDP by Year**

For each year, display:

- Year
- Highest GDP value

Sort the results by year.

**Report 24: Regional GDP Summary for 2023**

For each region, display:

- Region name
- Total GDP
- Average GDP
- Number of countries

Use GDP data for 2023 only.

**Report 25: Regions with Multiple Countries**

Display regions that contain at least two countries.

Include:

- Region name
- Number of countries

The query must use an aggregate filter.

**Report 26: Number of Exports per Country**

Display:

- Country name
- Number of associated exports

Sort from the highest number of exports to the lowest.

**Report 27: Common Exports**

Display exports that are associated with more than one country.

Include:

- Export name
- Number of associated countries

**Report 28: Population Growth**

Calculate the population growth between 2020 and 2023 for each country.

Display:

- Country name
- Population in 2020
- Population in 2023
- Population increase

Sort from the highest population increase to the lowest.

**Report 29: GDP per Person**

Calculate the approximate GDP per person for each country using 2023 data.

Remember that GDP is stored in billions of US dollars, while population is stored as a whole number.

Display:

- Country name
- 2023 GDP
- 2023 population
- Calculated GDP per person

Sort from the highest GDP per person to the lowest.

**Report 30: Percentage GDP Growth**

Calculate the percentage change in GDP between 2020 and 2023 for each country.

Use the following calculation:

`((GDP in 2023 - GDP in 2020) / GDP in 2020) × 100`

Display:

- Country name
- GDP in 2020
- GDP in 2023
- Percentage change

Round the percentage change to two decimal places.

## Part D: Supabase PostgREST Data Retrieval

Use the Supabase-generated PostgREST API to create read-only requests that retrieve information from your database.

Only `GET` requests are required for this assessment.

Do not use PostgREST aggregate functions for this activity.

Do not use:

- `POST`
- `PUT`
- `PATCH`
- `DELETE`

Do not include a real API key in your submitted evidence. API keys shown in screenshots or copied request headers must be hidden or replaced with a placeholder.

For each PostgREST task, provide:

- Task number and title
- HTTP method
- Request URL
- Request headers with secret values hidden
- HTTP response status
- Screenshot or copy of the returned JSON
- Number of records returned
- Brief explanation of the request

**PostgREST Task 1: Retrieve All Countries**

Retrieve all country records and all available country columns.

**PostgREST Task 2: Retrieve Selected Country Columns**

Retrieve only:

- Country name
- ISO code

**PostgREST Task 3: Sort Countries by Surface Area**

Retrieve:

- Country name
- Surface area

Sort the countries from the largest surface area to the smallest.

**PostgREST Task 4: Retrieve the Five Largest Countries**

Retrieve the five countries with the largest surface area.

Include:

- Country name
- ISO code
- Surface area

**PostgREST Task 5: Filter Countries by Surface Area**

Retrieve countries with a surface area greater than 1,000,000 square kilometres.

Include:

- Country name
- Surface area

**PostgREST Task 6: Filter by ISO Code**

Retrieve the country with the following ISO code:

`AUS`

**PostgREST Task 7: Search Country Names**

Retrieve countries whose name contains:

`United`

The search must not be case-sensitive.

**PostgREST Task 8: Retrieve Statistics for 2023**

Retrieve all annual statistics for 2023.

Include:

- Country identifier
- Year
- GDP
- Population

**PostgREST Task 9: Filter Statistics by Year and GDP**

Retrieve annual statistics that meet both of the following conditions:

- Year is 2023
- GDP is greater than USD $2 trillion

Include:

- Country identifier
- Year
- GDP
- Population

**PostgREST Task 10: Retrieve Countries with Regions**

Retrieve:

- Country name
- ISO code
- Related region name

Return the related region information as nested JSON.

**PostgREST Task 11: Retrieve Countries with Annual Statistics**

Retrieve:

- Country name
- Related annual statistics

For each statistics record, include:

- Year
- GDP
- Population

Return the annual statistics as nested JSON.

**PostgREST Task 12: Retrieve Countries with 2023 Statistics**

Retrieve:

- Country name
- Related statistics for 2023

For each related record, include:

- Year
- GDP
- Population

Only statistics for 2023 should appear in the nested result.

**PostgREST Task 13: Retrieve Countries with Exports**

Retrieve:

- Country name
- Related export names

Return the export information as nested JSON.

The request must use the relationships created in the Supabase database.

**PostgREST Task 14: Retrieve Countries Exporting Cars**

Retrieve countries associated with the `Cars` export.

Include:

- Country name
- ISO code
- Export name

The request must use the normalised database relationships rather than searching the original semicolon-separated field.

**PostgREST Task 15: Retrieve Countries with Industries**

Retrieve:

- Country name
- Related industry names

Return the industry information as nested JSON.

**PostgREST Task 16: Regional Country Directory**

Retrieve:

- Region name
- Countries associated with each region
- Country ISO codes
- Country surface areas

Return countries as nested JSON within each region.

Sort the regions alphabetically.

