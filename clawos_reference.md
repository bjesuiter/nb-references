---
title: ClawOS - Full macOS VMs for OpenClaw
anchor: Provision fully-configured macOS VMs on Apple Silicon from a single command
tags: [macos, vm, virtualization, openclaw, apple-silicon, automation]
description: YAML-driven pipeline to provision macOS VMs with Homebrew, npm, and custom scripts
source_url: https://github.com/aessam/clawos
---

## Summary

Provision fully-configured macOS VMs on Apple Silicon from a single command. Built on Apple's Virtualization.framework.

## Features

- **One YAML file** defines CPU/RAM/disk, user account, SSH keys, Homebrew, npm tools, GUI apps
- **8-stage pipeline**: IPSW resolve → Download → Restore → Inject → Boot → Provision → Verify → Done
- **Offline disk injection**: user account, SSH, VNC, Setup Assistant bypass
- **SwiftUI Control Panel**: Live VM display, metrics, provisioning log, SSH/VNC quick-connect
- **Headless mode**: `--no-ui` for server-style automation

## Requirements

- Apple Silicon Mac
- macOS 15.0+
- Xcode 16+

## Example claw.yml

```yaml
vm:
  cpu: 4
  ram: 8GB
  disk: 100GB
  macos: latest

tools:
  homebrew: true
  packages: [git, node, python3]
  casks: [visual-studio-code]
  npm_global:
    - "@anthropic-ai/claude-code"
    - "@openai/codex"
```

## Usage

```bash
sudo createClawOS --config claw.yml
```
