---
title: GitPick - Modern Degit Alternative
anchor: Zero-dependency project scaffolding tool that clones files/folders/branches from GitHub without .git directory
tags: [git, scaffolding, degit-alternative, cli, project-starter]
description: GitPick - drop-in replacement for degit with more features and zero dependencies
source_url: https://npmjs.com/package/gitpick
---

## Summary

**GitPick** is a modern, zero-dependency alternative to degit for cloning files, folders, branches, commits, or entire repos from GitHub without the `.git` directory.

### Key Features
- **Zero dependencies** - Unpacked <35KB
- **Drop-in replacement** for degit with more features
- **Flexible URLs** - Copy-paste any GitHub URL, no editing needed
- **Auto-detection** - Detects branches/targets like `git clone`
- **Shorthands work** - `owner/repo` or full URLs
- **Overwrite support** - `-o` flag to replace existing files
- **Watch mode** - `--watch` with intervals (15s, 1m, 1h)
- **Submodules** - `-r` recursive cloning
- **Private repos** - Use PAT in URL

### Usage Examples
```bash
# Clone entire repo (without .git)
npx gitpick owner/repo
npx gitpick https://github.com/owner/repo

# Clone a folder
npx gitpick owner/repo/tree/main/path/to/folder

# Clone a file
npx gitpick owner/repo/blob/main/path/to/file

# Clone a branch
npx gitpick owner/repo -b canary

# Clone a commit SHA
npx gitpick owner/repo -b cc8e93

# Clone with submodules
npx gitpick owner/repo -r

# Watch and sync every 30s
npx gitpick owner/repo -w 30s

# Private repo with token
npx gitpick https://<token>@github.com/owner/repo

# Overwrite existing files
npx gitpick owner/repo -o
```

### Install
```bash
npm install -g gitpick
gitpick owner/repo
```

### Related
- [tiged](https://github.com/tiged/tiged) - degit fork
- [giget](https://github.com/unjs/giget) - alternative approach
