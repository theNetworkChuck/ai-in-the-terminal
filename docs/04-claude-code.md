# Claude Code Complete Guide

**Video Timestamp:** 8:44-14:26

Claude Code is Anthropic's terminal AI tool - Chuck's daily driver. It's the most powerful tool covered in the video.

## Why Claude Code?

Chuck's endorsement:
> "I use Claude Code for pretty much everything. It's my default. And here's why: it has a feature that changes the game - **agents**."

> "If you can only pay for one AI subscription, Claude Pro is the one I would choose, especially for the last feature I'm going to show you." *(Output Styles)*

**Best for:**
- ✅ Professional workflows with AI agents
- ✅ Complex multi-step tasks
- ✅ Custom personalities (Output Styles)
- ✅ Planning mode for strategic thinking
- ✅ Maximum control and customization

**Requires:** Claude Pro subscription ($20/mo)

## Installation

### All Platforms (npm)

```bash
# Install globally
npm install -g @anthropic-ai/claude-code

# Or with sudo if needed
sudo npm install -g @anthropic-ai/claude-code
```

### Verify Installation

```bash
claude --version
```

## First Launch & Setup

### Basic Launch

```bash
# Navigate to your project
cd coffee-project

# Launch Claude Code
claude
```

### Initial Login

First time:
1. Prompted to login with Claude Pro account
2. Opens browser for authentication
3. Select directory permissions (approve access to current folder)

**Permission prompt:**
```
📁 Allow Claude Code to access /Users/you/coffee-project? (y/n)
```

**Chuck's take:** "It's security first. It asks permission for most things, and that's good."

## Interface Overview

### TUI (Terminal User Interface)

```
┌─ Claude Code ──────────────────────────────────────┐
│ 💭 Thinking...                                      │
│                                                     │
│ [Your question here]                                │
│                                                     │
│ [Claude's response]                                 │
│                                                     │
│ Context: 42% used (85,234 tokens)                  │
│ Mode: Normal | Thinking: ON                        │
└─────────────────────────────────────────────────────┘
```

### Toggle Thinking Mode

Press **TAB** to turn thinking on/off:

```
Thinking: OFF  →  Press TAB  →  Thinking: ON
```

**Thinking mode:** See Claude's internal reasoning process

## Context Files: claude.md

### Initialize Context

```bash
> /init
```

Same concept as Gemini, but creates `claude.md`:

```markdown
# Project: Coffee Project

## Overview
[Claude analyzes your directory and creates context]

## Files
- best-coffee-method.md
- coffee-blog-outline.md

## Goals
[Project objectives]
```

### View Context Usage

```bash
> /context
```

**Shows detailed breakdown:**
```
Context Usage: 85,234 tokens (42% used)

Loaded Files:
- claude.md (1,234 tokens)
- best-coffee-method.md (2,456 tokens)
- coffee-blog-outline.md (890 tokens)

Conversation: 80,654 tokens
```

**Chuck's observation:**
> "With Claude, that doesn't really matter too much as long as you know how to use their most powerful feature: **agents**."

## 🚀 Agents: The Game-Changer

### What Are Agents?

**From the video:**
> "Claude was like, 'Cool, I've got a task, but it's not for me. I'm gonna delegate this task to one of my employees or coworkers.' This is another Claude instance... He's giving him a fresh set of instructions and get this: a **fresh context window**."

**Key concept:** Agents are separate Claude instances with:
- ✅ Fresh context window (200K tokens each)
- ✅ Specialized instructions
- ✅ Custom tool access
- ✅ Independent memory

### Create Your First Agent

**Video Timestamp:** 10:41-11:20

```bash
> /agents
```

**Menu appears:**
```
┌─ Agent Management ─────────────────────────┐
│ 1. Create new agent                        │
│ 2. View agents                             │
│ 3. Edit agent                              │
│ 4. Delete agent                            │
└────────────────────────────────────────────┘
```

#### Step-by-Step Agent Creation

**From Chuck's demo:**

1. **Select "Create new agent"**

2. **Choose scope:**
   ```
   📁 Project-specific agent (coffee-project)
   🌍 Personal agent (available everywhere)
   ```
   Chuck chooses: "Just this project"

3. **Describe the agent:**
   ```
   Name: homelab-guru
   Description: Expert in homelab hardware, networking, and infrastructure
   ```

4. **Configure:**
   ```
   Tools: [x] All tools
   Model: Sonnet 4.5
   Color: Auto
   ```

5. **Press Enter to save, ESC to exit**

**Agent created!** 🎉

### Using Agents

#### Deploy an Agent

**Chuck's example:**

```bash
> @homelab-guru
  Research document and create a buying guide.
  Make sure you reference the research we made in @nas-rec-folder
```

**What happens:**
1. Main Claude sees the task
2. Delegates to `homelab-guru` agent
3. Agent gets fresh 200K context window
4. Agent works independently
5. Returns results to main Claude

**Visual in terminal:**
```
┌─ Agent: homelab-guru ──────────────────────┐
│ 🔍 Researching NAS solutions...             │
│ 📊 Context: 15% used (30,000 tokens)       │
└────────────────────────────────────────────┘
```

