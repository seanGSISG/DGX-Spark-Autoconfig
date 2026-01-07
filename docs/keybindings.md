# Keybindings

Keyboard shortcuts for Ghostty terminal and tmux.

## Ghostty Terminal

### Tabs

| Action | Keybinding |
|--------|------------|
| New tab | `Ctrl+Shift+T` |
| Close tab | `Ctrl+Shift+W` |
| Next tab | `Ctrl+Tab` |
| Previous tab | `Ctrl+Shift+Tab` |
| Go to tab 1-9 | `Ctrl+1` through `Ctrl+9` |

### Splits

| Action | Keybinding |
|--------|------------|
| Split right (vertical) | `Ctrl+Shift+D` |
| Split down (horizontal) | `Ctrl+Shift+E` |
| Navigate left | `Ctrl+Shift+H` |
| Navigate down | `Ctrl+Shift+J` |
| Navigate up | `Ctrl+Shift+K` |
| Navigate right | `Ctrl+Shift+L` |
| Close split | `Ctrl+Shift+W` |

### Font Size

| Action | Keybinding |
|--------|------------|
| Increase font | `Ctrl++` or `Ctrl+=` |
| Decrease font | `Ctrl+-` |
| Reset font | `Ctrl+0` |

### Other

| Action | Keybinding |
|--------|------------|
| Copy | `Ctrl+Shift+C` |
| Paste | `Ctrl+Shift+V` |
| Clear screen | `Ctrl+Shift+K` |
| Open config | Edit `~/.config/ghostty/config` |

## Tmux

**Prefix key:** `Ctrl+b` (press this first, then the command key)

### Sessions

| Action | Keys |
|--------|------|
| New session | `:new -s name` |
| Detach | `Ctrl+b`, `d` |
| List sessions | `Ctrl+b`, `s` |
| Rename session | `Ctrl+b`, `$` |

### Windows (Tabs)

| Action | Keys |
|--------|------|
| New window | `Ctrl+b`, `c` |
| Next window | `Ctrl+b`, `n` |
| Previous window | `Ctrl+b`, `p` |
| Go to window 0-9 | `Ctrl+b`, `0-9` |
| Rename window | `Ctrl+b`, `,` |
| Close window | `Ctrl+b`, `&` |
| List windows | `Ctrl+b`, `w` |

### Panes (Splits)

| Action | Keys |
|--------|------|
| Split horizontal | `Ctrl+b`, `"` |
| Split vertical | `Ctrl+b`, `%` |
| Navigate panes | `Ctrl+b`, arrow keys |
| Toggle layouts | `Ctrl+b`, `Space` |
| Zoom pane (fullscreen) | `Ctrl+b`, `z` |
| Close pane | `Ctrl+b`, `x` |
| Resize pane | `Ctrl+b`, `Ctrl+arrow` |

### Copy Mode (Scroll/Search)

| Action | Keys |
|--------|------|
| Enter copy mode | `Ctrl+b`, `[` |
| Exit copy mode | `q` |
| Scroll up | `Page Up` or `Ctrl+u` |
| Scroll down | `Page Down` or `Ctrl+d` |
| Search forward | `/` |
| Search backward | `?` |
| Next match | `n` |
| Previous match | `N` |

### Useful Commands

```bash
# From command line
tmux new -s work        # New session named "work"
tmux ls                 # List sessions
tmux attach -t work     # Attach to session
tmux kill-session -t work  # Kill session

# Inside tmux (prefix + :)
:resize-pane -D 10      # Resize down 10 lines
:resize-pane -R 20      # Resize right 20 cols
:setw synchronize-panes # Type in all panes
```

## Zsh / Shell

### Line Editing

| Action | Keybinding |
|--------|------------|
| Move to start of line | `Ctrl+a` or `Home` |
| Move to end of line | `Ctrl+e` or `End` |
| Move word left | `Ctrl+←` or `Alt+←` |
| Move word right | `Ctrl+→` or `Alt+→` |
| Delete word backward | `Ctrl+Backspace` or `Ctrl+w` |
| Delete word forward | `Ctrl+Delete` |
| Delete to end of line | `Ctrl+k` |
| Delete to start of line | `Ctrl+u` |
| Undo | `Ctrl+_` |

### History

| Action | Keybinding |
|--------|------------|
| Search history | `Ctrl+r` (uses Atuin if installed) |
| Previous command | `↑` |
| Next command | `↓` |
| Run last command | `!!` |
| Run last command with sudo | `sudo !!` |

### Completion

| Action | Keybinding |
|--------|------------|
| Complete | `Tab` |
| Show completions | `Tab Tab` |
| Accept autosuggestion | `→` (right arrow) |
| Accept word from suggestion | `Ctrl+→` |

## Lazygit

| Action | Key |
|--------|-----|
| Open | `lg` (alias) |
| Stage/unstage file | `Space` |
| Stage all | `a` |
| Commit | `c` |
| Push | `P` |
| Pull | `p` |
| Fetch | `f` |
| Stash | `s` |
| Help | `?` |
| Quit | `q` |

## btop (Resource Monitor)

| Action | Key |
|--------|-----|
| Open | `btop` or `top` (alias) |
| Quit | `q` |
| Help | `h` |
| Process menu | `Enter` |
| Kill process | `k` |
| Filter processes | `f` |
| Sort by CPU | `c` |
| Sort by memory | `m` |
| Tree view | `t` |

## ncdu (Disk Usage)

| Action | Key |
|--------|-----|
| Navigate | Arrow keys |
| Delete file/dir | `d` |
| Info | `i` |
| Refresh | `r` |
| Quit | `q` |
| Sort by size | `s` |
| Sort by name | `n` |
| Toggle hidden | `e` |
