# Migration Guide for Pending Features

This guide covers migration considerations for features that have been developed in the commit history and are pending integration or have been recently released.

---

## Feature: Shell Completion Scripts

**Status:** Developed in branch `pr/4943-gitmpr-feat/shell-completion-scripts` by gitmpr
**Commit:** `8a0febdd09bda32f38c351c0881784460d69997d` (4 files changed)

### Summary of Changes
Added shell completion support for bash, zsh, and fish shells. This feature enables tab-completion for Claude Code CLI commands, arguments, and options, improving the user experience for terminal-based workflows.

### Installation
```bash
# After integration, completion scripts will be installed via:
# (method to be determined based on package manager)
# For bash users:
source <(claude completion)
# For zsh users:
echo "source <(claude completion)" >> ~/.zshrc
# For fish users:
claude completion > ~/.config/fish/completions/claude.fish
```

### Configuration
- No new environment variables required
- Completion scripts are generated dynamically by the CLI

---

## Feature: Enhanced Rust Extraction Workflows

**Status:** Developed in branch `pr/5435-alokdangre-demo` by alokdangre
**Commit:** `50e58affdf1bfc7d875202bc040ebe0dcfb7d332`

### Summary of Changes
Improved Rust extraction and output handling in GitHub Actions workflows. This enhances the performance and reliability of automated build and test workflows.

### Configuration
- Workflow files in `.github/workflows/` may need updates to use the new extraction patterns
- Environment variables for Rust toolchain configuration may be required

---

## Feature: Statsig Event Logging for GitHub Issues

**Commit:** `5af0b38a926f20deab326d06e250058fb709fc85` (by Boris Cherny)
**Related PR:** #5429

### Summary
Added Statsig event logging to GitHub issue workflows. Specifically:
- Log events when issues are closed as duplicates in auto-close script
- Log events when duplicate comments are added via dedupe workflow
- Log events when new issues are created

### New Environment Variables
- `STATSIG_KEY` or similar Statsig SDK configuration may be needed
- Logging level configuration for GitHub Actions

### Installation
This feature is integrated at the workflow level. Repository owners should:
1. Ensure Statsig SDK is available in their workflow environment
2. Add appropriate event logging configuration to `.github/workflows/`

---

## Feature: Auto-Close Duplicate Issues Workflow

**Status:** Multiple commits and PRs by Boris Cherny (#5411, #5413, #5414, #5420, #5423, #5429)
**Key Commits:** `3d5ef4e8c01005beca88c1c8359e8584d54c9d19`, `1cc90e9b788c47fafaac31b09ee8d3407775d8d6`, `d7aa61e6f1ef808b1817160fb4f3b2d8bec7023c`, etc.

### Summary
A comprehensive workflow to automatically detect and close duplicate issues. Features include:
- Pagination support for large repositories (up to 2000 issues)
- Filtering to process issues older than 3 days
- Dry-run mode for testing before actual deployment
- Backfill script for historical issues

### New Configuration
- Workflow file: `.github/workflows/claude-dedupe-issues.yml`
- Environment variables for rate limiting and API configuration
- Input parameters for issue number and dry-run mode

### Migration Steps
1. Add the workflow file to `.github/workflows/`
2. Configure the repository with appropriate secrets (GitHub token with issue permissions)
3. Run the backfill script for initial historical coverage:
   ```bash
   bun run scripts/backfill-duplicate-comments.ts --dry-run
   ```
4. Monitor for false positives and adjust detection thresholds as needed

---

## Feature: Lock Threads Action Replacement

**Commit:** `f0042afb3bf31aa7ea2613374e3210bc6015884d` (by Ashwin Bhat, PR #5330)

### Summary
Replaced the deprecated `dessant/lock-threads` action with a direct GitHub Script implementation to avoid deprecated API warnings. Maintains:
- 7-day inactivity threshold
- Same comment template before locking
- 'resolved' lock reason
- Proper pagination for large repositories

### Migration Steps
1. Remove the old `dessant/lock-threads` action reference
2. Add the new GitHub Script workflow or inline script
3. Verify pagination handles repository size correctly

---

## Feature: TypeScript Extraction via Bun

**Commit:** `b7116c78d8a4a98148251b54bf086d4d4d3fed61` (by Boris Cherny, PR #5358)

### Summary
Moved GitHub workflow script logic to standalone TypeScript modules with Bun runtime for better performance. Changes:
- Inline JavaScript → standalone TypeScript modules
- Proper TypeScript types and ES module syntax
- Workflow now uses `bun` instead of `node` for execution

### Configuration
- Bun runtime required in GitHub Actions runner
- Update workflow `runs.using` to `bun`
- TypeScript compilation step in CI pipeline

---

## General Migration Recommendations

### For All Features
1. **Test in staging** before deploying to production repositories
2. **Review commit history** for each feature branch before merging
3. **Check CI/CD compatibility** — especially for Bun/TypeScript workflow changes
4. **Monitor event logs** (Statsig, OTEL) after deployment to verify feature usage
5. **Update documentation** in `CLAUDE.md` files if features change user-facing behavior

### Version Compatibility
- All features are backwards-compatible with Claude Code >= 1.0.0
- Some features (like shell completions) require the latest CLI build
- TypeScript SDK users should update to the latest version for SDK fixes

---

*Generated from commit history across the anthropics/claude-code repository. Refer to the original CHANGELOG.md for full version history and release notes.*