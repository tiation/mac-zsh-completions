# Installation Guide

## Prerequisites

- macOS 10.15 (Catalina) or later
- zsh shell (default on macOS 10.15+)
- Git (for cloning the repository)

## Installation Methods

### 1. Quick Install (Recommended)

The fastest way to get started:

```zsh
# Clone the repository
git clone https://github.com/tiaastor/mac-zsh-completions.git ~/.tiation-macos-toolkit

# Add to your .zshrc
echo 'fpath=(~/.tiation-macos-toolkit/completions $fpath)' >> ~/.zshrc
echo 'autoload -U compinit && compinit' >> ~/.zshrc

# Reload your shell
source ~/.zshrc
```

### 2. Manual Installation

For more control over the installation process:

```zsh
# 1. Clone the repository to your preferred location
git clone https://github.com/tiaastor/mac-zsh-completions.git ~/Projects/tiation-macos-toolkit

# 2. Edit your .zshrc file
nano ~/.zshrc

# 3. Add these lines to your .zshrc:
fpath=(~/Projects/tiation-macos-toolkit/completions $fpath)
autoload -U compinit && compinit

# 4. Reload your configuration
source ~/.zshrc
```

### 3. Oh-My-Zsh Plugin

If you're using Oh-My-Zsh:

```zsh
# Clone as a plugin
git clone https://github.com/tiaastor/mac-zsh-completions.git "$ZSH_CUSTOM/plugins/tiation-macos-toolkit"

# Edit your .zshrc and add to plugins array
plugins=(... tiation-macos-toolkit)

# Reload your shell
source ~/.zshrc
```

## Verification

Test that the installation worked:

```zsh
# Test Swift completions
swift --<TAB>

# Test Xcode completions
xed --<TAB>

# Test system completions
installer --<TAB>
```

## Troubleshooting

### Completions not appearing

1. **Clear completion cache:**
   ```zsh
   rm ~/.zcompdump
   compinit
   ```

2. **Check fpath:**
   ```zsh
   echo $fpath
   # Should include the completions directory
   ```

3. **Verify completion files:**
   ```zsh
   ls ~/.tiation-macos-toolkit/completions/
   # Should show completion files like _swift, _xed, etc.
   ```

### Performance issues

Enable completion caching:

```zsh
# Add to your .zshrc
zstyle ':completion:*' use-cache on
zstyle ':completion:*' cache-path ~/.zsh/cache
```

### Conflicts with other plugins

Load tiation-macos-toolkit last in your plugins array:

```zsh
plugins=(other-plugins tiation-macos-toolkit)
```

## Updating

To update to the latest version:

```zsh
cd ~/.tiation-macos-toolkit
git pull origin main
```

## Uninstallation

To remove the toolkit:

```zsh
# Remove the directory
rm -rf ~/.tiation-macos-toolkit

# Remove lines from .zshrc
# Edit ~/.zshrc and remove the fpath line
```
