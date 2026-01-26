---
title: Destructive Command Guard (dcg)
anchor: AI agent hook that blocks destructive git/filesystem commands
tags: [ai, safety, security, agent, claude-code, cli, git, shell]
description: High-performance hook for AI coding agents that blocks destructive commands before execution
source_url: https://github.com/Dicklesworthstone/destructive_command_guard
---

## Overview

**dcg** (Destructive Command Guard) is a high-performance hook for AI coding agents that blocks destructive commands before they execute, protecting your work from accidental deletion.

## Supported Agents

- **Claude Code** – full support
- **Gemini CLI** – full support
- **Aider** – limited (git hooks only)
- **Continue** – detection only
- **Codex CLI** – detection only

## Key Features

| Feature | Description |
|---------|-------------|
| **Zero-Config Protection** | Blocks dangerous git/filesystem commands out of the box |
| **49+ Security Packs** | Databases, Kubernetes, Docker, AWS/GCP/Azure, Terraform, and more |
| **Sub-Millisecond Latency** | SIMD-accelerated filtering |
| **Heredoc/Inline Script Scanning** | Catches `python -c "os.remove(...)"` and embedded shell scripts |
| **Smart Context Detection** | Won't block `grep "rm -rf"` (data) but will block `rm -rf /` (execution) |
| **Scan Mode for CI** | Pre-commit hooks and CI integration |
| **Fail-Open Design** | Never blocks your workflow due to timeouts or parse errors |
| **Explain Mode** | `dcg explain "command"` shows exactly why something is blocked |

## Quick Install

```bash
curl -fsSL "https://raw.githubusercontent.com/Dicklesworthstone/destructive_command_guard/master/install.sh?$(date +%s)" | bash -s -- --easy-mode
```

Works on Linux, macOS, and Windows (WSL).

## Example

```bash
$ git reset --hard HEAD~5

# dcg intercepts and blocks:
═══════════════════════════════════════════════════════════════
BLOCKED dcg
───────────────────────────────────────────────────────────────
Reason: git reset --hard destroys uncommitted changes

Command: git reset --hard HEAD~5

Tip: Consider using 'git stash' first to save your changes.
═══════════════════════════════════════════════════════════════
```

## Configuration

### Enable More Protection

```toml
# ~/.config/dcg/config.toml
[packs]
enabled = [
  "database.postgresql",  # Blocks DROP TABLE, TRUNCATE
  "kubernetes.kubectl",   # Blocks kubectl delete namespace
  "cloud.aws",           # Blocks aws ec2 terminate-instances
  "containers.docker",   # Blocks docker system prune
]
```

### Agent-Specific Profiles

```toml
# Trust Claude Code more
[agents.claude-code]
trust_level = "high"
additional_allowlist = ["npm run build"]

# Restrict unknown agents
[agents.unknown]
trust_level = "low"
extra_packs = ["paranoid"]
```

## Use Cases

- Protect against accidental `rm -rf` commands
- Block dangerous git operations (`git reset --hard`, `git clean -fd`)
- Prevent database drops/truncates
- Guard against cloud provider terminate commands
- Block Kubernetes namespace deletions

## Author

Jeffrey Emanuel – Original concept and Python implementation
