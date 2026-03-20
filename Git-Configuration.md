# Git Configuration

> **See also:** [First Steps](First-Steps) for SSH key generation and GitHub 2FA setup.

---

## Global `.gitconfig`

Set your identity and preferred defaults once, globally:

```sh
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"

# Use VS Code (or Sublime) as the default editor
git config --global core.editor "code --wait"
# git config --global core.editor "subl -n -w"

# Default branch name
git config --global init.defaultBranch main

# Always rebase on pull instead of merge
git config --global pull.rebase true

# Use macOS Keychain for credential storage
git config --global credential.helper osxkeychain

# Colourized output
git config --global color.ui auto
```

The resulting `~/.gitconfig` will look similar to:

```ini
[user]
  name  = Your Name
  email = you@example.com
[core]
  editor        = code --wait
  excludesfile  = ~/.gitignore_global
[init]
  defaultBranch = main
[pull]
  rebase = true
[credential]
  helper = osxkeychain
[color]
  ui = auto
[alias]
  st  = status
  co  = checkout
  br  = branch
  lg  = log --oneline --graph --decorate --all
  undo = reset HEAD~1 --mixed
  aliases = config --get-regexp alias
```

---

## Global `.gitignore`

Tell Git to ignore common OS and editor noise in every repo:

```sh
git config --global core.excludesfile ~/.gitignore_global
```

**`~/.gitignore_global`** contents:

```gitignore
# macOS
.DS_Store
.AppleDouble
.LSOverride
._*

# Thumbnails
Thumbs.db

# Editors
.idea/
.vscode/
*.suo
*.swp
*~

# Logs & caches
*.log
npm-debug.log*
yarn-error.log*
.cache/
```

---

## Useful Git Aliases

Beyond the core aliases in `.gitconfig`, these are handy for day-to-day work:

| Alias | Expands to | Description |
|---|---|---|
| `git st` | `status` | Short status |
| `git co` | `checkout` | Less typing |
| `git br` | `branch` | List/create branches |
| `git lg` | `log --oneline --graph --decorate --all` | Visual branch graph |
| `git undo` | `reset HEAD~1 --mixed` | Undo last commit, keep changes staged |
| `git aliases` | `config --get-regexp alias` | List all aliases |

Add additional aliases with:

```sh
git config --global alias.<name> '<expansion>'
```

---

## SSH Key Setup (recap)

If you haven't already configured SSH for GitHub (covered in [First Steps](First-Steps)):

```sh
# Generate a new Ed25519 key
ssh-keygen -t ed25519 -C "you@example.com"

# Add to the SSH agent
eval "$(ssh-agent -s)"
ssh-add --apple-use-keychain ~/.ssh/id_ed25519

# Copy public key to clipboard and paste into GitHub Settings → SSH keys
pbcopy < ~/.ssh/id_ed25519.pub

# Verify
ssh -T git@github.com
```

---

## Useful Resources

- [Pro Git Book](https://git-scm.com/book/en/v2) – comprehensive free reference
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Oh My Zsh `git` plugin aliases](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git)