#### Reference Files with @

```bash
# Reference specific files
> @homelab-guru create a summary of @nas-comparison.md

# Reference folders
> @homelab-guru review all documents in @research-folder
```

### Multiple Agents Simultaneously

**Video Timestamp:** 13:50-14:04

**Chuck's incredible demo:**

```bash
> Launch @homelab-guru to research the best proxmox servers.
  At the same time, use a general agent to find the best pizza place in Dallas.
  And another @homelab-guru to find the best graphics card for gaming.
  Put it all together in a comprehensive report.
```

**What happens:**
- 🤖 Agent 1: Proxmox server research
- 🍕 Agent 2: Pizza recommendations
- 🎮 Agent 3: Graphics card research
- 📊 Main Claude: Compiles all results

**Chuck's reaction:**
> "I feel so powerful right now. This is so fun!"

### Pre-Built Agents from the Video

#### 1. Homelab Guru
```bash
Agent: homelab-guru
Purpose: Network equipment, server recommendations, homelab setup
Tools: All
Model: Sonnet
```

#### 2. Brutal Critic
```bash
Agent: brutal-critic
Purpose: Ruthlessly review scripts/outlines against NetworkChuck framework
Personality: Intentionally harsh, framework-focused
Tools: Read, Web Search
Model: Sonnet
```

**Chuck's use case:**
> "I want it to be super mean. So that when it DID tell me I did a good job, I knew it was good."

#### 3. Gemini Research Agent
```bash
Agent: gemini-research
Purpose: Use Gemini CLI in headless mode for research tasks
Tools: Bash (to run gemini -p)
Model: Sonnet
```

**Chuck's example:**
```bash
> @gemini-research find the best AI terminal videos on YouTube
```

Agent runs:
```bash
gemini -p "find the top 10 AI terminal videos on YouTube"
```

## 🎨 Output Styles: Custom Personalities

**Video Timestamp:** 16:31-17:27

**Chuck's discovery:**
> "I'm embarrassed to say I just found this out while making this video."

### What Are Output Styles?

**System prompts** that control:
- How Claude responds
- Persona and tone
- Domain expertise
- Task-specific behaviors

### View Output Styles

```bash
> /output-style
```

**Default styles:**
```
📋 Available Output Styles:
- code (default) - Optimized for software development
- concise - Brief, to-the-point responses
- detailed - Comprehensive explanations
```

### Create Custom Output Style

**Chuck's demo:**

```bash
> /output-style new
```

**Prompt:**
```
Name: homelab-expert
Description: You are a homelab expert designed to help me create
the best homelab possible.
```

