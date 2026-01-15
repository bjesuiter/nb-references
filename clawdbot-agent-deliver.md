---
title: Clawdbot Agent --deliver Mechanism
anchor: How clawdbot agent --deliver works between Claude Code and Clawdbot
tags: [clawdbot, cli, integration, testing]
description: How to use clawdbot agent --deliver to test Clawdbot skills bidirectionally
source_url: Telegram message from Clawd
---

## How Message Sending Works

Claude Code uses the `clawdbot agent --deliver` CLI command:

```bash
cd ~/path/to/clawdbot
node dist/index.js agent --to "channel:DISCORD_CHANNEL_ID" --provider discord --deliver --message "Hey Clawd, can you test this skill?"
```

### Flow
1. Claude Code sends via CLI → arrives in Clawd's session as a real message
2. Clawd sees it, responds normally to Discord
3. Claude Code reads CLI output which includes the response
4. Rinse and repeat as needed

### Not an Endless Loop
- Claude Code initiates (sends question)
- Clawd responds once
- Claude Code decides if follow-up needed
- Each side waits — no automatic ping-pong

### Use Case
Bidirectional testing: "outsourcing testing to the running Clawdbot" — Claude Code asks Clawd to test, Clawd reports issues, Claude Code fixes and asks again.

### Setup Requirements
- Gateway must be running
- Use `clawdbot agent --deliver` from any terminal (or Claude Code's exec)
- `--to` can be:
  - Phone number (Signal/WhatsApp)
  - Telegram ID
  - `channel:DISCORD_CHANNEL_ID`
