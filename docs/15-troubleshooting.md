# Troubleshooting Guide

## Installation Issues

### "Command not found" after installation

**Problem:** Installed tool but terminal doesn't recognize command

**Solutions:**
```bash
# 1. Reload shell configuration
source ~/.bashrc     # for bash
source ~/.zshrc      # for zsh

# 2. Close and reopen terminal

# 3. Check if actually installed
which gemini
which claude
which opencode

# 4. Verify PATH includes npm global packages
echo $PATH | grep npm
```

### "Permission denied" during installation

**Problem:** npm permission errors

**Solutions:**
```bash
# Option 1: Use sudo (quick fix)
sudo npm install -g @google/generative-ai-cli

# Option 2: Fix npm permissions (proper fix)
sudo chown -R $USER /usr/local/lib/node_modules
sudo chown -R $USER /usr/local/bin
```

### "Node.js not found"

**Problem:** npm commands fail, Node.js not installed

**Solution:**
1. Install Node.js from [nodejs.org](https://nodejs.org/)
2. Choose LTS (Long Term Support) version
3. Restart terminal after installation

## Authentication Issues

### Can't login to Gemini CLI

**Solutions:**
```bash
# 1. Ensure browser opens for OAuth
# Check if browser is set as default

# 2. Try incognito/private browser window
# Sometimes cached auth causes issues

# 3. Clear Gemini config and retry
rm -rf ~/.config/gemini-cli
gemini
```

### Claude Code authentication fails

**Solutions:**
```bash
# 1. Verify Claude Pro subscription is active
# Check at claude.ai

# 2. Clear auth cache
rm -rf ~/.config/claude-code/auth

# 3. Re-authenticate
claude auth login
```

### opencode provider authentication issues

**Solutions:**
```bash
# 1. Check auth status
opencode auth whoami

# 2. Re-login
opencode auth login

# 3. For Claude Pro: ensure correct provider selected
# Select "Anthropic" not "OpenAI"

# 4. Check API key validity (if using API keys)
```

## Context File Issues

### Context file not loading automatically

**Solutions:**
```bash
# 1. Verify correct filename (case-sensitive!)
ls gemini.md     # ✓ Correct
ls Gemini.md     # ✗ Wrong
ls GEMINI.md     # ✗ Wrong

# 2. Ensure you're in the right directory
pwd
# Should show your project directory

# 3. Recreate context file
> /init

# 4. Check file isn't empty
cat gemini.md
```

### Multiple context files out of sync

**Problem:** Using Claude + Gemini + Codex, context files differ

**Solution:**
```bash
# Use one AI to sync all files
claude
> Read claude.md and copy its content exactly to gemini.md and agents.md

# Verify they match
diff claude.md gemini.md
diff claude.md agents.md
```

### Context seems stale/outdated

**Solutions:**
```bash
# 1. Exit and restart session (forces reload)
exit
gemini  # or claude/codex

# 2. Manually update context file
nano gemini.md
# Make your changes
# Save and exit
# Restart session

# 3. Ask AI to update context
> Update gemini.md to reflect our latest progress
```

## Agent Issues (Claude Code)

### Can't create agent

**Solutions:**
```bash
# 1. Verify you're in Claude Code (not Gemini/Codex)
# Agents only work in Claude Code

# 2. Ensure Claude Pro subscription is active

# 3. Try creating via menu
> /agents
# Select "Create new agent"
```

### Agent not responding

**Solutions:**
```bash
# 1. Check agent syntax
> @agent-name do task    # ✓ Correct
> agent-name do task     # ✗ Wrong (missing @)

# 2. Verify agent exists
> /agents
# Check list of available agents

# 3. Check agent has appropriate tools enabled
> /agents
# Select "Edit agent"
# Verify tools are enabled
```

### "Agent not found" error

**Solutions:**
```bash
# 1. Check agent scope
# Project agents only available in that project directory

# 2. Verify agent name (case-sensitive)
> @homelab-guru    # ✓ Correct
> @Homelab-Guru    # ✗ Wrong

# 3. Recreate agent if necessary
> /agents
# Delete and recreate
```

## File Operation Issues

### AI can't read my files

**Solutions:**
```bash
# 1. Verify file permissions
ls -la yourfile.md

# 2. Check you're in correct directory
pwd
ls

# 3. Use absolute path if needed
> Read /full/path/to/file.md

# 4. Check file isn't binary
file yourfile.md
# Should show: "ASCII text" or "UTF-8 text"
```

### AI can't write files

**Solutions:**
```bash
# 1. Check directory permissions
ls -la

# 2. Verify disk space
df -h .

# 3. Try different filename
> Create test.md with content "hello"

# 4. Check if file exists and is read-only
ls -la existing-file.md
chmod 644 existing-file.md  # Make writable
```

## Performance Issues

### AI responses are very slow

**Solutions:**
```bash
# 1. Check internet connection
ping 8.8.8.8

# 2. Try different model (for opencode)
> /model grok-fast-1
# Faster model for quick tasks

# 3. Reduce context size
# Start new session if context window is full

# 4. Close unused terminal sessions
# Multiple AI sessions can slow things down
```

### Terminal freezes/hangs

**Solutions:**
```bash
# 1. Try Ctrl+C to interrupt
# Press once, wait 2 seconds

# 2. Force quit if needed
# Ctrl+C twice rapidly

# 3. Kill process from another terminal
ps aux | grep gemini
kill -9 [PID]

# 4. Close and reopen terminal
```

## Multi-Tool Issues

### AIs giving conflicting information

**Expected behavior!** Different models have different strengths.

**Strategy:**
- Claude: Best for deep work
- Gemini: Best for current info
- Codex: Best for analysis

Cross-check important decisions across multiple AIs.

### File conflicts (multiple AIs editing same file)

**Prevention:**
```bash
# Assign clear responsibilities
# Claude: sections/1.md
# Gemini: research/1.md
# Never overlap!
```

**Solution if it happens:**
```bash
# 1. Check file with git diff
git diff file.md

# 2. Review changes manually
cat file.md

# 3. Use version control to restore
git checkout file.md
```

## Platform-Specific Issues

### Windows / WSL Issues

**Problem:** Commands not working in PowerShell

**Solution:** Use WSL (Windows Subsystem for Linux)
```powershell
# Install WSL
wsl --install

# Launch Ubuntu
wsl

# Install tools in WSL, not PowerShell
```

### macOS Issues

**Problem:** "Developer tools not installed"

**Solution:**
```bash
xcode-select --install
# Wait for installation
# Retry npm install
```

### Linux Issues

**Problem:** npm permissions complex

**Solution:**
```bash
# Use nvm (Node Version Manager) instead
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
source ~/.bashrc
nvm install --lts
nvm use --lts

# Now install tools
npm install -g @google/generative-ai-cli
```

## Still Having Issues?

### Check Official Documentation
- [Gemini CLI Docs](https://ai.google.dev/gemini-api/docs/cli)
- [Claude Code Docs](https://docs.anthropic.com/claude/docs/claude-code)
- [opencode GitHub](https://github.com/stackblitz-labs/opencode)

### Community Support
- NetworkChuck Discord
- GitHub Issues for opencode
- Tool-specific forums

### Nuclear Option: Complete Reinstall
```bash
# 1. Remove all tools
npm uninstall -g @google/generative-ai-cli
npm uninstall -g @anthropic-ai/claude-code
rm -rf ~/.config/gemini-cli
rm -rf ~/.config/claude-code
rm -rf ~/.config/opencode

# 2. Reinstall from scratch
npm install -g @google/generative-ai-cli
npm install -g @anthropic-ai/claude-code
curl -fsSL https://opencode.sh/install.sh | sh

# 3. Reload shell
source ~/.bashrc
```

---

[← Back to README](../README.md)
