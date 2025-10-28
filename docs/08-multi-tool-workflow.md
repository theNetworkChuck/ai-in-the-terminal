# Multi-Tool Workflow Guide

**Video Timestamp:** 18:03-19:25

**The Ultimate Power Move:** Using Gemini CLI, Claude Code, and Codex simultaneously on the same project.

## Why Use Multiple AI Tools?

**Chuck's philosophy:**
> "I will use all AI. I'll use the best AI. No one can stop me."

### Each AI Has Strengths

**Gemini CLI:**
- ✅ Fast web research
- ✅ Current information (web search built-in)
- ✅ Quick iterations

**Claude Code:**
- ✅ Deep analysis and planning
- ✅ Long-form writing
- ✅ Agents for specialized tasks

**Codex (ChatGPT):**
- ✅ High-level analysis
- ✅ Strategic thinking
- ✅ Different perspective

### Chuck's Strategy

**From the video:**
> "I find ChatGPT is very good at analyzing things from a high view. Gemini and Claude are very good at the work, the deep work."

## The Setup: Two Simple Steps

### Step 1: Same Directory

**All AI tools must work from the SAME project folder:**

```bash
cd ~/my-project
```

**Open multiple terminal tabs/windows:**

```bash
# Terminal Tab 1: Claude
cd ~/my-project
claude

# Terminal Tab 2: Gemini
cd ~/my-project
gemini

# Terminal Tab 3: Codex
cd ~/my-project
codex
```

**Result:** All three AIs can access the same files!

### Step 2: Sync Context Files

**Ensure these files have identical content:**
- `claude.md`
- `gemini.md`
- `agents.md` (for Codex)

**Chuck's method:**
```bash
# In Claude terminal
> Read claude.md and sync it to gemini.md and agents.md.
  Make sure all three files have identical project context.
```

**Verification:**
```bash
# In project directory
diff claude.md gemini.md
diff claude.md agents.md

# Should show: "Files are identical" or no output
```

## The Power: Parallel Workflows

**Video Timestamp:** 18:45-19:01

### Chuck's Live Demo

**The command:**
```bash
# In Claude terminal
> Write a hook for this video, authority angle.
  Write it to authority-hook.md

# In Gemini terminal
> Write a hook on a discovery angle.
  Write it to discovery-hook.md

# In Codex terminal
> Review both hooks and compare their strengths
```

**What happens:**
- 🎯 Claude: Writes authority-focused hook
- 🔍 Gemini: Writes discovery-focused hook
- 📊 Codex: Analyzes and compares both

**Chuck's observation:**
> "They're all using the same context, different roles. You have three different AIs working on the same thing at the same time. No copying and pasting. They can see each other's work."

## Real-World Workflow Examples

### Example 1: Content Creation

**Scenario:** Writing a technical blog post

```bash
# TERMINAL 1: Claude (long-form writing)
claude
> Write the introduction section for the ZFS storage blog post.
  Save to sections/intro.md

# TERMINAL 2: Gemini (research)
gemini
> Research the latest ZFS performance benchmarks.
  Compile findings in research/zfs-benchmarks.md

# TERMINAL 3: Codex (review)
codex
> Review the intro in sections/intro.md and check if it aligns
  with the benchmarks research. Suggest improvements.
```

**Result:**
- Claude writes deep content
- Gemini gathers current data
- Codex ensures quality and alignment

### Example 2: Homelab Planning

**Scenario:** Designing a new homelab setup

```bash
# TERMINAL 1: Claude (planning)
claude
> Create a detailed homelab architecture plan.
  Include network diagram, hardware specs, and budget.
  Save to homelab-plan.md

# TERMINAL 2: Gemini (current prices/availability)
gemini
> Research current pricing for enterprise NAS systems.
  Check availability of the hardware in the homelab plan.
  Save to pricing-research.md

# TERMINAL 3: Codex (risk analysis)
codex
> Review homelab-plan.md and identify potential issues:
  - Single points of failure
  - Budget overruns
  - Compatibility problems
  Save analysis to risk-assessment.md
```

### Example 3: Video Script Writing (Chuck's Process)

**Video Timestamp:** 18:41-19:25

**Chuck's actual workflow:**

```bash
# TERMINAL 1: Claude with script-writing output style
claude
> Continue working on Segment 3 of the AI Terminal script.
  Reference the outline at outline.md

# TERMINAL 2: Gemini with research focus
gemini
> Verify the technical accuracy of the Claude Code section.
  Cross-check commands and features against official docs.

# TERMINAL 3: Codex for high-level review
codex
> Read the current script at script.md.
  Evaluate narrative flow and retention strategy.
  Does it deliver on the hook promise?
```

**Chuck's approach:**
> "I'm using all three right now to work on this video script."

## File-Based Collaboration

### How AIs "See" Each Other's Work

**The secret:** Everything is just files!

