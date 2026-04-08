# Dotfiles

Personal configuration files managed with [chezmoi](https://www.chezmoi.io/).

## Prerequisites

Before using this repository, you must install the following tools:

### 1. Install Homebrew

[Homebrew](https://brew.sh/) is required for managing packages on macOS/Linux.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, follow the instructions in your terminal to add Homebrew to your PATH.

### 2. Install chezmoi

[chezmoi](https://www.chezmoi.io/) manages your dotfiles across multiple machines.

```bash
brew install chezmoi
```

## Quick Start

Once Homebrew and chezmoi are installed, you can initialize your dotfiles:

```bash
# Initialize chezmoi with this repository
chezmoi init https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Preview the changes that will be made
chezmoi diff

# Apply the dotfiles
chezmoi apply
```

## Usage

```bash
# Edit a dotfile
chezmoi edit ~/.zshrc

# See what changes would be made
chezmoi diff

# Apply changes
chezmoi apply -v

# Update dotfiles from the repository
chezmoi update

# Add a new dotfile to be managed
chezmoi add ~/.config/newfile
```

## Documentation

For more information, visit the [chezmoi documentation](https://www.chezmoi.io/user-guide/command-overview/).
