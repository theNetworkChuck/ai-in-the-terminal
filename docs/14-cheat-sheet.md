# Command Cheat Sheet

Quick reference for all AI terminal tools covered in the video.

## Installation Commands

### Gemini CLI
```bash
# Linux/macOS/WSL (npm)
npm install -g @google/gemini-cli

# With sudo (if permission error)
sudo npm install -g @google/gemini-cli

# macOS (Homebrew)
brew install gemini-cli
```

### Claude Code
```bash
# All platforms (npm)
npm install -g @anthropic-ai/claude-code

# With sudo
sudo npm install -g @anthropic-ai/claude-code
```

### Codex (ChatGPT CLI)
```bash
# Installation command
npm install -g @openai/codex

# Or follow OpenAI documentation
```

### opencode
```bash
# Installation (one command - from video)
curl -fsSL https://opencode.sh/install.sh | sh

# Reload shell
source ~/.bashrc
# or
source ~/.zshrc
```

## Launch Commands

### Basic Launch
```bash
gemini              # Launch Gemini CLI
claude              # Launch Claude Code
codex               # Launch Codex
opencode            # Launch opencode
```

### Launch with Flags
```bash
# Claude Code
claude -r                               # Resume previous session
claude --dangerously-skip-permissions   # Skip safety prompts
claude -r --dangerously-skip-permissions  # Both flags combined

# Gemini CLI
gemini -p "your prompt here"           # Headless mode (one-shot)

# opencode
opencode --model claude-sonnet-4       # Specify model
```

## In-Session Commands

### Gemini CLI
```bash
/init               # Create gemini.md context file
/tools              # Show available tools
/help               # Show help
exit                # Exit Gemini (or Ctrl+C)
```

### Claude Code
```bash
/init               # Create claude.md context file
/context            # Show context usage details
/agents             # Agent management menu
/output-style       # Output style management
exit                # Exit Claude (or Ctrl+C)
```

**Keyboard shortcuts:**
```bash
Tab                 # Toggle thinking mode
Shift+Tab           # Toggle planning mode
Ctrl+C              # Interrupt/exit
Ctrl+O              # View agent details (when agent running)
```

### opencode
```bash
/model              # Change AI model
/share              # Share current session
/timeline           # View session timeline
/sessions           # View all sessions
exit                # Exit opencode
```

## Project Setup

### Create New Project
```bash
# Standard workflow
mkdir my-project
cd my-project

# Launch AI and create context
gemini
> /init

# Verify context file created
ls *.md
```

### Multi-Tool Project Setup
```bash
# Create project
mkdir my-project
cd my-project

# Initialize all three context files
# Terminal 1
gemini
> /init

# Terminal 2
claude
> /init

# Terminal 3
codex
> /init

# Sync context files
claude
> Sync claude.md to gemini.md and agents.md
```

## Context File Management

### Create Context Files
```bash
# Let AI create it
> /init

# Manual creation
nano gemini.md      # Edit manually
nano claude.md
nano agents.md
```

### Update Context
```bash
# Ask AI to update
> Update gemini.md with: [your updates]

# Manual edit
nano gemini.md
```

### Sync Context Files
```bash
# Use Claude to sync
claude
> Read claude.md and make gemini.md and agents.md identical
```

### View Context
```bash
# View file contents
cat gemini.md
cat claude.md
cat agents.md

# In Claude, check context usage
> /context
```

## Agent Commands (Claude Code)

### Agent Management
```bash
> /agents                      # Open agent menu
> /agents                      # Then: "Create new agent"
> /agents                      # Then: "View agents"
> /agents                      # Then: "Edit agent"
> /agents                      # Then: "Delete agent"
```

### Deploy Agents
```bash
> @agent-name do a task
> @homelab-guru research NAS options
> @brutal-critic review my script
```

### Multi-Agent Tasks
```bash
> @agent1 do task A, @agent2 do task B, and compile results
```

## Output Styles (Claude Code)

### Manage Output Styles
```bash
> /output-style                # View available styles
> /output-style new            # Create new style
> /output-style                # Select active style
```

### Create Output Style
```bash
> /output-style new

# Then describe the style:
Name: my-expert
Description: You are an expert in [domain]...
```

## File Operations

### Create Files
```bash
# Ask AI to create
> Create a file named project-plan.md with [content]

# Manual creation
nano project-plan.md
```

### Read Files
```bash
# AI reads files automatically when mentioned
> Read project-plan.md and summarize

# Reference with @
> Review @project-plan.md
```

### Update Files
```bash
# AI updates
> Update project-plan.md to add [new section]

# Manual edit
nano project-plan.md
```

### List Files
```bash
# Terminal command
ls
ls -la

# AI command
> What files are in this directory?
> Show me all markdown files
```

## Git Integration

### Initialize Repository
```bash
git init
git add .
git commit -m "Initial commit"
```

### Regular Commits
```bash
# After work session
git add .
git commit -m "Session summary: [what you did]"
git push
```

### Chuck's Automated Approach
```bash
# Using session-closer agent
> @script-session-closer run

# Agent automatically:
# - Summarizes session
# - Updates context files
# - Commits to git
```

