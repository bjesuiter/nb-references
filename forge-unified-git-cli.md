---
title: forge - Unified Git Forge CLI
anchor: When I need one CLI to work with GitHub, GitLab, Gitea/Forgejo, and Bitbucket
tags: [git, cli, github, gitlab, gitea, forges, automation]
description: Go library and CLI for working with git forges through a single interface. Supports GitHub, GitLab, Gitea/Forgejo, and Bitbucket Cloud.
source_url: https://github.com/git-pkgs/forge
---

## Summary

A unified CLI and Go library for working with multiple git forges (GitHub, GitLab, Gitea/Forgejo, Bitbucket Cloud) through a single interface.

## CLI Commands

```bash
forge repo view
forge issue list --state open
forge pr create --title "Fix bug" --head fix-branch
forge release list
forge ci list
forge branch list
forge label list
forge api repos/{owner}/{repo}
```

## Features

- **Auto-detection** - Detects which forge to use from your git remote
- **Authentication** - `forge auth login` for interactive or flag-based token setup
- **Unified API** - Same commands work across all supported forges
- **Config precedence** - CLI flags → env vars → .forge file → ~/.config/forge/config

## Use Cases

- Scripts that work with multiple git hosting platforms
- Cross-forge automation without learning different CLIs
- Projects that move between hosting providers
