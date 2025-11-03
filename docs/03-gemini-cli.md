# Gemini CLI Complete Guide

**Video Timestamp:** 1:27-4:14

Gemini CLI is Google's terminal AI tool. It's **FREE** (with generous limits) and perfect for getting started with terminal AI.

## Why Start with Gemini CLI?

Chuck's reasoning:
> "We're diving straight into Gemini CLI first. Why? Because it has a very generous free tier. That's right, you heard it - FREE."

**Best for:**
- ✅ Getting started (no credit card required)
- ✅ Research and web searches
- ✅ File creation and manipulation
- ✅ Learning context file workflows
- ✅ Writing and content creation

## Installation

### Linux / WSL / macOS

```bash
# Install globally with npm
npm install -g @google/gemini-cli
```

**Permission error?** Run with sudo:
```bash
sudo npm install -g @google/gemini-cli
```

### macOS (Alternative with Homebrew)

```bash
brew install gemini-cli
```

### Verify Installation

```bash
gemini --version
```

## First Launch

### 1. Create a Project Directory

Chuck's approach from the video:

```bash
# Create a new directory for your project
mkdir coffee-project
cd coffee-project

# Launch Gemini
gemini
```

**Why create a directory first?**
- Gemini can read/write files in the current directory
- Keeps your work organized
- Context files will be saved here

### 2. Initial Setup

First time you run `gemini`:

1. **Sign in with Google account** - Opens browser automatically
2. **Authorize the CLI** - Click "Allow"
3. **Return to terminal** - You're logged in!

```
     _____                 _       _    ____ _     ___
    / ____|               (_)     (_)  / ___| |   |_ _|
   | |  __  ___ _ __ ___  _ _ __  _  | |   | |    | |
   | | |_ |/ _ \ '_ ` _ \| | '_ \| | | |   | |    | |
   | |__| |  __/ | | | | | | | | | | | |___| |___ | |
    \_____|\___|_| |_| |_|_|_| |_|_|  \____|_____|___|

   Welcome to Gemini CLI!
```

## Basic Usage

### Your First Question

```bash
# Just start typing after the prompt
> How do I make the best cup of coffee in the world?
```

**What happens:**
1. Gemini searches the web (if relevant)
2. "Herding digital cats..." (loading message)
3. Response appears with formatting

### Key Interface Elements

```
> Your question here

Herding digital cats... 🐱 (processing)
Crafting the guide... ✨ (generating response)

[Response appears]

99% context left
```

**Context indicator:** Shows how much of your conversation window remains

## The Superpower: File System Access

### Creating Files

Chuck's demo from the video:

```bash
> I really want you to find the best way to make coffee.
  Research the top 10 sites, only reputable sources,
  and then compile the results into a document named best-coffee-method.
  And then create me a blog plan, just an outline.
```

**Gemini will ask:**
```
📝 Do you want me to create a file for you? (y/n)
```

Type `y` and hit enter.

**Result:**
```
Created files:
- best-coffee-method.md
- coffee-blog-outline.md
```

### Reading Files

Gemini automatically reads files in your current directory when relevant.

```bash
> What files are in this directory?
> Read the coffee blog outline and suggest improvements
> Add a new section to best-coffee-method.md about water temperature
```

## The Game-Changer: Context Files

### The `/init` Command

**Video Timestamp:** 4:00-4:14

This is THE feature that changes everything:

```bash
> /init
```

**What it does:**
1. Analyzes your current directory
2. Reads all files in the project
3. Creates a `gemini.md` context file
4. Saves project understanding for future sessions

**Gemini asks:**
```
📝 Create Gemini.md context file? (y/n)
```

Say yes!

### What's in gemini.md?

```bash
# View your context file
cat gemini.md
```

**Example content:**
```markdown
# Project: Coffee Blog Series

## Overview
This project involves researching and creating content about coffee brewing methods.

## Current Files
- best-coffee-method.md: Research compilation
- coffee-blog-outline.md: Blog series outline

## Project Goals
- Create comprehensive coffee brewing guide
- Develop blog series structure
```

### Using Context Across Sessions

**The magic moment from the video:**

1. Close your Gemini session (Ctrl+C or type `exit`)
2. Open a NEW Gemini session: `gemini`
3. Notice it loads `gemini.md` automatically

```
Loading context from gemini.md... ✓
100% context left (fresh session)
```

Now try:

```bash
> Write the intro for blog post 1 in the coffee series
```

**No additional context needed!** It knows what you're working on.

Chuck's reaction:
> "I didn't give it ANY context. It just knew. This is a new chat session."

## Real-World Workflow (from the video)

### Chuck's Actual Video Project

**Video Timestamp:** 5:48-6:09

```bash
# Navigate to video project
cd ~/Projects/531-ai-terminal