## Multi-Terminal Workflows

### Open Multiple Terminals
```bash
# Terminal 1: Claude
cd ~/my-project
claude

# Terminal 2: Gemini
cd ~/my-project
gemini

# Terminal 3: Codex
cd ~/my-project
codex
```

### tmux (Advanced)
```bash
# Start tmux session
tmux new -s ai-work

# Create windows
Ctrl+B, C           # New window
Ctrl+B, [0-9]       # Switch to window N
Ctrl+B, "           # Split horizontal
Ctrl+B, %           # Split vertical
```

## opencode Specific Commands

### Model Management
```bash
# View available models
> /model

# Switch to specific model
> /model claude-sonnet-4
> /model grok-fast
> /model llama-3.2
```

### Configuration
```bash
# Edit config file
nano ~/.config/opencode/opencode.jsonc

# Example config for local model
{
  "model": "llama-3.2"
}
```

### Authentication
```bash
# Login with Claude Pro
opencode auth login
# Select "Anthropic"
# Paste auth code from browser

# Verify login
opencode auth whoami
```

### Session Management
```bash
> /sessions         # View all sessions
> /timeline         # View current session timeline
> /share            # Generate shareable link
```

## Advanced Techniques

### Headless Mode
```bash
# Gemini one-shot command
gemini -p "Research ZFS performance and save to report.md"

# Claude with pipe
echo "Analyze this file" | claude

# Chain commands
gemini -p "Research topic" && claude -r
```

### Agent as Tool
```bash
# Claude agent using Gemini
> @gemini-research search for latest Docker security updates

# Agent runs:
gemini -p "search for latest Docker security updates"
```

### Obsidian Integration
```bash
# Navigate to vault
cd ~/Obsidian/MyVault

# Launch AI
gemini

# Work with notes
> Read my daily note and summarize tasks
> Create a new note about [topic] with backlinks
```

## Troubleshooting Commands

### Permission Issues
```bash
# Reinstall with sudo
sudo npm install -g @google/gemini-cli

# Fix permissions
sudo chown -R $USER /usr/local/lib/node_modules
```

### Command Not Found
```bash
# Reload shell
source ~/.bashrc
source ~/.zshrc

# Verify installation
which gemini
which claude
which opencode

# Check PATH
echo $PATH
```

### Context File Issues
```bash
# Verify file exists
ls *.md

# Check file contents
cat gemini.md

# Recreate if needed
> /init
```

### Clear Cache/Reset
```bash
# Claude Code
rm -rf ~/.config/claude-code

# Gemini CLI
rm -rf ~/.config/gemini-cli

# opencode
rm -rf ~/.config/opencode
```

## Common Workflows

### Research & Write
```bash
# Step 1: Research (Gemini)
gemini
> Research [topic] and compile findings

# Step 2: Write (Claude)
claude
> Read research.md and write comprehensive blog post

# Step 3: Review (Codex)
codex
> Review blog-post.md for accuracy and clarity
```

### Project Kickoff
```bash
# Create project
mkdir project-name
cd project-name

# Initialize
gemini
> /init
> Help me plan this project: [description]

# Track with git
git init
git add .
git commit -m "Project initialized"
```

### Daily Work Session
```bash
# Start
cd ~/current-project
claude

# Check status
> Where are we in the project?

# Work
> [Your tasks]

# End session
> @script-session-closer run
# Or manually:
git add .
git commit -m "Session: [summary]"
```

## Quick Tips

### Keyboard Shortcuts
```bash
Ctrl+C              # Interrupt AI / Exit
Ctrl+D              # Exit (alternative)
Tab                 # Toggle thinking (Claude)
Shift+Tab           # Toggle planning (Claude)
Ctrl+O              # Check agent status (Claude)
```

### Speed Tips
```bash
# Use dangerous mode (when safe)
claude --dangerously-skip-permissions

# Use headless for quick tasks
gemini -p "quick question"

# Deploy agents for parallel work
> @agent1 task A, @agent2 task B
```

### Organization Tips
```bash
# One directory per project
~/projects/project-a/
~/projects/project-b/

# Consistent context file naming
gemini.md, claude.md, agents.md

# Use git for everything
git commit regularly
```

## Emergency Commands

### Kill Stuck Process
```bash
# Find process ID
ps aux | grep gemini
ps aux | grep claude

# Kill it
kill -9 [PID]

# Or use Ctrl+C twice rapidly
```

### Reset Everything
```bash
# Remove config directories
rm -rf ~/.config/gemini-cli
rm -rf ~/.config/claude-code
rm -rf ~/.config/opencode

# Reinstall
npm install -g @google/gemini-cli
npm install -g @anthropic-ai/claude-code
curl -fsSL https://opencode.sh/install.sh | sh
```

## Official Documentation Links

```bash
# Gemini CLI
https://ai.google.dev/gemini-api/docs/cli

# Claude Code
https://docs.anthropic.com/claude/docs/claude-code

# opencode
https://github.com/stackblitz-labs/opencode

# Codex
https://platform.openai.com/docs/tools/codex
```

---

**Print this page for quick reference!**

[← Back to README](../README.md)
