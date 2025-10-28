# Prerequisites

Before diving into AI terminal tools, let's make sure you have everything you need.

## Required

### 1. Terminal Access

You need a terminal/command line:

- **macOS**: Built-in Terminal app (Cmd+Space, type "Terminal")
- **Linux**: Any terminal emulator (usually Ctrl+Alt+T)
- **Windows**:
  - Windows Subsystem for Linux (WSL) - **Recommended**
  - PowerShell
  - Git Bash

#### Why WSL for Windows?
Chuck uses WSL (Ubuntu) in the video. It provides a Linux environment on Windows, which most terminal tools are optimized for.

**Install WSL:** [Chuck's WSL video](https://www.youtube.com/watch?v=[WSL_VIDEO_ID])

```powershell
# In PowerShell (Admin)
wsl --install
```

### 2. Node.js & npm

Most terminal AI tools are installed via npm (Node Package Manager).

**Check if you have it:**
```bash
node --version
npm --version
```

**Don't have it?** Install from [nodejs.org](https://nodejs.org/) (LTS version recommended)

### 3. A Google Account (for Gemini CLI)

- Any free Gmail account works
- No Google One AI Premium required for basic usage

### 4. AI Subscriptions (Optional but Recommended)

| Tool | Free Option | Paid Option | Chuck's Take |
|------|-------------|-------------|--------------|
| Gemini CLI | ✅ Generous free tier | Google One AI Premium $20/mo | "Start here - it's FREE" |
| Claude Code | ❌ Requires Claude Pro | Claude Pro $20/mo | "This is my daily driver - worth it" |
| Codex | Limited free | ChatGPT Plus $20/mo | "Good for analysis" |
| opencode | ✅ Grok free / Local models | Various providers | "Great for experimentation" |

**Chuck's Recommendation:**
> "If you can only pay for one AI subscription, Claude Pro is the one I would choose."

## Recommended

### 5. Git (Optional but Useful)

Chuck treats his projects like code - version control for everything.

**Check if installed:**
```bash
git --version
```

**Install:**
- macOS: `xcode-select --install`
- Linux: `sudo apt install git` (Ubuntu/Debian)
- Windows: [git-scm.com](https://git-scm.com/)

### 6. Text Editor

You'll be editing context files. Any text editor works:
- **Terminal-based**: nano (easiest), vim, emacs
- **GUI**: VS Code, Sublime Text, Notepad++

### 7. Basic Terminal Skills

You should be comfortable with:
- Navigating directories (`cd`, `ls`/`dir`)
- Creating directories (`mkdir`)
- Basic file operations (`cat`, `nano`)
- Understanding file paths

**New to terminal?** Don't worry - Chuck walks through everything in the video!

## System Requirements

### Minimum
- **RAM**: 4GB (8GB recommended)
- **Storage**: 1GB free space
- **Internet**: Required for cloud AI models
- **OS**: macOS 10.15+, Ubuntu 20.04+, Windows 10+ (with WSL)

### Recommended for Local Models (opencode)
- **RAM**: 16GB+
- **Storage**: 10GB+ (for model files)
- **Ollama installed** (for local models)

## Permissions & Security

### What These Tools Can Access

⚠️ **Important Security Note:**

Terminal AI tools can:
- ✅ Read files in directories you open them in
- ✅ Write files to your system
- ✅ Execute bash commands
- ✅ Access your Obsidian vault (or any files)
- ✅ Run Python/bash scripts

This is POWERFUL but requires responsibility.

### Chuck's Security Tips

1. **Start in a test directory** - Don't open AI tools in your root or home directory initially
2. **Review file permissions** - Claude Code asks permission by default (good!)
3. **Use `--dangerously-skip-permissions` carefully** - Only when you trust what you're doing
4. **Secure your remote access** - If using AI on remote servers, use zero-trust tools like TwinGate

### Dangerous Mode Flag

Many tools have a "skip permissions" mode:

```bash
# Claude Code without safety checks
claude --dangerously-skip-permissions

# Use this ONLY when you know what you're doing
# Chuck uses it for speed in the video
```

## Quick Environment Check

Run this to verify you're ready:

```bash
# Check terminal
echo "Terminal works!"

# Check Node.js
node --version && npm --version

# Check available space
df -h .

# Create test directory
mkdir -p ~/ai-terminal-test
cd ~/ai-terminal-test
echo "Setup complete! Ready to install tools."
```

## What's Next?

✅ Prerequisites complete? → [Quick Start Guide](02-quickstart.md)

❓ Having issues? → [Troubleshooting](15-troubleshooting.md)

---

[← Back to README](../README.md) | [Next: Quick Start →](02-quickstart.md)
