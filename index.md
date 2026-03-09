---
layout: home
title: Terminal Guide for Designers
---

# The Mac Terminal: A Guide for Designers

You don't need to be a developer to use the terminal. This guide covers the practical commands and workflows that make a real difference in a designer's day-to-day work.

---

## Why Bother with the Terminal?

- **Speed** — Rename 500 files in seconds instead of clicking through each one.
- **Automation** — Repetitive tasks like image optimization, file conversion, and build steps become one-liners.
- **Tool access** — Many modern design tools (Figma plugins, font utilities, static site generators) run from the terminal.
- **Version control** — Git is how teams collaborate on code, content, and even design tokens.

---

## Getting Started

### Opening Terminal

- Press **Cmd + Space**, type **Terminal**, and hit Enter.
- Or find it in **Applications > Utilities > Terminal**.

### Anatomy of a Command

```
command  -flag  argument
```

| Part | What it does | Example |
|------|-------------|---------|
| Command | The program you're running | `ls` |
| Flag | Modifies behavior | `-l` (long format) |
| Argument | What you're acting on | `~/Desktop` |

So `ls -l ~/Desktop` means: *list the contents of my Desktop in long format.*

---

## Essential Commands

### Navigating Files

| Command | What it does | Example |
|---------|-------------|---------|
| `pwd` | Print where you are | `pwd` |
| `ls` | List files here | `ls` |
| `ls -la` | List all files with details | `ls -la` |
| `cd` | Change directory | `cd ~/Projects` |
| `cd ..` | Go up one level | `cd ..` |
| `cd ~` | Go to home directory | `cd ~` |

**Tip:** Drag a folder from Finder into Terminal to paste its path.

### Working with Files and Folders

| Command | What it does | Example |
|---------|-------------|---------|
| `mkdir` | Create a folder | `mkdir new-project` |
| `touch` | Create an empty file | `touch index.html` |
| `cp` | Copy a file | `cp logo.png backup-logo.png` |
| `cp -r` | Copy a folder | `cp -r assets/ assets-backup/` |
| `mv` | Move or rename | `mv old-name.sketch new-name.sketch` |
| `rm` | Delete a file (permanent!) | `rm unused-file.png` |
| `rm -r` | Delete a folder (permanent!) | `rm -r old-project/` |
| `open` | Open file in default app | `open mockup.fig` |
| `open .` | Open current folder in Finder | `open .` |

**Warning:** `rm` does not move files to the Trash. They're gone for good. Double-check before you run it.

---

## Practical Workflows for Designers

### Batch Rename Files

Rename every `.jpeg` to `.jpg` in the current folder:

```bash
for f in *.jpeg; do mv "$f" "${f%.jpeg}.jpg"; done
```

### Resize Images with sips (Built into macOS)

Resize all PNGs in a folder to a max width of 1200px:

```bash
sips --resampleWidth 1200 *.png
```

### Convert HEIC to JPG

```bash
for f in *.HEIC; do sips -s format jpeg "$f" --out "${f%.HEIC}.jpg"; done
```

### Optimize Images with ImageOptim (CLI)

If you have [ImageOptim](https://imageoptim.com) installed:

```bash
open -a ImageOptim *.png
```

### Generate a Quick File Tree

Great for documentation or project overviews:

```bash
find . -not -path '*/.*' | head -50
```

---

## Git for Designers

Git tracks changes to files so you can collaborate, undo mistakes, and keep a history of your work.

### First-Time Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Daily Git Workflow

```bash
# Check what's changed
git status

# Stage your changes
git add .

# Commit with a message
git commit -m "Update hero section layout"

# Push to the remote repo
git push
```

### Common Scenarios

| I want to... | Command |
|--------------|---------|
| Clone a project | `git clone <url>` |
| Create a branch | `git checkout -b feature/new-icons` |
| Switch branches | `git checkout main` |
| Pull latest changes | `git pull` |
| See commit history | `git log --oneline` |
| Undo uncommitted changes | `git checkout -- filename` |

---

## Installing Tools

### Homebrew (The Mac Package Manager)

Install it once:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install tools easily:

```bash
brew install node        # For running build tools
brew install ffmpeg      # For video/audio conversion
brew install imagemagick # For advanced image processing
```

### Node.js and npm

Many design tools and static site generators run on Node:

```bash
# After installing node via Homebrew
npm install -g live-server   # Local dev server with auto-reload
```

---

## Customizing Your Terminal

### Oh My Zsh

Makes your terminal more readable and pleasant:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Useful Aliases

Add these to your `~/.zshrc` file to create shortcuts:

```bash
alias ll="ls -la"
alias proj="cd ~/Projects"
alias gs="git status"
alias gp="git push"
```

After editing, reload with:

```bash
source ~/.zshrc
```

---

## Quick Reference Cheat Sheet

| Action | Command |
|--------|---------|
| Where am I? | `pwd` |
| List files | `ls -la` |
| Go to folder | `cd folder-name` |
| Go up | `cd ..` |
| Create folder | `mkdir name` |
| Create file | `touch name` |
| Open in Finder | `open .` |
| Open file | `open file.png` |
| Copy | `cp source dest` |
| Move / rename | `mv source dest` |
| Delete file | `rm file` |
| Git status | `git status` |
| Git commit | `git commit -m "message"` |
| Git push | `git push` |
| Clear screen | `clear` |
| Cancel a command | `Ctrl + C` |

---

## Keep Going

The terminal is a skill that builds over time. You don't need to memorize everything — bookmark this page and come back when you need it. The more you use it, the more natural it feels.
