# Homebrew Packages

[Homebrew](https://brew.sh/) is the de-facto package manager for macOS. This page lists the recommended formulae (CLI tools) and casks (GUI apps) to install after completing the [First Steps](First-Steps) guide.

---

## Brewfile (Recommended Approach)

Rather than running individual `brew install` commands, use a **Brewfile** to declare all dependencies in one file and install them in a single command. This makes it easy to reproduce the setup on a new machine.

**`~/Brewfile`:**

```ruby
# ── Taps ────────────────────────────────────────────────────────────────────
tap "homebrew/cask-fonts"

# ── CLI Formulae ─────────────────────────────────────────────────────────────
brew "bat"          # cat with syntax highlighting
brew "curl"         # data transfer
brew "fzf"          # fuzzy finder
brew "gh"           # GitHub CLI
brew "git"          # version control
brew "htop"         # interactive process viewer
brew "httpie"       # user-friendly curl
brew "jq"           # JSON processor
brew "n"            # Node.js version manager
brew "ripgrep"      # fast grep (rg)
brew "tldr"         # simplified man pages
brew "tree"         # directory tree viewer
brew "wget"         # file downloader
brew "yarn"         # JS package manager
brew "zsh"          # Z shell

# ── GUI Casks ────────────────────────────────────────────────────────────────
cask "iterm2"
cask "visual-studio-code"
cask "google-chrome"
cask "firefox"
cask "github"
cask "postman"
cask "slack"
cask "spectacle"
cask "spotify"
cask "the-unarchiver"
cask "vlc"

# ── Fonts ────────────────────────────────────────────────────────────────────
cask "font-meslo-lg-nerd-font"
cask "font-fira-code-nerd-font"
```

Install everything at once:

```sh
brew bundle --file ~/Brewfile
```

---

## Essential CLI Formulae

| Formula | Description | Install |
|---|---|---|
| `bat` | `cat` clone with syntax highlighting and Git integration | `brew install bat` |
| `fzf` | Fuzzy finder for files, history, and more | `brew install fzf` |
| `gh` | Official GitHub CLI | `brew install gh` |
| `git` | Version control system | `brew install git` |
| `htop` | Interactive process viewer | `brew install htop` |
| `httpie` | Human-friendly HTTP client | `brew install httpie` |
| `jq` | Lightweight JSON processor | `brew install jq` |
| `n` | Node.js version manager | `brew install n` |
| `ripgrep` | Blazing-fast `grep` replacement (`rg`) | `brew install ripgrep` |
| `tldr` | Simplified, community-driven man pages | `brew install tldr` |
| `tree` | Display directory tree in the terminal | `brew install tree` |
| `wget` | Non-interactive file downloader | `brew install wget` |
| `yarn` | JavaScript package manager | `brew install yarn` |

---

## Developer-Focused Casks

These GUI apps supplement the full list in [Desktop Applications](Desktop-Applications):

| Cask | Description |
|---|---|
| `iterm2` | Feature-rich terminal emulator |
| `visual-studio-code` | Modern code editor |
| `github` | GitHub Desktop GUI client |
| `postman` | API development & testing |
| `tableplus` | Database GUI (MySQL, Postgres, SQLite…) |
| `docker` | Container platform |
| `insomnia` | REST & GraphQL client |

---

## Maintenance

Keep everything up to date with a single command (add to your shell aliases as `bup`):

```sh
brew update && brew upgrade && brew cleanup
```

List outdated packages:

```sh
brew outdated
```

Audit installed packages for known vulnerabilities:

```sh
brew audit
```

---

## Useful Resources

- [Homebrew Formulae search](https://formulae.brew.sh/)
- [Homebrew Cask search](https://formulae.brew.sh/cask/)
- [Homebrew Bundle docs](https://github.com/Homebrew/homebrew-bundle)
