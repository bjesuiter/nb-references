---
title: Clawdspace - Self-hosted Sandboxed Execution Environments
anchor: self-hosted docker sandboxes tailscale
tags:
  - selfhost
  - docker
  - sandbox
  - tailscale
  - infrastructure
description: Self-hosted sandboxed execution environments - run isolated spaces on your own machines
source_url: https://github.com/adam91holt/clawdspace
---

# Clawdspace

Self-hosted sandboxed execution environments — run isolated "spaces" on your own machines (Docker + Tailscale).

## What You Get

- **Docker-based sandboxes** — one container per space
- **Persistent workspace** — per-space Docker volume mounted at `/workspace`
- **Auto-sleep** — idle spaces pause to save resources
- **Dashboard** — spaces, stats, files, terminal, audit log (mobile-friendly)
- **Multi-node (Tailscale)** — auto-discovery + cached node health
- **GPU support** — opt-in GPU spaces (where available)
- **Templates** — presets for resources/image/network posture
- **Audit + history** — API audit + bash history ingestion
- **Clawdbot tool integration** — agents can call Clawdspace via a native tool

## Architecture

- Clawdbot Agent → Clawdspace Extension → clawdspace CLI → Clawdspace API → Docker Engine
- Web Dashboard connects to API
- Tailscale for multi-node discovery
- Audit JSONL for logging

## Key Features

- Spaces with persistent volumes at `/workspace`
- WebSocket terminal (docker exec)
- Bash history ingestion to audit log
- Template-based space creation
- Multi-node support via Tailscale
- GPU support for ML workloads

## CLI Commands

```
clawdspace system
clawdspace list
clawdspace create dev
clawdspace exec dev "python3 --version"
clawdspace stop dev
clawdspace start dev
clawdspace destroy dev
clawdspace dashboard
```

## Docs

- `docs/API.md` — REST API reference
- `docs/ARCHITECTURE.md` — system design + mermaid diagrams
- `docs/CLI.md` — CLI reference
- `docs/SETUP.md` — setup guide
- `docs/USAGE.md` — day 2 workflows
- `docs/TROUBLESHOOTING.md` — common errors

## Related

Clawdbot integration plugin: `clawdbot/plugins/clawdspace/`
