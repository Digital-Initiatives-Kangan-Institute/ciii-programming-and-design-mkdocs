# Interfaces: GUI and Command Line

Every operating system provides at least one way for users to interact with it. The two main types of interface are the Graphical User Interface (GUI) and the Command Line Interface (CLI). Both serve the same purpose — letting you control the computer — but they work in different ways and are suited to different tasks.

---

## What is a Graphical User Interface?

A GUI uses visual elements — windows, icons, menus, and buttons — that you interact with using a mouse, keyboard, or touch. It is designed to be intuitive and accessible.

### Common GUI Elements

| Element | Purpose | Example |
|---|---|---|
| **Desktop** | The main workspace with a background and shortcuts | Windows desktop with icons |
| **Taskbar / Dock** | Launches and switches between applications | Windows taskbar, macOS Dock |
| **Start Menu / App Launcher** | Central menu for finding and opening programs | Windows Start, GNOME Activities |
| **File Manager** | Browse, copy, move, and delete files graphically | File Explorer, Finder, Nautilus |
| **System Tray** | Shows background apps and status indicators | Wi-Fi, volume, battery, clock |
| **Settings App** | Configure system preferences through menus | Windows Settings, System Preferences |

### Benefits of a GUI

- Easy to learn and use without technical knowledge
- Visual feedback makes it clear what is happening
- Multiple windows allow multitasking with a clear overview
- Drag-and-drop, right-click menus, and keyboard shortcuts make tasks efficient

***

## What is a Command Line Interface?

A CLI is a text-based interface where you type commands and the computer responds with text output. It does not use windows, icons, or a mouse — everything happens through typed instructions.

### Terminal Applications

Every major OS includes a CLI application:

| OS | CLI Application | Shell (Default) |
|---|---|---|
| Windows | Command Prompt, PowerShell, Windows Terminal | cmd.exe, PowerShell |
| macOS | Terminal | zsh |
| Linux | Terminal, Console | bash |

The **shell** is the program that interprets your commands. The terminal is the window that hosts the shell. Different shells have slightly different syntax, but the core concepts are the same.

### When to Use the Command Line

- **Automation** — Write scripts to perform repetitive tasks
- **System administration** — Manage users, services, and configurations
- **Server management** — Most servers have no GUI, only a CLI
- **Batch operations** — Rename, convert, or process many files at once
- **Precision** — Commands are exact; no risk of clicking the wrong button
- **Speed** — Experienced users can work faster with a keyboard than a mouse

***

## Basic CLI Commands

These commands work across Windows (PowerShell/CMD) and Linux/macOS. Where the command differs, both are shown.

### Navigation

| Action | Windows (CMD) | Linux / macOS |
|---|---|---|
| Show current directory | `cd` | `pwd` |
| List files | `dir` | `ls` |
| Change directory | `cd <folder>` | `cd <folder>` |
| Go up one level | `cd ..` | `cd ..` |
| Go to root of drive | `cd \` | `cd /` |

### File Operations

| Action | Windows (CMD) | Linux / macOS |
|---|---|---|
| Create folder | `mkdir <name>` | `mkdir <name>` |
| Create empty file | `type nul > file.txt` | `touch file.txt` |
| Copy file | `copy <src> <dest>` | `cp <src> <dest>` |
| Move/rename file | `move <src> <dest>` | `mv <src> <dest>` |
| Delete file | `del <file>` | `rm <file>` |
| Delete folder | `rmdir <folder>` | `rm -r <folder>` |
| View file contents | `type <file>` | `cat <file>` |

### System Information

| Action | Windows (CMD) | Linux / macOS |
|---|---|---|
| Display hostname | `hostname` | `hostname` |
| Show IP configuration | `ipconfig` | `ip a` or `ifconfig` |
| List running processes | `tasklist` | `ps aux` |
| Show disk usage | `chkdsk` | `df -h` |
| Clear screen | `cls` | `clear` |

### PowerShell vs Command Prompt

Windows offers two CLI environments:

| Feature | Command Prompt (CMD) | PowerShell |
|---|---|---|
| Age | Legacy (1980s) | Modern (2006+) |
| Output | Plain text | Structured objects |
| Scripting | Batch files (.bat) | PowerShell scripts (.ps1) |
| Capability | Basic operations | Advanced administration |
| Modern Windows | Still available | Recommended for new work |

PowerShell commands use a verb-noun format (e.g. `Get-Process`, `Set-Location`) and can pipe objects rather than just text. It is the preferred CLI for Windows system administration.

***

## GUI vs CLI: When to Use Each

| Task | Best Interface | Why |
|---|---|---|
| Browsing the web | GUI | Visual content, links, and media |
| Writing a document | GUI | Formatting, layout, spell check visible |
| Renaming 100 files | CLI | A single command can do it in seconds |
| Installing one program | GUI | Double-click installer or app store |
| Checking disk space | Either | GUI shows a chart; CLI shows exact numbers |
| Configuring a web server | CLI | Servers rarely have a GUI installed |
| Editing a photo | GUI | Visual adjustments need a graphical preview |

The best IT professionals are comfortable with both. The GUI handles everyday tasks efficiently; the CLI provides power, precision, and automation for technical work.

***

## Customising the Interface

### GUI Customisation

- Change wallpaper, theme, and accent colours through Settings
- Rearrange the taskbar or dock position
- Adjust display scaling and resolution
- Add or remove desktop shortcuts

### CLI Customisation

- **Prompt** — Customise the text shown before each command (e.g. show the current directory, username, or time)
- **Aliases** — Create shortcuts for long commands
- **Colour scheme** — Change terminal background and text colours for readability
- **Profile** — Save preferred settings as a default profile

---

## Summary

- A GUI uses windows, icons, and a mouse — it is intuitive and visual
- A CLI uses typed text commands — it is powerful and precise
- Every OS includes both: terminal applications for CLI, desktop environments for GUI
- Navigate the CLI with `cd`, `dir`/`ls`, and `mkdir`
- Windows offers both Command Prompt (legacy) and PowerShell (modern)
- Use the right interface for the job; skilled IT workers use both
