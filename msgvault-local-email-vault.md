---
title: Msgvault - Local Email Vault for Gmail Backup
anchor: Local-first Gmail backup with offline search, analytics, and MCP server for AI assistants
tags: [email, gmail, backup, self-hosted, local-first, search, mcp, offline]
description: Full Gmail backup tool with offline search, DuckDB analytics, and MCP integration. Your data, owned and controlled.
source_url: https://www.msgvault.io/
repo_url: https://github.com/wesm/msgvault
---

## My Reference

### Summary
Local-first email vault that archives your Gmail (and upcoming WhatsApp) into a local SQLite/Parquet archive. Everything works offline — search, analytics, TUI, and AI access via MCP.

### Key Features
- **Complete Gmail Backup:** Raw MIME, labels, metadata, all attachments
- **Offline Everything:** SQLite FTS5 search, DuckDB analytics
- **MCP Server:** Expose archive to Claude Desktop or other MCP-compatible LLMs
- **Incremental Sync:** Uses Gmail History API, resumable checkpoints
- **Safe Deletion:** Stage & review before permanent deletion
- **Multi-Account:** Archive multiple Gmail accounts in one database
- **Local Storage:** Parquet + SQLite, deduplicated by content hash

### Install
```bash
curl -fsSL https://msgvault.io/install.sh | bash
```

### Why It Matters
- No background OAuth sessions or persistent API connections
- Your data = files on disk you own and control
- Zero risk from compromised tokens accessing live mailbox
- AI assistants query local archive, not your Gmail API

### Stack
- DuckDB for fast aggregations
- SQLite FTS5 for full-text search
- Parquet for efficient storage
- MCP protocol for AI integration
