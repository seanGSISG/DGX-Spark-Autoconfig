# Installed Tools

Complete list of tools installed by linux-dev-autoconfig.

## Shell Environment

| Tool | Description | Usage |
|------|-------------|-------|
| **zsh** | Z shell - modern shell with better completion | Default shell after install |
| **Oh My Zsh** | Zsh framework with plugins and themes | Auto-loaded in ~/.zshrc |
| **Powerlevel10k** | Fast, customizable zsh theme | Run `p10k configure` to customize |
| **zsh-autosuggestions** | Fish-like command suggestions | Type, then press → to accept |
| **zsh-syntax-highlighting** | Syntax highlighting while typing | Auto-enabled |

## Modern CLI Replacements

These replace standard commands with better alternatives:

| Tool | Replaces | Key Features |
|------|----------|--------------|
| **lsd** | `ls` | Icons, colors, tree view |
| **bat** | `cat` | Syntax highlighting, line numbers, git integration |
| **ripgrep (rg)** | `grep` | 10x faster, respects .gitignore |
| **fd** | `find` | Simpler syntax, faster, respects .gitignore |
| **btop** | `top/htop` | Beautiful resource monitor with mouse support |
| **duf** | `df` | Modern disk usage with better formatting |
| **ncdu** | `du` | Interactive disk usage analyzer |

### Usage Examples

```bash
# lsd (aliased to ls)
ls              # Icons + names only
ll              # Long format
la              # All files, long format
tree            # Tree view (lsd --tree)

# bat (aliased to cat)
cat file.py     # Syntax highlighted output
bat -p file.py  # Plain output (no line numbers)

# ripgrep (aliased to grep)
rg "pattern"           # Search current directory
rg "pattern" -t py     # Search only Python files
rg "pattern" -C 3      # Show 3 lines of context

# fd (aliased to find)
fd "pattern"           # Find files matching pattern
fd -e py               # Find all .py files
fd -e py -x wc -l      # Count lines in all .py files

# duf
duf                    # Show disk usage (pretty)
duf /home              # Show specific mount

# ncdu
ncdu /var              # Interactive disk analyzer
# Navigate with arrows, press 'd' to delete
```

## VPS & Remote Access

| Tool | Description | Usage |
|------|-------------|-------|
| **Tailscale** | VPN mesh network | `sudo tailscale up` to connect |
| **mosh** | Mobile shell (resilient SSH) | `mosh user@host` |
| **tmux** | Terminal multiplexer | `tmux new -s name` |

### Tailscale Quick Reference

```bash
# First time setup
sudo tailscale up

# Check status
tailscale status

# Get your Tailscale IP
tailscale ip -4

# SSH to another device on tailnet
ssh user@100.x.x.x

# Share a file (generates URL)
tailscale file cp myfile.txt user@device:
```

### Mosh Quick Reference

```bash
# Connect (like SSH but handles disconnects)
mosh user@host

# With specific SSH port
mosh --ssh="ssh -p 2222" user@host

# Mosh automatically reconnects after:
# - Network changes (WiFi → cellular)
# - Laptop sleep/wake
# - Temporary connection loss
```

## Git Tools

| Tool | Description | Usage |
|------|-------------|-------|
| **lazygit** | Terminal UI for git | `lg` or `lazygit` |
| **git-lfs** | Large file storage | Auto-configured |
| **gh** | GitHub CLI | `gh pr create`, `gh issue list` |

### Lazygit Quick Reference

```bash
lg              # Open lazygit in current repo

# Key bindings in lazygit:
# Space     - Stage/unstage file
# c         - Commit
# P         - Push
# p         - Pull
# ?         - Help
# q         - Quit
```

## Development Tools

| Tool | Description | Usage |
|------|-------------|-------|
| **UV** | Fast Python package manager | `uv pip install`, `uv venv` |
| **Bun** | Fast JavaScript runtime | `bun install`, `bun run` |
| **neovim** | Modern vim | `nvim` (aliased to `vim`) |
| **fzf** | Fuzzy finder | `Ctrl+R` for history search |
| **direnv** | Directory-specific env vars | Add `.envrc` to project |

### UV Quick Reference

```bash
# Create virtual environment
uv venv

# Activate it
source .venv/bin/activate

# Install packages (10-100x faster than pip)
uv pip install requests pandas

# Install from requirements.txt
uv pip install -r requirements.txt
```

## AI Coding Assistants

| Tool | Description | Usage |
|------|-------------|-------|
| **Claude Code** | Anthropic's CLI assistant | `claude` or `ccd` (dangerous mode) |
| **Codex CLI** | OpenAI's CLI assistant | `codex` or `cod` (dangerous mode) |

## Utility Tools

| Tool | Description | Usage |
|------|-------------|-------|
| **tldr** | Simplified man pages | `tldr tar`, `tldr git-rebase` |
| **curl** | HTTP client | `curl -fsSL url` |
| **jq** | JSON processor | `cat file.json \| jq '.key'` |

### TLDR Quick Reference

```bash
# First time: update the pages
tldr --update

# Get quick help for any command
tldr tar
tldr git-stash
tldr docker-compose

# Much easier to read than man pages!
```