# Launch Gemini
gemini

# It loads the context file automatically
# Ask about project status
> Where are we at in the project?
```

**Gemini responds with:**
- Current phase
- Completed tasks
- Next steps
- Referenced documents

### Updating Context

```bash
> Update the gemini.md file with:
  - We completed the coffee brewing research
  - Next step is writing the first blog post
  - Decision made: Focus on pour-over method first
```

Gemini updates the file. Next session? It remembers everything.

## Available Commands

### View All Tools

```bash
> /tools
```

**Shows capabilities:**
- Web search
- File read/write
- Code execution
- Data analysis

### Common Commands

```bash
> /init           # Create context file
> /tools          # Show available tools
> /help           # Show help
> exit            # Exit Gemini (or Ctrl+C)
```

## Context Window Management

### What is Context?

Every AI has a "context window" - how much conversation it can remember.

**Browser AI:** Hides this from you (you hit limits unexpectedly)
**Gemini CLI:** Shows you exactly where you're at

```
99% context left  ← Plenty of room
50% context left  ← Halfway through
10% context left  ← Start new session or summarize
```

### When Context Gets Low

**Option 1:** Start a new session
```bash
# Exit current session
exit

# Start fresh
gemini
# Context file loads automatically!
```

**Option 2:** Ask Gemini to update context file
```bash
> Summarize our conversation and update gemini.md with key decisions
```

## Tips from Chuck

### 1. One Directory = One Project

```bash
# Good: Separate projects
~/coffee-project/      → One Gemini session
~/video-script/        → Another Gemini session
~/homelab-docs/        → Another Gemini session
```

### 2. Let Gemini Create Your Context File

Don't write `gemini.md` manually - let `/init` analyze your project.

### 3. Update Context as You Work

```bash
> Add to gemini.md: We decided to use the French press method instead
```

### 4. Context Files = Your Project Memory

Think of `gemini.md` as your project's brain:
- Current state
- Decisions made
- Files to reference
- Next steps

## Advanced: Multiple Gemini Sessions

**From the video:** Chuck opens multiple terminal tabs with different Gemini sessions.

```bash
# Terminal Tab 1: Coffee project
cd ~/coffee-project
gemini

# Terminal Tab 2: Video project
cd ~/video-script
gemini

# Terminal Tab 3: Homelab docs
cd ~/homelab-docs
gemini
```

Each session loads its own context file - no mixing!

## Example Workflows

### Research Workflow

```bash
mkdir research-project
cd research-project
gemini

> Research the top 5 enterprise NAS solutions for small business.
  Include pricing, features, and pros/cons.
  Create a comparison document called nas-comparison.md

> /init

> Based on the research, write a recommendation for a 10-person company
  with 5TB storage needs. Save as nas-recommendation.md
```

### Writing Workflow

```bash
mkdir blog-series
cd blog-series
gemini

> Help me plan a 5-part blog series about network security basics.
  Create an outline file.

> /init

> Write the introduction for part 1. Save as part-1-intro.md

# Later (new session):
gemini

> Review the part-1-intro and suggest improvements
```

### Obsidian Integration

**As mentioned in the video:**

```bash
# Navigate to your Obsidian vault
cd ~/Obsidian/MyVault
gemini

> Read my daily note for today and summarize key tasks

> Create a new note about [topic] with backlinks to related notes
```

Gemini can access ALL your Obsidian notes because they're just markdown files!

## Troubleshooting

### "Permission Denied" on Install

```bash
# Use sudo
sudo npm install -g @google/generative-ai-cli
```

### "Command not found: gemini"

```bash
# Reload your shell
source ~/.bashrc  # or ~/.zshrc

# Or close and reopen terminal
```

### Context File Not Loading

```bash
# Make sure you're in the right directory
pwd
ls gemini.md

# Recreate if needed
> /init
```

### Web Search Not Working

Gemini needs internet access. Check your connection.

## Pricing & Limits

### Free Tier

- **Generous usage limits** (exact limits vary)
- **Gemini 2.5 Pro model** (latest and greatest!)
- **Web search included**
- **No credit card required**

### Google One AI Premium ($20/mo)

- Higher rate limits
- Priority access
- Integrated with other Google services

**Chuck's take:**
> "Everyone has a Google account, and yes, this can be a free regular Gmail account."

## What's Next?

Now that you understand Gemini CLI, you're ready for the big leagues:

➡️ [Claude Code Guide](04-claude-code.md) - Chuck's daily driver with AI agents

Or explore:
- [Context Files Deep Dive](07-context-files.md)
- [Productivity Workflows](11-productivity-workflows.md)

---

[← Back to Prerequisites](01-prerequisites.md) | [Next: Claude Code →](04-claude-code.md)
