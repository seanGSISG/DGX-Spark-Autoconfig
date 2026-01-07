# Linux Dev Autoconfig

Automated development environment setup for **Linux systems** (Debian/Ubuntu). Provides a modern shell environment optimized for Python and AI development.

**Supports:** x86_64 and ARM64 architectures (auto-detected)

## Features

- **Shell**: zsh + Oh My Zsh + Powerlevel10k (lean theme)
- **CLI Tools**: lsd, bat, ripgrep, fzf, fd, btop, lazygit, neovim, ncdu, duf
- **VPS/Remote**: Tailscale (VPN), mosh (resilient SSH), tmux
- **Python**: UV (Astral) for fast venv/package management
- **AI Agents**: Claude Code + Codex CLI (with "vibe mode" aliases)
- **Configs**: Ghostty terminal, tmux, Claude Code git safety hooks

## Quick Start

**One-liner install:**
```bash
curl -fsSL https://raw.githubusercontent.com/seanGSISG/linux-dev-autoconfig/main/install.sh | bash
```

**Or clone and run:**
```bash
git clone https://github.com/seanGSISG/linux-dev-autoconfig.git
cd linux-dev-autoconfig
./install.sh
exec zsh
```

**After installation:**
```bash
# Connect to Tailscale (first time)
sudo tailscale up

# Update tldr pages
tldr --update

# Check what's installed
devenv info
```

## Documentation

Comprehensive documentation is available in the [`docs/`](docs/) folder:

| Document | Description |
|----------|-------------|
| [docs/tools.md](docs/tools.md) | All installed tools with usage examples |
| [docs/aliases.md](docs/aliases.md) | Complete shell alias reference |
| [docs/commands.md](docs/commands.md) | CLI commands and utilities |
| [docs/keybindings.md](docs/keybindings.md) | Ghostty, tmux, and shell shortcuts |

## Installation Phases

| Phase | Description |
|-------|-------------|
| 1 | Base dependencies (apt packages, zsh) |
| 2 | User setup (permissions, groups) |
| 3 | Filesystem (directories, configs) |
| 4 | Shell setup (Oh My Zsh, Powerlevel10k, plugins) |
| 5 | CLI tools (lsd, bat, ripgrep, Tailscale, mosh, etc.) |
| 6 | AI agents (UV, Bun, Codex CLI, hooks) |

## Installed Tools

### Modern CLI Replacements

| Tool | Replaces | Features |
|------|----------|----------|
| `lsd` | `ls` | Icons, colors, tree view |
| `bat` | `cat` | Syntax highlighting |
| `ripgrep` | `grep` | 10x faster, respects .gitignore |
| `fd` | `find` | Simpler syntax, faster |
| `btop` | `top` | Beautiful resource monitor |
| `duf` | `df` | Modern disk usage |
| `ncdu` | `du` | Interactive disk analyzer |

### VPS & Remote Access

| Tool | Purpose |
|------|---------|
| `Tailscale` | VPN mesh networking - secure access without opening ports |
| `mosh` | Mobile shell - survives disconnects and roaming |
| `tmux` | Terminal multiplexer - persistent sessions |

### Key Aliases

| Alias | Description |
|-------|-------------|
| `ts` | Tailscale status |
| `tsup` | Connect to Tailscale |
| `tsip` | Show Tailscale IP |
| `help` | Simplified man pages (tldr) |
| `lg` | Lazygit TUI |
| `ccd` | Claude Code (dangerous mode) |

See [docs/aliases.md](docs/aliases.md) for the complete list.

## Directory Structure

```
~/.devenv/             # Main config directory
  zsh/
    devenv.zshrc       # Main shell config
    aliases.zsh        # All shell aliases
    p10k.zsh           # Powerlevel10k config
  tmux/
    tmux.conf          # Tmux config

~/.config/ghostty/     # Ghostty terminal config
~/.claude/             # Claude Code config
  hooks/
    git_safety_guard.py  # Git safety hook
```

## Commands

### devenv CLI

```bash
devenv info      # Show system info (GPU, CUDA, tools)
devenv doctor    # Check system health
devenv update    # Update tools
devenv version   # Show version
devenv help      # Show help
```

## Requirements

- Debian/Ubuntu-based Linux (apt package manager)
- x86_64 or ARM64 architecture
- Sudo access
- Internet connection

## License

MIT License

---

Originally adapted from [WSL2-AI-AUTOCONFIG](https://github.com/seanGSISG/WSL2-AI-AUTOCONFIG).
