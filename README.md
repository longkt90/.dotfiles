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

## Configuration

This repository uses chezmoi's template system to keep personal information private. Before using these dotfiles, create your personal configuration file:

```bash
# Create your chezmoi config with personal data
cat > ~/.config/chezmoi/chezmoi.toml << EOF
[data]
    name = "Your Name"
    email = "your.email@example.com"
    github_user = "your-github-username"
EOF
```

These variables can then be referenced in template files (e.g., `dot_gitconfig.tmpl`) using `{{ .name }}`, `{{ .email }}`, etc.

## Quick Start

Once Homebrew and chezmoi are installed, you can initialize your dotfiles:

```bash
# Initialize chezmoi with this repository
chezmoi init https://github.com/longkt90/.dotfiles.git

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

# Add a dotfile as a template (for files with personal info)
chezmoi add --template ~/.gitconfig
# Note: This just marks it as a template. You must manually edit the template
# to replace personal values with variables like {{ .name }} and {{ .email }}
chezmoi edit ~/.gitconfig
```

## File Naming Convention

Chezmoi uses special naming conventions in this repository:
- `dot_filename` → `.filename` (hidden files)
- `dot_filename.tmpl` → `.filename` (templates with variables)
- `private_dot_filename` → `.filename` (with 0600 permissions)
- `executable_filename` → `filename` (with execute permission)

Example: `dot_gitconfig.tmpl` becomes `~/.gitconfig` with template variables replaced.

## Important: Keeping Personal Information Private

**Never commit files with personal information directly!** Always use templates for files containing:
- Names, emails, usernames
- API keys, tokens, credentials
- Machine-specific paths
- Any other personal or sensitive data

Use `chezmoi add --template` for these files and reference variables from `~/.config/chezmoi/chezmoi.toml`.

## Documentation

For more information, visit the [chezmoi documentation](https://www.chezmoi.io/user-guide/command-overview/).
