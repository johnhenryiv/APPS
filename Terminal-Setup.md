# Terminal Setup

## iTerm2

[iTerm2](https://www.iterm2.com/) is the recommended terminal emulator for macOS, offering split panes, search, autocomplete, and rich customization over the built-in Terminal app.

### Installation

Install via Homebrew:

```sh
brew install --cask iterm2
```

Or download directly from [iterm2.com](https://www.iterm2.com/downloads.html).

### Profiles & Preferences

1. Open **iTerm2 → Preferences** (`⌘,`)
2. Under **Profiles → Colors**, import a color preset (see [Color Schemes](#color-schemes) below)
3. Under **Profiles → Text**, set font to a [Nerd Font](#fonts) at 13–14pt
4. Under **Profiles → Window**, set columns to `220` and rows to `50`
5. Under **General → Closing**, uncheck *Confirm closing multiple sessions*

---

## Shell: Zsh & Oh My Zsh

macOS ships with zsh as the default shell. [Oh My Zsh](https://ohmyz.sh/) adds plugin management, themes, and helpful defaults on top.

### Install Oh My Zsh

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Recommended Plugins

Add these to the `plugins=(...)` array in `~/.zshrc`:

| Plugin | Purpose |
|---|---|
| `git` | Git aliases and prompt info (bundled) |
| `z` | Jump to frecently used directories (bundled) |
| `zsh-autosuggestions` | Fish-like command suggestions |
| `zsh-syntax-highlighting` | Syntax coloring in the prompt |
| `web-search` | Search Google/DuckDuckGo from the terminal (bundled) |

#### Install community plugins

```sh
# zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Then update `~/.zshrc`:

```zsh
plugins=(git z web-search zsh-autosuggestions zsh-syntax-highlighting)
```

### Theme

[Powerlevel10k](https://github.com/romkatv/powerlevel10k) is the recommended prompt theme — fast, informative, and highly configurable:

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set in `~/.zshrc`:

```zsh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Run `p10k configure` after restarting your shell to walk through the setup wizard.

---

## Useful Aliases

Add these to `~/.zshrc` (or a sourced `~/.aliases` file):

```zsh
# Navigation
alias ..='cd ..'
alias ...='cd ../..'
alias ll='ls -lAh'
alias la='ls -A'

# Git shortcuts (beyond oh-my-zsh defaults)
alias gs='git status'
alias gd='git diff'
alias gl='git log --oneline --graph --decorate'

# Homebrew
alias bup='brew update && brew upgrade && brew cleanup'

# Reload shell config
alias reload='source ~/.zshrc'
```

---

## Color Schemes

Popular iTerm2 color presets:

- **[Solarized Dark](https://ethanschoonover.com/solarized/)** – classic low-contrast dark theme
- **[Dracula](https://draculatheme.com/iterm)** – vibrant dark theme
- **[Catppuccin](https://github.com/catppuccin/iterm)** – pastel dark/light themes
- **[Nord](https://www.nordtheme.com/)** – cool arctic palette

Download a `.itermcolors` file and import via **Preferences → Profiles → Colors → Color Presets → Import**.

---

## Fonts

Nerd Fonts patch popular monospace fonts with developer icons used by Powerlevel10k and many plugins.

```sh
brew tap homebrew/cask-fonts
brew install --cask font-meslo-lg-nerd-font
```

Other popular choices: `font-fira-code-nerd-font`, `font-jetbrains-mono-nerd-font`, `font-hack-nerd-font`.

Set the font in **iTerm2 → Preferences → Profiles → Text → Font**.
