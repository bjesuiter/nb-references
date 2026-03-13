---
title: Git Worktree Management Tools
anchor: CLI tools for easier git worktree management
tags: git, worktree, cli, tools
description: Tools to simplify git worktree creation and management
---

## Git Worktree CLI Tools

### 1. **wtp** (Recommended)
🌳 Powerful Git worktree CLI with automated setup, branch tracking, and smart navigation.

- Branch names with slashes → directory structure
- Auto-organizes worktrees by type/category
- https://github.com/satococoa/wtp

```bash
# Install
cargo install wtp

# Usage
wtp add feature_branch    # Create worktree
wtp list                 # List worktrees
wtp delete feature_branch
```

### 2. **Treekanga**
CLI tool to manage git worktrees intuitively.

- `treekanga add feature_branch` - intelligent creation based on branch existence
- `treekanga delete` - interactive multi-select removal
- https://github.com/coderabbitai/treekanga

### 3. **worktree-cli**
Modern CLI tool for managing git worktrees with ease.

- https://github.com/fnebenfuehr/worktree-cli

### 4. **git-worktree-runner** (CodeRabbit)
Bash-based manager with editor + AI tool integration.

- Per-branch worktree creation
- Config copying, dependency installation, workspace setup
- Built-in Claude/CodeRabbit integration

```bash
git gtr new my-feature --editor  # Create + open in Cursor
git gtr new my-feature --ai      # Create + start AI
```
