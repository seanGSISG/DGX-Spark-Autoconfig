# CLAUDE.md - Linux Dev Autoconfig

## Project Overview

Self-contained development environment setup for **Linux systems** (Debian/Ubuntu). Installs tools, shell, configs, and AI agents in one command.

## Quick Start

```bash
curl -fsSL https://raw.githubusercontent.com/seanGSISG/linux-dev-autoconfig/main/install.sh | bash
```

## Repository Structure

```
linux-dev-autoconfig/
├── install.sh                    # Main installer (6 phases)
├── config/
│   ├── zsh/
│   │   ├── devenv.zshrc         # Main shell config
│   │   ├── aliases.zsh          # Shell aliases
│   │   └── p10k.zsh             # Powerlevel10k theme
│   ├── tmux/tmux.conf           # Tmux configuration
│   └── ghostty/config           # Ghostty terminal config
└── scripts/lib/
    ├── doctor.sh                # System health check
    ├── update.sh                # Update tools/configs
    └── dgx.sh                   # DGX utilities
```

## Install Location

The repo clones to `~/.devenv/` and configs are copied to:
- `~/.zshrc` - Shell config
- `~/.p10k.zsh` - Prompt theme
- `~/.devenv/zsh/aliases.zsh` - Aliases
- `~/.tmux.conf` - Tmux
- `~/.config/ghostty/config` - Terminal

## Installation Phases

1. **Base Dependencies** - apt packages (zsh, curl, git, jq, build-essential)
2. **CLI Tools** - lsd, bat, ripgrep, fzf, fd, btop, lazygit, tmux, tailscale
3. **Shell Setup** - Oh My Zsh + Powerlevel10k + plugins
4. **AI Agents** - UV, Bun, Claude Code, Codex CLI
5. **Apply Configs** - Copy configs from repo
6. **Private Dotfiles** - Optional chezmoi setup for encrypted secrets

## The `devenv` Command

After installation, the `devenv` shell function provides environment management:

```bash
devenv doctor    # Check system health (tools, configs, plugins)
devenv update    # Update tools and configs
devenv info      # System overview (hostname, GPU, tools)
devenv version   # Show version
```

### Update Options

```bash
devenv update            # Update everything
devenv update --configs  # Configs only
devenv update --tools    # CLI tools only
devenv update --agents   # AI agents only
devenv update --plugins  # Shell plugins only
```

## Architecture

```
Fresh Ubuntu/Debian
        │
        ▼
┌─────────────────────────────────┐
│  linux-dev-autoconfig           │  ← Self-contained (no chezmoi required)
│  • CLI tools                    │
│  • Shell + plugins              │
│  • Configs (zsh, tmux, etc.)    │
│  • AI agents                    │
│  Installs to: ~/.devenv/        │
└─────────────────────────────────┘
        │
        ▼ (optional, prompted)
┌─────────────────────────────────┐
│  dotfiles (via chezmoi + age)   │  ← Requires age key from Bitwarden
│  • SSH config (encrypted)       │
│  • Claude knowledge base        │
│  Installs to: ~/dev/github/dotfiles/
└─────────────────────────────────┘
```

## Key Design Decisions

### Architecture Detection
Auto-detects x86_64 or ARM64 and downloads appropriate binaries.

### Dangerous Mode Aliases
```bash
ccd   # Claude Code with --dangerously-skip-permissions
cod   # Codex CLI with --dangerously-bypass-approvals-and-sandbox
```

### Modern Tool Aliases
```bash
ls → lsd --icon=always
cat → bat
grep → rg
find → fd
```

## Development Notes

- Use `as_root` helper instead of direct `sudo` calls
- Fallback installations for tools not in Ubuntu repos (lazygit, lsd)
- Scripts support both x86_64 and ARM64
- The `devenv` function is defined in `devenv.zshrc` and calls scripts in `~/.devenv/scripts/lib/`
