---
title: Browser-Use - AI Agent Browser Automation (v0.11.4)
anchor: Efficient AI agent browser control without extra extensions - browser-use CLI and skill
tags: [browser-use, ai, automation, agent, selenium, playwright, claude-code, codex, cli]
description: Browser-Use enables AI agents (Claude Code, Codex) to control browsers with simple commands. No extra extension needed. Open source, supports local and cloud browsers.
source_url: https://github.com/browser-use/browser-use
source_url_release: https://github.com/browser-use/browser-use/releases/tag/0.11.4
---

## Summary

**Browser-Use** makes websites accessible for AI agents. A Python library and CLI that lets AI agents automate browser tasks with simple commands — no extra extension required.

**Key difference from other tools:** Works without installing a browser extension. The agent controls the browser directly via Playwright.

## Quick Start

### Human Quickstart

```bash
# 1. Create environment with uv (Python >= 3.11)
uv init my-agent

# 2. Install browser-use
cd my-agent
uv add browser-use
uv sync

# 3. Get API key from cloud.browser-use.com (free $10 credits)
# Add to .env:
# BROWSER_USE_API_KEY=your-key

# 4. Install Chromium
uvx browser-use install

# 5. Run your first agent
uvx browser-use init --template default
python browser_use_default.py
```

### Claude Code Skill Install

```bash
mkdir -p ~/.claude/skills/browser-use
curl -o ~/.claude/skills/browser-use/SKILL.md \
 https://raw.githubusercontent.com/browser-use/browser-use/main/skills/browser-use/SKILL.md
```

## CLI Commands

Fast, persistent browser automation from terminal:

```bash
browser-use open https://example.com      # Navigate to URL
browser-use state                         # See clickable elements
browser-use click 5                       # Click element by index
browser-use type "hello@example.com"      # Type text
browser-use screenshot page.png           # Take screenshot
browser-use close                         # Close browser
```

**State output example:**
```
Returns clickable elements: [0] button "Submit", [1] input "Email"...
```

### Multiple Sessions

```bash
browser-use -s work open https://work.example.com
browser-use -s personal open https://gmail.com
browser-use sessions                    # List all
browser-use close --all                 # Close all
```

## Browser Modes

| Mode | Command | Description |
|------|---------|-------------|
| **Headless** | `browser-use open <url>` | Default, fast, no window |
| **Headed** | `browser-use open --headed <url>` | Visible window |
| **Real Chrome** | `browser-use --browser real open <url>` | Your Chrome with existing logins |
| **Cloud** | `browser-use --browser remote open <url>` | Stealth browser + proxies |

### Cloud Browser

Requires `BROWSER_USE_API_KEY` from [cloud.browser-use.com](https://cloud.browser-use.com):

```bash
browser-use --browser remote open https://example.com
```

- Automatic proxies and anti-detection
- Returns live preview URL
- Best for avoiding CAPTCHAs

## Python API

### Basic Agent

```python
from browser_use import Agent, Browser, ChatBrowserUse
import asyncio

async def example():
    browser = Browser()
    llm = ChatBrowserUse()
    
    agent = Agent(
        task="Find the number of stars of the browser-use repo",
        llm=llm,
        browser=browser,
    )
    
    history = await agent.run()
    return history

if __name__ == "__main__":
    history = asyncio.run(example())
```

### With Real Chrome Profile

```python
from browser_use import Agent, Browser

browser = Browser(
    browser_profile="default"  # Reuses your Chrome profile with logins
)

agent = Agent(
    task="Check my emails",
    browser=browser,
    llm=ChatBrowserUse()
)
await agent.run()
```

### Custom Tools

```python
from browser_use import Tools, Agent

tools = Tools()

@tools.action(description='Get stock price')
def get_stock_price(symbol: str) -> str:
    # Your custom logic
    return f"{symbol}: $150.00"

agent = Agent(
    task="Check AAPL and GOOGL stock prices",
    llm=ChatBrowserUse(),
    browser=Browser(),
    tools=tools,
)
await agent.run()
```

## Demo Use Cases

### Form Filling
```python
task="Fill in this job application with my resume and information."
```

### Grocery Shopping
```python
task="Put this list of items into my Instacart."
```

### Personal Assistant
```python
task="Help me find parts for a custom PC."
```

See more examples at [docs.browser-use.com/examples](https://docs.browser-use.com/examples)

## Pricing

| Service | Price |
|---------|-------|
| **Browser-Use (open source)** | Free |
| **ChatBrowserUse LLM** | $0.20/input token, $2.00/output token |
| **Cloud Browser** | Pay-per-use (proxies, stealth) |
| **API Key** | Get from cloud.browser-use.com ($10 free credits) |

## For Your Skills

### Add to agent-skills Repo

```bash
mkdir -p ~/Develop/bjesuiter/agent-skills/skills/browser-use
# Copy SKILL.md from browser-use repo
```

### Codex/OpenCode Integration

The CLI works directly with Codex:

```
Codex prompt: "Use browser-use to open https://github.com/bjesuiter and find the latest repo"
```

### Comparison with Other Tools

| Tool | Extension Required | Local Browser | Cloud Option | Price |
|------|-------------------|---------------|--------------|-------|
| **Browser-Use** | ❌ No | ✅ Yes | ✅ Yes | Free / Pay-per-use |
| **SweetLink** | ❌ No (DevTools) | ✅ Yes | ❌ No | Free |
| **agent-browser** | ✅ Yes (Chrome extension) | ✅ Yes | ❌ No | Free |
| **Playwright** | ❌ No | ✅ Yes | ❌ No | Free |

**Browser-Use advantages:**
- No extension required
- Simple CLI for humans
- Built-in cloud/stealth option
- Multiple session support

## Production Use

For production with many agents:

```python
from browser_use import Browser, sandbox, ChatBrowserUse
from browser_use.agent.service import Agent
import asyncio

@sandbox()
async def my_task(browser: Browser):
    agent = Agent(
        task="Find the top HN post",
        browser=browser,
        llm=ChatBrowserUse()
    )
    await agent.run()

asyncio.run(my_task())
```

**Production considerations:**
- Memory management (Chrome can consume a lot)
- Parallel execution scaling
- Use Browser Use Cloud for infrastructure

## Related Skills

- **SweetLink** — DevTools-based browser automation (uses your real Chrome)
- **agent-browser** — Clawdbot's built-in browser control
- **oracle** — Prompt bundler for multi-model runs

## Links

- **GitHub:** https://github.com/browser-use/browser-use
- **Docs:** https://docs.browser-use.com
- **Cloud:** https://cloud.browser-use.com
- **Discord:** https://link.browser-use.com/discord
- **X (Twitter):** https://x.com/browser_use
