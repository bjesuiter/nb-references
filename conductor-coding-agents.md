---
title: Conductor - Team of Coding Agents on Your Mac
anchor: Run parallel Claude Code + Codex agents in isolated workspaces with git worktrees
tags: [agent, mac, coding, parallel, claude-code, codex, git-worktree]
description: Conductor runs multiple coding agents in parallel with isolated workspaces, reviewing and merging their changes
source_url: https://www.conductor.build/
source_url_alt: https://bsky.app/profile/hmans.dev/post/3mcpkxzxffc2a
---

# Conductor Reference

**What it is:** A tool to run a team of coding agents on your Mac. Deploy parallel Claude Code + Codex agents in isolated workspaces, see what they're working on, and merge their changes.

Website: https://www.conductor.build/

---

## How It Works

1. **Add your repo** — Conductor clones it and works entirely on your Mac
2. **Deploy agents** — Each Claude Code agent gets an isolated workspace
3. **Conduct** — See who's working, what needs attention, and review code

---

## Key Features

- **Parallel agents** — Run Claude Code and Codex simultaneously
- **Isolated workspaces** — Each agent gets its own git worktree
- **Visual oversight** — See at a glance what agents are working on
- **Review & merge** — Inspect changes before merging
- **Local execution** — All runs on your Mac, no external services

---

## Technical Details

### Git Worktrees

- Each workspace is a new git worktree
- No separate clones needed
- Clean isolation between agents

### Supported Agents

| Agent | Status |
|-------|--------|
| Claude Code | ✅ Supported |
| Codex | ✅ Supported |

### Billing

- Conductor uses your existing Claude Code login
- Works with API key, Pro, or Max plan

---

## Use Cases

- **Parallel implementation** — Multiple agents work on different features
- **Code review** — One agent writes, another reviews
- **Exploration** — One agent researches, another implements
- **Testing** — Agents work in parallel on different test suites

---

## Why It Matters

- **Faster development** — Parallel work = faster completion
- **Better oversight** — See everything at a glance
- **Safety** — Review before merging
- **Simplicity** — No complex infrastructure

---

## Related

- See [Claude Code](../claude-code-setup.md) for agent setup
- See [Multi-agent patterns](../multi-agent-organization-strategies.md)
