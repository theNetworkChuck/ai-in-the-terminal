# Quick Start Guide

Get up and running with AI in the terminal in **5 minutes**.

## Choose Your Path

### Path A: Free Start (Gemini CLI)
**Best for:** First-timers, budget-conscious users, testing the concept

### Path B: Power User Start (Claude Code)
**Best for:** Professionals ready to commit, agent users, serious workflows

## Path A: Free Start (Gemini CLI)

### Step 1: Install (30 seconds)

**Linux / macOS / WSL:**
```bash
npm install -g @google/generative-ai-cli
```

**macOS (Homebrew):**
```bash
brew install gemini-cli
```

**Permission error?** Add `sudo`:
```bash
sudo npm install -g @google/generative-ai-cli
```

### Step 2: Create Project (10 seconds)

```bash
mkdir ai-test-project
cd ai-test-project
```

### Step 3: Launch & Login (1 minute)

```bash
gemini
```

**First launch:**
1. Browser opens automatically
2. Sign in with Google account (any Gmail works!)
3. Click "Allow"
4. Return to terminal - you're in!

### Step 4: Your First Task (2 minutes)

**Try this:**
```bash
> How do I make the best cup of coffee?
```

**Watch it:**
- Search the web
- Craft response
- Return results

**Now try this (the magic part):**
```bash
> Research the top 5 coffee brewing methods.
  Create a comparison document called coffee-methods.md
```

**Gemini asks:** "Create file?" → Type `y`

**Check it out:**
```bash
ls
# You'll see: coffee-methods.md

cat coffee-methods.md
# Your research, saved locally!
```

### Step 5: Create Context File (1 minute)

**The game-changer:**
```bash
> /init
```

Gemini analyzes your project and creates `gemini.md`

**Now exit and reopen:**
```bash
exit
gemini
```

**Try this:**
```bash
> Continue working on the coffee project
```

**It remembers!** No re-explaining needed.

### ✅ You're Done! (5 minutes total)

**What you learned:**
- ✅ Gemini can create files
- ✅ Context files persist knowledge
- ✅ No more re-explaining your project
- ✅ Everything stored locally

**Next steps:**
- [Full Gemini CLI Guide](03-gemini-cli.md)
- [Understanding Context Files](07-context-files.md)

---

## Path B: Power User Start (Claude Code)

**Requirements:**
- Claude Pro subscription ($20/mo)
- Node.js installed

### Step 1: Install (30 seconds)

```bash
npm install -g @anthropic-ai/claude-code
```

**Permission error?**
```bash
sudo npm install -g @anthropic-ai/claude-code
```

### Step 2: Create Project (10 seconds)

```bash
mkdir my-project
cd my-project
```

### Step 3: Launch & Authenticate (1 minute)

```bash
claude
```

**First launch:**
1. Browser opens for authentication
2. Login with Claude Pro account
3. Approve directory access
4. Return to terminal

### Step 4: Create Context File (30 seconds)

```bash
> /init
```

Claude analyzes directory and creates `claude.md`

### Step 5: Create Your First Agent (2 minutes)

**This is where it gets powerful:**

```bash
> /agents
```

**Select:** "Create new agent"

**Choose:** "Project-specific agent"

**Name it:** `research-expert`

**Describe it:**
```
You are a research specialist. When given a topic:
1. Search for authoritative sources
2. Compile key findings
3. Create structured summaries
```

**Configure:**
- Tools: All tools
- Model: Sonnet

**Press Enter** to save

### Step 6: Deploy Your Agent (1 minute)

```bash
> @research-expert
  Research zero-trust network architecture.
  Create a summary document.
```

**Watch your agent work:**
- Fresh context window (200K tokens!)
- Independent research
- Returns results

**Check the file:**
```bash
ls
cat zero-trust-summary.md
```

### ✅ You're Done! (5 minutes total)

**What you learned:**
- ✅ Claude Code basics
- ✅ Agent creation
- ✅ Context persistence
- ✅ Agent deployment

**Next steps:**
- [Full Claude Code Guide](04-claude-code.md)
- [AI Agents Deep Dive](09-agents.md)
- [Output Styles Guide](10-customization.md)

---

## Quick Comparison

