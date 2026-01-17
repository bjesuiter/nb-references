---
title: Beans CLI - Local Issue Tracker
anchor: How to use beans for tracking issues alongside code
tags: [cli, issue-tracker, ai-agents, markdown, project-management]
description: A CLI-based flat-file issue tracker for humans and robots that stores beans as markdown files in .beans/ directory
source_url: https://github.com/hmans/beans
---

## Beans CLI Reference

**What it is:** A lightweight, flat-file issue tracker that stores issues as markdown files in a `.beans/` directory alongside your code. Designed for humans and AI coding agents.

### Installation

```bash
brew install hmans/beans/beans
# or
go install github.com/hmans/beans@latest
```

### Setup in a Project

```bash
beans init  # Creates .beans/ directory and .beans.yml config
```

### Core Commands

| Command | Description |
|---------|-------------|
| `beans help` | Show all commands |
| `beans create` | Create a new bean (issue/task) |
| `beans list` | List all beans |
| `beans show <id>` | Show a bean's contents |
| `beans update` | Update a bean's properties |
| `beans archive` | Delete all archived beans |
| `beans tui` | Open interactive TUI |
| `beans prime` | Output instructions for AI coding agents |
| `beans roadmap` | Generate Markdown roadmap from milestones/epics |
| `beans check` | Validate configuration and bean integrity |

### Agent Integration

Add to your `AGENTS.md`, `CLAUDE.md`, or `.claude/settings.json`:

```markdown
**IMPORTANT**: before you do anything else, run the `beans prime` command and heed its output.
```

Or in `.claude/settings.json`:
```json
{
  "hooks": {
    "SessionStart": [{ "type": "command", "command": "beans prime" }],
    "PreCompact": [{ "type": "command", "command": "beans prime" }]
  }
}
```

### Example Agent Workflows

- "Are there any tasks we should track? If so, create beans for them."
- "What should we work on next?"
- "It's time to tackle myproj-123."
- "Please inspect this project's beans and reorganize them into epics."

### Key Features

- Plain Markdown files in `.beans/` — version control friendly
- GraphQL query engine for agents to get context efficiently
- Completed beans serve as project memory
- Built-in TUI for terminal browsing
- Generates Markdown roadmaps from milestones/epics

### Stability Warning

Beans is under heavy development. APIs and data formats may change. Follow release notes closely.
