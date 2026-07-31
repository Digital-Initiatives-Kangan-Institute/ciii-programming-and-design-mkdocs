# Optimizing AI Token Usage

Every interaction with an AI tool consumes tokens — the basic units of text that models process. Understanding how tokens work and how to manage them efficiently will help you get better results, stay within limits, and avoid unnecessary costs.

---

## What Are Tokens?

A token is a chunk of text that an AI model reads and generates. Tokens do not map directly to words or characters. As a rough guide:

- **1 token ≈ ¾ of a word** in English
- **1 token ≈ 4 characters** (including spaces and punctuation)
- **Code is more token-dense** than natural language — symbols, operators, and syntax characters each count as individual tokens

For example, the sentence *"Write a function that sorts an array"* uses about 8 tokens. The equivalent code `const sort = arr => arr.sort()` uses about 14 tokens because of the punctuation and syntax.

| Text | Approximate Tokens |
|---|---|
| `"Hello, how are you?"` | ~6 |
| `for (let i = 0; i < items.length; i++)` | ~15 |
| `font-family: 'Segoe UI', sans-serif;` | ~12 |
| 1000 words of English prose | ~1300 |

---

## Why Token Efficiency Matters

### Context Limits

Every AI model has a context window — the maximum number of tokens it can consider at once. This includes your prompt, the conversation history, and the model's response. When you exceed the context limit:

- **Older messages get dropped** — the AI *forgets* instructions or code shared earlier
- **Responses become incomplete** — the model may cut off mid-explanation
- **Quality degrades** — the model loses track of what you asked

| Model | Approximate Context Limit |
|---|---|
| ChatGPT (GPT-4o) | 128,000 tokens |
| Claude (Sonnet) | 200,000 tokens |
| Copilot (GPT-4o in VS Code) | Varies by plan |
| OpenCode | Depends on the underlying model |

### Response Speed

More tokens mean more processing time. A concise prompt with 200 tokens generates a response faster than a verbose prompt with 2000 tokens.

### Cost

Many AI services charge based on token usage:
- **Input tokens** (your prompt + conversation history)
- **Output tokens** (the AI's response)

Even on free tiers, staying within usage limits means you can get more done without hitting rate limits.

---

## Strategies for Reducing Token Usage

### Write Concise Prompts

Be direct. Remove filler words and redundant explanations.

| Instead of... | Try... |
|---|---|
| "I was wondering if you could possibly help me write some HTML code that would create a simple webpage with a heading..." | "Write an HTML page with an H1 heading that says 'Welcome'" |
| "So I have this issue where my JavaScript code isn't working and I've been trying to figure it out for a while..." | "This JavaScript function is returning undefined. How do I fix it?" |

### Send Only Relevant Code

Do not paste an entire file when only one function or section is relevant. Instead:

- Paste only the function, component, or block you need help with
- Use line number references when your AI tool can read files directly (e.g., "See `styles.css` lines 42-65")
- Reference specific files by name rather than pasting their contents

```
# Inefficient — pasting the whole file
Here is my entire styles.css (300 lines). I need help with the .navbar section:

[paste all 300 lines]

# Efficient — paste only what matters
I need help with this CSS for .navbar. I am using flexbox and the links are not spacing evenly:

.navbar {
  display: flex;
  justify-content: space-between;
  background-color: #333;
}
```

### Start New Conversations for Unrelated Tasks

Every message in a conversation includes all previous messages as context — even if they are no longer relevant. This is called *context accumulation*.

When you switch to a completely different topic:

1. Start a new conversation or chat
2. Provide fresh context for the new task
3. Keep each conversation focused on a single feature, bug, or topic

!!! note
    Some AI tools let you edit or delete earlier messages in a conversation. Removing dead ends and failed approaches can reclaim tokens when you want to stay in the same chat.

### Use Agent Project Files

Files like `AGENTS.md`, `CLAUDE.md`, or `.cursorrules` give the AI standing instructions without you repeating them in every prompt. Define your conventions once:

- Project overview and tech stack
- Coding conventions (naming, indentation, file structure)
- Rules (never modify certain files, never guess URLs)
- Build and test commands

The AI reads these files automatically at the start of a session, so you do not need to explain your project every time.

### Break Large Tasks into Smaller Steps

A single prompt asking for an entire feature produces a very large response and is hard to verify. Instead:

1. Ask the AI to plan the feature first (use plan mode if available)  
2. Implement one small piece at a time
3. Verify each piece before moving on

This keeps each prompt focused and uses fewer tokens per exchange, while making it easier to spot problems.

### Use Targeted Follow-Ups

After an AI response, do not say "that didn't work, try again" — that resends the entire conversation history for a vague retry. Be specific:

| Instead of... | Try... |
|---|---|
| "That's wrong, fix it" | "The function on line 12 should return a number, but it is returning a string" |
| "Make it better" | "Add error handling for when the API call fails" |
| "I don't like the look" | "Change the button colour to a darker blue and increase the border radius to 8px" |

### Leverage Agent File Access

When using an AI agent (OpenCode, Copilot Agent, Cursor):

- **Let the agent read files itself** instead of pasting code into the chat
- Reference files by relative path: "Update the `handleSubmit` function in `src/form.js`"
- Agents can search the codebase, so you do not need to explain where things are

This dramatically reduces the tokens you spend providing context.

### Clean Up Your Prompts Before Sending

- Remove commented-out code that is not relevant to your question
- Strip debugging `console.log` statements unless they are part of the issue
- Delete unrelated notes or drafts from your prompt

---

## Estimating Token Usage

Most AI tools display token counts for each response. Some show per-conversation totals.

A quick manual estimate:

```
English text:   token count ≈ word count × 1.3
Code (JS/TS):   token count ≈ character count ÷ 3
Code (HTML/CSS): token count ≈ character count ÷ 3.5
```

If you are approaching a context limit, you can reduce usage by:

- Summarising the conversation so far and starting a new chat with the summary
- Pasting only the most recent relevant code
- Asking the AI to summarise what has been done, then feeding that summary into a new conversation

---

## Token Checklist

Before sending a prompt, ask yourself:

- Did I include only the relevant code, not the whole file?
- Is my prompt as concise as it can be while still being clear?
- Am I asking for one thing, or should this be broken into smaller steps?
- Would starting a new conversation save tokens?
- Can the agent read this file itself instead of me pasting it?
- Did I remove commented-out code, debug logs, and unrelated notes?

---

## Summary

- Tokens are the fundamental unit AI models process — roughly ¾ of a word or 4 characters
- Efficient token use avoids context limits, speeds up responses, and reduces costs
- Write concise prompts and send only relevant code
- Start new conversations for unrelated tasks to avoid context accumulation
- Use project files like `AGENTS.md` for standing instructions
- Break large tasks into smaller, focused exchanges
- Let agents read files directly rather than pasting code into prompts
- Clean up prompts before sending — remove unrelated code, logs, and notes
