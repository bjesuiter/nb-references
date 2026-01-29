---
title: Moltworker - Moltbot on Cloudflare Workers
anchor: Cloudflare's implementation of Moltbot running on Workers with Sandboxes, AI Gateway, R2, and Browser Rendering
tags: [moltbot, cloudflare, workers, ai-agents, self-hosted, serverless, sandbox]
description: Cloudflare's proof-of-concept running Moltbot on their Developer Platform using Sandboxes, AI Gateway, R2 storage, and Browser Rendering
source_url: https://blog.cloudflare.com/moltworker-self-hosted-ai-agent/
---

## Moltworker

### Summary
Cloudflare built **Moltworker** — a self-hosted AI agent (Moltbot/Clawdbot) running on Cloudflare Workers instead of local hardware. Uses Sandboxes for secure code execution, R2 for persistence, AI Gateway for model routing, and Browser Rendering for web automation.

### Architecture

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Entrypoint     │────▶│   Sandbox       │────▶│  Moltbot        │
│  Worker         │     │  Container      │     │  Gateway        │
│  (API Router)   │     │  (Secure Exec)  │     │  (Runtime)      │
└─────────────────┘     └─────────────────┘     └─────────────────┘
         │                       │                       │
         │                       │                       │
    ┌────▼────┐            ┌────▼────┐            ┌────▼────┐
    │ Access  │            │   R2    │            │ Browser │
    │ (Auth)  │            │ Storage │            │Rendering│
    └─────────┘            └─────────┘            └─────────┘
```

### Key Components Used

| Component | Purpose |
|-----------|---------|
| **Workers** | API router, entrypoint, admin UI |
| **Sandboxes** | Run Moltbot in isolated container, execute commands |
| **AI Gateway** | Proxy AI requests, BYOK, Unified Billing, observability |
| **R2** | Persistent storage for sessions, memory files |
| **Browser Rendering** | Headless Chromium for web automation (Puppeteer/Playwright) |
| **Zero Trust Access** | Authentication, JWT validation, observability |

### How It Works

1. **Entrypoint Worker** — Routes API calls, proxies between services
2. **Sandbox Container** — Runs full Moltbot Gateway runtime
3. **R2 Mount** — Persistent storage survives container lifecycle
4. **CDP Proxy** — Connects container to Browser Rendering API
5. **Access Protection** — All endpoints protected, JWT tokens

### Advantages Over Local Deployment

- **No dedicated hardware** — Run on Cloudflare's global network
- **Serverless scaling** — No container management overhead
- **Built-in observability** — AI Gateway logs, cost tracking
- **Zero Trust security** — Access policies, authentication handled
- **Edge location** — Low latency worldwide

### Demo Features Shown

- Route finding with Google Maps (screenshot in Slack)
- Memory persistence across requests
- Food recommendations with visual browsing
- Video generation using ffmpeg + browser frames

### Code Example: AI Gateway Integration

```bash
# Create AI Gateway instance
# Enable Anthropic provider
# Add Claude API key OR use Unified Billing
# Set environment variable:
export ANTHROPIC_BASE_URL="https://gateway.ai.cloudflare.com/..."
```

### Resources

- **Blog post:** https://blog.cloudflare.com/moltworker-self-hosted-ai-agent/
- **GitHub:** https://github.com/cloudflare/moltworker
- **Pricing:** $5/month Workers paid plan for Sandboxes; AI Gateway free; R2 has free tier

### Quote

> "Moltworker is a proof of concept, not a Cloudflare product. Our goal is to showcase... features of our Developer Platform that can be used to run AI agents and unsupervised code efficiently and securely."
