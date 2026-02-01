---
title: bgproc - Simple Process Manager for Agents
anchor: Manage background processes for AI agents with JSON output
tags: [process-manager, background-processes, agents, dev-tools, npm]
description: CLI tool for managing dev servers and background processes with agent-friendly JSON output
source_url: https://github.com/ascorbic/bgproc
author: Matt Kane
---

## Summary

**bgproc** is a simple process manager designed for AI agents. It manages background processes like dev servers from the command line with agent-friendly JSON output and easy status checking.

## Installation

```bash
npm install -g bgproc
# or
npx bgproc start -n myserver -- npm run dev
```

## Core Commands

| Command | Description |
|---------|-------------|
| `bgproc start -n <name> -- <cmd>` | Start a process |
| `bgproc start -n <name> -w -- <cmd>` | Start and wait for port |
| `bgproc status <name>` | Check status (JSON output) |
| `bgproc logs <name>` | View logs |
| `bgproc list` | List all processes |
| `bgproc stop <name>` | Stop a process |
| `bgproc clean <name>` | Clean up dead processes |

## Features

- **JSON Output:** All commands output JSON to stdout, errors to stderr
- **Port Detection:** Auto-detects listening ports via lsof (checks child processes)
- **Wait for Port:** `--wait-for-port` blocks until port is detected
- **Force Restart:** `--force` kills existing process before starting
- **Duplicate Prevention:** Prevents multiple processes with same name
- **Log Management:** Stdout/stderr captured, capped at 1MB
- **Timeout Support:** `--timeout 60` kills after N seconds
- **CWD Filtering:** Filter process list by working directory

## AI Agent Workflow

```
1. bgproc start -n devserver -- npm run dev    # Start process
2. bgproc status devserver                     # Check if running, get port
3. bgproc logs devserver                       # View output if wrong
4. bgproc stop devserver                       # Stop when done
```

## Add as Skill for AI Assistants

```bash
npx skills add ascorbic/bgproc
```

Works with Claude Code, Cursor, Codex, and other AI coding tools.

## AGENTS.md Integration

```markdown
## Background Processes

Use `bgproc` to manage dev servers and background processes. All commands output JSON.
```

## Platform Support

- macOS ✅
- Linux ✅
- Windows ❌ (not supported)
