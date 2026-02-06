---
title: Xcode MCP Tools - External Client Integration
anchor: Using Xcode 26.3 MCP tools from Cursor, Claude Code, and Codex
tags: [xcode, mcp, cursor, claude-code, codex, apple, ide]
description: Guide to using Xcode's native AI tools from external MCP clients
source_url: https://rudrank.com/exploring-xcode-using-mcp-tools-cursor-external-clients
---

## Summary

Xcode 26.3 exposes 20 native MCP tools that can be used from external clients like Cursor, Claude Code, and Codex via the `mcpbridge` binary.

## Setup

### Enable in Xcode
1. Open Xcode > Settings (⌘,)
2. Select Intelligence
3. Toggle "Model Context Protocol" → Xcode Tools on

### Claude Code
```bash
claude mcp add --transport stdio xcode -- xcrun mcpbridge
```

### Codex
```bash
codex mcp add xcode -- xcrun mcpbridge
```

### Cursor (3 Options)

**Option 1:** One-click link → `cursor://anysphere.cursor-deeplink/mcp/install?name=xcode-tools&config=...`

**Option 2:** Settings > Features > MCP > Add Server > stdio
- Name: `xcode-tools`
- Command: `xcrun mcpbridge`

**Option 3:** `~/.cursor/mcp.json`
```json
{
  "mcpServers": {
    "xcode-tools": {
      "command": "xcrun",
      "args": ["mcpbridge"]
    }
  }
}
```

## Xcode MCP Tools (20 Total)

| Category | Tools |
|----------|-------|
| **File Ops** | XcodeRead, XcodeWrite, XcodeUpdate, XcodeGlob, XcodeGrep, XcodeLS, XcodeMakeDir, XcodeRM, XcodeMV |
| **Build/Test** | BuildProject, GetBuildLog, RunAllTests, RunSomeTests, GetTestList |
| **Diagnostics** | XcodeListNavigatorIssues, XcodeRefreshCodeIssuesInFile |
| **Execution** | ExecuteSnippet, RenderPreview |
| **Docs** | DocumentationSearch (powered by Squirrel MLX embeddings) |
| **UI** | XcodeListWindows |

## Known Issue: Cursor Schema Error

**Error:** `MCP error -32600: Tool XcodeListWindows has an output schema but did not return structuredContent`

Xcode 26.3 RC returns `content` instead of `structuredContent` (Apple partnership clients handle this, Cursor doesn't).

**Fix:** Use wrapper script at `~/bin/mcpbridge-wrapper` that copies `content` → `structuredContent`, then update Cursor config to use the wrapper.

## Workflow

1. Open project in Xcode: `open MyApp.xcodeproj`
2. MCP client auto-discovers window via `XcodeListWindows`
3. Agent uses `tabIdentifier` for all subsequent operations
4. Ask: "Build my project" → auto-builds, returns result + timing

## Permission

First connection prompts an Apple permission dialog — click "Allow".

