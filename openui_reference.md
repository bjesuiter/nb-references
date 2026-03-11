---
title: OpenUI - The Open Standard for Generative UI
anchor: Compact streaming-first language for AI-generated UI, up to 67% more token-efficient than JSON
tags: [ai, generative-ui, react, streaming, ui-framework, open-source]
description: Full-stack Generative UI framework with built-in component libraries
source_url: https://github.com/thesysdev/openui
---

## Summary

OpenUI is a full-stack Generative UI framework with a compact streaming-first language, React runtime, and ready-to-use chat interfaces. Up to **67% more token-efficient** than JSON.

## Core Features

- **OpenUI Lang** — Compact language for structured UI generation designed for streaming
- **Built-in component libraries** — Charts, forms, tables, layouts
- **Prompt generation** — Generate model instructions from your component library
- **Streaming renderer** — Parse and render progressively as tokens arrive
- **Chat & app surfaces** — Use for assistants, copilots, interactive flows

## Packages

| Package | Description |
|---------|-------------|
| `@openuidev/react-lang` | Core runtime (parser, renderer, prompt generation) |
| `@openuidev/react-headless` | Headless chat state, streaming adapters |
| `@openuidev/react-ui` | Prebuilt chat layouts, component libraries |
| `@openuidev/cli` | CLI for scaffolding apps |

## Token Efficiency

OpenUI Lang vs JSON benchmarks:
- Simple table: **-56.5%** tokens
- Chart with data: **-55.6%**
- Contact form: **-67.1%**
- Dashboard: **-45.4%**

## Quick Start

```bash
npx @openuidev/cli@latest create --name genui-chat-app
cd genui-chat-app
echo "OPENAI_API_KEY=sk-your-key-here" > .env
npm run dev
```

## How It Works

1. Define component library
2. Generate system prompt from components
3. Send to LLM
4. Stream OpenUI Lang back
5. Render progressively with React renderer
