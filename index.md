---
layout: default
title: Terminal Guide for Designers
---

<header class="page-header" markdown="1">

# Terminal Guide<br>for Designers

<p class="lede">You don't need to be a developer to use the terminal. This is a practical guide to the commands and workflows that make a real difference in a designer's day-to-day work.</p>

</header>

<nav class="toc" markdown="0">
<p class="toc-label">Contents</p>
<ol>
  <li><a href="#why-the-terminal">Why the Terminal</a></li>
  <li><a href="#getting-started">Getting Started</a></li>
  <li><a href="#essential-commands">Essential Commands</a></li>
  <li><a href="#workflows-for-designers">Workflows for Designers</a></li>
  <li><a href="#git-for-designers">Git for Designers</a></li>
  <li><a href="#installing-tools">Installing Tools</a></li>
  <li><a href="#customizing-your-terminal">Customizing Your Terminal</a></li>
  <li><a href="#quick-reference">Quick Reference</a></li>
</ol>
</nav>

<div class="content" markdown="1">

## Why the Terminal
{: #why-the-terminal}

- **Speed** — Rename 500 files in seconds instead of clicking through each one.
- **Automation** — Image optimization, file conversion, and build steps become one-liners.
- **Tool access** — Figma plugins, font utilities, and static site generators run from the terminal.
- **Version control** — Git is how teams collaborate on code, content, and design tokens.

## Getting Started
{: #getting-started}

### Opening Terminal

Press **Cmd + Space**, type **Terminal**, and hit Enter. Or find it in **Applications > Utilities > Terminal**.

### Anatomy of a Command

```
command  -flag  argument
```

| Part | What it does | Example |
|------|-------------|---------|
| Command | The program you're running | `ls` |
| Flag | Modifies behavior | `-l` |
| Argument | What you're acting on | `~/Desktop` |

So `ls -l ~/Desktop` means: *list the contents of my Desktop in long format.*

## Essential Commands
{: #essential-commands}

### Navigating Files

| Command | What it does | Example |
|---------|-------------|---------|
| `pwd` | Print where you are | `pwd` |
| `ls` | List files here | `ls` |
| `ls -la` | List all files with details | `ls -la` |
| `cd` | Change directory | `cd ~/Projects` |
| `cd ..` | Go up one level | `cd ..` |
| `cd ~` | Go to home directory | `cd ~` |

Drag a folder from Finder into Terminal to paste its path automatically.

### Working with Files and Folders

| Command | What it does | Example |
|---------|-------------|---------|
| `mkdir` | Create a folder | `mkdir new-project` |
| `touch` | Create an empty file | `touch index.html` |
| `cp` | Copy a file | `cp logo.png backup.png` |
| `cp -r` | Copy a folder | `cp -r assets/ backup/` |
| `mv` | Move or rename | `mv old.sketch new.sketch` |
| `rm` | Delete a file | `rm unused.png` |
| `rm -r` | Delete a folder | `rm -r old-project/` |
| `open` | Open in default app | `open mockup.fig` |
| `open .` | Open folder in Finder | `open .` |

> `rm` does not move files to the Trash. They are permanently deleted. Double-check before running it.

## Workflows for Designers
{: #workflows-for-designers}

### Batch Rename Files

Rename every `.jpeg` to `.jpg` in the current folder:

```bash
for f in *.jpeg; do mv "$f" "${f%.jpeg}.jpg"; done
```

### Resize Images with sips

Built into macOS. Resize all PNGs to a max width of 1200px:

```bash
sips --resampleWidth 1200 *.png
```

### Convert HEIC to JPG

```bash
for f in *.HEIC; do sips -s format jpeg "$f" --out "${f%.HEIC}.jpg"; done
```

### Optimize Images

If you have [ImageOptim](https://imageoptim.com) installed:

```bash
open -a ImageOptim *.png
```

### Generate a File Tree

Useful for documentation or project overviews:

```bash
find . -not -path '*/.*' | head -50
```

## Git for Designers
{: #git-for-designers}

Git tracks changes to files so you can collaborate, undo mistakes, and keep a complete history of your work.

### First-Time Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Daily Workflow

```bash
git status
git add .
git commit -m "Update hero section layout"
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
| Undo changes | `git checkout -- filename` |

## Installing Tools
{: #installing-tools}

### Homebrew

The Mac package manager. Install it once:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install tools:

```bash
brew install node        # Build tools and scripts
brew install ffmpeg      # Video and audio conversion
brew install imagemagick # Advanced image processing
```

### Node.js and npm

Many design tools and static site generators run on Node:

```bash
npm install -g live-server
```

## Customizing Your Terminal
{: #customizing-your-terminal}

### Oh My Zsh

Makes your terminal more readable and pleasant to use:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Aliases

Add shortcuts to your `~/.zshrc` file:

```bash
alias ll="ls -la"
alias proj="cd ~/Projects"
alias gs="git status"
alias gp="git push"
```

After editing, reload with `source ~/.zshrc`.

## Quick Reference
{: #quick-reference}

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
| Git commit | `git commit -m "msg"` |
| Git push | `git push` |
| Clear screen | `clear` |
| Cancel command | `Ctrl + C` |

<footer class="page-footer" markdown="0">
  The terminal is a skill that compounds over time. Bookmark this page and return when you need it.
</footer>

</div>
