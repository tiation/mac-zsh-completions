---
layout: default
title: Tiation macOS Toolkit
---

# Tiation macOS Toolkit

**Enterprise-grade macOS terminal productivity toolkit with intelligent zsh completions**

## Features

- **🔧 Developer Tools**: Comprehensive completions for Xcode, Swift, BBEdit, and development utilities
- **⚙️ System Administration**: Complete coverage of macOS system commands like `installer`, `softwareupdate`, `plutil`
- **📱 Mobile Development**: Full support for iOS/macOS development workflows
- **🎯 Enterprise Ready**: Streamlined for professional development environments
- **🔄 Regular Updates**: Continuously updated with new tools and enhancements

## Available Completions

### Development Tools
| Tool | Description | Status |
|------|-------------|--------|
| `swift` | Swift compiler and REPL | ✅ Complete |
| `xed` | Xcode text editor | ✅ Complete |
| `xcrun` | Xcode command line tools | ✅ Complete |
| `bbedit` | BBEdit text editor | ✅ Complete |

### System Utilities
| Tool | Description | Status |
|------|-------------|--------|
| `installer` | macOS package installer | ✅ Complete |
| `softwareupdate` | System update utility | ✅ Complete |
| `plutil` | Property list utility | ✅ Complete |
| `PlistBuddy` | Property list editor | ✅ Complete |

### Third-Party Tools
| Tool | Description | Status |
|------|-------------|--------|
| `gh` | GitHub CLI | ✅ Complete |
| `jamf` | Jamf Pro management | ✅ Complete |
| `desktoppr` | Desktop management | ✅ Complete |
| `see` | File viewer utility | ✅ Complete |
| `project` | Project management | ✅ Complete |

## Installation

### Quick Install (Recommended)

```zsh
# Clone the repository
git clone https://github.com/tiation/mac-zsh-completions.git ~/.tiation-macos-toolkit

# Add to your .zshrc
echo 'fpath=(~/.tiation-macos-toolkit/completions $fpath)' >> ~/.zshrc
echo 'autoload -U compinit && compinit' >> ~/.zshrc

# Reload your shell
source ~/.zshrc
```

### Manual Installation

1. **Download the toolkit:**
   ```zsh
   git clone https://github.com/tiation/mac-zsh-completions.git
   ```

2. **Update your `.zshrc`:**
   ```zsh
   # Add to your .zshrc file
   fpath=(/path/to/tiation-macos-toolkit/completions $fpath)
   autoload -U compinit && compinit
   ```

3. **Reload your configuration:**
   ```zsh
   source ~/.zshrc
   # If needed, clear completion cache
   rm ~/.zcompdump && compinit
   ```

## Usage Examples

### Swift Development
```zsh
# Tab completion for Swift compiler options
swift build --<TAB>
# Shows: --build-path, --configuration, --verbose, etc.

# Tab completion for Swift package manager
swift package <TAB>
# Shows: init, build, test, clean, etc.
```

### Xcode Tools
```zsh
# Tab completion for xed (Xcode editor)
xed --<TAB>
# Shows: --create, --line, --column, etc.

# Tab completion for xcrun
xcrun --<TAB>
# Shows: --sdk, --toolchain, --find, etc.
```

### System Administration
```zsh
# Tab completion for installer
installer -pkg <TAB>
# Shows available .pkg files

# Tab completion for softwareupdate
softwareupdate --<TAB>
# Shows: --list, --install, --download, etc.
```

## Advanced Features

### Intelligent Context Awareness
- Completions adapt based on current directory context
- Project-specific completions for Xcode projects
- Git repository awareness for development tools

### Enterprise Integration
- Jamf Pro management tool completions
- Enterprise deployment script support
- System administration utilities

## Contributing

We welcome contributions! Here's how to get started:

1. **Fork the repository**
2. **Create a feature branch:** `git checkout -b feature/new-completion`
3. **Add your completion file** to the `completions/` directory
4. **Test thoroughly** with various scenarios
5. **Submit a pull request** with detailed description

## Support & Discussion

- **Issues & Bug Reports**: [GitHub Issues](https://github.com/tiation/mac-zsh-completions/issues)
- **Feature Requests**: [GitHub Discussions](https://github.com/tiation/mac-zsh-completions/discussions)
- **Community Chat**: `#zsh` channel on [MacAdmins Slack](http://macadmins.org)
- **Documentation**: [Wiki](https://github.com/tiation/mac-zsh-completions/wiki)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  Made with ❤️ for macOS developers and system administrators
</div>
