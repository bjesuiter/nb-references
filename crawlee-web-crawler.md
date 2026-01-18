---
title: Crawlee - Reliable Open-Source Web Crawler Framework
anchor: Production-ready Node.js web scraping and crawling library by Apify
tags: [web-scraper, crawler, nodejs, typescript, apify, scraping]
description: Crawlee is an open-source library for building reliable, production-ready web crawlers with intelligent request handling, storage persistence, and browser automation
source_url: https://www.opensourceprojects.dev/post/4cb65fad-e2df-4954-b180-fe022b779872
---

# Crawlee Reference

**What it is:** Open-source web scraping/crawling library built by Apify. Handles the messy infrastructure so you focus on data extraction logic.

Website: https://github.com/apify/crawlee

---

## Key Features

| Feature | Description |
|---------|-------------|
| **Multiple crawl modes** | HTTP, Puppeteer, Playwright, JSDOM |
| **Persistent storage** | Request queue, data, state saved to disk |
| **Smart retries** | Exponential backoff, auto-retry failed requests |
| **Proxy rotation** | Built-in session/proxy management |
| **TypeScript** | Clean, modern, type-safe code |
| **Scalable** | Script to distributed system without code changes |

---

## Why Crawlee

- **Storage persistence** — Stop/restart without losing progress
- **Smart request handling** — Auto-retries, parallel execution, session cookies
- **Developer experience** — Clean API, comprehensive docs, good examples
- **Open source** — No lock-in, inspectable code

---

## Quick Start

```bash
# Create new crawler project
npx crawlee create my-crawler

# Navigate and run
cd my-crawler
npm start
```

**Templates available:**
- Basic HTTP crawler
- Browser-based crawler (Puppeteer/Playwright)

---

## Architecture

### Storage (Persisted by Default)

```
/storage
  /datasets        # Extracted data
  /key_valueStores # Request inputs, outputs
  /request_queues  # URLs to crawl
  /profiles        # Proxy sessions
```

### Request Handling

- Automatic retry with exponential backoff
- Failed request marking
- Parallel execution control
- Session cookie management

### Browser Support

| Engine | Use Case |
|--------|----------|
| HTTP (axios) | Simple pages, APIs |
| Puppeteer | Light browser automation |
| Playwright | Modern, feature-rich browser |
| JSDOM | Legacy support |

---

## Use Cases

- **Data aggregation** — Collect data from multiple sources
- **Monitoring** — Track price changes, content updates
- **Testing** — Automated site testing
- **Automation** — Form submissions, workflows

---

## Comparison

| Tool | Pros | Cons |
|------|------|------|
| **Crawlee** | Full-featured, persistent, scalable | Heavier than simple scripts |
| **Cheerio** | Lightweight, fast | No browser, no persistence |
| **Puppeteer** | Browser control | Manual queue/retries needed |
| **Playwright** | Modern browser API | Same as Puppeteer |

---

## Code Example

```typescript
import { CheerioCrawler } from 'crawlee';

const crawler = new CheerioCrawler({
  async requestHandler({ request, $ }) {
    const title = $('title').text();
    console.log(`Title: ${title}`);
  },
});

await crawler.addUrls(['https://example.com']);
await crawler.run();
```

---

## Best Practices

1. **Use CheerioCrawler** for static HTML
2. **Use Playwright/Puppeteer** for JavaScript-heavy sites
3. **Persist storage** for long-running crawls
4. **Rotate proxies** to avoid blocking
5. **Respect robots.txt** and rate limits

---

## Related

- See [CyberScraper 2077](cyberscraper-2077.md) for AI-powered scraping
- See [Playwright automation](../playwright-automation.md) for browser control
