# Context Files Explained

**The Secret Weapon of Terminal AI**

Context files are THE feature that makes terminal AI 10x better than browser AI. This guide explains everything.

## The Browser Problem

**Chuck's frustration:**
> "You're in the browser. You're asking questions, research mode. You're diving deep into a project. Can't even see your scroll bar anymore. And this is your fifth chat because ChatGPT lost its context or its mind."

**What goes wrong:**
- 📜 Infinite scrolling (lose track of conversation)
- 🗂️ Multiple scattered chats (context split across 20 tabs)
- 📋 Copy/paste chaos (trying to save important parts)
- 🔄 Re-explaining context every new chat
- 💾 No way to "save" your project state

## The Terminal Solution: Context Files

### What Are Context Files?

**Simple answer:** Markdown files that tell AI what your project is about.

**Each tool has its own:**
- Gemini CLI: `gemini.md`
- Claude Code: `claude.md`
- Codex: `agents.md`

### The Magic

**Every time you launch the AI in a directory:**
1. Tool looks for its context file
2. Loads it automatically
3. Immediately understands your project
4. No re-explaining needed!

**Chuck's aha moment:**
> "It can access your Obsidian vault, all your notes, because those are just files sitting there on your hard drive."

## How Context Files Work

### Visual Representation

```
my-project/
├── gemini.md          ← Gemini reads this
├── claude.md          ← Claude reads this
├── agents.md          ← Codex reads this
├── project-files/
│   ├── research.md
│   ├── outline.md
│   └── draft.md
```

**When you launch:**
```bash
cd my-project
gemini

# Loading context from gemini.md... ✓
```

### Anatomy of a Context File

**Example `claude.md`:**

```markdown
# Project: Coffee Blog Series

## Overview
Creating a comprehensive blog series about coffee brewing methods,
targeted at home coffee enthusiasts.

## Current Phase
Research complete, writing first draft

## Key Files
- research/coffee-methods.md - Compiled research
- outlines/series-outline.md - 5-part series structure
- drafts/part-1.md - First draft (in progress)

## Decisions Made
- Focus on pour-over, French press, and espresso
- Avoid super technical chemistry details
- Include beginner-friendly equipment recommendations

## Next Steps
1. Complete part-1.md draft
2. Get feedback on tone/style
3. Create equipment recommendations list

## Reference Documents
- Brand guidelines in guidelines.md
- Target audience research in audience-profile.md
```

### What to Include

**✅ DO include:**
- Project overview
- Current phase/status
- Key files and their purpose
- Major decisions made
- Next steps
- Links to reference documents

**❌ DON'T include:**
- Full project content (just reference files)
- Conversation history (let AI build this naturally)
- Temporary notes (keep focused)

## Creating Context Files

### Method 1: Let AI Do It (Recommended)

**Gemini CLI:**
```bash
cd your-project
gemini
> /init
```

**Claude Code:**
```bash
cd your-project
claude
> /init
```

**What happens:**
1. AI scans your directory
2. Reads your files
3. Asks clarifying questions
4. Generates context file

**Chuck's approach:**
> "Let's take a look at it. And while we didn't do much in this project, it knows what's going on."

### Method 2: Manual Creation

```bash
# Create manually
nano gemini.md

# Or use your AI to help!
gemini
> Create a gemini.md file describing this project
```

## Using Context Files

### Fresh Session = Full Context

**The killer demo from the video:**

1. **First session:**
   ```bash
   gemini
   > Research coffee brewing methods and create a blog outline
   > /init
   ```

2. **Close and reopen (NEW session):**
   ```bash
   gemini
   # Context loaded automatically
   > Write the intro for blog post 1 in the coffee series
   ```

**Chuck's reaction:**
> "I didn't give it ANY context. It just knew. This is a new chat session."

### Updating Context

**As you work, update the file:**

```bash
> Update gemini.md to reflect:
  - Research phase complete
  - First draft started
  - Decision: Focus on pour-over method first
```

