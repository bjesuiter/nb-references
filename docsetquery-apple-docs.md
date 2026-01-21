---
title: DocSetQuery - Apple/SwiftUI Documentation Tool for Agents
anchor: Local-first Apple documentation extraction for agent workflows
tags: [apple, documentation, ios, macos, docset, agents, dash, docc]
description: Tooling for agents to create markdown documentation from DocSet bundles - avoids scraping Apple docs every time
source_url: https://github.com/PaulSolt/DocSetQuery
---

## Overview

DocSetQuery is a local-first toolkit for extracting, cleaning, and searching Apple documentation. Built specifically for agent workflows that need deterministic, citeable Markdown instead of scraping the web repeatedly.

## Why It Exists

- **Apple docs are large and dynamic** — agents need stable, local references
- **DocC exports are noisy** — predictable front matter and trimmed TOCs needed
- **Local search should be instant** — no re-reading docsets for every query

## Tools Included

| Tool | Purpose |
|------|---------|
| `tools/docset_query.py` | Exports DocC content from Apple docset to Markdown |
| `tools/docset_sanitize.py` | Rebuilds front matter + trims TOC for cleaner context |
| `tools/docindex.py` | Builds local JSON index for fast search |
| `tools/docmeta.py` | Peeks front matter/TOC for debugging |
| `scripts/sync_docs.sh` | Syncs canonical docs cache into `docs/apple` |

## Quickstart

```bash
# Export a framework/topic tree to Markdown
python tools/docset_query.py export \
  --root /documentation/vision \
  --output docs/apple/vision.md

# Sanitize the export (trim TOC, rebuild front matter)
python tools/docset_sanitize.py --input docs/apple/vision.md --in-place --toc-depth 2

# Build or refresh the search index
python tools/docindex.py rebuild

# Search headings/key sections
python tools/docindex.py search "CVPixelBuffer"
```

## Agent Workflow

This is the recommended flow for repos needing grounded Apple citations:

1. **Search locally first** — agents call `docindex.py search` against `docs/apple`
2. **Fetch only what's missing** — use `docset_query.py fetch` or `export` if topic isn't there
3. **Sanitize for stable context** — run `docset_sanitize.py` for consistent front matter + TOC
4. **Rebuild the index** — `docindex.py rebuild` keeps agent search fast
5. **Keep a canonical cache** — sync with `scripts/sync_docs.sh` (gitignored)

## Requirements

- Apple API Reference docset (Dash format) on disk
- brotli CLI available
- Python 3.x

## Where to Get Docsets

- **Dash app**: https://kapeli.com/dash
- **Feed repo (download without app)**: https://github.com/Kapeli/feeds

## Related

- **Default docset path**: `~/Library/Application Support/Dash/DocSets/Apple_API_Reference/Apple_API_Reference.docset`
- **Cache**: `~/.cache/apple-docs`

## JB's Notes

Use this when building iOS/macOS apps with agents to avoid:
- Repeated web scraping of Apple docs
- Inconsistent/random API versions
- Slow agent responses from searching the web

Setup once, then agents query locally via `docindex.py search`.
