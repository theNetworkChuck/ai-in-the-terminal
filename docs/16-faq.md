# Frequently Asked Questions

## Getting Started

### Which tool should I start with?
**Start with Gemini CLI** if you want free access. It's generous and perfect for learning the concepts.

**Upgrade to Claude Code** if you need agents and are serious about terminal AI workflows.

### Do I need all three tools?
No! Chuck uses all three because they have different strengths:
- **Gemini**: Research and web search
- **Claude**: Deep work and agents  
- **Codex**: High-level analysis

Start with one, add others as needed.

### Is this just for developers?
**Absolutely not!** Chuck uses these tools for YouTube video scriptwriting. They work for:
- Writing and content creation
- Research and analysis
- Project planning
- Documentation
- Any text-based work

Coding is just ONE use case.

## Cost & Subscriptions

### How much does this cost?
- **Gemini CLI**: FREE (generous limits)
- **Claude Code**: $20/mo (Claude Pro required)
- **Codex**: $20/mo (ChatGPT Plus) or pay-per-use API
- **opencode**: FREE (Grok), or use existing subscriptions

### Can I use existing AI subscriptions?
**Yes!** 
- Have Claude Pro? Use it with Claude Code
- Have ChatGPT Plus? Use it with Codex
- Have Claude Pro? Use it with opencode too!

### Which subscription is most worth it?
**Chuck's recommendation:** Claude Pro ($20/mo)
- Access to Claude Code (terminal)
- Access to Claude web
- Works with opencode
- Agents feature is game-changing

## Technical Questions

### What's a context file?
A markdown file (gemini.md, claude.md, agents.md) that tells the AI what your project is about. It loads automatically every session so you never re-explain your work.

### Why do I need different context files?
Each AI tool looks for its own:
- Gemini CLI → gemini.md
- Claude Code → claude.md
- Codex/opencode → agents.md

Keep them synced when using multiple tools!

### What's an agent?
(Claude Code feature) A separate AI instance with:
- Specialized instructions
- Fresh context window
- Custom tool access
- Independent from main conversation

Think: delegating tasks to specialized coworkers.

### Can AI access all my files?
Only files in the directory where you launch it. 

**Safety tip:** Start AI tools in project directories, not your home folder!

## Workflow Questions

### How do I use multiple AI tools together?
1. Launch all tools in the same directory
2. Sync context files (claude.md = gemini.md = agents.md)
3. Each AI can read/write the same files
4. No copy/paste needed!

### How do I avoid losing my work?
Use git! Chuck commits his projects regularly:
```bash
git init
git add .
git commit -m "Session summary"
```

Everything is local files, perfect for version control.

### Can I access my Obsidian vault?
**Yes!** Just launch the AI in your vault directory:
```bash
cd ~/Obsidian/MyVault
gemini
```

AI can read all your notes (they're markdown files).

## Troubleshooting

### "Command not found"
```bash
# Reload shell
source ~/.bashrc

# Or close and reopen terminal
```

### "Permission denied" 
```bash
# Use sudo
sudo npm install -g [package-name]
```

### Context file not loading
```bash
# Verify you're in right directory
pwd
ls gemini.md

# Recreate
> /init
```

## Comparison Questions

### Browser AI vs Terminal AI?
**Browser AI:**
- Lost context after scrolling
- Scattered across multiple chats
- Copy/paste nightmare
- Vendor lock-in

**Terminal AI:**
- Persistent context files
- One project folder
- Direct file access
- You own everything

### Which AI is "best"?
Depends on the task:
- **Claude**: Best for writing, deep work, agents
- **Gemini**: Best for web research, current info
- **ChatGPT**: Best for high-level analysis
- **opencode**: Best for flexibility, local models

Chuck uses all three for different strengths.

## Philosophy Questions

### Why does Chuck care about owning his context?
**Vendor lock-in avoidance.** Browser AI traps your work in their platform.

With terminal AI:
- Everything is local files
- Copy folder anywhere
- Switch AI tools anytime
- Full control

### What's the "It's just a folder" philosophy?
Your project = one folder containing:
- Context files
- Work products
- Research
- Everything

Portable, version-controlled, tool-agnostic. **You own it.**

## Need More Help?

→ [Troubleshooting Guide](15-troubleshooting.md)

→ [Command Cheat Sheet](14-cheat-sheet.md)

---

[← Back to README](../README.md)