**Or update manually:**
```bash
nano gemini.md
# Edit and save
```

**Next session automatically loads the updates!**

## Real-World Example: Chuck's Video Project

**Video Timestamp:** 5:48-6:09

### The Setup

```bash
cd ~/Projects/531-ai-terminal
ls
```

**Files present:**
```
gemini.md
claude.md
agents.md
531-script.md
research/
  ├── claude-code-research.md
  ├── gemini-cli-research.md
  └── opencode-research.md
```

### The Workflow

**Chuck opens a fresh Gemini session:**

```bash
gemini

# Loads gemini.md automatically
```

**Asks with ZERO additional context:**
```bash
> Where are we at in the project?
```

**Gemini responds:**
```
Based on your project files:

Current Status: Script writing phase (100% complete)
- All segments finished (307 lines, ~17 min runtime)
- Hook finalized
- Ready for filming

Key Files:
- 531-script.md (complete script)
- research/ folder (comprehensive research on all tools)
- session-summary.md (session history)

Next Steps:
- Optional script polish
- OR proceed to filming
```

**Chuck's amazement:**
> "Are you seeing this? This has completely changed the way I create or do anything now."

## Multi-Tool Context Syncing

**Video Timestamp:** 18:28-18:40

### The Challenge

You want to use:
- ✅ Gemini CLI
- ✅ Claude Code
- ✅ Codex

All on the SAME project... how do you keep context in sync?

### Chuck's Solution

**Two-step process:**

#### Step 1: Same Directory

```bash
# All tools launched from same directory
cd my-project

# Terminal Tab 1
gemini

# Terminal Tab 2
claude

# Terminal Tab 3
codex
```

#### Step 2: Sync Context Files

**Make sure these files say the same thing:**
- `gemini.md`
- `claude.md`
- `agents.md`

**Chuck's method:**
```bash
# Use one AI to sync the others
claude

> Read claude.md and update both gemini.md and agents.md
  to match, ensuring all three context files are synchronized
```

**Result:**
```
my-project/
├── gemini.md    ← Same content
├── claude.md    ← Same content
├── agents.md    ← Same content
```

### Why This Works

**From Chuck:**
> "Everything I'm doing, talking with these three different AIs on a project... It's not tied in a browser. It's not tied in a GUI. It's just this folder right here on my hard drive."

**Each AI:**
- Reads its own context file
- Sees the same project state
- Works on the same files
- No copy/paste between tools!

## Advanced Context Strategies

### 1. Layered Context

**Structure:**
```
project/
├── claude.md              ← Main context
├── docs/
│   ├── framework.md       ← Reference in claude.md
│   ├── brand-guide.md     ← Reference in claude.md
│   └── audience.md        ← Reference in claude.md
```

**In claude.md:**
```markdown
## Reference Documents
For detailed guidelines, see:
- docs/framework.md - Scriptwriting framework
- docs/brand-guide.md - Brand voice guidelines
- docs/audience.md - Target audience research
```

**AI reads main context, pulls in references as needed.**

### 2. Session Summaries

**Chuck uses an agent for this (from video):**

```bash
> @script-session-closer run

# Agent does:
# 1. Summarizes current session
# 2. Updates context files (all three!)
# 3. Updates session-summary.md
# 4. Commits to git
```

**Result:** Next session picks up EXACTLY where you left off.

### 3. Multiple Projects

**Keep them separate:**

```bash
~/coffee-project/
  ├── gemini.md      ← Coffee project context

~/video-script/
  ├── gemini.md      ← Video project context

~/homelab-docs/
  ├── gemini.md      ← Homelab context
```

**No cross-contamination!**

### 4. Decision Log

**Track major decisions in context:**

```markdown
## Decision Log

### 2025-10-15: Brew Method Selection
**Decision:** Focus on pour-over primarily
**Reasoning:** Most beginner-friendly, popular, equipment accessible
**Impact:** Affects equipment recommendations and tutorial structure

### 2025-10-20: Series Length
**Decision:** 5 parts instead of 3
**Reasoning:** Too much content to compress, better to go deep
**Impact:** Updated outline, adjusted timeline
```

