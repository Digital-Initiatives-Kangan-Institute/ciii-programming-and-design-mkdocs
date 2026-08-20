# Working with Text Editors

When you work on the command line, you often need to create and edit text files — configuration files, scripts, and notes. This page covers two popular command-line text editors on Raspberry Pi OS: **nano** (pre-installed) and **micro** (installed separately). For file-management commands such as `pwd`, `ls`, `cd`, `mkdir`, and `touch`, see [Command Line Basics](command-line-basics.md).

---

## nano — The Pre-Installed Editor

`nano` is a simple editor that is pre-installed on Raspberry Pi OS.

```bash
nano notes.txt
```

- Type normally to edit.
- `Ctrl+O` then Enter — **save** (write out).
- `Ctrl+X` — **exit**.
- `Ctrl+K` — cut a line; `Ctrl+U` — paste.
- `Ctrl+W` — search.

The keyboard shortcuts are shown at the bottom of the nano screen.

---

## micro — A Modern Editor

`micro` is a more modern editor with mouse support and familiar shortcuts. Install it first:

```bash
sudo apt update
sudo apt install micro -y
```

Then open a file:

```bash
micro notes.txt
```

- Type normally to edit.
- `Ctrl+S` — **save**.
- `Ctrl+Q` — **quit**.
- `Ctrl+Z` — undo, `Ctrl+Y` — redo.
- `Ctrl+F` — find.

---

## A Worked Example

Create a folder, move into it, create a file and add text to it:

```bash
cd ~
mkdir IT_Maintenance
cd IT_Maintenance
nano maintenance_log.txt
```

Inside `nano`, type:

```text
Raspberry Pi Zero Setup Completed
Date: 21 August 2026
Technician Name: Alex Smith
OS Installed: Raspberry Pi OS Lite (32-bit)
This file created using: nano
```

Save (`Ctrl+O`, Enter) and exit (`Ctrl+X`). Then confirm the contents:

```bash
cat maintenance_log.txt
```

---

## Summary

| Task | nano | micro |
|---|---|---|
| Open a file | `nano <file>` | `micro <file>` |
| Save | `Ctrl+O` then Enter | `Ctrl+S` |
| Exit / quit | `Ctrl+X` | `Ctrl+Q` |
| Undo / redo | — | `Ctrl+Z` / `Ctrl+Y` |
| Search | `Ctrl+W` | `Ctrl+F` |
