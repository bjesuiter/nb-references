---
title: Webspace Invaders - Protecting Personal Sites from AI Bots
anchor: Strategies to protect small personal websites from AI crawler scraping
tags: [security, bots, ai, website, protection, crawl]
description: Matthias Ott's article on how AI bots are overwhelming personal websites and strategies to protect them
source_url: https://matthiasott.com/articles/webspace-invaders
---

## My Reference

### Summary
Matthias Ott describes how AI companies' crawlers (GPTBot, Claude-SearchBot, OAI-Searchbot, etc.) are systematically harvesting personal websites for training data, causing significant server load. His hosting provider blocked countries like Canada to stop the "attack," making his site inaccessible to legitimate readers. ~50% of web traffic is now non-human bots. AI bot traffic surged to 4.2% of HTML requests (excluding Google), with Googlebot alone at 11% on some days.

### Key Points
- **Problem:** AI crawlers from OpenAI, Meta, Anthropic are "binge reading" personal sites multiple times daily
- **Impact:** Small sites on shared hosting get overwhelmed; hosting providers implement extreme geo-blocking
- **Scale:** 50% of web traffic is bots; AI bot traffic constantly growing
- **Hypocrisy:** Companies externalize crawling costs while small site owners pay for bandwidth
- **Solution approaches:** robots.txt compliance, rate limiting, firewall rules, hosting-level protection

### Protection Strategies Mentioned
1. robots.txt - but compliance is voluntary
2. Rate limiting - at server/hosting level
3. Firewall rules - block known AI bot IP ranges
4. Hosting-level geo-blocking - but blocks legitimate users
5. DDoS protection services - may help absorb bot traffic
