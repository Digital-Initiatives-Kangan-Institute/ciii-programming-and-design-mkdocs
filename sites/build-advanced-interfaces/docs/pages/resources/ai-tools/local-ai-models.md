# Local AI Models

Running AI models locally on your own machine gives you privacy, offline access, and no usage limits. Two popular tools for this are Ollama and LM Studio.

---

## Why Run Models Locally?

| Benefit | Description |
|---|---|
| Privacy | Your code and prompts never leave your machine |
| Offline | No internet connection required after download |
| No limits | No rate limits, no subscription fees |
| Speed | Low latency — no network round-trip |
| Experimentation | Try different models freely |

---

## Ollama

Ollama is a command-line tool for running large language models (LLMs) locally. It handles downloading, running, and managing models with simple commands.

### Installation

```bash
# Linux / macOS
curl -fsSL https://ollama.com/install.sh | sh

# Verify installation
ollama --version
```

### Pulling and Running Models

```bash
# Download a model
ollama pull llama3

# Run it interactively
ollama run llama3
```

Once running, you can chat with the model directly in the terminal. Type `/bye` to exit.

### Available Models

Ollama supports many models:

| Model | Strengths |
|---|---|
| `llama3` | General purpose, strong reasoning |
| `codellama` | Code generation and explanation |
| `mistral` | Fast, efficient for smaller machines |
| `phi3` | Lightweight, good for constrained hardware |

### API Access

Ollama exposes a local API at `http://localhost:11434`. You can use it from any application:

```bash
# Generate a response via the API
curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Explain what a REST API is in one sentence."
}'
```

This means you can integrate local AI into your own tools and scripts.

---

## LM Studio

LM Studio provides a graphical interface for discovering, downloading, and running local LLMs. It is ideal if you prefer a visual tool over the command line.

### Key Features

- **Model Browser** — Discover and download models from Hugging Face directly within the app
- **Chat Interface** — Built-in chat with conversation history
- **Local Server** — Exposes a local API compatible with OpenAI client libraries (drop-in replacement for `https://api.openai.com`)
- **Hardware Monitoring** — Shows GPU/CPU usage and memory consumption

### Getting Started

1. Download LM Studio from [lmstudio.ai](https://lmstudio.ai)
2. Use the search bar to find a model (e.g., "Llama 3")
3. Download the model
4. Start a new chat or enable the local server

### Using the Local Server

```javascript
// Your app can use the local LM Studio server as if it were OpenAI:
const response = await fetch("http://localhost:1234/v1/chat/completions", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
        model: "local-model",
        messages: [{ role: "user", content: "Hello!" }]
    })
});
```

---

## Choosing Between Ollama and LM Studio

| Feature | Ollama | LM Studio |
|---|---|---|
| Interface | Command line | Graphical (GUI) |
| Resource usage | Lightweight | Heavier (GUI overhead) |
| Automation | Excellent (CLI + API) | Limited to local server |
| Model discovery | Manual (`ollama pull`) | Built-in browser |
| Best for | Developers comfortable with terminal | Users who prefer visual tools |

Both are free and can run simultaneously.

---

## Summary

- Local AI models give you **privacy**, **offline access**, and **no usage limits**
- **Ollama** is a lightweight CLI tool — ideal for developers
- **LM Studio** provides a graphical interface with a built-in model browser
- Both expose **local APIs** you can call from your applications
