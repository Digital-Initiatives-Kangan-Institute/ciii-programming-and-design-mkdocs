# Writing Effective Prompts

The quality of an AI's output depends heavily on the quality of your prompt. A vague prompt produces vague results. A well-structured prompt gets you closer to what you need on the first try.

---

## What Makes a Good Prompt?

A good prompt is:

- **Specific** — describe exactly what you want, not generally what you need
- **Contextual** — include relevant details about your project, language, or framework
- **Structured** — break complex requests into clear requirements
- **Actionable** — the AI should understand what output you expect

---

## Prompt Structure

A well-formed prompt for a coding task often follows this pattern:

```
1. Role or context — what kind of code is this, what project
2. Task — what do you want the AI to do
3. Requirements — specific details, constraints, or preferences
4. Format — how should the response be structured
```

### Examples

**Poor prompt:**
```
Write some CSS for a navbar.
```

**Good prompt:**
```
I am building a cafe website with HTML and CSS. Write CSS for a navigation bar that sits at the top of the page. It should have a dark background, white links, and the links should be spaced evenly. Use flexbox. Include hover effects.
```

**Poor prompt:**
```
My code is broken, fix it.
```

**Good prompt:**
```
I am getting this error in my Next.js app: "useState is not defined". Here is my component code. What is causing this error and how do I fix it?

[paste code here]
```

---

## Providing Context

Context helps the AI understand your situation and avoid assumptions.

| Instead of... | Try... |
|---|---|
| "Write a function" | "Write a JavaScript function that... I am using vanilla JS, no frameworks" |
| "Style this" | "Style this HTML form using CSS. The design should be clean and minimal. The project already uses a white background and a sans-serif font." |
| "Fix the bug" | "This code is supposed to filter a list of products by category, but it returns an empty array every time. Here is the code:" |

---

## Iterative Prompting

Rarely does the first response give you exactly what you want. Treat prompting as a conversation:

1. **Start with a clear ask**
2. **Review the response** — what is right and what needs changing
3. **Refine** — "That is close, but can you change the layout to use grid instead of flexbox?"
4. **Narrow down** — "Remove the animation and make the button wider"
5. **Verify** — test the final output

Each follow-up is an opportunity to steer the AI closer to your goal.

---

## Keeping Token Use Low

Tokens are the units AI models use to process text — roughly, a token is a piece of a word. Long prompts and long conversations use more tokens, which can:

- Slow down responses
- Hit context limits (the AI forgets earlier parts of a long conversation)
- Cost more on paid tiers

To keep prompts efficient:

- **Be concise** — remove filler words and redundant explanations
- **Send only what is relevant** — paste the specific function or file, not the entire project
- **Start new conversations** for unrelated tasks to reset the context window
- **Use bullet points** instead of paragraphs when listing requirements

---

## Common Prompt Patterns

### Explain This

```
Explain what this code does in simple terms:
[paste code]
```

### Generate From Scratch

```
Create a [language] [thing] that [requirements].
Use [framework/library] if applicable.
Include [specific features].
```

### Debug

```
I am getting this error: [error message]
Here is the relevant code:
[paste code]
What is causing this and how do I fix it?
```

### Refactor

```
Rewrite this function to [improvement, e.g. "use arrow function syntax", "be more readable", "handle errors"]:
[paste code]
```

---

## Summary

- A good prompt is specific, contextual, structured, and actionable
- Follow the pattern: context, task, requirements, format
- Provide relevant code and describe your environment
- Iterate — refine your prompt based on the response
- Keep prompts concise to reduce token use and stay within context limits