```
my-project/
├── claude.md              ← Shared context
├── gemini.md              ← Shared context
├── agents.md              ← Shared context
├── research/
│   ├── topic-a.md        ← Gemini wrote this
│   └── topic-b.md        ← Gemini wrote this
├── drafts/
│   ├── section-1.md      ← Claude wrote this
│   └── section-2.md      ← Claude wrote this
└── reviews/
    └── analysis.md       ← Codex wrote this
```

**When Claude asks:**
```bash
> Review the research in research/ folder
```

**Claude sees:**
- ✅ Files Gemini created
- ✅ Their exact content
- ✅ Timestamps
- ✅ Everything!

**No copy/paste. No export/import. Just files.**

## Specialized Roles Strategy

### Assign Each AI a Role

**Based on strengths from video:**

#### Claude → Deep Work
```bash
# Long-form writing
# Complex planning
# Agent deployment
# Custom output styles
```

#### Gemini → Research & Speed
```bash
# Web research
# Fast iterations
# Current information
# Quick file creation
```

#### Codex → Analysis & Review
```bash
# High-level strategy
# Quality review
# Competitive analysis
# Meta-thinking
```

### Role Assignment in Practice

**In your context files:**

**claude.md:**
```markdown
# Project: Technical Blog Series

## Claude's Role
Primary writer for long-form content.
- Draft all blog posts
- Create detailed technical explanations
- Deploy agents for specialized sections
```

**gemini.md:**
```markdown
# Project: Technical Blog Series

## Gemini's Role
Research and verification specialist.
- Gather current technical information
- Verify accuracy of claims
- Find supporting examples and case studies
```

**agents.md:**
```markdown
# Project: Technical Blog Series

## Codex's Role
Strategic reviewer and analyst.
- Review drafts for clarity and flow
- Ensure technical accuracy
- Validate against target audience needs
```

## Context Syncing Strategies

### Manual Sync

**After major changes:**

```bash
# Update all three manually
nano claude.md
nano gemini.md
nano agents.md
```

**Or use one AI to update others:**

```bash
# In Claude terminal
> I just made major updates to claude.md (added new project phase).
  Update gemini.md and agents.md to match.
```

### Automated Sync (Chuck's Method)

**Using a Claude agent:**

```bash
# In Claude terminal
> @context-sync-agent
  Read claude.md and sync to gemini.md and agents.md.
  Ensure all three files are identical.
```

**Agent does:**
1. Reads `claude.md`
2. Overwrites `gemini.md` with same content
3. Overwrites `agents.md` with same content
4. Confirms sync complete

### Git-Based Sync

**For ultimate control:**

```bash
# After each session, commit context files
git add *.md
git commit -m "Update project context: research phase complete"

# All terminals pull latest
git pull
```

**Each AI automatically loads updated context on next launch.**

## Communication Patterns

### Cross-AI References

**Gemini creates file → Claude uses it:**

```bash
# GEMINI TERMINAL
gemini
> Research ZFS performance. Save to zfs-research.md

# CLAUDE TERMINAL (moments later)
claude
> Read zfs-research.md and write a blog intro incorporating
  those performance numbers. Save to blog-intro.md
```

### Review Loops

**Claude writes → Codex reviews → Claude revises:**

```bash
# CLAUDE TERMINAL
claude
> Write the authentication section. Save to auth-section.md

# CODEX TERMINAL
codex
> Review auth-section.md for security concerns.
  Save feedback to reviews/auth-feedback.md

# CLAUDE TERMINAL
claude
> Read reviews/auth-feedback.md and revise auth-section.md
  to address the security concerns.
```

### Parallel Tasks

**All three work simultaneously:**

```bash
# CLAUDE: Long task
> Create comprehensive system architecture document

# GEMINI: Quick research
> Find 5 examples of similar architectures in production

# CODEX: Analysis
> Analyze current requirements and identify gaps
```

**All running at once, no waiting!**

## Advanced: Cross-Tool Agents

**Video Timestamp:** 16:06-16:17

### Claude Agent Uses Gemini

**Chuck's demo:**

```bash
# In Claude terminal
> @gemini-research find the best AI terminal videos on YouTube
```

**What happens:**
1. Claude deploys `gemini-research` agent
2. Agent runs: `gemini -p "search YouTube for top AI terminal videos"`
3. Gemini performs search (better at current info)
4. Returns results to Claude agent
5. Claude compiles final report

**Chuck's amazement:**
> "We're having an AI use an AI right now!"

### Create Gemini Research Agent

**In Claude:**

```bash
> /agents
# Create new agent

Name: gemini-research
Description: Uses Gemini CLI in headless mode for research tasks.
              Gemini excels at web search and current information.

Instructions:
You are a research specialist that uses Gemini CLI to gather information.

When given a research task:
1. Format it as a clear search query
2. Run: gemini -p "your search query here"
3. Compile and summarize the results

You have access to Bash tool to run gemini command.

Tools: Bash, Read, Write
Model: Sonnet
```

