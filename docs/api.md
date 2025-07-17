# API Reference

This document provides detailed information about the available completions in the Tiation macOS Toolkit.

## Development Tools

### Swift (`_swift`)

Provides completions for the Swift compiler and package manager.

**Supported Commands:**
- `swift build` - Build Swift packages
- `swift test` - Run Swift tests
- `swift run` - Run Swift executables
- `swift package` - Swift Package Manager commands

**Key Options:**
- `--configuration` - Build configuration (debug/release)
- `--build-path` - Build directory path
- `--package-path` - Package directory path
- `--enable-test-discovery` - Enable test discovery
- `--verbose` - Verbose output

### Xcode Editor (`_xed`)

Completions for the Xcode text editor command.

**Supported Options:**
- `--line` - Jump to specific line number
- `--column` - Jump to specific column
- `--create` - Create file if it doesn't exist
- `--wait` - Wait for editor to close
- `--find` - Find and select text

### Xcode Command Line Tools (`_xcrun`)

Completions for Xcode command line tool runner.

**Supported Options:**
- `--sdk` - SDK to use
- `--toolchain` - Toolchain to use
- `--find` - Find tool path
- `--show-sdk-path` - Show SDK path
- `--show-sdk-version` - Show SDK version

### BBEdit (`_bbedit`)

Completions for BBEdit text editor.

**Supported Options:**
- `--new-window` - Open new window
- `--launch` - Launch BBEdit
- `--resume` - Resume previous session
- `--clean` - Clean up temp files

## System Utilities

### Installer (`_installer`)

Completions for macOS package installer.

**Supported Options:**
- `-pkg` - Package file to install
- `-target` - Installation target
- `-verbose` - Verbose output
- `-dumplog` - Dump installation log
- `-showChoicesXML` - Show choices XML

**File Completion:**
- Automatically completes `.pkg` files in current directory

### Software Update (`_softwareupdate`)

Completions for macOS software update utility.

**Supported Options:**
- `--list` - List available updates
- `--install` - Install updates
- `--download` - Download updates
- `--ignore` - Ignore specific updates
- `--reset-ignored` - Reset ignored updates
- `--schedule` - Set automatic update schedule

### Property List Utility (`_plutil`)

Completions for property list manipulation.

**Supported Options:**
- `-lint` - Check syntax
- `-convert` - Convert format
- `-insert` - Insert value
- `-replace` - Replace value
- `-remove` - Remove value
- `-extract` - Extract value

**File Completion:**
- Automatically completes `.plist` files

### PlistBuddy (`_PlistBuddy`)

Completions for advanced property list editing.

**Supported Commands:**
- `Help` - Show help
- `Exit` - Exit PlistBuddy
- `Save` - Save changes
- `Revert` - Revert changes
- `Clear` - Clear all entries
- `Print` - Print values
- `Set` - Set values
- `Add` - Add entries
- `Copy` - Copy entries
- `Delete` - Delete entries
- `Merge` - Merge plists

## Third-Party Tools

### GitHub CLI (`_gh`)

Completions for GitHub command line interface.

**Supported Commands:**
- `gh repo` - Repository operations
- `gh issue` - Issue management
- `gh pr` - Pull request management
- `gh workflow` - GitHub Actions workflows
- `gh release` - Release management

### Jamf Pro (`_jamf`)

Completions for Jamf Pro management tool.

**Supported Commands:**
- `jamf policy` - Run policies
- `jamf recon` - Update inventory
- `jamf version` - Show version
- `jamf help` - Show help
- `jamf checkJSSConnection` - Test server connection

### Desktop Manager (`_desktoppr`)

Completions for desktop management utility.

**Supported Options:**
- `--help` - Show help
- `--version` - Show version
- `--verbose` - Verbose output

### File Viewer (`_see`)

Completions for file viewing utility.

**Supported Options:**
- `--help` - Show help
- `--version` - Show version

### Project Management (`_project`)

Completions for project management utility.

**Supported Commands:**
- `project list` - List projects
- `project create` - Create project
- `project delete` - Delete project
- `project info` - Show project info

