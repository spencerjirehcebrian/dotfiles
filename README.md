# Dotfiles

Personal configuration files for my development environment.

## What's Inside

This repository contains configuration files for:

- **Ghostty** - Terminal emulator (renderer only)
- **tmux** - Terminal multiplexer (window/pane management, copy mode, search)
- **Zsh** - Shell configuration with Oh My Zsh and vim mode
- **Powerlevel10k** - Zsh prompt theme
- **Neovim** - Text editor configuration

## Installation

### Prerequisites

```bash
brew install ghostty tmux neovim
```

Also install:
- [Oh My Zsh](https://ohmyz.sh/)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)

### Fresh Installation

Clone this repository and run the install script:

```bash
git clone git@github-personal:spencerjirehcebrian/dotfiles.git ~/.dotfiles
cd ~/.dotfiles
./install.sh
```

### What the Install Script Does

The script creates symlinks for:

- Ghostty config: `~/Library/Application Support/com.mitchellh.ghostty/config`
- tmux config: `~/.tmux.conf`
- Zsh configuration: `~/.zshrc`
- Powerlevel10k theme: `~/.p10k.zsh`
- Neovim configuration: `~/.config/nvim`

## Directory Structure

```
~/.dotfiles/
├── ghostty/
│   └── config              # Ghostty terminal configuration
├── tmux/
│   └── tmux.conf           # tmux configuration
├── zsh/
│   ├── .zshrc              # Zsh shell configuration
│   └── .p10k.zsh           # Powerlevel10k theme settings
├── nvim/
│   └── ...                 # Neovim configuration
└── install.sh              # Installation script
```

## tmux Keybinds

Prefix: `cmd+shift+space` (Ghostty translates to ctrl+space for tmux)

### Copy Mode

| Action | Keys |
|--------|------|
| Enter copy mode | `prefix + v` |
| Search forward | `/` |
| Search backward | `?` |
| Start selection | `v` |
| Yank to clipboard | `y` |
| Exit copy mode | `Escape` |

### Panes

| Action | Keys |
|--------|------|
| Navigate | `prefix + hjkl` |
| Split vertical | `prefix + \|` |
| Split horizontal | `prefix + -` |
| Resize | `prefix + HJKL` |
| Close pane | `prefix + x` |

### Windows

| Action | Keys |
|--------|------|
| New window | `prefix + c` |
| Next window | `prefix + ctrl+l` |
| Previous window | `prefix + ctrl+h` |
| Window by number | `prefix + 1-9` |
| Close window | `prefix + X` |

### Sessions

| Action | Keys |
|--------|------|
| New session | `prefix + S` |
| List sessions | `prefix + s` |
| Detach | `prefix + d` |
| Kill session | `prefix + q` |

### Auto-start

tmux automatically starts when opening Ghostty, attaching to the `main` session or creating it if it doesn't exist.

### Shell Aliases

```bash
tm              # attach existing or create new session
tls             # list sessions
tks <name>      # kill session by name
```

## Theme

All tools use the Vesper color scheme:

- Background: `#101010`
- Foreground: `#ffffff`
- Accent: `#ffc799` (orange)
- Selection: `#2a2a2a`

## Making Changes

Since files are symlinked, changes are automatically reflected in this repo:

```bash
cd ~/.dotfiles
git add .
git commit -m "Description of changes"
git push
```

## Updating on Another Machine

```bash
cd ~/.dotfiles
git pull
```

## Troubleshooting

### Symlinks Not Working

Recreate them by running:

```bash
cd ~/.dotfiles
./install.sh
```

### tmux Colors Wrong

Ensure your terminal reports as 256-color. The config sets `default-terminal` to `tmux-256color`.

### Permission Issues

```bash
chmod +x ~/.dotfiles/install.sh
```
