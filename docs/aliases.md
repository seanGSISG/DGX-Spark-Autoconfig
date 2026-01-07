# Shell Aliases

All aliases configured by linux-dev-autoconfig. Located in `~/.devenv/zsh/aliases.zsh`.

## Git

| Alias | Command | Description |
|-------|---------|-------------|
| `gs` | `git status` | Show working tree status |
| `gd` | `git diff` | Show unstaged changes |
| `gdc` | `git diff --cached` | Show staged changes |
| `gp` | `git push` | Push to remote |
| `gpu` | `git pull` | Pull from remote |
| `gco` | `git checkout` | Switch branches or restore files |
| `gcm` | `git commit -m` | Commit with message |
| `gca` | `git commit -a -m` | Stage all and commit |
| `gb` | `git branch` | List or create branches |
| `glog` | `git log --oneline --graph --decorate` | Pretty git log |
| `lg` | `lazygit` | Open lazygit TUI |

## Docker

| Alias | Command | Description |
|-------|---------|-------------|
| `dc` | `docker compose` | Docker Compose shortcut |
| `dps` | `docker ps` | List running containers |
| `dpsa` | `docker ps -a` | List all containers |
| `dimg` | `docker images` | List images |
| `dex` | `docker exec -it` | Execute in container |
| `lzd` | `lazydocker` | Open lazydocker TUI |

## Navigation

| Alias | Command | Description |
|-------|---------|-------------|
| `dev` | `cd ~/dev` | Go to dev directory |

## System / Package Management

| Alias | Command | Description |
|-------|---------|-------------|
| `update` | `sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y` | Full system update |
| `install` | `sudo apt install` | Install package |
| `search` | `apt search` | Search packages |

## AI Coding Assistants

| Alias | Command | Description |
|-------|---------|-------------|
| `ccd` | `claude --dangerously-skip-permissions` | Claude Code (dangerous mode) |
| `cod` | `codex --dangerously-bypass-approvals-and-sandbox` | Codex CLI (dangerous mode) |
| `uca` | Update Claude + Codex | Update all AI agent CLIs |

**Note:** "Dangerous mode" bypasses confirmation prompts. Use when you trust the AI to make changes autonomously.

## Bun Project Helpers

| Alias | Command | Description |
|-------|---------|-------------|
| `br` | `bun run dev` | Start dev server |
| `bl` | `bun run lint` | Run linter |
| `bt` | `bun run type-check` | Run type checker |

## Modern CLI Replacements

These automatically replace standard commands when the modern alternative is installed:

| Alias | Replaced By | Features |
|-------|-------------|----------|
| `ls` | `lsd` | Icons, colors |
| `ll` | `lsd -l` | Long format with icons |
| `la` | `lsd -la` | All files, long format |
| `tree` | `lsd --tree` | Tree view with icons |
| `cat` | `bat` | Syntax highlighting |
| `grep` | `rg` (ripgrep) | 10x faster search |
| `find` | `fd` | Simpler, faster |
| `top` | `btop` | Beautiful resource monitor |
| `df` | `duf` | Modern disk free |
| `du` | `ncdu` | Interactive disk usage |
| `vim` | `nvim` | Neovim |

## Tailscale (VPN)

| Alias | Command | Description |
|-------|---------|-------------|
| `ts` | `tailscale status` | Show connection status |
| `tsup` | `sudo tailscale up` | Connect to tailnet |
| `tsdown` | `sudo tailscale down` | Disconnect from tailnet |
| `tsip` | `tailscale ip -4` | Show your Tailscale IPv4 |

### Tailscale Usage Example

```bash
# First time setup on a new machine
tsup                    # Connect (opens browser for auth)

# Check your status
ts                      # Shows connected devices

# Get your IP for SSH
tsip                    # e.g., 100.64.0.1

# From another machine on your tailnet:
ssh user@100.64.0.1
```

## Quick Help

| Alias | Command | Description |
|-------|---------|-------------|
| `help` | `tldr` | Simplified man pages |

### Usage Example

```bash
help tar                # Shows common tar examples
help git-rebase         # Shows git rebase examples
help docker-compose     # Shows docker compose examples
```

## SSH / Remote Access

| Alias | Command | Description |
|-------|---------|-------------|
| `mssh` | `mosh --ssh="ssh -o StrictHostKeyChecking=no"` | Mosh without host key check |

### Usage Example

```bash
# Regular mosh (handles disconnects gracefully)
mosh user@host

# Using the alias (skips host key confirmation)
mssh user@host
```

## Adding Custom Aliases

Add your own aliases to `~/.zshrc.local` (created automatically, not overwritten by updates):

```bash
# Example custom aliases
alias proj='cd ~/projects/my-project'
alias serve='python -m http.server 8000'
```