**More complex example (Chuck's actual script-writing style):**

```bash
Name: networkchuck-scriptwriter
Description:
You are an AI assistant specialized in writing NetworkChuck YouTube scripts.
You understand:
- Hook psychology and CTR optimization
- Viewer retention patterns
- NetworkChuck's energetic, coffee-fueled voice
- Educational entertainment balance
- The "you" voice (viewer as hero)

Always:
- Keep lines short and punchy
- Add coffee transitions between segments
- Use "Let's go!" at key moments
- Explain complex topics simply
- Add pattern breaks every 20-40 seconds
```

### Activate Output Style

```bash
> /output-style

# Select from list, or it activates on next launch
```

**Verify:**
```
Current Output Style: networkchuck-scriptwriter ✓
```

**Chuck's actual usage:**
> "I'm using the output style right now to make this video. This is what it looks like. It's pretty intense, optimized for what I do."

### Scope: Project vs Global

**Project-specific:**
- Lives in `.claude/output-styles/` in current project
- Only available in this project

**Global:**
- Lives in `~/.config/claude/output-styles/`
- Available in all projects

## 🎯 Planning Mode

**Video Timestamp:** 17:39-17:54

### Activate Planning Mode

Press **Shift+Tab** to toggle:

```
Mode: Normal  →  Shift+Tab  →  Mode: Planning
```

### How It Works

1. You give Claude a task
2. Claude creates a detailed plan
3. You review and approve
4. Claude executes the plan

**Example:**

```bash
> Refactor the authentication system to use JWT tokens
```

**Planning mode response:**
```
📋 Plan:
1. Review current authentication implementation
2. Install jsonwebtoken package
3. Create JWT utility functions
4. Update login endpoint
5. Add token verification middleware
6. Update protected routes
7. Add token refresh logic
8. Update tests

Approve this plan? (y/n/edit)
```

Type `y` to execute, or `edit` to modify.

**Chuck's take:**
> "This will put a very well thought-out plan together, and then you approve it. And then it just does it."

## 🎮 Advanced Features

### Resume Previous Session

**From the video:** "Yes, you can do that."

```bash
# Resume last session
claude -r

# Choose from recent sessions
```

### Dangerous Mode (Skip Permissions)

**Video Timestamp:** 14:36-14:52

```bash
# Launch without permission prompts
claude --dangerously-skip-permissions
```

⚠️ **Warning:** Claude will execute actions without asking

**Chuck's take:**
> "This is Claude without training wheels."

**Use when:**
- You trust your instructions completely
- You want maximum speed
- You're doing repetitive tasks

### Combine Flags

```bash
# Resume previous session + dangerous mode
claude -r --dangerously-skip-permissions
```

## Real-World Workflows

### 1. Outline Review with Brutal Critic

**Video Timestamp:** 12:56-13:05

```bash
# Working on a YouTube script
> @brutal-critic review my outline at @outline.md
```

**Agent launches with fresh context:**
- Reads outline.md
- Applies NetworkChuck framework
- Returns ruthless critique

**Chuck's result:** "8.2/10 - Not bad!"

### 2. Cross-Tool Research

**Video Timestamp:** 16:06-16:17

```bash
> Find the best AI terminal videos on YouTube.
  Use the @gemini-research agent.
```

**What happens:**
- Claude deploys gemini-research agent
- Agent runs: `gemini -p "search YouTube for AI terminal videos"`
- Gemini returns top 10 results
- Claude compiles into report

**Chuck's observation:**
> "We're having an AI use an AI right now!"

### 3. Context-Protected Reviews

**Video Timestamp:** 12:27-12:35

**Problem:** Your main conversation is 85K tokens deep with the outline

**Solution:** Deploy fresh agent with 200K tokens

```bash
> @brutal-critic review my current work
```

**Why this matters:**
- Main context: 85K tokens (cluttered with iterations)
- Agent context: 0K tokens (fresh eyes)
- No bias from previous conversation

**Chuck's take:**
> "I want a fresh cup of coffee. Ready to go. Fresh eyes."

## Tips from Chuck

### 1. Protect Your Context

> "I use agents all the time to **protect my context** and avoid any kind of weird bias."

**Strategy:** Delegate reviews, research, and analysis to agents

### 2. One Project = One Claude Session

```bash
# Terminal Tab 1: Video script
cd ~/video-project
claude

# Terminal Tab 2: Homelab docs
cd ~/homelab-project
claude
```

### 3. Name Agents by Function

**Good names:**
- `homelab-guru`
- `brutal-critic`
- `research-assistant`
- `code-reviewer`

**Bad names:**
- `agent1`
- `test`
- `bob`

### 4. Give Agents Specific Instructions

**Vague:**
```
You are helpful.
```

**Specific:**
```
You are a homelab expert specializing in enterprise NAS solutions.
When making recommendations:
- Consider budget constraints
- Explain technical trade-offs
- Provide specific product recommendations
- Include pricing and availability
```

## Agent Management

### List All Agents

```bash
> /agents
```

**View:**
- Project agents (local to current directory)
- Personal agents (available everywhere)

### Edit an Agent

```bash
> /agents
# Select "Edit agent"
# Choose agent
# Modify instructions
```

### Delete an Agent

```bash
> /agents
# Select "Delete agent"
# Confirm
```

## Hidden Features

### Paste Images

**From the video:**
> "You can paste images into your terminal."

```bash
# In Claude Code session
> Analyze this screenshot
[Paste image]
```

### Custom Hooks

**From the video mention:**
> "They have prompts, hooks, custom status lines."

Advanced: Create event-triggered actions

### Status Line Customization

Customize your terminal status bar with project info

## Troubleshooting

### "Not authorized" Error

Ensure you have:
1. Active Claude Pro subscription
2. Logged in correctly: `claude auth login`

### Agent Not Working

```bash
# Verify agent exists
> /agents

# Check agent configuration
> /agents
# Select "View agents"
```

### Context Not Loading

```bash
# Recreate context file
> /init
```

### Permission Denied on Files

```bash
# Relaunch with directory approval
claude
# Approve file access when prompted
```

## Pricing

**Requires:** Claude Pro ($20/mo)

**Includes:**
- Access to Claude Code terminal tool
- Use your existing web subscription
- No separate API key needed
- Unlimited-ish usage (fair use policy)

**Chuck's recommendation:**
> "If you already pay for Claude Pro, which starts at like 20 bucks a month, you can log into the terminal with this subscription and use it. So yeah, you don't have to use API keys."

## Comparison: Gemini vs Claude

| Feature | Gemini CLI | Claude Code |
|---------|------------|-------------|
| **Price** | Free | $20/mo |
| **Agents** | ❌ No | ✅ Yes |
| **Output Styles** | ❌ No | ✅ Yes |
| **Planning Mode** | ❌ No | ✅ Yes |
| **Context Window** | 200K | 200K (per agent!) |
| **Best For** | Getting started | Professional work |

**Chuck's verdict:**
> "Gemini's not even close to the best one."

## What's Next?

**Master these features:**
1. Create 2-3 specialized agents for your work
2. Design a custom output style
3. Practice delegating tasks to agents
4. Try planning mode on complex tasks

**Then explore:**
➡️ [Multi-Tool Workflow](08-multi-tool-workflow.md) - Use Claude + Gemini + Codex simultaneously

---

[← Back to Gemini CLI](03-gemini-cli.md) | [Next: Codex →](05-codex.md)
