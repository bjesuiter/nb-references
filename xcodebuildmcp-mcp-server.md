---
title: XcodeBuildMCP - MCP Server for Xcode Integration
anchor: MCP server providing Xcode-related tools for AI assistants integration
tags: [xcode, mcp, ai-assistant, build, apple]
description: Model Context Protocol server for Xcode integration with AI assistants
source_url: https://github.com/cameroncooke/XcodeBuildMCP
---

## Summary

A Model Context Protocol (MCP) server that provides Xcode-related tools for integration with AI assistants and other MCP clients.

## Requirements

- macOS 14.5+
- Xcode 16.x+
- Node.js 18.x+

## Installation

### Quick Install via npx
```json
{
  "mcpServers": {
    "XcodeBuildMCP": {
      "command": "npx",
      "args": ["-y", "xcodebuildmcp@latest", "mcp"]
    }
  }
}
```

### Per Client

**Cursor:**
Add to `~/.cursor/mcp.json`

**Claude Code:**
```bash
claude mcp add XcodeBuildMCP -- npx -y xcodebuildmcp@latest mcp
```

**Codex CLI:**
```bash
codex mcp add XcodeBuildMCP -- npx -y xcodebuildmcp@latest mcp
```

Or add to `~/.codex/config.toml`:
```toml
[mcp_servers.XcodeBuildMCP]
command = "npx"
args = ["-y", "xcodebuildmcp@latest", "mcp"]
```

**Claude Desktop:**
Add to `~/Library/Application Support/Claude/claude_desktop_config.json`

**VS Code / VS Code Insiders:**
Add to VS Code settings JSON:
```json
{
  "mcp": {
    "servers": {
      "XcodeBuildMCP": {
        "command": "npx",
        "args": ["-y", "xcodebuildmcp@latest", "mcp"]
      }
    }
  }
}
```

**Windsurf:**
Add to `~/.codeium/windsurf/mcp_config.json`

**Trae:**
Add to `~/Library/Application Support/Trae/User/mcp.json`

## Features

- Xcode build tool integration for AI assistants
- Provides Xcode-related MCP tools
- Supports multiple AI coding clients

## Note

Ensure the command includes the `mcp` subcommand: `npx -y xcodebuildmcp@latest mcp`
