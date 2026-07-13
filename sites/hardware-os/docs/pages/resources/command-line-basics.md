# Command Line Basics

The command line is a powerful way to control your computer by typing instructions instead of clicking. While it looks different from the windows and icons you are used to, every command follows a simple structure. Once you understand the pattern, you can learn new commands quickly.

---

## What is a Command?

A **command** is a text instruction you type into the terminal that tells the computer to do something. When you press Enter, the computer runs that instruction and shows you the result.

For example, on Windows you can type `dir` to see a list of files in the current folder. On Linux or macOS you would type `ls` instead. Different operating systems have slightly different commands, but the way commands are structured is the same everywhere.

---

## How Commands Are Structured

Most commands follow this pattern:

```text
command [options] [arguments]
```

| Part | What It Is | Example |
|---|---|---|
| **Command** | The program you want to run | `mkdir` (make directory) |
| **Options (or flags)** | Change how the command behaves. Usually start with `-` or `--` | `-p` or `--verbose` |
| **Arguments** | The thing you want the command to act on | `projects` (the name of a folder) |

Putting it together:

```bash
mkdir projects
```

This runs the `mkdir` command with the argument `projects` — it creates a new folder called `projects`.

```bash
mkdir -p projects/website/images
```

The `-p` option tells `mkdir` to create all the parent folders automatically. Without `-p`, the command would fail if `projects` or `website` did not already exist.

---

## Options and Flags

Options modify what a command does. They come in two forms:

| Form | Example | Description |
|---|---|---|
| **Short option** | `-h` | Single letter, prefixed with a single dash |
| **Long option** | `--help` | Full word, prefixed with two dashes |

Short options can often be combined. On Linux, `ls -l -a` (long format, show hidden files) can be written as `ls -la`.

Not every command uses the same options. `-h` might mean "help" for one command and "human-readable" for another. You always need to check what a command supports.

---

## Getting Help

You do not need to memorise every option. Commands include their own documentation that you can read right in the terminal.

### The `--help` Flag

Almost every command supports `--help`. It prints a quick summary of what the command does and what options it accepts:

```bash
mkdir --help
```

On Windows Command Prompt, many commands use `/?` instead:

```cmd
mkdir /?
```

### The Manual (`man`)

Linux and macOS include a built-in manual called `man`. It provides detailed documentation for almost every command:

```bash
man ls
```

This opens a full page describing what `ls` does, every option it supports, and examples of how to use it. Press the **arrow keys** to scroll, and press **Q** to quit and return to the terminal.

Windows PowerShell has a similar feature with the `Get-Help` command:

```powershell
Get-Help Get-Process
```

---

## Understanding Command Output

When a command runs successfully, it may:

- **Print something to the screen** — for example, `dir` lists files
- **Do something silently** — for example, `mkdir` creates a folder but prints nothing unless there is an error
- **Ask for confirmation** — some commands ask "Are you sure?" before doing something destructive

If a command fails, it usually prints an error message explaining what went wrong. Common errors include:

| Error | What It Means |
|---|---|
| `command not found` | The command is misspelled or not installed |
| `permission denied` | You do not have the right to do that — you may need administrative access |
| `no such file or directory` | The file or folder you named does not exist |
| `is a directory` | You tried to use a file command on a folder |

***

## Administrative Access (`sudo`)

Some commands affect the entire system and require extra permission to run. On Linux and macOS, you prefix these commands with `sudo` (short for "superuser do"):

```bash
sudo apt install firefox
```

The terminal will ask for your password. When you type it, nothing appears on screen — that is normal. Press Enter and the command runs with elevated permissions.

Windows has a similar concept called "Run as Administrator." Right-click the Command Prompt or PowerShell icon and select **Run as administrator** to get the same level of access.

---

## Safety Tips

### Be Careful with Destructive Commands

Commands that delete files or modify the system cannot be undone. There is no Recycle Bin for the command line. Before running a command you found online:

- Read what it does — use `--help` or `man`
- Make sure you understand which files or folders it affects
- Double-check the spelling of file paths
- Start with a test folder if you are unsure

### Copy and Paste Carefully

Do not paste commands from websites into your terminal without understanding them. Malicious websites sometimes hide extra commands in copied text. If you are learning, type commands out instead of copying them.

### Avoid These Patterns Until You Are Confident

- `rm -rf` — deletes files and folders without asking and cannot be undone
- Commands that include `/dev/` — these affect hardware devices directly
- Commands that include `chmod 777` — this gives everyone full access to a file, which is rarely correct

---

## Next Steps

Now that you understand the structure of commands, options, and arguments, and you know how to get help with `--help` and `man`, you are ready to learn specific commands. The pages in this site introduce commands in context — installing software, checking system information, managing files — so you learn them as you need them rather than memorising a long list.

If you ever get stuck, ask the command itself for help first. It is the fastest way to find the right option.
