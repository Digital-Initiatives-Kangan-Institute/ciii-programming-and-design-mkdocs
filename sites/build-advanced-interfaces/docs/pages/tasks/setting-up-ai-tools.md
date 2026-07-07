# Setting Up AI Tools

Configure your development environment with AI-assisted coding tools.

---

## Task 1: Install and Run Ollama

!!! abstract "Instructions"
    Install Ollama on your machine, then pull and run a model. Test it by asking a programming question.

??? hint "Hint - Click to expand"
    ```bash
    # Install Ollama
    curl -fsSL https://ollama.com/install.sh | sh

    # Pull a model (llama3 or mistral are good choices)
    ollama pull llama3

    # Run the model
    ollama run llama3
    ```

    Once running, ask: *"Explain what a REST API is in one paragraph."*

---

## Task 2: GitHub Copilot Setup

!!! abstract "Instructions"
    Set up GitHub Copilot in VS Code:
    
    1. Install the GitHub Copilot extension in VS Code
    2. Sign in with your GitHub account
    3. Test inline completions by opening a `.js` or `.py` file and typing a comment like `// function that calculates the fibonacci sequence`
    4. Use Copilot Chat (`Ctrl+Shift+I`) to ask: *"How do I reverse a string in JavaScript?"*

---

## Task 3: VS Code Extensions

!!! abstract "Instructions"
    Install and configure the following VS Code extensions:

    - **Live Preview** — Preview HTML pages in real time
    - **Prettier** — Automatic code formatting
    - **ESLint** — JavaScript linting

    After installing, configure Prettier to format on save:

    1. Open VS Code settings (`Ctrl+,`)
    2. Search for "format on save"
    3. Enable the option

    Test by creating a messy HTML file and saving it — it should auto-format.

---

## Task 4: CLI Navigation

!!! abstract "Instructions"
    Open a terminal and complete the following tasks using only the command line:

    1. Navigate to your Documents folder
    2. Create a new folder called `dev-projects`
    3. Inside it, create a file called `notes.txt`
    4. List the contents of the folder to confirm
    5. Delete `notes.txt` and then the `dev-projects` folder

??? hint "Hint - Click to expand"
    ```bash
    cd ~/Documents
    mkdir dev-projects
    cd dev-projects
    touch notes.txt
    ls
    rm notes.txt
    cd ..
    rmdir dev-projects
    ```

---

## Task 5: Project Planning with AI

!!! abstract "Instructions"
    Plan a small web application before writing any code. The application should be a "Book Library" where users can:

    - View a list of books
    - Search for a book by title
    - Add a new book

    Write out your plan covering:

    1. What pages or views are needed?
    2. What data does each book need (title, author, etc.)?
    3. What components will you build?
    4. What API endpoints will you need (if using a backend)?
    5. What is the user flow?

    Use an AI tool (Copilot Chat or Ollama) to review your plan and get suggestions.

??? hint "Hint - Example Plan Structure"
    ```
    BOOK LIBRARY APP - PLAN

    1. Pages:
       - Home page (list of books + search bar)
       - Add Book page (form to add a new book)

    2. Book Data:
       - id, title, author, year, genre, coverImage

    3. Components:
       - BookCard (displays one book)
       - BookList (renders all BookCards)
       - SearchBar (text input with filter logic)
       - AddBookForm (form with validation)

    4. API Endpoints:
       - GET /api/books (list all books)
       - GET /api/books?search=query (search)
       - POST /api/books (add a new book)

    5. User Flow:
       - User lands on home → sees book list
       - Types in search → list filters in real time
       - Clicks "Add Book" → navigates to form
       - Fills form and submits → redirected to home with new book
    ```
