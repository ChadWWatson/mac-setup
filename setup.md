# Mac Setup for Web Development [2026]

Source: https://www.robinwieruch.de/mac-setup-web-development/

## Overview

This comprehensive guide covers the complete development environment setup for macOS, including system preferences, package managers, terminal configuration, IDE settings, and version control tools.

## MacBook Pro Specification

- 14-inch display
- Apple Silicon (M1 Pro: 10-core CPU, 16-core GPU, 16-core Neural Engine)
- 32 GB RAM
- 512 GB SSD
- QWERTY English (International) keyboard
- macOS Sequoia or newer

## System Preferences Configuration

### Visual & Interface Settings

Enable Dark Mode and adjust visibility options by setting scroll bars to always display. Configure the Dock to hide automatically with a smaller size, disable recent applications display, and enable indicators for active apps. Show battery percentage in the menu bar.

### Input & Keyboard Settings

Disable automatic capitalization, period insertion via double-space, and smart quotes. Turn off all Mission Control keyboard shortcuts and disable Spotlight's CMD+Space activation (Raycast will replace this functionality).

### Finder Configuration

Set new Finder windows to open Downloads by default. Show all filename extensions and enable the path bar. Configure sidebar favorites and remove desktop clutter.

### Security & Privacy

Enable FileVault encryption and add browsers to screen recording permissions.

### Terminal System Preferences

Execute these commands for additional configurations:

```bash
defaults write com.apple.screencapture type jpg
defaults write com.apple.Preview ApplePersistenceIgnoreState YES
chflags nohidden ~/Library
defaults write com.apple.finder AppleShowAllFiles YES
defaults write com.apple.finder ShowPathbar -bool true
defaults write com.apple.finder ShowStatusBar -bool true
killall Finder;
```

## Homebrew Package Manager

Install Homebrew as your macOS package manager:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew update
```

### GUI Applications via Homebrew Casks

Install these desktop applications:

```bash
brew install --cask \
  raycast \
  bitwarden \
  google-chrome \
  firefox \
  iterm2 \
  visual-studio-code \
  rectangle \
  slack \
  discord \
  signal \
  vlc \
  calibre \
  maccy \
  zoom \
  ngrok \
  obs \
  shotcut \
  claude-code \
  codex \
  font-hack-nerd-font
```

### Terminal Applications via Homebrew

Install command-line tools:

```bash
brew install \
  wget \
  eza \
  git \
  gh \
  jq \
  nvm \
  pnpm \
  colima \
  docker \
  docker-compose \
  commitizen \
  cmatrix \
  starship
```

## GUI Applications Configuration

**Raycast**: Replaces Spotlight with CMD+Space. Enable File Search, Snippets, and System features.

**Bitwarden**: Use as password manager with Touch ID enabled and dark mode activated.

**Google Chrome**: Set as default browser, enable dark mode, disable password saving, and install these extensions:
- uBlock Origin Lite
- Bitwarden
- React Developer Tools
- Mortality / Death Clock
- 7TV

Configure Chrome DevTools for dark mode and limit Network tab to "Fetch/XHR" requests.

**Firefox**: Secondary browser for web development testing.

**iTerm2**: Primary terminal application.

**Visual Studio Code**: Main IDE for development.

**Claude Code**: Terminal-based AI coding agent.

**Rectangle**: Window management without using Spectacle.

**Other Tools**: Slack, Discord, Signal for communication; VLC for video playback; Calibre for eBook management; Maccy for clipboard history; Zoom for video calls; ngrok for tunneling; OBS for streaming; Shotcut for video editing.

## iTerm2 Terminal Setup

Configure iTerm2 preferences:

- Disable native fullscreen windows
- Hide scrollbars and tab bar in fullscreen
- Set transparency to 30% with full-screen style on main display
- Enable semantic history with VS Code as editor
- Configure split pane to open in current directory
- Use CMD+Enter to activate fullscreen mode

## Oh My Zsh & Shell Configuration

Install Oh My Zsh for enhanced terminal experience:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/shell/master/tools/install.sh)"
omz update
```

Install the Starship prompt theme:

```bash
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

Set iTerm2 font to Hack Nerd Font via Preferences → Profile → Text → Font.

Install these Oh My Zsh plugins:
- zsh-completions
- zsh-autosuggestions
- zsh-syntax-highlighting

### ZSH Configuration File (~/.zshrc)

```bash
export ZSH="$HOME/.oh-my-zsh"

plugins=(
  git
  zsh-completions
  zsh-autosuggestions
  zsh-syntax-highlighting
)

# Networking
alias ip="ipconfig getifaddr en0"

# Configuration shortcuts
alias zshconfig="vim ~/.zshrc"
alias zshsource="source ~/.zshrc"
alias ohmyzsh="cd ~/.oh-my-zsh"
alias sshhome="cd ~/.ssh"
alias sshconfig="vim ~/.ssh/config"

# Git shortcuts
alias gitconfig="vim ~/.gitconfig"
alias gits="git status"
alias gitd="git diff"
alias gitl="git lg"
alias gita="git add ."
alias gitc="cz commit"
alias gitb="git branch --sort=-committerdate"

# Utilities
alias c="clear"
alias ls="eza --long"
alias cc="claude"

# Initialize completions and plugins
autoload -U compinit && compinit

# Node version manager
source /opt/homebrew/opt/nvm/nvm.sh

