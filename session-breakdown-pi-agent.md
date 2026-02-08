---
title: "session-breakdown — pi-agent Usage Analytics TUI"
anchor: "Interactive TUI showing coding LLM usage breakdown by model, sessions, messages, tokens, and cost over 7/30/90 days"
tags: [pi-agent, analytics, tui, coding, llm, usage, cost-tracking]
description: "Interactive TUI extension for pi-agent that displays usage analytics: sessions, messages, tokens, and cost breakdown by model over configurable time ranges"
source_url: "https://github.com/mitsuhiko/agent-stuff/blob/main/pi-extensions/session-breakdown.ts"
---

## Reference

### Summary
A pi-agent extension providing an interactive TUI for analyzing coding LLM usage patterns. Displays GitHub-contributions-style heatmaps showing:

- **Sessions per day**
- **Messages per day**
- **Tokens per day** (if available)
- **Cost per day** (if available)
- **Model breakdown** (sessions/messages/tokens + cost by model)

### Features
- **Time Ranges:** Last 7, 30, or 90 days
- **Metrics:** Toggle between sessions, messages, tokens, or cost view
- **Visualization:** GitHub-contributions-style calendar heatmap
  - Color intensity based on selected metric (log-scaled)
  - Hue represents weighted mix of model colors
- **Model Breakdown Table:** Top models by selected metric with cost and share percentage
- **Data Source:** Parses `~/.pi/agent/sessions/*.jsonl` files recursively

### Key Metrics Tracked
| Metric | Description |
|--------|-------------|
| Sessions | Number of coding sessions per day |
| Messages | Total messages exchanged |
| Tokens | Token usage (if available from provider) |
| Cost | Actual cost in USD (parsed from usage data) |

### Usage
```bash
# In pi-agent, run:
/session-breakdown
```

### Navigation
| Key | Action |
|-----|--------|
| `←` / `→` | Switch time range (7d / 30d / 90d) |
| `Tab` | Toggle metric (sessions → messages → tokens) |
| `1` / `2` / `3` | Quick select 7d / 30d / 90d |
| `q` / `Esc` | Close |

### Model Color Palette
Top 4 models are assigned distinct colors:
1. Green
2. Blue
3. Purple
4. Orange

Remaining models shown as "other" (gray).

### Data Parsing
The extension handles varying session formats across pi-agent versions:
- **Newer:** `{ provider, model, usage }` on message wrapper
- **Older:** `{ message: { provider, model, usage } }`

**Token formats supported:**
- `totalTokens` / `total_tokens`
- `promptTokens` / `prompt_tokens` / `inputTokens` / `input_tokens`
- `completionTokens` / `completion_tokens` / `outputTokens` / `output_tokens`

### Installation
Place in your pi-agent extensions directory:
```bash
# Typically ~/.pi/agent/extensions/
# The extension auto-registers the /session-breakdown command
```

### Example Output
```
Session breakdown  [7d] [30d] [90d]   [sess] [msg] [tok]

Last 30 days: 42 sessions · 1.2K messages · $12.34

Mon     ████       ██
Wed     █████      ███
Fri     ███        ██

model                    sessions    cost      share
anthropic/claude-opus-4    18      $5.20      43%
openai/gpt-4               12      $4.10      29%
openai/gpt-3.5-turbo        8      $0.45      19%
anthropic/claude-sonnet-4    4      $2.59      10%
```

### Requirements
- pi-agent (coding LLM agent)
- Node.js runtime (for TUI rendering)
- Terminal with ANSI color support

### Developer
[mitsuhiko](https://github.com/mitsuhiko) — Part of [agent-stuff](https://github.com/mitsuhiko/agent-stuff) repository

### Related
- pi-agent: https://github.com/mariozechner/pi-coding-agent
- TUI framework: @mariozechner/pi-tui