**Usage:**
```bash
> @gemini-research What are the latest Proxmox features?
> @gemini-research Find pricing for enterprise SSDs
> @gemini-research Research zero-trust network solutions
```

## Managing Multiple Terminal Windows

### Terminal Layouts

**Chuck's setup (visible in video):**

```
┌─────────────────┬─────────────────┬─────────────────┐
│  CLAUDE         │  GEMINI         │  CODEX          │
│                 │                 │                 │
│  Deep work      │  Research       │  Analysis       │
│  Writing        │  Web search     │  Review         │
│  Agents         │  Fast iteration │  Strategy       │
└─────────────────┴─────────────────┴─────────────────┘
```

**Tools for multi-terminal:**
- **tmux** (Linux/Mac) - Terminal multiplexer
- **Windows Terminal** (Windows) - Native tabs/panes
- **iTerm2** (Mac) - Split panes
- **Terminator** (Linux) - Multiple terminals

### Quick Switching

**tmux example:**

```bash
# Start tmux session for project
tmux new -s ai-project

# Window 1: Claude
claude

# Create new window: Ctrl+B, C
# Window 2: Gemini
gemini

# Create new window: Ctrl+B, C
# Window 3: Codex
codex

# Switch windows: Ctrl+B, [0-9]
```

## Workflow Optimization Tips

### 1. Primary AI for Context Updates

**Choose ONE AI to maintain context files:**

```bash
# Claude is "source of truth"
# Only Claude updates context files
# Others sync from Claude's version
```

**Why:** Prevents conflicts, single source of truth

### 2. Clear File Naming

**Make it obvious who created what:**

```
research-gemini-zfs-performance.md    ← Gemini research
draft-claude-section-1.md             ← Claude draft
review-codex-analysis.md              ← Codex review
```

### 3. Session Start Ritual

**Every work session:**

```bash
# 1. Pull latest (if using git)
git pull

# 2. Check context sync
diff claude.md gemini.md

# 3. Launch all three AIs
# Terminal 1: claude
# Terminal 2: gemini
# Terminal 3: codex

# 4. Verify each loaded context
# (Check context indicators in each terminal)
```

### 4. Session End Ritual

**Chuck's approach (using agent):**

```bash
# In Claude terminal
> @script-session-closer run
```

**Agent does:**
- Summarizes session
- Updates all context files
- Syncs gemini.md and agents.md
- Commits to git

**Manual version:**

```bash
# 1. Update context files
> Update claude.md with today's progress

# 2. Sync to other files
> Copy claude.md content to gemini.md and agents.md

# 3. Commit
git add .
git commit -m "Session end: [what you accomplished]"
git push
```

## The "It's Just a Folder" Philosophy

**Chuck's key insight:**

> "Everything I'm doing, talking with these three different AIs on a project... It's not tied in a browser. It's not tied in a GUI. It's just this folder right here on my hard drive."

### What This Enables

```
my-project/     ← This is ALL you need
├── claude.md
├── gemini.md
├── agents.md
└── all-your-work-files/
```

**You can:**
- ✅ Copy to another computer
- ✅ Backup easily
- ✅ Version control with git
- ✅ Switch AI tools anytime
- ✅ Share with team (just the folder!)

**Chuck's freedom:**

> "I can copy and paste that folder anywhere. All the work, all the decisions, all the context - it's mine. I own my context."

## Troubleshooting

### AIs Seem Out of Sync

```bash
# Check context files
diff claude.md gemini.md

# Re-sync
claude
> Sync all context files from claude.md
```

### File Conflicts

**Two AIs editing same file:**

```bash
# Solution: Assign clear responsibilities
# Claude: Writes sections/1.md
# Gemini: Writes research/1.md
# Never overlap!
```

### Context Drift

**Over time, conversations diverge:**

```bash
# Regular re-sync
# Every 30-60 minutes:
> @context-sync-agent run
```

## Summary: Multi-Tool Benefits

| Single AI | Multi-Tool Workflow |
|-----------|---------------------|
| One perspective | Three perspectives |
| One strength | Combined strengths |
| Sequential tasks | Parallel tasks |
| One context window | Three independent contexts |
| Vendor lock-in risk | Tool agnostic |

**Chuck's verdict:**

> "I will use the best AI. No one can stop me. If a new greater better AI comes out, I'm ready for it."

## What's Next?

**Master the multi-tool workflow:**

➡️ [Productivity Workflows](11-productivity-workflows.md) - Real examples using multiple AIs

➡️ [AI Agents Deep Dive](09-agents.md) - Advanced agent strategies

---

[← Back to Context Files](07-context-files.md) | [Next: AI Agents →](09-agents.md)