| Feature | Gemini CLI | Claude Code |
|---------|------------|-------------|
| **Cost** | Free | $20/mo |
| **Setup Time** | 2 min | 3 min |
| **Best Feature** | Web research | AI agents |
| **Context File** | gemini.md | claude.md |
| **Learning Curve** | Easy | Medium |

**Chuck's recommendation:**
> "Start with Gemini CLI. It's FREE. But if you can afford one subscription, Claude Pro is the one I'd choose."

---

## Common First-Time Issues

### "Command not found"

```bash
# Reload your shell
source ~/.bashrc
# or
source ~/.zshrc

# Or close and reopen terminal
```

### "Permission denied"

```bash
# Run with sudo
sudo npm install -g [package-name]
```

### "Node.js not found"

Install from [nodejs.org](https://nodejs.org/) (LTS version)

### Context file not loading

```bash
# Verify you're in the right directory
pwd
ls gemini.md

# Recreate if needed
> /init
```

---

## What to Try Next

### Beginner Tasks
1. **Research task:** Ask Gemini to research a topic and create a summary
2. **Writing task:** Ask Claude to write a blog intro
3. **File organization:** Create a project structure and let AI populate it

### Intermediate Tasks
4. **Create an agent:** Make a specialized agent for your work
5. **Multi-session work:** Exit, reopen, verify context loads
6. **File manipulation:** Update existing files with AI help

### Advanced Tasks
7. **Multiple AIs:** Run Gemini and Claude simultaneously
8. **Context syncing:** Keep gemini.md and claude.md in sync
9. **Custom output style:** Create personality for your work

---

## 5-Minute Challenges

### Challenge 1: Coffee Research (Gemini)
**Goal:** Research, create file, reload context

```bash
mkdir coffee-challenge
cd coffee-challenge
gemini

> Research French press vs pour-over coffee.
  Create comparison-chart.md

> /init

exit
gemini

> Add a recommendation section to comparison-chart.md
  based on taste preferences
```

**Success if:** File created and AI remembers project without re-explaining

### Challenge 2: Agent Deploy (Claude)
**Goal:** Create and use an agent

```bash
mkdir agent-challenge
cd agent-challenge
claude

> /agents
# Create "homelab-helper" agent
# Instructions: "Expert in homelab hardware and networking"

> @homelab-helper
  What's the best budget NAS for a home lab?
```

**Success if:** Agent responds with detailed recommendations

### Challenge 3: Multi-Tool (Advanced)
**Goal:** Use Gemini and Claude together

```bash
mkdir multi-tool-challenge
cd multi-tool-challenge

# Terminal 1:
gemini
> Research the top 3 text editors
> /init

# Terminal 2:
claude
> /init
> Read the research and write a blog post intro
```

**Success if:** Claude reads Gemini's research file

---

## Next Steps by Interest

### I want to use AI for writing
→ [Productivity Workflows](11-productivity-workflows.md)
→ [Output Styles Guide](10-customization.md)

### I want to use AI for coding
→ [Development Workflows](12-development-workflows.md)
→ [Claude Code Guide](04-claude-code.md)

### I want to use AI for IT/homelab work
→ [Homelab Workflows](13-homelab-workflows.md)
→ [AI Agents Guide](09-agents.md)

### I want to understand the concepts deeply
→ [Context Files Explained](07-context-files.md)
→ [Multi-Tool Workflow](08-multi-tool-workflow.md)

---

## Questions?

**"Which tool should I start with?"**
- Free: Gemini CLI
- Professional: Claude Code
- Experimental: opencode

**"Do I need all three?"**
- No! Start with one
- Add others as you see benefits
- Chuck uses all three for different strengths

**"How much does this cost?"**
- Gemini CLI: FREE
- Claude Code: $20/mo (Claude Pro)
- opencode: Free (Grok) or various providers

**"Is this just for developers?"**
- NO! Chuck uses it for video scripts
- Works for writing, research, planning, any text work
- Coding is just one use case

---

**Ready to dive deeper?** → [Full Guide Navigation](../README.md)

**Having issues?** → [Troubleshooting](15-troubleshooting.md)

**Want the commands?** → [Cheat Sheet](14-cheat-sheet.md)

---

[← Back to Prerequisites](01-prerequisites.md) | [Next: Gemini CLI →](03-gemini-cli.md)
