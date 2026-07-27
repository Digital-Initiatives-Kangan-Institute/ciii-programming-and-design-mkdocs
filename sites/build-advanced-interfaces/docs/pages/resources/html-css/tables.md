# Tables

Tables display data in a grid of rows and columns. They are for presenting structured information — not for page layout.

---

## Basic Table Structure

A table is built from a set of nested elements:

```html
<table>
    <tr>
        <th>Item</th>
        <th>Price</th>
    </tr>
    <tr>
        <td>Espresso</td>
        <td>$3.50</td>
    </tr>
    <tr>
        <td>Cappuccino</td>
        <td>$4.50</td>
    </tr>
</table>
```

| Element | Purpose |
|---|---|
| `<table>` | Wraps the entire table |
| `<tr>` | Table row — contains cells |
| `<th>` | Table heading cell — bold and centred by default |
| `<td>` | Table data cell — normal text |

---

## Table Sections

Larger tables benefit from being divided into head, body, and foot sections:

```html
<table>
    <thead>
        <tr>
            <th>Product</th>
            <th>Qty</th>
            <th>Price</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Espresso</td>
            <td>2</td>
            <td>$7.00</td>
        </tr>
        <tr>
            <td>Croissant</td>
            <td>1</td>
            <td>$5.50</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2">Total</td>
            <td>$12.50</td>
        </tr>
    </tfoot>
</table>
```

| Element | Purpose |
|---|---|
| `<thead>` | Groups the heading rows |
| `<tbody>` | Groups the data rows |
| `<tfoot>` | Groups the footer/summary rows |

These sections help with styling and make the table more accessible. Browsers can repeat `<thead>` and `<tfoot>` when printing across pages.

---

## Spanning Columns and Rows

Cells can span multiple columns or rows using the `colspan` and `rowspan` attributes:

```html
<table>
    <tr>
        <th>Name</th>
        <th colspan="2">Contact</th>
    </tr>
    <tr>
        <td>Alice</td>
        <td>alice@example.com</td>
        <td>0412 345 678</td>
    </tr>
    <tr>
        <td rowspan="2">Cafe</td>
        <td>hello@cafe.com</td>
        <td>0399990000</td>
    </tr>
    <tr>
        <td>info@cafe.com</td>
        <td>0399990001</td>
    </tr>
</table>
```

- `colspan` merges cells horizontally across columns
- `rowspan` merges cells vertically across rows

---

## Adding a Caption

The `<caption>` element provides a title or description for the table:

```html
<table>
    <caption>Monthly Sales — June 2026</caption>
    <tr>
        <th>Week</th>
        <th>Revenue</th>
    </tr>
    <tr>
        <td>Week 1</td>
        <td>$4,200</td>
    </tr>
</table>
```

`<caption>` must be the first element inside `<table>`. It helps users understand what the table represents at a glance.

---

## Borders and Styling

By default, tables have no visible borders. Use CSS to add them:

```css
table {
    border-collapse: collapse;
    width: 100%;
}

th, td {
    border: 1px solid #ccc;
    padding: 8px;
    text-align: left;
}

th {
    background-color: #f5f5f5;
}
```

`border-collapse: collapse` merges adjacent borders into a single line, creating a cleaner look.

---

## When to Use Tables

Tables are for **tabular data** — information that naturally fits into rows and columns:

| Good Use | Bad Use |
|---|---|
| Schedules and timetables | Page layout |
| Price lists and menus | Creating columns for text |
| Comparison charts | Positioning images and text side by side |
| Financial data | Building a navigation bar |

For page layout, use CSS Flexbox or Grid instead.

---

## Summary

- `<table>`, `<tr>`, `<th>`, and `<td>` build the core table structure
- `<thead>`, `<tbody>`, and `<tfoot>` organise rows into logical sections
- `colspan` and `rowspan` merge cells across columns or rows
- `<caption>` provides a title for the table
- Style tables with CSS — `border-collapse: collapse` gives clean borders
- Tables are for data, not page layout
