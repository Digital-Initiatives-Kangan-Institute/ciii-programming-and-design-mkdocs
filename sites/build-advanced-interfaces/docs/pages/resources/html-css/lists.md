# Lists

Lists organise related items together. HTML provides three types of lists: unordered, ordered, and description lists.

---

## Unordered Lists

Unordered lists display items with bullet points. The order of items does not matter:

```html
<ul>
    <li>Espresso</li>
    <li>Cappuccino</li>
    <li>Latte</li>
    <li>Flat White</li>
</ul>
```

- `<ul>` creates the unordered list container
- `<li>` defines each list item

Common uses: navigation menus, ingredient lists, feature lists, tags.

---

## Ordered Lists

Ordered lists display items with numbers or letters. Use them when the sequence matters:

```html
<ol>
    <li>Preheat the oven to 180C</li>
    <li>Mix the flour and sugar</li>
    <li>Add the eggs and stir</li>
    <li>Bake for 25 minutes</li>
</ol>
```

### Changing the Numbering Style

Use the `type` attribute to change the marker:

```html
<ol type="A">
    <li>Option A</li>
    <li>Option B</li>
    <li>Option C</li>
</ol>
```

| Type | Marker |
|---|---|
| `type="1"` | Numbers (default): 1, 2, 3 |
| `type="A"` | Uppercase letters: A, B, C |
| `type="a"` | Lowercase letters: a, b, c |
| `type="I"` | Uppercase Roman numerals: I, II, III |
| `type="i"` | Lowercase Roman numerals: i, ii, iii |

### Starting at a Specific Number

```html
<ol start="5">
    <li>Step five</li>
    <li>Step six</li>
</ol>
```

The `start` attribute sets the starting number (always a number, even for letter types — `start="3"` with `type="A"` begins at C).

---

## Nested Lists

Lists can be nested inside other lists to create hierarchies:

```html
<ul>
    <li>Hot Drinks
        <ul>
            <li>Coffee</li>
            <li>Tea</li>
            <li>Hot Chocolate</li>
        </ul>
    </li>
    <li>Cold Drinks
        <ul>
            <li>Iced Coffee</li>
            <li>Lemonade</li>
            <li>Smoothies</li>
        </ul>
    </li>
</ul>
```

Nested lists are commonly used for multi-level navigation menus and category groupings.

---

## Description Lists

Description lists pair terms with their definitions or descriptions:

```html
<dl>
    <dt>Espresso</dt>
    <dd>A concentrated coffee brewed by forcing hot water through fine grounds.</dd>

    <dt>Cappuccino</dt>
    <dd>Espresso with steamed milk foam, equal parts espresso, milk, and foam.</dd>

    <dt>Flat White</dt>
    <dd>Espresso with velvety steamed milk and a thin layer of microfoam.</dd>
</dl>
```

- `<dl>` creates the description list container
- `<dt>` defines the term
- `<dd>` provides the description or definition

---

## Using Lists for Navigation

Lists are the standard way to build navigation menus:

```html
<nav>
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/menu">Menu</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

CSS removes the bullets and arranges the items horizontally to create a navigation bar.

---

## Summary

- `<ul>` creates unordered (bulleted) lists; `<ol>` creates ordered (numbered) lists
- `<li>` defines a list item in both types
- Use `type` and `start` attributes to customise ordered list numbering
- Nest lists for subcategories or multi-level menus
- `<dl>`, `<dt>`, and `<dd>` create term-definition pairs
- Lists wrapped in `<nav>` form the standard structure for site navigation
