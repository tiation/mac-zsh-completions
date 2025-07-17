# Usage Examples

Explore how to make the most of Tiation macOS Toolkit with these practical examples.

## Developer Tools

### Swift

Leverage the power of Swift with robust completions:

```zsh
# Swift Compiler Options
swift build --	
# Completes: --configuration, --enable-test-discovery, --destination, etc.

# Swift Package Manager
swift package 	
# Completes: init, update, resolve, describe, etc.
```

### Xcode

Speed up Xcode commands with completions:

```zsh
# Xcode Editor
xed 	
# Completes: --line, --wait, --find, etc.

# Xcode Command Line Tools
xcrun 	
# Completes: --sdk, --toolchain, --find, etc.
```

## System Administration

Manage macOS with ease:

### Installer

Quickly navigate installer options:

```zsh
installer -pkg 	
# Lists: Available .pkg files in the current directory
```

### Software Update

Stay up-to-date with macOS updates:

```zsh
softwareupdate --	
# Completes: --install, --list, --download, etc.
```

## Third-Party Tools

### GitHub CLI

Enhance GitHub workflows with `gh`:

```zsh
# GitHub CLI Commands
gh issue 	
# Completes: list, create, view, etc.

# GitHub Repos
gh repo 	
# Completes: clone, fork, view, etc.
```

### Jamf Pro

Simplify Jamf Pro device management:

```zsh
# Jamf Commands
jamf 	
# Completes: policy, recon, version, etc.
```

## Advanced Usage

### Verbose Mode

Enable verbose output to understand more about completion processes:

```zsh
export TIATION_TOOLKIT_VERBOSE=1
```

### Caching

Improve performance with caching:

```zsh
zstyle ':completion:*' use-cache on
zstyle ':completion:*' cache-path ~/.zsh/cache
```

### Custom Configuration

Adapt completions to your specific needs by editing options in your `.zshrc`:

```zsh
# Customize completion styles
zstyle ':completion:*:descriptions' format '%B%d%b'
```

---

