# Codex (ChatGPT CLI) Guide

**Video mentions:** 18:07-18:28, 18:54-19:13

Codex is OpenAI's terminal tool that brings ChatGPT to the command line.

## Overview

**Chuck's usage:**
> "I find ChatGPT is very good at analyzing things from a high view. Gemini and Claude are very good at the work, the deep work."

**Best for:**
- High-level analysis
- Strategic thinking
- Quality review
- Different perspective from Claude/Gemini

## Installation

```bash
npm install -g @openai/codex

# Or follow official OpenAI documentation
```

## Basic Usage

### Launch

```bash
cd your-project
codex
```

### Context File

Uses **agents.md** (same as opencode)

```bash
> /init
```

Creates `agents.md` in your project directory.

## Chuck's Workflow

**In multi-tool setup:**

```bash
# Terminal 1: Claude (writing)
claude
> Write a hook for this video, authority angle

# Terminal 2: Gemini (research)
gemini
> Write a hook on discovery angle

# Terminal 3: Codex (review)
codex
> Review both hooks and compare their strengths
```

**Chuck's observation:**
> "They're all using the same context, different roles."

## Role in Multi-Tool Workflow

### When to Use Codex

**✅ Use Codex for:**
- Reviewing Claude's output
- High-level strategy
- Comparing approaches
- Ensuring clarity
- Catching issues Claude/Gemini miss

**❌ Don't use Codex for:**
- Deep technical writing (Claude better)
- Current web research (Gemini better)
- Long-form content creation

### Typical Workflow

```bash
# 1. Claude creates
claude
> Write a technical blog post about ZFS

# 2. Gemini researches
gemini
> Verify technical accuracy and find recent benchmarks

# 3. Codex reviews
codex
> Review the blog post at blog.md
  Check: clarity, flow, technical accuracy, audience fit
```

## Context File Syncing

**Important:** Codex uses `agents.md`

**Sync with other tools:**

```bash
# In Claude terminal
claude
> Sync claude.md content to gemini.md and agents.md
```

**Now all three tools share context!**

## Pricing

**Requires:** ChatGPT Plus ($20/mo) or API key

- ChatGPT Plus: Use existing subscription
- API key: Pay per token usage

## Comparison

| Feature | Codex | Claude Code | Gemini CLI |
|---------|-------|-------------|------------|
| **Strength** | Analysis | Deep work | Research |
| **Context File** | agents.md | claude.md | gemini.md |
| **Cost** | $20/mo | $20/mo | Free |
| **Best For** | Review | Creating | Research |

## Tips from Chuck

### 1. Use for High-Level Analysis

> "ChatGPT is very good at analyzing things from a high view."

**Good prompts:**
```bash
> Review this architecture and identify weaknesses
> Is this explanation clear for beginners?
> Compare these two approaches strategically
```

### 2. Last Step in Pipeline

```
Claude writes → Gemini verifies → Codex reviews
```

### 3. Different Perspective

When Claude and Gemini agree, ask Codex for a third opinion:

```bash
> Claude and Gemini both recommend approach A.
  What do you think? Any risks we're missing?
```

## Official Documentation

[OpenAI Codex Documentation](https://platform.openai.com/docs/tools/codex)

## What's Next?

**Understand multi-tool workflows:**

➡️ [Multi-Tool Workflow Guide](08-multi-tool-workflow.md)

➡️ [Context Files Explained](07-context-files.md)

---

[← Back to Claude Code](04-claude-code.md) | [Next: opencode →](06-opencode.md)
