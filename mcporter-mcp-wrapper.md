---
title: MCPorter - Wrap MCP Servers as CLIs
anchor: If I need to wrap an MCP server with mcporter for a skill
tags: [mcporter, mcp, cli, typescript, wrapper, skill, automation]
description: MCPorter helps wrap MCP servers as TypeScript APIs or single-purpose CLIs for skill development
source_url: https://github.com/steipete/mcporter
---

## Summary

**MCPorter** 🧳 is a TypeScript runtime, CLI, and code-generation toolkit for the Model Context Protocol. It helps you:
- Discover MCP servers on your system
- Call MCP tools directly from TypeScript
- Generate standalone CLIs from any MCP server
- Wrap MCP servers for use in skills

## Key Capabilities

### Zero-Config Discovery
- Auto-discovers MCP servers from Cursor, Claude Code/Desktop, Codex, Windsurf, OpenCode, VS Code
- Uses `createRuntime()` to merge configs from `~/.mcporter/mcporter.jsonc`, `./config/mcporter.json`, and imports
- Supports `${ENV}` placeholders

### One-Command CLI Generation
```bash
# Generate CLI from any MCP server
npx mcporter generate-cli --command https://mcp.linear.app/mcp

# Outputs: context7.ts (template) and context7.js (bundled CLI)
```

### Typed Tool Clients
```bash
# Generate TypeScript interfaces
npx mcporter emit-ts linear --out types/linear-tools.d.ts

# Generate client wrapper
npx mcporter emit-ts linear --mode client --out clients/linear.ts
```

### Friendly TypeScript API
```typescript
import { createRuntime, createServerProxy } from "mcporter";

const runtime = await createRuntime();
const linear = createServerProxy(runtime, "linear");

const docs = await linear.searchDocumentation({ query: "automations" });
console.log(docs.text());
```

### Ad-Hoc Connections
```bash
# Try an MCP without editing config
npx mcporter list --http-url https://mcp.linear.app/mcp --name linear --persist
```

## For Skill Development

### Wrap MCP for a Skill
1. **Generate CLI from MCP server:**
   ```bash
   mcporter generate-cli --command <mcp-server-url> --name my-skill
   ```

2. **Generate TypeScript types:**
   ```bash
   mcporter emit-ts <server> --mode client --out skills/my-skill/client.ts
   ```

3. **Use in skill:**
   ```typescript
   import { createRuntime } from "mcporter";
   const runtime = await createRuntime();
   const tools = await runtime.listTools("my-mcp-server");
   ```

### Daemon Mode
```bash
# Keep MCP servers warm
mcporter daemon start|status|stop|restart
```

## Installation

```bash
# Run instantly with npx
npx mcporter list

# Add to project
pnpm add mcporter

# Homebrew
brew tap steipete/tap
brew install steipete/tap/mcporter
```

## Config Location

- Default: `./config/mcporter.json`
- Home: `~/.mcporter/mcporter.jsonc`

## Related Tools

- **CodexBar** 🟦🟩 — Keep Codex token windows visible in macOS menu bar
- **Oracle** 🧿 — Prompt bundler/CLI for multi-model runs
- **Trimmy** ✂️ — Flatten multi-line shell snippets

## Links

- GitHub: https://github.com/steipete/mcporter
- NPM: https://www.npmjs.com/package/mcporter
- Docs: https://mcporter.dev
