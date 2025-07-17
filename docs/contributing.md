# Contributing Guidelines

We welcome contributions to the Tiation macOS Toolkit! This guide will help you get started.

## Getting Started

### Prerequisites

- macOS 10.15 or later
- zsh shell
- Git
- Basic knowledge of zsh completion system

### Development Setup

1. **Fork the repository**
   ```zsh
   # Fork on GitHub, then clone your fork
   git clone https://github.com/YOUR_USERNAME/mac-zsh-completions.git
   cd mac-zsh-completions
   ```

2. **Create a development branch**
   ```zsh
   git checkout -b feature/new-completion
   ```

3. **Test your local changes**
   ```zsh
   # Add the local completions to your fpath
   fpath=($(pwd)/completions $fpath)
   autoload -U compinit && compinit
   ```

## Creating Completions

### File Structure

Completion files should be placed in the `completions/` directory with the naming convention `_command`:

```
completions/
├── _bbedit
├── _swift  
├── _xed
└── _your_new_completion
```

### Basic Completion Template

Here's a basic template for creating a new completion:

```zsh
#compdef your_command

_your_command() {
  local context state state_descr line
  typeset -A opt_args

  _arguments \
    '(-h --help)'{-h,--help}'[show help message]' \
    '(-v --verbose)'{-v,--verbose}'[enable verbose output]' \
    '*:file:_files'

  return 0
}

_your_command "$@"
```

### Advanced Features

#### Subcommands

For commands with subcommands:

```zsh
_your_command() {
  local context state state_descr line
  typeset -A opt_args

  _arguments \
    '1: :->command' \
    '*:: :->args'

  case $state in
    command)
      _describe 'command' '(
        init:"initialize project"
        build:"build project"
        test:"run tests"
      )'
      ;;
    args)
      case $words[1] in
        init)
          _arguments \
            '--name[project name]:name:' \
            '--template[template type]:template:(basic advanced)'
          ;;
        build)
          _arguments \
            '--release[release build]' \
            '--debug[debug build]'
          ;;
      esac
      ;;
  esac
}
```

#### File Completion

For file-specific completions:

```zsh
# Complete only .pkg files
'*:package file:_files -g "*.pkg"'

# Complete directories only
'*:directory:_directories'

# Complete specific file types
'*:source file:_files -g "*.{swift,m,mm,cpp,c}"'
```

## Testing

### Manual Testing

1. **Install your completion locally**
   ```zsh
   fpath=($(pwd)/completions $fpath)
   autoload -U compinit && compinit
   ```

2. **Test the completion**
   ```zsh
   your_command <TAB>
   your_command --<TAB>
   ```

3. **Test edge cases**
   - Empty completions
   - Long option lists
   - File completions
   - Subcommand completions

### Automated Testing

We recommend testing with different scenarios:

```zsh
# Test in a clean environment
zsh -c 'fpath=(completions $fpath); autoload -U compinit && compinit; your_command <TAB>'

# Test with different zsh versions
zsh --version
```

## Code Style

### Formatting

- Use 2-space indentation
- Use single quotes for strings when possible
- Include descriptive help text for all options
- Group related options together

### Documentation

- Add inline comments for complex logic
- Include a header comment with command description
- Document any special requirements or dependencies

### Example

```zsh
#compdef mycommand
# Completion for mycommand - A tool for managing projects
# Requires: mycommand >= 2.0

_mycommand() {
  local context state state_descr line
  typeset -A opt_args

  # Global options available to all subcommands
  local global_opts=(
    '(-h --help)'{-h,--help}'[show help message]'
    '(-v --verbose)'{-v,--verbose}'[enable verbose output]'
    '(-q --quiet)'{-q,--quiet}'[suppress output]'
  )

  _arguments \
    $global_opts \
    '1: :->command' \
    '*:: :->args'

  case $state in
    command)
      _describe 'command' '(
        init:"initialize a new project"
        build:"build the project"
        test:"run project tests"
        clean:"clean build artifacts"
      )'
      ;;
    args)
      case $words[1] in
        init)
          _arguments \
            $global_opts \
            '--name[project name]:name:' \
            '--template[template type]:template:(basic advanced minimal)'
          ;;
        build)
          _arguments \
            $global_opts \
            '(-r --release)'{-r,--release}'[build in release mode]' \
            '(-d --debug)'{-d,--debug}'[build in debug mode]' \
            '--target[build target]:target:(all main tests)'
          ;;
      esac
      ;;
  esac
}

_mycommand "$@"
```

## Submission Process

### Before Submitting

1. **Test thoroughly**
   - Test all options and subcommands
   - Verify help text is accurate
   - Check for typos and formatting

2. **Document your changes**
   - Update README.md if needed
   - Add usage examples
   - Update the completion status table

3. **Follow the checklist**
   - [ ] Completion file follows naming convention
   - [ ] All options have help text
   - [ ] File completions work correctly
   - [ ] Tested with different zsh versions
   - [ ] No conflicts with existing completions

### Pull Request

1. **Create a descriptive PR title**
   ```
   Add completion for mycommand
   ```

2. **Include a detailed description**
   - What command does this complete?
   - What features are supported?
   - Any special requirements?
   - Testing performed

3. **Reference related issues**
   ```
   Closes #123
   ```

## Review Process

### What We Look For

- **Correctness**: Does the completion work as expected?
- **Completeness**: Are all major options covered?
- **Performance**: Does it complete quickly?
- **Compatibility**: Works with different zsh versions?
- **Style**: Follows project conventions?

### Feedback

- We'll provide constructive feedback
- Changes may be requested
- We'll help you improve the completion

## Recognition

Contributors will be:
- Listed in the README acknowledgments
- Credited in git history
- Invited to join the maintainer team (for significant contributions)

## Questions?

- Open an issue for questions
- Join the discussion in MacAdmins Slack #zsh channel
- Email the maintainers: [tiatheone@protonmail.com](mailto:tiatheone@protonmail.com)

Thank you for contributing to the Tiation macOS Toolkit!
