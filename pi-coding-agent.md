---
title: PI Coding Agent by Mario Zechner
anchor: Minimalist Terminal-Based AI Coding Agent
tags: [ai-agent, coding, terminal, pi-agent, mario-zechner, armin-ronacher]
description: A minimal, terminal-based AI coding agent philosophy and implementation
source_url: https://mariozechner.at/posts/2025-11-30-pi-coding-agent/
---

## My Reference

### Summary (Mario Zechner)
Mario Zechner introduces "pi" - a minimalist, terminal-based AI coding agent built with Claude, emphasizing simplicity over complex tooling. The agent runs in a tmux session with the model seeing terminal output directly, avoiding sophisticated context engineering in favor of raw terminal interaction.

### Armin Ronacher's Perspective
Armin Ronacher (creator of Flask, OpenClaw) wrote about why he's obsessed with pi-mono after using it extensively:

**Core Philosophy:**
- Tiny core with shortest system prompt of any agent (~1000 tokens)
- Only 4 tools: Read, Write, Edit, Bash
- YOLO mode by default - no safety rails, embrace code execution
- No MCP support - instead use mcporter or build CLI tools with READMEs

**Extension System:**
- Extensions can persist state into sessions (incredibly powerful)
- Hot reloading - agent writes code, reloads, tests in a loop
- Sessions are trees - branch, navigate, rewind, summarize
- Can build custom TUI components (Mario ran Doom in it!)

**What Pi is NOT:**
- No built-in todos - use a file instead
- No plan mode - use a PLAN.md file
- No background bash - use tmux directly
- No sub-agents - just spawn pi via bash if needed

**Armin's Extensions:**
- `/answer` - Extracts questions from agent responses into nice input box
- `/todos` - Agent-specific issue tracker with markdown files
- `/review` - Branch into fresh review context, get findings, bring fixes back
- `/control` - Simple multi-agent system via prompts
- `/files` - List changed files, reveal in Finder, diff in VS Code

**Why It Matters:**
- Pi's underlying SDK handles multi-provider sessions portably
- Custom messages in session files for extension state
- Enables "software building software" workflow
- OpenClaw is built on pi-mono - same philosophy: LLMs are great at writing/running code

### Key Concepts

**Design Philosophy:**
- Minimalism over complexity - pi just gives the model a tmux session
- Direct terminal output visibility for the model
- "You are the agent" approach - model executes commands, human observes
- Inspired by Terminus 2 and the belief that context engineering hype is largely unfounded

**Architecture:**
- Claude as the model (Opus 4.5)
- tmux for terminal session management
- No sophisticated tool abstractions or context management
- Model sees raw terminal output, not UI-wrapped responses

**Context Gathering:**
- Using sub-agents mid-session signals poor planning
- Better to gather context first, create artifacts for later use
- pi can spawn itself via bash if needed

**Performance:**
- Benchmarked on Terminal-Bench 2.0 against Codex, Cursor, Windsurf, and other harnesses
- Competitive results despite minimal tooling
- Hundreds of exchanges in single sessions without context compaction

**Why Minimalism Works:**
- Terminal provides natural structure through prompts and command output
- Context engineering posts may be overthinking the problem
- The terminal itself provides the necessary scaffolding

**Lessons for Other Harnesses:**
- Simplicity can outperform complexity
- Context engineering may be less important than assumed
- Raw terminal visibility can replace sophisticated tooling

**Links:**
- Mario's article: https://mariozechner.at/posts/2025-11-30-pi-coding-agent/
- Armin's article: https://lucumr.pocoo.org/2026/1/31/pi/
- GitHub: https://github.com/badlogic/pi-mono/
