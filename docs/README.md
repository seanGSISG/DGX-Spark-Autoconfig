# Linux Dev Autoconfig - Documentation

Quick reference for everything installed by this script.

## Documentation Index

| File | Description |
|------|-------------|
| [tools.md](tools.md) | All installed tools with descriptions and usage |
| [aliases.md](aliases.md) | Shell aliases for common commands |
| [commands.md](commands.md) | The `devenv` CLI and other utilities |
| [keybindings.md](keybindings.md) | Ghostty terminal and tmux keybindings |

## Quick Start After Installation

```bash
# Start a new shell (or restart terminal)
exec zsh

# Check what's installed
devenv info

# Connect to Tailscale VPN (first time setup)
sudo tailscale up

# Update tldr pages (first time)
tldr --update
```

## Directory Structure

```
~/.devenv/              # Main config directory
  zsh/
    devenv.zshrc        # Shell configuration (symlinked to ~/.zshrc)
    aliases.zsh         # All shell aliases
    p10k.zsh            # Powerlevel10k theme config
  tmux/
    tmux.conf           # Tmux configuration (symlinked to ~/.tmux.conf)
  scripts/lib/
    dgx.sh              # System utilities
  VERSION               # Installed version

~/.config/ghostty/      # Ghostty terminal config
~/.claude/              # Claude Code config
  hooks/
    git_safety_guard.py # Git safety hook (blocks dangerous commands)
```

## Getting Help

```bash
# Show system info
devenv info

# Check tool versions
devenv doctor

# Get quick command help
tldr <command>

# Example: tldr tar, tldr git-rebase
```

## Common Tasks

### VPS Access via Tailscale

```bash
# On VPS: Start Tailscale and get IP
sudo tailscale up
tailscale ip -4

# From any device on your tailnet:
ssh user@100.x.x.x    # Use Tailscale IP
mosh user@100.x.x.x   # Or use mosh for unstable connections
```

### Disk Usage

```bash
# Modern df replacement
duf

# Interactive disk usage analyzer
ncdu /path/to/check
```

### Session Management

```bash
# Start a tmux session (persists after disconnect)
tmux new -s work

# Detach: Ctrl+b, then d
# Reattach after reconnecting:
tmux attach -t work
```
