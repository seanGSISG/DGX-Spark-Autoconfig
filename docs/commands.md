# Commands & Utilities

## devenv CLI

The `devenv` command provides utilities for managing your development environment.

### Usage

```bash
devenv <command>
```

### Commands

| Command | Description |
|---------|-------------|
| `devenv info` | Show system information (hostname, GPU, tools) |
| `devenv doctor` | Check system health and tool status |
| `devenv update` | Update installed tools |
| `devenv version` | Show installed version |
| `devenv help` | Show help message |

### Examples

```bash
# Quick system overview
$ devenv info
Linux Dev Autoconfig Environment
=================================
Hostname: my-vps
User: admin
Shell: /usr/bin/zsh
Arch: x86_64

CUDA: not found
GPU: not found

Python: Python 3.12.0
UV: uv 0.5.14
Claude: 1.0.0
Codex: 0.1.0

# Check version
$ devenv version
1.0.0
```

## Common Tool Commands

### Disk Usage

```bash
# Modern df (shows all mounts nicely)
duf
df                      # Aliased to duf

# Interactive disk analyzer
ncdu /home              # Analyze /home
du /var                 # Aliased to ncdu
# Navigate with arrows, 'd' to delete, 'q' to quit
```

### File Operations

```bash
# List files (with icons)
ls                      # Icons + names
ll                      # Long format
la                      # All files
tree                    # Tree view

# Find files
fd "pattern"            # Find by name
fd -e py                # Find by extension
fd -H "pattern"         # Include hidden

# Search file contents
rg "pattern"            # Search in files
rg "pattern" -t py      # Only Python files
rg "TODO"               # Find all TODOs
```

### Process Management

```bash
# Resource monitor
btop                    # Interactive (mouse supported)
top                     # Aliased to btop

# Quick process check
ps aux | rg python      # Find python processes
```

### Git Operations

```bash
# Quick status check
gs                      # git status
gd                      # git diff
glog                    # Pretty log

# Lazygit TUI
lg                      # Opens lazygit
# Space to stage, c to commit, P to push
```

## VPS / Remote Access

### Tailscale

```bash
# Connect to your tailnet
tsup                    # sudo tailscale up

# Check status
ts                      # Shows all devices

# Get your IP
tsip                    # Your Tailscale IP

# Disconnect
tsdown                  # sudo tailscale down
```

### SSH with Mosh

```bash
# Regular SSH (drops on network change)
ssh user@host

# Mosh (survives disconnects)
mosh user@host

# Mosh without host key check
mssh user@host
```

### Tmux Sessions

```bash
# New session
tmux new -s work        # Named session

# Detach (inside tmux)
Ctrl+b, then d

# List sessions
tmux ls

# Reattach
tmux attach -t work
tmux a -t work          # Short form

# Kill session
tmux kill-session -t work
```

## Development

### Python with UV

```bash
# Create virtual environment
uv venv

# Activate
source .venv/bin/activate

# Install packages (super fast)
uv pip install requests pandas numpy
uv pip install -r requirements.txt

# Run scripts
uv run python script.py
```

### JavaScript with Bun

```bash
# Install dependencies
bun install

# Run dev server
bun run dev
br                      # Alias

# Run scripts
bun run build
bun run test
```

### Quick Help

```bash
# Get simplified man pages
help tar                # tldr tar
help git-stash
help docker

# Update tldr database
tldr --update
```

## AI Assistants

### Claude Code

```bash
# Normal mode (asks for permission)
claude

# Dangerous mode (autonomous)
ccd
```

### Codex CLI

```bash
# Normal mode
codex

# Dangerous mode
cod
```

### Update All Agents

```bash
uca                     # Updates Claude + Codex
```

## System Administration

### Package Management

```bash
# Full system update
update                  # apt update + upgrade + autoremove

# Install package
install nginx           # sudo apt install nginx

# Search packages
search python           # apt search python
```

### Network

```bash
# Check ports
ss -tlnp                # Listening TCP ports
ss -ulnp                # Listening UDP ports

# Test connectivity
ping -c 3 google.com
curl -I https://example.com
```

### Logs

```bash
# System logs
journalctl -f           # Follow system log
journalctl -u nginx     # Specific service

# With bat (syntax highlighted)
journalctl -u nginx | bat -l log
```
