---
title: OpenAI Codex App - Agent Command Center for macOS
anchor: New desktop app for managing multiple coding agents in parallel with skills support
tags: [ai-agent, openai, codex, macos, gui, skills, multi-agent, automation]
description: OpenAI's new desktop app for orchestrating multiple Codex agents with project-based threads, worktrees, skills, and automations
source_url: https://openai.com/index/introducing-the-codex-app/
---

## My Reference

### What is the Codex App?

OpenAI's new **Codex desktop app for macOS** - a command center for managing multiple coding agents. It's designed for the new way of working where developers orchestrate multiple agents across projects, running tasks in parallel and trusting agents with substantial projects.

### Key Features

**Multi-Agent Management:**
- Agents run in separate threads organized by projects
- Seamlessly switch between tasks without losing context
- Review agent changes in thread, comment on diff, or open in editor

**Worktrees Support:**
- Multiple agents can work on the same repo without conflicts
- Each agent works on an isolated copy of your code
- Explore different paths without affecting local git state
- Check out changes locally or let agent continue without touching local state

**Skills System:**
- Same [Agent Skills standard](https://agentskills.io) that pi-mono uses
- Bundle instructions, resources, and scripts
- Codex can use skills wherever you work (app, CLI, IDE extension)
- Check skills into repository to share with team

**Built-in Skills (from OpenAI):**
- **Implement designs**: Fetch from Figma and translate to UI code
- **Manage projects**: Triage bugs, track releases in Linear
- **Deploy to cloud**: Cloudflare, Netlify, Render, Vercel
- **Generate images**: GPT Image powered image generation
- **Build with OpenAI APIs**: Reference up-to-date documentation
- **Create documents**: PDF, spreadsheet, docx files with formatting

**Automations:**
- Background work on automatic schedule
- Combine instructions with optional skills
- Results land in review queue when finished
- Examples: daily issue triage, CI failure summaries, release briefs

**Personalities:**
- Two modes: terse/pragmatic vs conversational/empathetic
- No capability difference, just style preference
- Use `/personality` command to switch

**Security:**
- Native, open-source system-level sandboxing (like Codex CLI)
- Default: limited to editing files in current folder
- Cached web search by default, asks permission for elevated access
- Configurable rules for project/team permissions

### Architecture

```
┌─────────────────────────────────────────────────┐
│ Codex App (macOS)                               │
├─────────────────────────────────────────────────┤
│ Project Threads                                 │
│ ┌─────────────┐  ┌─────────────┐               │
│ │ Agent A     │  │ Agent B     │  ...         │
│ │ (worktree)  │  │ (worktree)  │               │
│ └─────────────┘  └─────────────┘               │
├─────────────────────────────────────────────────┤
│ Skills Library                                  │
│ Automations (scheduled tasks)                   │
├─────────────────────────────────────────────────┤
│ Sandbox (system-level isolation)                │
└─────────────────────────────────────────────────┘
```

### Skills System Details

Skills bundle:
- Instructions for the agent
- Resources (files, configs)
- Scripts for tools and workflows

**Skill workflow:**
1. User explicitly asks for skill OR
2. Agent automatically uses based on task context
3. Skill executes with bundled instructions

**Sharing:**
- Check into repository for team availability
- Works across app, CLI, and IDE extension

### Example: Racing Game Build

OpenAI asked Codex to build a racing game with:
- Different racers
- 8 maps
- Items usable with space bar

Used:
- Image generation skill (GPT Image)
- Web game development skill

**Result:** Built independently using 7+ million tokens with one initial prompt. Agent acted as designer, developer, and QA tester.

### Availability

**Platform:** macOS (Windows coming later)

**Pricing:** 
- Included in ChatGPT Plus, Pro, Business, Enterprise, Edu
- Additional credits available to purchase
- **Limited time:** Also available to ChatGPT Free and Go users
- **Rate limits doubled** for paid plans during this period

### Technical Notes

- Picks up session history and config from Codex CLI and IDE extension
- Seamless continuity with existing workflows
- Open-source sandboxing: https://github.com/openai/codex

### Roadmap

- **Windows** app coming
- Refine multi-agent workflows based on feedback
- Cloud-based triggers for Automations (run continuously in background)
- Faster inference

### Comparison with pi-mono

| Aspect | Codex App | pi-mono |
|--------|-----------|---------|
| Platform | GUI app (macOS) | Terminal-based |
| Multi-agent | Native (threads, worktrees) | Via extensions/sub-agents |
| Skills | Built-in, curated library | Supported (Agent Skills standard) |
| Automations | Scheduled, review queue | Events system (mom) |
| Sandbox | System-level, open-source | Docker/Apple Container |
| Personalities | Two modes (terse/conversational) | AGENTS.md customization |
| IDE | Full IDE extension | N/A (terminal focus) |
| Provider | OpenAI only | Multi-provider (Anthropic, OpenAI, Google...) |

### Why This Matters

1. **GUI for agents** - Not everyone wants terminal-based workflow
2. **Worktrees** - Brilliant solution for parallel agent work
3. **Skills standard** - Shared ecosystem with pi-mono
4. **Multi-agent orchestration** - Growing need as agents handle larger projects
5. **Automations** - Scheduled background work without user interaction

### Inspiration for Mobile Coding App

**Ideas from Codex app:**
- Project-based threads with isolated contexts
- Worktree-style isolation for mobile sandboxes (Daytona already does this)
- Skills library UI for discovering/managing skills
- Review queue for automation results
- Personality switching for different interaction styles

**Links:**
- Announcement: https://openai.com/index/introducing-the-codex-app/
- Skills repo: https://github.com/openai/skills
- Sandbox source: https://github.com/openai/codex
- Agent Skills: https://agentskills.io/
