---
title: Pi Interactive Shell - Autonomous CLI Control Extension
anchor: Pi extension for controlling interactive CLIs in observable overlay - works with Codex, vim, etc.
tags: [pi-agent, cli, terminal, interactive, automation, codex, extension]
description: Pi coding agent extension for autonomous CLI control with full PTY overlay - run vim, htop, psql, ssh, npm, git rebase, etc.
source_url: https://github.com/nicobailon/pi-interactive-shell
---

## My Reference

### What It Does
Extension for Pi coding agent that lets it autonomously control interactive CLIs in an observable TUI overlay. Works with any CLI: vim, htop, psql, ssh, docker logs, npm run dev, git rebase -i, etc.

### Install
```bash
pi install npm:pi-interactive-shell
```

### Three Modes

| Mode | Agent Blocked? | Use Case |
|------|----------------|----------|
| **Interactive** | Yes - waits for result | Editors, REPLs, DB shells |
| **Hands-Free** | No - polls periodically | Dev servers, builds to monitor |
| **Dispatch** | No - notified on completion | Delegating to subagents |

### Quick Examples

**Interactive (blocking):**
```javascript
interactive_shell({ command: 'vim config.yaml' })
```

**Hands-Free (non-blocking, polls):**
```javascript
interactive_shell({
  command: 'npm run dev',
  mode: "hands-free",
  reason: "Dev server"
})
// → Returns { sessionId: "calm-reef", status: "running" }

// Poll for output
interactive_shell({ sessionId: "calm-reef" })

// Send input
interactive_shell({ sessionId: "calm-reef", inputKeys: ["ctrl+c"] })

// Kill when done
interactive_shell({ sessionId: "calm-reef", kill: true })
```

**Dispatch (fire-and-forget):**
```javascript
interactive_shell({
  command: 'codex "Refactor the auth module"',
  mode: "dispatch",
  reason: "Auth refactor"
})
// → Returns immediately, agent notified on completion
```

**Background (headless, no overlay):**
```javascript
interactive_shell({
  command: 'codex "Fix all lint errors"',
  mode: "dispatch",
  background: true
})
// → No overlay, runs invisibly
```

### Key Features
- **Full PTY emulation** - subprocess thinks it's in a real terminal
- **User take over anytime** - type anything to gain control
- **Transfer output** - Ctrl+T to send subagent output to main agent
- **Background sessions** - Ctrl+B to background, /attach to reattach
- **Configurable overlay** - size, scrollback, transfer limits

### Config File
`~/.pi/agent/interactive-shell.json`:
```json
{
  "overlayWidthPercent": 95,
  "overlayHeightPercent": 45,
  "scrollbackLines": 5000,
  "transferLines": 200,
  "transferMaxChars": 20000,
  "handsFreeUpdateMode": "on-quiet",
  "handsFreeQuietThreshold": 5000
}
```

### Why Use This
- Run interactive CLI tools that normally block agents
- Watch agent actions in real-time overlay
- Take over anytime if agent gets stuck
- Delegate tasks to Codex/other agents with notification on completion
- More token-efficient than tmux/screen wrappers
