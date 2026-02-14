# Dotfiles

Personal development environment for macOS and Linux.

## What's Inside

- **Ghostty** - GPU-accelerated terminal (renderer only, titlebar hidden)
- **tmux** - Window/pane management, vi-style copy mode
- **Zsh** - Shell with Oh My Zsh, Powerlevel10k, and vi mode
- **Neovim** - Single-file config (`init.lua`) with lazy.nvim

All tools share the **Vesper** color scheme (`#101010` bg, `#ffffff` fg, `#ffc799` accent).

## Installation

### Prerequisites

- [Homebrew](https://brew.sh/)
- [Oh My Zsh](https://ohmyz.sh/)

### Setup

```bash
git clone git@github.com:spencerjireh/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
./install.sh
```

### What the Install Script Does

1. **Installs brew packages**: neovim, tmux, fzf, fd, eza, bat, ripgrep, git-delta, zoxide, pyenv, imagemagick, trash, GohuFont Nerd Font
2. **Creates symlinks** (with automatic backup of existing files):
   - `ghostty/config` → Ghostty config dir (platform-aware)
   - `tmux/tmux.conf` → `~/.tmux.conf`
   - `zsh/.zshrc` → `~/.zshrc`
   - `zsh/.p10k.zsh` → `~/.p10k.zsh`
   - `nvim/` → `~/.config/nvim`
3. **Sets up plugins**: TPM (tmux), zsh-autosuggestions, zsh-syntax-highlighting, powerlevel10k
4. **Optional (interactive prompts)**:
   - GitHub SSH key + CLI setup
   - Global Git config (name, email, delta pager)
   - macOS defaults (key repeat, Finder, Dock, trackpad, screenshots)

### Uninstallation

```bash
./uninstall.sh  # Removes symlinks, restores backups
```

## Directory Structure

```
├── ghostty/
│   └── config
├── tmux/
│   └── tmux.conf
├── zsh/
│   ├── .zshrc
│   └── .p10k.zsh
├── nvim/
│   ├── init.lua
│   └── lazy-lock.json
├── install.sh
└── uninstall.sh
```

## tmux Keybinds

Prefix: `Cmd+Shift+Space` (Ghostty translates to `Ctrl+Space`)

### Navigation

| Action | Keys |
|--------|------|
| Seamless pane/vim nav | `C-h/j/k/l` (no prefix) |
| Navigate panes | `prefix + h/j/k/l` |
| Window by number | `Alt+1-9` (no prefix) |
| Next/prev window | `prefix + n/p` |

### Copy Mode

| Action | Keys |
|--------|------|
| Enter copy mode | `prefix + Enter` |
| Start selection | `v` |
| Select line | `V` |
| Yank to clipboard | `y` |
| Exit | `Escape` |

### Management

| Action | Keys |
|--------|------|
| Split vertical | `prefix + v` or `\|` |
| Split horizontal | `prefix + s` or `-` |
| Resize panes | `prefix + H/J/K/L` |
| New window | `prefix + c` |
| Close window | `prefix + X` |
| Close pane | `prefix + x` |
| New session | `prefix + S` |
| Session tree | `prefix + w` |
| Kill session | `prefix + q` |
| Toggle status bar | `prefix + b` |
| Reload config | `prefix + r` |

tmux auto-starts when opening Ghostty, attaching to the `main` session.

## Shell Aliases

```bash
# tmux
tm              # attach or create session
tls             # list sessions
tks <name>      # kill session

# editors & tools
v               # nvim
cld             # claude
ccd             # claude --dangerously-skip-permissions

# modern replacements
ls → eza        # with icons and git status
cat → bat       # with syntax highlighting
rm → trash      # safe delete
```

## Troubleshooting

**Symlinks not working** — Re-run `./install.sh`

**tmux colors wrong** — Ensure terminal reports 256-color. Config sets `default-terminal` to `tmux-256color`.

**tmux plugins not loaded** — Press `prefix + I` inside tmux to install plugins via TPM.
