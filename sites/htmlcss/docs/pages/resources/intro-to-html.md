# Introduction to HTML
This site will guide you through the fundamentals of how websites are built. You’ll learn how to create simple webpages, modify them by editing and adding new elements, and then link them together into a complete website.

## What is HTML?
**H**yper**T**ext **M**arkup **L**anguage (HTML) is the standard language used to create and structure webpages. HTML tells a web browser what each part of a page is, such as headings, paragraphs, images, and links. It uses simple tags to organise content so that it can be displayed correctly on the screen. Without HTML, a webpage would not have any structure or meaning.

## Example
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example Web Page</title>
  </head>
  <body>
    <h1>Welcome!</h1>
    <p>This is a paragraph on my webpage.</p>

    <a href="https://w3.org/">Visit W3C</a>
  </body>
</html>
```

## Elements
HTML is made up of **elements**, which are the building blocks of a webpage. An element consists of an **opening tag**, **content**, and a **closing tag** (1).
{.annotate}

1. Some elements do not require a **closing tag** such as `img`, `link`, `input`, and many others. These are known as **self-closing tags**.

```html
<h1>This is a heading</h1>
```

- `<h1>` - Opening Tag
- `This is a heading` - Content
- `</h1>` - Closing Tag

### Preview
??? example "Click to Preview HTML"
    <div style="font-size: 1.25rem">This is a heading</div>

As you can see above, when **marking up** you must wrap the tags around the content to apply

## Attributes
HTML elements can contain **attributes** that change the way the element interacts with the page.