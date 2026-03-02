---
title: "stereOS - Linux OS for AI agents"
anchor: Linux OS hardened and purpose-built for AI agents with NixOS, mixtapes for agent harnesses
tags: [linux, ai-agents,操作系统, nixos, infrastructure]
description: A Linux-based operating system hardened and purpose-built for AI agents
source_url: https://github.com/papercomputeco/stereos
---

## Reference

### Summary
Linux OS hardened and built specifically for AI agents. Based on NixOS, produces "mixtapes" — machine images bundling a minimal Linux system with specific AI agent harnesses.

### Mixtapes (Pre-built Images)
- **opencode-mixtape**: Includes OpenCode agent binary, accepts ANTHROPIC_API_KEY or OPENAI_API_KEY

### System Architecture
- Minimal Linux with orchestration daemons
- `admin` user: /home/admin (administrative operations)
- `agent` user: /home/agent/workspace (agent workspace)
- `stereosd`: system daemon
- `agentd`: agent management daemon

### Image Formats
- Raw EFI (stereos.img) - Apple Virt Framework bootable
- QCOW2 (stereos.qcow2) - QEMU/KVM
- Kernel artifacts (bzImage, initrd) - Direct-kernel boot

### Links
- https://stereos.ai/
- Discord: https://discord.gg/T6Y4XkmmV5
