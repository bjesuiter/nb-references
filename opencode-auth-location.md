---
title: OpenCode Auth Storage Location
anchor: Location for building OpenCode account switcher - auth.json path
tags: [opencode, auth, credentials, switcher, api, openai, codex]
description: OpenCode stores login credentials in plaintext at ~/.local/share/opencode/auth.json
source_url: https://opencode.ai/docs/cli/
---

## Summary

**OpenCode** stores authentication credentials in a plaintext JSON file:

```
~/.local/share/opencode/auth.json
```

## Auth File Structure

The `auth.json` contains API keys and provider configurations for:
- **OpenAI** — API keys for GPT models
- **Anthropic** — API keys for Claude models
- **Codex** — API keys for code generation
- **Other providers** — Models.dev provider list

## Building an Account Switcher

### Reading Auth
```bash
cat ~/.local/share/opencode/auth.json
```

### Security Warning
⚠️ **The auth file is NOT encrypted** — it's stored in plaintext.

There is an [open GitHub issue](https://github.com/anomalyco/opencode/issues/4318) requesting system credential store integration.

### Switcher App Ideas

1. **Menu bar app** — Store multiple profiles, switch via dropdown
2. **CLI tool** — `opencode-switch --profile personal`
3. **GUI** — Visual management of multiple API keys

### Features Needed

- **Secure storage** — Encrypt credentials (Keychain on macOS)
- **Profile switching** — Quick toggle between accounts
- **Usage tracking** — Per-account API usage monitoring
- **API key management** — Add/edit/remove keys safely

## Related

- OpenCode CLI docs: https://opencode.ai/docs/cli/
- Issue #4318: Use system credential store: https://github.com/anomalyco/opencode/issues/4318
- Environment variables also supported: `OPENAI_API_KEY`, etc.
