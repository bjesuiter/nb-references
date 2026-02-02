---
title: Mom (Master of Mischief) - OpenClaw-like Agent by Mario Zechner
anchor: Slack bot powered by LLM with full bash access, self-managing tools
tags: [ai-agent, slack-bot, openclaw-alternative, mario-zechner, self-managing]
description: A self-managing Slack bot that installs tools, writes scripts, and maintains its workspace autonomously
source_url: https://github.com/badlogic/pi-mono/tree/main/packages/mom
---

## My Reference

### What is Mom?

**Mom (Master Of Mischief)** is a Slack bot powered by an LLM that can execute bash commands, read/write files, and interact with your development environment. Unlike traditional bots, Mom is **self-managing** - she installs her own tools, programs CLI skills, configures credentials, and maintains her workspace autonomously.

### Key Features

- **Minimal by Design**: Turn mom into whatever you need. She builds her own tools without pre-built assumptions
- **Self-Managing**: Installs tools (apk, npm, brew, etc.), writes scripts, configures credentials. Zero setup from you
- **Slack Integration**: Responds to @mentions in channels and DMs
- **Full Bash Access**: Execute any command, read/write files, automate workflows
- **Docker Sandbox**: Isolate mom in a container (recommended for all use)
- **Persistent Workspace**: All conversation history, files, and tools stored in one directory you control
- **Working Memory & Custom Tools**: Mom remembers context across sessions and creates workflow-specific CLI tools (skills) for your tasks
- **Thread-Based Details**: Clean main messages with verbose tool details in threads
- **Events System**: Schedule reminders and periodic tasks (immediate, one-shot, periodic)

### Architecture

```
./data/                         # Mom's workspace directory
  ├── MEMORY.md                 # Global memory (shared across channels)
  ├── settings.json             # Global settings (compaction, retry, etc.)
  ├── skills/                   # Global custom CLI tools mom creates
  ├── C123ABC/                  # Each Slack channel gets a directory
  │   ├── MEMORY.md             # Channel-specific memory
  │   ├── log.jsonl             # Full message history (source of truth)
  │   ├── context.jsonl         # LLM context (synced from log.jsonl)
  │   ├── attachments/          # Files users shared
  │   ├── scratch/              # Mom's working directory
  │   └── skills/               # Channel-specific CLI tools
  └── D456DEF/                  # DM channels also get directories
      └── ...
```

### How Mom Works

1. **Message arrives**: Written to channel's `log.jsonl` (source of truth)
2. **Context sync**: Unseen messages synced from `log.jsonl` to `context.jsonl`
3. **Memory load**: Reads MEMORY.md files (global and channel-specific)
4. **Response**: Uses tools to answer - read attachments, invoke commands, write files, attach files
5. **Storage**: Direct reply in `log.jsonl`, tool details in `context.jsonl`

### Tools

- **bash**: Execute shell commands (primary tool)
- **read**: Read file contents
- **write**: Create or overwrite files
- **edit**: Make surgical edits to existing files
- **attach**: Share files back to Slack

### Execution Environments

**Docker mode (recommended)**:
- Commands execute inside isolated Linux container
- Can only access mounted data directory + container internals
- Installs tools inside container (apk, apt, yum, brew)
- Host system protected

**Host mode (not recommended)**:
- Commands execute directly on your machine
- Full access to your system
- See security section below

### Skills System

Skills are custom CLI tools that mom creates for specific workflows:

```
skills/
  └── note/
      ├── SKILL.md              # Skill definition
      └── note.sh               # Implementation
```

Mom knows skill names/descriptions and reads full SKILL.md when deciding to use a skill. Skills can be:
- Global (`/workspace/skills/`)
- Channel-specific (`/workspace/<channel>/skills/`)

**Example skills**:
- Gmail (read, search, send via IMAP/SMTP)
- GitHub CLI workflows
- Email management
- Custom note-taking

### Events System

Three event types for scheduled wake-ups:

| Type | Trigger | Use Case |
|------|---------|----------|
| **Immediate** | As soon as file created | Webhooks, external signals |
| **One-shot** | Specific date/time, once | Reminders |
| **Periodic** | Cron schedule, repeatedly | Daily summaries, inbox checks |

```json
// Immediate
{"type": "immediate", "channelId": "C123ABC", "text": "New GitHub issue"}

// One-shot
{"type": "one-shot", "channelId": "C123ABC", "text": "Dentist reminder", "at": "2025-12-15T09:00:00+01:00"}

// Periodic
{"type": "periodic", "channelId": "C123ABC", "text": "Check inbox", "schedule": "0 9 * * 1-5"}
```

### Context Management

- **log.jsonl**: Append-only source of truth (all messages)
- **context.jsonl**: What's sent to LLM (synced from log.jsonl)
- **Compaction**: When context exceeds window, older messages summarized, recent kept in full
- **Infinite history**: Grep log.jsonl for anything beyond context window

### Memory System

- **Global memory** (`data/MEMORY.md`): Shared across all channels (project architecture, coding conventions, communication preferences)
- **Channel memory** (`data/<channel>/MEMORY.md`): Channel-specific context, decisions, ongoing work

Memory contains: email writing tone, coding conventions, team responsibilities, troubleshooting steps, workflow patterns.

### Security Considerations

**Prompt Injection Risks**:
- Direct: Malicious user asks for credentials
- Indirect: Fetches malicious content with hidden instructions

**Mitigations**:
- Use dedicated bot accounts with minimal permissions
- Scope credentials tightly (read-only when possible)
- Never give production credentials
- Use Docker mode (limits to container)
- Monitor activity in threads
- Audit data directory regularly

### Relationship to OpenClaw

Mom is built on **pi-mono** - the same minimal agent framework that powers OpenClaw. Key differences:
- Mom targets Slack specifically (vs OpenClaw's multi-channel support)
- Both share philosophy: LLMs are great at writing/running code
- Mom's extension system enables custom skills
- Both use YOLO mode (full bash access, embrace code execution)

### Quick Start

```bash
# Set environment variables
export MOM_SLACK_APP_TOKEN=xapp-...
export MOM_SLACK_BOT_TOKEN=xoxb-...
export ANTHROPIC_API_KEY=sk-ant-...

# Create Docker sandbox
docker run -d \
  --name mom-sandbox \
  -v $(pwd)/data:/workspace \
  alpine:latest \
  tail -f /dev/null

# Run mom
mom --sandbox=docker:mom-sandbox ./data
```

**Links**:
- GitHub: https://github.com/badlogic/pi-mono/tree/main/packages/mom
- Skills repo: https://github.com/badlogic/pi-skills
