# Module 5: Slicers and Interactivity

## Module Overview

One of Power BI's greatest strengths is the ability to create interactive reports that allow users to explore data for themselves. Rather than viewing a static report, users can filter information, focus on specific areas of interest, and investigate trends using built-in interactive features.

In this module, students will learn how slicers work, how they interact with report visuals, and how they can be used to create a more engaging and flexible reporting experience.

---

## Learning Outcomes

By the end of this module, students will be able to:

- Explain the purpose of slicers.
- Create slicers using common fields.
- Configure different slicer types.
- Use slicers to filter reports.
- Synchronise slicers across report pages.
- Create reports that support interactive exploration.

---

## What is Interactivity?

Interactivity allows report users to explore data without modifying the underlying dataset.

Instead of creating multiple reports for different users, a single interactive report can answer many business questions.

Users can:

- Filter information.
- Focus on specific categories.
- Explore dates and time periods.
- Investigate trends.
- Compare different segments.

---

## What is a Slicer?

A slicer is a visual filter that allows users to select values directly from a report page.

When a slicer is used, Power BI automatically updates connected visuals.

### Example

A user may select:

- Victoria

from a State slicer.

Power BI will then update all connected visuals to display only records relating to Victoria.

---

## Why Use Slicers?

Slicers make reports easier to use because they allow users to customise what they see.

Benefits include:

- Faster analysis
- Better user experience
- Increased flexibility
- Reduced need for multiple reports
- Improved decision-making

---

## How Slicers Work

A slicer uses a field from a table within the semantic model.

Examples include:

- State
- Suburb
- Customer Segment
- Product Category
- Order Date

When values are selected, Power BI filters the data behind the report visuals.

---

## Common Slicer Types

### List Slicer

Displays all available values as a selectable list.

Examples:

- State
- Customer Segment
- Product Category

Benefits:

- Easy to understand
- Good for small numbers of categories

---

### Dropdown Slicer

Displays values inside a dropdown menu.

Benefits:

- Uses less screen space
- Suitable for reports with many values

Examples:

- Product Names
- Customer Names
- Suburbs

---

### Date Slicer

Allows users to select dates and date ranges.

Examples:

- Sales Date
- Order Date
- Transaction Date

Benefits:

- Supports trend analysis
- Allows reporting for selected periods

---

### Relative Date Slicer

Filters data relative to today's date.

Examples:

- Last 30 days
- Last 90 days
- This month
- This year

Benefits:

- Automatically updates over time
- Useful for operational reporting

---

## Single Select vs Multi Select

### Single Select

Allows users to choose only one value.

Example:

- Select one state

Benefits:

- Simpler analysis
- Prevents conflicting selections

---

### Multi Select

Allows users to choose multiple values.

Example:

- Select Victoria and New South Wales

Benefits:

- Greater flexibility
- Broader analysis

---

## Cross-Filtering

When a slicer is used, multiple visuals can update simultaneously.

### Example

A Product Category slicer may affect:

- Bar charts
- Line charts
- Treemaps
- Tables

This creates a connected reporting experience.

---

## Interactions Between Visuals

Power BI visuals can interact with one another.

### Example

Selecting a category in a bar chart may:

- Filter a table
- Highlight related data in a treemap
- Update summary metrics

These interactions allow users to explore data naturally.

---

## Synchronising Slicers

Reports often contain multiple pages.

A slicer can be synchronised so that the selected value applies across several pages.

### Example

A State slicer can be applied across:

- Overview page
- Sales page
- Customer page
- Product page

Benefits:

- Consistent filtering
- Better user experience
- Reduced duplication

---

## Effective Slicer Design

Good slicer design helps users understand and navigate reports.

Recommended practices:

- Place slicers consistently.
- Use meaningful labels.
- Avoid excessive numbers of slicers.
- Group related slicers together.
- Use dropdown slicers where space is limited.

---

## Common Slicer Fields

For the retail dataset, useful slicers may include:

- State
- Customer Segment
- Product Category
- Product Tier
- Order Date

These allow users to explore different aspects of the business.

---

## Final Activity: Interactive Retail Report

### Scenario

You have already created visualisations using the Customers, Products, and Sales tables.

Your task is to improve the report by adding interactive filtering.

---

## Requirements

Create the following slicers:

### Slicer 1

State

---

### Slicer 2

Customer Segment

---

### Slicer 3

Product Category

---

### Slicer 4

Order Date

---

## Testing

After creating the slicers:

- Select different states.
- Filter by customer segment.
- Filter by product category.
- Select different date ranges.

Observe how each report visual changes.

---

## Analysis Questions

1. Which slicer produces the largest change in the report?
2. Which categories generate the highest activity?
3. Which customer segment appears most active?
4. How does changing the date range affect trends?
5. Why are slicers useful for business users?

---

## Knowledge Check

1. What is a slicer?
2. Why are slicers useful?
3. What is the difference between a list slicer and a dropdown slicer?
4. What is a date slicer?
5. What is a relative date slicer?
6. What does cross-filtering mean?
7. Why might slicers be synchronised across pages?
8. What are some best practices for slicer design?

---

## Module Summary

In this module, you learned how to create interactive reports using slicers.

You explored:

- List slicers
- Dropdown slicers
- Date slicers
- Relative date slicers
- Cross-filtering
- Visual interactions
- Slicer synchronisation

In the next module, you will build drill-through functionality that allows users to move from summary information to detailed analysis.
