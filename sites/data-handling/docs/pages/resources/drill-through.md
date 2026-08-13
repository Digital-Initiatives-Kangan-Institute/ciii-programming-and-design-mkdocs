# Module 6: Drill Through

## Module Overview

Business users often need to move from high-level summaries to detailed information. A manager may identify an issue in a chart and want to understand the records that contributed to that result.

Drill-through functionality allows users to navigate from summary-level information to a more detailed report page while maintaining context.

In this module, students will learn how drill-through works, how drill-through pages are created, and how users can explore detailed information within a report.

---

## Learning Outcomes

By the end of this module, students will be able to:

- Explain the purpose of drill-through.
- Create drill-through pages.
- Configure drill-through fields.
- Add navigation controls.
- Use drill-through to investigate data.
- Improve report usability through guided exploration.

---

## What is Drill Through?

Drill-through allows users to navigate from one report page to another while passing selected filter values.

This enables detailed investigation of specific items.

### Example

A user selects:

- Technology Category

The drill-through page displays:

- Products within Technology
- Related sales transactions
- Associated customer information

---

## Why Use Drill Through?

Benefits include:

- Supports detailed analysis
- Reduces report clutter
- Improves navigation
- Creates a better user experience
- Helps users investigate anomalies

---

## Summary vs Detail Reporting

### Summary Page

Shows high-level information such as:

- Total sales
- Category performance
- Customer segment analysis

---

### Detail Page

Shows supporting information such as:

- Individual products
- Sales records
- Customer details

---

## How Drill Through Works

When users drill through:

1. A value is selected.
2. A drill-through action is performed.
3. Power BI passes the selected value.
4. The destination page automatically filters to that value.

---

## Drill Through Fields

A drill-through field determines which value Power BI passes to the destination page.

Examples include:

- Product Category
- Product Name
- Customer Segment
- State

---

## Designing Drill Through Pages

Good drill-through pages should:

- Focus on one topic.
- Display detailed information.
- Include context from the selected item.
- Provide navigation options.

---

## Back Buttons

Users should be able to return to the previous page.

Power BI provides built-in back buttons.

Benefits:

- Easy navigation
- Better user experience
- Reduced confusion

---

## Common Drill Through Scenarios

### Product Analysis

Summary page:

- Sales by Category

Detail page:

- Product-level analysis

---

### Customer Analysis

Summary page:

- Sales by Customer Segment

Detail page:

- Customer details

---

### Regional Analysis

Summary page:

- Sales by State

Detail page:

- Suburb-level information

---

## Best Practices

When creating drill-through pages:

- Use meaningful page names.
- Keep detail pages focused.
- Include relevant visuals.
- Add a back button.
- Limit unnecessary complexity.

---

## Final Activity: Product Category Drill Through

### Scenario

Management wants to investigate product categories in greater detail.

Create a drill-through experience using the existing semantic model.

---

## Summary Page

Create a page that includes:

- Sales by Product Category
- Sales Trend
- Product Category Treemap

---

## Detail Page

Create a page designed specifically for drill-through analysis.

Include:

- Product Name
- Product Category
- Product Tier
- Quantity Sold
- Discount Information

---

## Configure Drill Through

Use:

- Product Category

as the drill-through field.

---

## Testing

1. Select a product category.
2. Perform a drill-through action.
3. Confirm the detail page displays only information relating to the selected category.
4. Return using the back button.

---

## Analysis Questions

1. Which category contains the most products?
2. Which category appears most active?
3. What additional insights can be discovered from the detail page?
4. Why is drill-through preferable to placing all information on one page?

---

## Knowledge Check

1. What is drill-through?
2. Why is drill-through useful?
3. What is a drill-through field?
4. What happens when a user performs a drill-through action?
5. Why should drill-through pages remain focused?
6. Why should reports contain back buttons?

---

## Module Summary

In this module, you learned how to create drill-through functionality that allows users to investigate detailed information while maintaining context.

You explored:

- Drill-through concepts
- Summary and detail reporting
- Drill-through fields
- Navigation
- Back buttons
- Drill-through page design

In the next module, you will bring together all concepts from the course and create a complete dashboard solution.