## Context File Best Practices

### ✅ DO

1. **Update regularly** - After major work sessions
2. **Be concise** - Don't dump entire project
3. **Reference files** - Don't duplicate content
4. **Track decisions** - Why you chose something matters
5. **Sync across tools** - If using multiple AIs
6. **Version control** - Commit to git

### ❌ DON'T

1. **Include sensitive data** - Context files are readable
2. **Copy/paste everything** - Reference instead
3. **Let it get stale** - Update as project evolves
4. **Over-explain** - AI is smart, be concise
5. **Forget to sync** - When using multiple tools

## Context vs Conversation

### Understanding the Difference

**Context Window:**
- Current conversation messages
- Loaded files
- Context file content
- **Limited size** (200K tokens)

**Context File:**
- Project knowledge
- Persistent across sessions
- **Unlimited size** (within reason)
- Your project's "memory"

### Example

**Session 1 (85K tokens used):**
```
Conversation: 80K tokens
Context file: 2K tokens
Loaded files: 3K tokens
```

**Session 2 (NEW session, 2K tokens used):**
```
Conversation: 0K tokens (fresh start!)
Context file: 2K tokens (loaded automatically)
Loaded files: 0K tokens (not loaded yet)
```

**The magic:** Context file gives you project knowledge WITHOUT burning conversation tokens.

## The "It's Just a Folder" Philosophy

**Chuck's most important point:**
> "I can copy and paste that folder anywhere. All the work, all the decisions, all the context - it's mine."

### What This Means

**Your project = A folder containing:**
- Context files
- Work products
- Reference documents
- Research
- Drafts

**No vendor lock-in:**
- ✅ Works with any AI tool (that supports context files)
- ✅ Stored locally (you own it)
- ✅ Portable (copy to any machine)
- ✅ Version controlled (use git)

**Chuck's freedom:**
> "If a new, greater, better AI comes out, I'm ready for it because all my stuff is right here on my hard drive."

## Troubleshooting

### Context File Not Loading

```bash
# Check you're in right directory
pwd
ls *.md

# Verify filename (case-sensitive)
ls gemini.md    # ✓ Correct
ls Gemini.md    # ✗ Wrong
ls GEMINI.md    # ✗ Wrong

# Recreate if needed
> /init
```

### Context Seems Outdated

```bash
# AI might be caching old version
> Reload gemini.md and re-read the project

# Or restart session
exit
gemini
```

### Multiple Context Files Conflicting

**When using multiple AIs, ensure synced:**

```bash
# Use one AI to sync
claude
> Read claude.md and make gemini.md and agents.md identical
```

### Too Much Context

**If context file gets huge (>5K words):**

1. **Move details to separate docs**
2. **Reference them in main context**
3. **Keep main context concise**

## Summary: Why Context Files Win

| Browser AI | Terminal AI + Context Files |
|------------|----------------------------|
| 📜 Infinite scroll hell | 📁 Clean context file |
| 🔄 Re-explain every session | ✅ Auto-loads on launch |
| 🗂️ 20 scattered chats | 📋 One project folder |
| 📋 Copy/paste nightmare | 🔗 Direct file access |
| 🏢 Vendor lock-in | 🆓 You own everything |

**Chuck's verdict:**
> "I own my context. Nothing annoys me more than when ChatGPT tries to fence me in, give me vendor lock-in. No, I reject that."

## What's Next?

**Now that you understand context files:**

➡️ [Multi-Tool Workflow](08-multi-tool-workflow.md) - Use context files across multiple AIs

➡️ [Productivity Workflows](11-productivity-workflows.md) - Real examples using context files

---

[← Back to Claude Code](04-claude-code.md) | [Next: Multi-Tool Workflow →](08-multi-tool-workflow.md)