## Configuration

### Environment Variables

The toolkit supports several environment variables for customization:

- `TIATION_TOOLKIT_VERBOSE` - Enable verbose completion output
- `TIATION_TOOLKIT_CACHE` - Enable completion caching
- `TIATION_TOOLKIT_DEBUG` - Enable debug mode

### Zsh Styles

You can customize completion behavior using zsh styles:

```zsh
# Enable completion caching
zstyle ':completion:*' use-cache on
zstyle ':completion:*' cache-path ~/.zsh/cache

# Customize completion format
zstyle ':completion:*:descriptions' format '%B%d%b'
zstyle ':completion:*:warnings' format 'No matches for: %d'

# Group completions
zstyle ':completion:*' group-name ''
```

## File Patterns

### Completion Patterns

Different commands support different file pattern completions:

- **Swift files**: `*.swift`
- **Package files**: `*.pkg`
- **Property lists**: `*.plist`
- **Xcode projects**: `*.xcodeproj`, `*.xcworkspace`
- **Source files**: `*.{swift,m,mm,cpp,c,h}`

### Directory Patterns

Some completions are context-aware and will complete based on directory structure:

- Xcode project directories
- Swift package directories
- Git repositories
- Framework directories

## Advanced Features

### Context Awareness

The toolkit includes intelligent context awareness:

- **Git Integration**: Completions adapt based on git repository state
- **Project Detection**: Automatic detection of Xcode projects and Swift packages
- **Path Intelligence**: Smart path completion based on command context

### Performance Optimizations

- **Caching**: Completion results are cached for better performance
- **Lazy Loading**: Completions are loaded only when needed
- **Incremental Updates**: Only changed completions are regenerated

### Error Handling

The toolkit includes robust error handling:

- **Graceful Degradation**: Falls back to basic completion if advanced features fail
- **Error Messages**: Clear error messages for debugging
- **Logging**: Optional logging for troubleshooting

## Integration

### Oh-My-Zsh Integration

The toolkit integrates seamlessly with Oh-My-Zsh:

```zsh
# Plugin loading
plugins=(... tiation-macos-toolkit)

# Custom configuration
TIATION_TOOLKIT_VERBOSE=1
```

### Custom Completion Integration

You can extend the toolkit with custom completions:

```zsh
# Add custom completion directory
fpath=(~/.local/completions $fpath)

# Load custom completions
autoload -U compinit && compinit
```

## Troubleshooting

### Common Issues

1. **Completions not loading**
   - Check `fpath` includes completion directory
   - Verify `compinit` is called after setting `fpath`
   - Clear completion cache: `rm ~/.zcompdump && compinit`

2. **Slow completion performance**
   - Enable caching: `zstyle ':completion:*' use-cache on`
   - Reduce completion scope for large directories

3. **Conflicting completions**
   - Load toolkit completions last
   - Use `unsetopt AUTO_REMOVE_SLASH` if needed

### Debug Mode

Enable debug mode for troubleshooting:

```zsh
export TIATION_TOOLKIT_DEBUG=1
# Completions will show debug information
```

## Version Compatibility

### Zsh Versions

- **Minimum**: zsh 5.3 (macOS High Sierra)
- **Recommended**: zsh 5.7+ (macOS Catalina+)
- **Tested**: zsh 5.8, 5.9

### macOS Versions

- **Minimum**: macOS 10.15 (Catalina)
- **Recommended**: macOS 12.0+ (Monterey)
- **Tested**: macOS 11, 12, 13, 14

### Tool Versions

Completions are tested with the following tool versions:

- **Swift**: 5.5+
- **Xcode**: 13.0+
- **GitHub CLI**: 2.0+
- **Jamf Pro**: 10.35+

## Contributing

To contribute new completions or improvements:

1. Follow the [Contributing Guidelines](contributing.md)
2. Use the completion templates provided
3. Test thoroughly across different scenarios
4. Update this API reference with new features

## Support

For API questions or issues:

- Open an issue on GitHub
- Join the MacAdmins Slack #zsh channel
- Check the troubleshooting section
