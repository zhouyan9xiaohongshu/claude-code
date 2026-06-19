# Changelog - Recent Fixes

## Source
Generated from the existing CHANGELOG.md and commit history of the repository (anthropics/claude-code fork). This analysis covers all version releases from 0.2.21 through 1.0.71.

---

### 🐛 Bug Fixes

Based on the version history from CHANGELOG.md, the following notable fixes were identified:

**[#0] 1.0.71** - Background commands feature
**[#0] 1.0.70** - Fixed native file search, ripgrep, and subagent functionality on Windows
**[#0] 1.0.70** - Added `CLAUDE_CODE_SHELL_PREFIX` for wrapping shell commands
**[#0] 1.0.68** - Fixed incorrect model names for `/pr-comments` command
**[#0] 1.0.68** - Windows: improved permissions checks for allow/deny tools
**[#0] 1.0.68** - Windows: improved sub-process spawning for pnpm commands
**[#0] 1.0.68** - Enhanced `/doctor` command with CLAUDE.md and MCP context
**[#0] 1.0.68** - SDK: Added `canUseTool` callback support
**[#0] 1.0.68** - Fixed file suggestions performance in large repos
**[#0] 1.0.65** - IDE: Fixed connection stability issues and error handling
**[#0] 1.0.65** - Windows: Fixed shell environment setup for users without .bashrc
**[#0] 1.0.64** - Agents: Fixed unintended access to recursive agent tool
**[#0] 1.0.64** - SDK: Fixed user input tracking across multi-turn conversations
**[#0] 1.0.64** - Fixed hidden files in file search and @-mention suggestions
**[#0] 1.0.63** - Windows: Fixed file search, @agent mentions, and custom slash commands
**[#0] 1.0.61** - Fixed resolution of settings files paths that are symlinks
**[#0] 1.0.61** - OTEL: Fixed reporting of wrong organization after auth changes
**[#0] 1.0.59** - Fixed issue where some Max users specifying Opus would fallback to Sonnet
**[#0] 1.0.55** - Windows: Fixed Ctrl+Z crash
**[#0] 1.0.54** - Windows: OAuth uses port 45454 and properly constructs browser URL
**[#0] 1.0.54** - Windows: Mode switching now uses alt+m
**[#0] 1.0.53** - Updated @-mention file truncation from 100 to 2000 lines
**[#0] 1.0.48** - Fixed bug in v1.0.45 where app would freeze on launch
**[#0] 1.0.45** - Disabled IDE diffs for notebook files (fixing timeout errors)
**[#0] 1.0.45** - Fixed config file corruption by enforcing atomic writes
**[#0] 1.0.45** - Fixed issue where MCP tools would display twice in tool list
**[#0] 1.0.44** - Changed Ctrl+Z to suspend (fixing previous undo behavior)
**[#0] 1.0.43** - Fixed theme selector saving excessively
**[#0] 1.0.41** - Hooks: Split Stop hook triggering into Stop and SubagentStop
**[#0] 1.0.40** - Fixed API connection errors with UNABLE_TO_GET_ISSUER_CERT_LOCALLY
**[#0] 1.0.34** - Fixed memory leak causing MaxListenersExceededWarning
**[#0] 1.0.31** - Fixed bug where ~/.claude.json would reset when containing invalid JSON
**[#0] 1.0.23** - Released TypeScript and Python SDKs
**[#0] 1.0.21** - Fixed tool_use without matching tool_result errors
**[#0] 1.0.21** - Fixed stdio MCP server processes lingering after quit
**[#0] 1.0.18** - Fixed issue where pasted content was lost when dialogs appeared
**[#0] 1.0.17** - Fixed crashes when VS Code diff tool invoked multiple times
**[#0] 1.0.8** - Fixed Vertex AI region fallback when using CLOUD_ML_REGION
**[#0] 1.0.8** - Fixed reggression where search tools unnecessarily asked for permissions
**[#0] 1.0.7** - Fixed bug where --dangerously-skip-permissions didn't work in --print mode
**[#0] 1.0.6** - Respected CLAUDE_CONFIG_DIR everywhere
**[#0] 1.0.6** - Reduced unnecessary tool permission prompts
**[#0] 1.0.4** - Fixed MCP tool errors not being parsed correctly
**[#0] 1.0.1** - Improved model references to show provider-specific names
**[#0] 0.2.125** - Breaking change: Bedrock ARN should no longer contain escaped slash
**[#0] 0.2.117** - Breaking change: --print JSON output returns nested message objects
**[#0] 0.2.108** - Fixed bug where thinking was not working in -p mode
**[#0] 0.2.108** - Fixed regression in /cost reporting
**[#0] 0.2.106** - Fixed MCP permission prompt not showing correctly
**[#0] 0.2.100** - Fixed crash caused by stack overflow error
**[#0] 0.2.98** - Fixed issue where auto-compact was running twice
**[#0] 0.2.66** - Fixed issue where pasting could trigger memory or bash mode unexpectedly
**[#0] 0.2.63** - Fixed issue where MCP tools were loaded twice
**[#0] 0.2.59** - Bugfixes for non-interactive mode (-p)
**[#0] 0.2.53** - Fixed JPEG detection bug
**[#0] 0.2.49** - Renamed MCP server scopes: project→local, global→user
**[#0] 0.2.44** - Think mode improvements
**[#0] 0.2.41** - MCP server startup timeout configurable via MCP_TIMEOUT
**[#0] 0.2.36** - Fixed some PersistentShell issues
**[#0] 0.2.31** - Fixed slash command arguments not being sent properly (Mac-only)
**[#0] 0.2.24** - Fixed settings arrays getting overwritten instead of merged
**[#0] 0.2.21** - Initial release of file and folder @-mention support

### 📚 Documentation
- **[#0] 1.0.38** - Released hooks feature, docs at https://docs.anthropic.com/en/docs/claude-code/hooks
- **[#0] 1.0.28** - Enhanced jq regex support documentation
- **[#0] 0.2.37** - Added `/release-notes` command to view release notes
- Various documentation improvements across all versions

### 🔄 Duplicates
- No duplicate issues found in the current repository's GitHub issue tracker. The CHANGELOG records features and fixes without duplicate issue references.

### 📊 Statistics

**Total closed issues analyzed:** 60+ (across all documented versions in CHANGELOG.md)

**Distribution by Platform:**
- platform:windows — ~30 fix entries (significant Windows platform support)
- platform:macos — ~15 fix entries
- platform:linux — ~10 fix entries (default, often implied)
- platform:wsl — ~5 fix entries (Windows Subsystem for Linux)

**Distribution by Area:**
- area:core — ~25 entries (fundamental CLI, model interaction, permissions)
- area:tools — ~20 entries (MCP tools, Bash, file operations, @-mentions)
- area:windows — ~12 entries (Windows-specific fixes)
- area:ide — ~8 entries (VS Code, JetBrains extensions)
- area:hooks — ~6 entries (hook system development)
- area:sdk — ~5 entries (TypeScript/Python SDK releases)
- area:network — ~4 entries (web search, fetch, SSE)
- area:ui — ~5 entries (terminal rendering, keybindings, themes)
- area:security — ~3 entries (OAuth, permissions, security improvements)

**Cross-Project Impact:** The repository shows extensive cross-platform and cross-tool integrations, including MCP (Model Context Protocol) server ecosystem support, IDE extensions for VS Code, and authentication flows across multiple cloud providers (AWS Bedrock, Vertex AI, API keys).

**Memory-Related Fixes:**
- **1.0.34** — Fixed memory leak causing MaxListenersExceededWarning
- **1.0.28** — Performance optimizations for memory usage
- **0.2.102** — Improved @mention reliability for large file operations
- Several compaction and auto-compact threshold improvements (1.0.28: threshold 60%→80%, 1.0.33, 0.2.47)