# AI Chatbots

AI chatbots are conversational tools that respond to questions and instructions in natural language. For developers, they act as on-demand assistants that can explain concepts, generate code, and help solve problems.

---

## How Chatbots Work

A chatbot takes your input — a question or instruction — and predicts the most likely helpful response based on its training data. Modern chatbots are built on large language models (LLMs) trained on vast amounts of text, including code repositories, documentation, and technical discussions.

The key interaction pattern with a chatbot is:

1. You write a **prompt**
2. The chatbot generates a **response**
3. You review, ask follow-ups, or refine your prompt

This back-and-forth is a conversation, not a one-off query.

---

## Common Chatbot Tools

### ChatGPT (OpenAI)

The most widely known AI chatbot. The free tier is sufficient for most learning tasks. ChatGPT can:

- Explain programming concepts at any level of detail
- Generate code from natural language descriptions
- Debug errors by analysing code and error messages
- Compare approaches and suggest best practices

Available at [chat.openai.com](https://chat.openai.com).

### Claude (Anthropic)

Claude excels at longer, more detailed responses and has a large context window, meaning it can process more code or conversation history at once. It is strong at:

- Detailed code review and analysis
- Understanding large codebases
- Thoughtful, step-by-step reasoning

Available at [claude.ai](https://claude.ai).

### Copilot Chat (GitHub)

Copilot Chat lives inside VS Code, so you do not need to switch between your editor and a browser. It can:

- Answer questions about the code you have open
- Generate code with context from your project
- Explain selected code blocks
- Suggest fixes for errors

Accessible through the Copilot icon in the VS Code sidebar.

---

## Chatbot vs In-Editor Copilot

GitHub Copilot has two modes worth distinguishing:

| Copilot Chat | Copilot Inline |
|---|---|
| You ask a question in the chat panel | Suggestions appear as you type |
| Conversational, back-and-forth | Autocomplete-style completions |
| Can explain and discuss | Generates code inline |

Inline Copilot is the ghost text that appears as you type — press `Tab` to accept a suggestion. Copilot Chat is the panel where you have a conversation.

---

## When to Use a Chatbot

Chatbots are best for:

- **Learning** — "Explain how `useEffect` works in React"
- **Getting unstuck** — "Why am I getting this error: `undefined is not a function`?"
- **Generating snippets** — "Write a CSS flexbox layout for a navbar with a logo on the left and links on the right"
- **Exploring options** — "What are three ways to fetch data in Next.js?"
- **Code review** — "Is there a better way to structure this function?"

They are less suited for tasks that require reading and modifying files across a project — that is where agents come in.

---

## Best Practices

- **Be specific** — "Write a function that takes an array of numbers and returns the average" is better than "Write some code"
- **Provide context** — paste relevant code, error messages, or describe your project
- **Ask follow-ups** — if the first response is not quite right, refine your question
- **Verify everything** — test the code, check the logic, read the explanation critically

---

## Summary

- Chatbots are conversational AI tools for questions, explanations, and code generation
- ChatGPT, Claude, and Copilot Chat are the most common for developers
- Copilot Chat works inside VS Code with awareness of your open files
- Be specific, provide context, and always verify the output
