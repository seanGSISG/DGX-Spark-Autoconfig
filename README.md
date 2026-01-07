# DGX-Spark-Autoconfig

Automated development environment setup for **NVIDIA DGX Spark** systems. Provides a modern shell environment optimized for Python and AI development.

## Features

- **Shell**: zsh + Oh My Zsh + Powerlevel10k (lean theme)
- **CLI Tools**: lsd, bat, ripgrep, fzf, fd, btop, lazygit, neovim
- **Python**: UV (Astral) for fast venv/package management
- **AI Agents**: Claude Code + Codex CLI (with "vibe mode" aliases)
- **Configs**: Ghostty terminal, tmux, Claude Code git safety hooks

## Quick Start

**One-liner install:**
```bash
curl -fsSL https://raw.githubusercontent.com/seanGSISG/DGX-Spark-Autoconfig/main/install.sh | bash
```

**Or clone and run:**
```bash
git clone https://github.com/seanGSISG/DGX-Spark-Autoconfig.git
cd DGX-Spark-Autoconfig
./install.sh
exec zsh
```

## Installation Phases

| Phase | Description |
|-------|-------------|
| 1 | Base dependencies (apt packages, zsh) |
| 2 | User setup (permissions, groups) |
| 3 | Filesystem (directories, configs) |
| 4 | Shell setup (Oh My Zsh, Powerlevel10k, plugins) |
| 5 | CLI tools (lsd, bat, ripgrep, tmux, etc.) |
| 6 | AI agents (UV, Bun, Codex CLI, hooks) |

## Key Customizations

### Minimal `ls` Output (lsd)

By default, `ls` shows only **icons + names** (no dates, sizes, permissions):

```bash
alias ls='lsd --icon=always'      # Minimal: icons + names only
alias ll='lsd -l --icon=always'   # Long format when needed
alias la='lsd -la --icon=always'  # All files with long format
```

### Agent Aliases ("Vibe Mode")

```bash
ccd   # Claude Code with --dangerously-skip-permissions
cod   # Codex CLI with --dangerously-bypass-approvals-and-sandbox
uca   # Update all agent CLIs
```

### Ghostty Keybindings

| Action | Keybinding |
|--------|------------|
| New tab | Ctrl+Shift+T |
| Close tab | Ctrl+Shift+W |
| Next/prev tab | Ctrl+Tab / Ctrl+Shift+Tab |
| Split right | Ctrl+Shift+D |
| Split down | Ctrl+Shift+E |
| Navigate splits | Ctrl+Shift+H/J/K/L |
| Font size +/- | Ctrl++/- |
| Reset font | Ctrl+0 |

## Directory Structure

```
~/.dgxspark/           # Main config directory
  zsh/
    dgxspark.zshrc     # Main shell config
    p10k.zsh           # Powerlevel10k config
  tmux/
    tmux.conf          # Tmux config
  scripts/lib/
    dgx.sh             # DGX utilities

~/.config/ghostty/     # Ghostty terminal config
~/.claude/             # Claude Code config
  hooks/
    git_safety_guard.py  # Git safety hook
```

## Commands

### dgxspark CLI

```bash
dgxspark info      # Show system info (GPU, CUDA, tools)
dgxspark doctor    # Check system health
dgxspark update    # Update tools
dgxspark version   # Show version
dgxspark help      # Show help
```

### Common Aliases

| Alias | Command |
|-------|---------|
| `gs` | `git status` |
| `gd` | `git diff` |
| `lg` | `lazygit` |
| `p` | `cd ~/projects` |
| `dev` | `cd ~/dev` |

## Requirements

- NVIDIA DGX Spark with GB10 GPU (Blackwell architecture)
- Ubuntu 24.04 LTS (ARM64)
- Sudo access
- Internet connection

## Related Projects

- **[dgx-spark-vllm-setup](https://github.com/seanGSISG/dgx-spark-vllm-setup)** - vLLM installer with Blackwell-specific patches for LLM inference workloads

## License

MIT License

---

Adapted from [WSL2-AI-AUTOCONFIG](https://github.com/seanGSISG/WSL2-AI-AUTOCONFIG) for native Linux on DGX Spark.
