---
title: NanoClaw - Minimal OpenClaw Fork with Container Isolation
anchor: Claude assistant running in Apple containers with secure filesystem isolation
tags: [ai-agent, openclaw, apple-container, docker, security, claude-code, minimal]
description: A minimal, secure fork of OpenClaw that runs Claude Code in containers with filesystem isolation
source_url: https://github.com/gavrielc/nanoclaw
---

## My Reference

### What is NanoClaw?

NanoClaw is a personal Claude assistant that runs securely in containers. It's a minimal fork of OpenClaw designed to be understood in 8 minutes, with one process, a handful of files, and real OS-level isolation.

### Why NanoClaw?

**Problem with OpenClaw:**
- 52+ modules, 8 config files, 45+ dependencies
- Security is application-level (allowlists, pairing codes)
- Everything runs in one Node process with shared memory
- Too complex to understand and audit

**NanoClaw's Solution:**
- Single Node.js process, single codebase
- Agents run in Linux containers with filesystem isolation
- Not behind permission checks - OS-level security
- One process, a few source files, no microservices

### Architecture

```
┌─────────────────────────────────────────────────┐
│ WhatsApp (baileys)                              │
└───────────────────┬─────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────┐
│ SQLite Database                                 │
└───────────────────┬─────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────┐
│ Polling Loop                                    │
└───────────────────┬─────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────┐
│ Container Runner (Apple Container or Docker)    │
│ - Claude Agent SDK execution                    │
│ - Isolated filesystem mounts                    │
└───────────────────┬─────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────┐
│ Response → WhatsApp                             │
└─────────────────────────────────────────────────┘
```

### Key Files
- `src/index.ts` - Main app: WhatsApp connection, routing, IPC
- `src/container-runner.ts` - Spawns agent containers
- `src/task-scheduler.ts` - Runs scheduled tasks
- `src/db.ts` - SQLite operations
- `groups/*/CLAUDE.md` - Per-group memory files

### Container Isolation

**Apple Container (macOS):**
- Lightweight, fast, optimized for Apple Silicon
- Agents can only access explicitly mounted directories
- Bash access is safe - runs inside container, not on host

**Docker (macOS/Linux):**
- Full support, chosen during `/setup`
- Linux hosts use Docker automatically
- Same isolation guarantees

### Features

- **WhatsApp I/O** - Message Claude from your phone
- **Isolated group context** - Each group has:
  - Own `CLAUDE.md` memory file
  - Isolated filesystem
  - Separate container sandbox with only mounted directories
- **Main channel** - Private self-chat for admin control
- **Scheduled tasks** - Recurring jobs that run Claude and message back
- **Web access** - Search and fetch content
- **Optional integrations** - Add Gmail and more via skills

### Usage Examples

```
@Andy send an overview of the sales pipeline every weekday morning at 9am
@Andy review the git history for the past week each Friday and update the README
@Andy every Monday at 8am, compile news on AI developments from Hacker News

# From main channel (admin):
@Andy list all scheduled tasks across groups
@Andy pause the Monday briefing task
@Andy join the Family Chat group
```

### Philosophy

**Small enough to understand:**
- One process, a few source files
- No microservices, no message queues
- Claude Code guides you through setup

**Secure by isolation:**
- Agents run in Linux containers
- Can only see explicitly mounted directories
- Bash access is safe because it runs in container

**AI-native:**
- No installation wizard; Claude Code guides setup
- No monitoring dashboard; ask Claude what's happening
- No debugging tools; describe the problem, Claude fixes it

**Skills over features:**
- Don't add features to codebase
- Contribute skills (`.claude/skills/add-xyz/SKILL.md`)
- Users run skills to transform their fork
- Keeps base system minimal

### Security Model

- **OS-level isolation** vs application-level permission checks
- Containers can only access explicitly mounted directories
- Codebase small enough to actually audit
- See `docs/SECURITY.md` for full details

### Requirements

- macOS or Linux
- Node.js 20+
- Claude Code
- Apple Container (macOS) or Docker (macOS/Linux)

### Quick Start

```bash
git clone https://github.com/gavrielc/nanoclaw.git
cd nanoclaw
claude
/run setup  # Claude Code handles everything
```

### Request for Skills (RFS)

Skills the maintainer would love to see:

**Communication Channels:**
- `/add-telegram` - Add Telegram (option to replace WhatsApp or add as additional)
- `/add-slack` - Add Slack
- `/add-discord` - Add Discord

**Platform Support:**
- `/setup-windows` - Windows via WSL2 + Docker

**Session Management:**
- `/add-clear` - Add compaction command to summarize context

### Comparison: OpenClaw vs NanoClaw

| Aspect | OpenClaw | NanoClaw |
|--------|----------|----------|
| Modules | 52+ | ~5 core files |
| Config files | 8+ | None (code changes) |
| Dependencies | 45+ | Minimal |
| Isolation | Application-level | OS-level (containers) |
| Process model | Multi-process | Single process |
| Complexity | High | Low |
| Customization | Config files | Code changes + skills |
| Security model | Allowlists, pairing | Container isolation |

### Why This Matters

1. **Auditability** - Small codebase you can actually understand
2. **Security** - OS-level isolation beats application-level checks
3. **Transparency** - No magic, everything is visible
4. **Customization** - Skills let you modify without bloating base
5. **No ToS concerns** - Uses Claude Agent SDK natively with your auth token

**Links:**
- GitHub: https://github.com/gavrielc/nanoclaw
- Apple Container: https://github.com/apple/container
