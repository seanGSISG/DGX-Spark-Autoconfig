# CLAUDE.md - DGX-Spark-Autoconfig

## Project Overview

This repository provides automated development environment setup for **NVIDIA DGX Spark** systems (Blackwell GB10 architecture). It configures a modern shell environment optimized for Python and AI development.

## Target System

| Component | Specification |
|-----------|---------------|
| Hardware | NVIDIA DGX Spark Desktop AI Supercomputer |
| GPU | Blackwell GB10 (sm_121 architecture) |
| CPU | 20-core ARM (Grace Blackwell Superchip) |
| Memory | 128 GB Unified LPDDR5x |
| OS | Ubuntu 24.04 LTS (ARM64/aarch64) |
| CUDA | 13.0+ |

## Repository Structure

```
DGX-Spark-Autoconfig/
├── install.sh                    # Main installer (6 phases)
├── config/
│   ├── zsh/
│   │   ├── dgxspark.zshrc       # Main shell configuration
│   │   └── p10k.zsh             # Powerlevel10k theme config
│   ├── tmux/tmux.conf           # Tmux configuration
│   ├── ghostty/config           # Ghostty terminal config
│   └── claude/
│       ├── settings.json        # Claude Code hook settings
│       └── hooks/git_safety_guard.py  # Git safety hook
└── scripts/lib/
    └── dgx.sh                   # DGX-specific utilities
```

## Installation Phases

1. **Base Dependencies** - apt packages (zsh, curl, git, build-essential)
2. **User Setup** - permissions, docker group
3. **Filesystem** - create ~/projects, ~/.dgxspark, ~/.claude
4. **Shell Setup** - zsh + Oh My Zsh + Powerlevel10k + plugins
5. **CLI Tools** - lsd, bat, ripgrep, fzf, fd, btop, lazygit, tmux
6. **AI Agents** - UV (Astral), Bun, Codex CLI, Claude Code hooks

## Key Design Decisions

### Minimal ls Output
The `ls` alias uses `lsd --icon=always` for minimal output (icons + names only, no dates/sizes/permissions). This was a specific user requirement.

### Agent Configuration
- **Claude Code**: Assumed pre-installed; script configures hooks only
- **Codex CLI**: Installed via Bun (not npm/node)
- **Gemini CLI**: Intentionally excluded

### Dangerous Mode Aliases
```bash
ccd   # Claude Code with --dangerously-skip-permissions
cod   # Codex CLI with --dangerously-bypass-approvals-and-sandbox
```

### Git Safety Hook
The `git_safety_guard.py` hook blocks destructive git commands:
- `git reset --hard`
- `git push --force` (without --force-with-lease)
- `git clean -f`
- `git checkout .`
- `rm -rf` outside /tmp

## Commands

```bash
./install.sh              # Full installation
./install.sh --dry-run    # Preview without changes
./install.sh --skip-phase N  # Skip specific phase
dgxspark info             # Show system info
dgxspark doctor           # Health check
```

## Related Projects

- **dgx-spark-vllm-setup** - vLLM installer with Blackwell-specific patches (separate repo)

## Development Notes

- All scripts must work on ARM64 (aarch64) architecture
- Use `as_root` helper instead of direct `sudo` calls
- Fallback installations for tools not in Ubuntu repos (lazygit, lsd)
- Configs are symlinked from ~/.dgxspark/ to home directory
- Preserve existing ~/.claude/settings.json if present