# Starship theme (end of file)
eval "$(starship init zsh)"
```

## Visual Studio Code Setup

### Recommended Extensions

Essential development extensions include:
- Astro (framework support)
- Auto Close Tag & Auto Rename Tag
- Better Comments & Color Highlight
- DotENV & EditorConfig
- ESLint (code style)
- GitHub Dark Default (theme)
- GitLens (Git visualization)
- Headwind (Tailwind CSS sorting)
- JavaScript & TypeScript support tools
- MDX & Prisma support
- Prettier (code formatting)
- Pretty TypeScript Errors
- Relative Go to Line
- Status Bar Format Toggle
- Styled Components & Tailwind CSS tools
- TODO Highlight

### VS Code Settings (JSON)

```json
{
  "window.titleBarStyle": "native",
  "window.customTitleBarVisibility": "never",
  "window.title": "${activeEditorMedium}",

  "workbench.sideBar.location": "right",
  "workbench.startupEditor": "none",
  "workbench.statusBar.visible": true,
  "workbench.editor.enablePreview": false,
  "workbench.editor.restoreViewState": true,
  "workbench.activityBar.location": "hidden",
  "workbench.colorTheme": "GitHub Dark Colorblind (Beta)",
  "workbench.colorCustomizations": {
    "editor.lineHighlightBackground": "#102032",
    "editorCursor.foreground": "#ffffff",
    "terminalCursor.foreground": "#ffffff"
  },

  "editor.fontFamily": "Hack Nerd Font Mono",
  "editor.fontSize": 14,
  "editor.lineHeight": 0,
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": false,
  "editor.wordWrap": "off",
  "editor.lineNumbers": "on",
  "editor.minimap.enabled": false,
  "editor.stickyScroll.enabled": false,
  "editor.scrollBeyondLastLine": true,
  "editor.renderWhitespace": "none",
  "editor.renderLineHighlight": "all",
  "editor.padding.top": 36,

  "editor.cursorBlinking": "solid",
  "editor.cursorStyle": "line",
  "editor.cursorWidth": 2,

  "editor.lightbulb.enabled": "off",
  "editor.inlineSuggest.enabled": true,
  "editor.find.addExtraSpaceOnTop": true,
  "editor.find.seedSearchStringFromSelection": "never",

  "files.trimTrailingWhitespace": true,
  "files.associations": {
    ".env*": "makefile"
  },
  "explorer.confirmDelete": false,
  "explorer.confirmDragAndDrop": false,
  "explorer.compactFolders": false,

  "terminal.integrated.fontSize": 14,
  "terminal.integrated.fontFamily": "Hack Nerd Font Mono",

  "editor.formatOnSave": false,
  "editor.formatOnPaste": false,
  "editor.formatOnType": false,

  "[javascript]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "prettier.documentSelectors": ["**/*.astro"],
  "[astro]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  "editor.codeActionsOnSave": {
    "source.fixAll": "explicit",
    "source.fixAll.eslint": "explicit",
    "source.addMissingImports": "explicit"
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ],

  "js/ts.updateImportsOnFileMove.enabled": "never",
  "js/ts.preferences.autoImportFileExcludePatterns": ["@radix-ui"],
  "js/ts.implicitProjectConfig.checkJs": true,
  "debug.javascript.codelens.npmScripts": "never",

  "git.openRepositoryInParentFolders": "never",
  "gitlens.advanced.messages": {
    "suppressCommitHasNoPreviousCommitWarning": true
  },

  "github.copilot.nextEditSuggestions.enabled": true,
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": true,
    "scminput": false
  },

  "todohighlight.isEnable": true,
  "todohighlight.isCaseSensitive": true,

  "autoHide.autoHideSideBar": true,
  "autoHide.autoHidePanel": true,
  "autoHide.autoHideReferences": false,
  "autoHide.hideOnOpen": false,
  "autoHide.sideBarDelay": 0,
  "autoHide.panelDelay": 0
}
```

Move the Search feature from Activity Bar to Panel for cleaner workspace.

## Git Configuration

Configure global Git settings:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global init.defaultBranch main
```

Create an enhanced log alias:

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

Use with `git lg` command.

View all configurations:

```bash
git config --list
```

## SSH Key Configuration

Generate an SSH key per service (GitHub example):

```bash
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen -t ed25519 -C "github"
# File name: github
# Enter secure passphrase
```

Verify passphrase:

```bash
ssh-keygen -y -f github
```

Create SSH config file:

```bash
touch ~/.ssh/config
```

Add to `~/.ssh/config`:

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github
```

Add key to macOS keychain:

```bash
ssh-add --apple-use-keychain ~/.ssh/github
```

Upload public key to GitHub:

```bash
cat ~/.ssh/github.pub | pbcopy

# Or use GitHub CLI
gh ssh-key add ~/.ssh/github.pub -t github
```

## Node.js Version Management (NVM)

Complete NVM installation:

```bash
echo "source $(brew --prefix nvm)/nvm.sh" >> ~/.zshrc
source ~/.zshrc
```

Install latest LTS Node.js:

```bash
nvm install --lts
node -v && npm -v
```

Update npm:

```bash
npm install -g npm@latest
```

Configure npm defaults:

```bash
npm set init-author-name="your name"
npm set init-author-email="you@example.com"
npm set init-author-url="example.com"
```

Login to npm (for library authors):

```bash
npm adduser
```

Manage Node versions:

```bash
nvm list
nvm install <version> --reinstall-packages-from=$(nvm current)
nvm use <version>
nvm alias default <version>
```

List global packages:

```bash
npm list -g --depth=0
```

## Additional Built-in macOS Applications

**iMessage**: Sync iCloud temporarily for messages, then configure contact syncing. Enable message forwarding to Mac from iPhone.

**Mail**: Use Fastmail as email provider. Display most recent messages at top.

**Notes**: Start new notes with body content. Disable date grouping.

**Pages**: Enable word count display.

**QuickTime Player**: Set save location to Desktop.

---

This setup provides a complete development environment optimized for full-stack web development with JavaScript, TypeScript, React, and modern frameworks like Next.js and Astro.
