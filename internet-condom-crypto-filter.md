---
title: Internet Condom - Local Crypto Filter Extension
anchor: When you want to filter out crypto shills and spam from X (Twitter) locally without any network calls
tags: [crypto, spam-filter, chrome-extension, local-ai, x-twitter, privacy]
description: Browser extension that filters crypto scams, AI spam, and promotional content from social media feeds using local fastText model
source_url: https://github.com/InternetCondom/InternetCondom
---

## My Reference

### Summary
A Chrome extension by Onur (maintainer of OpenClaw) that filters unwanted content from X locally. Uses a 122KB quantized fastText model running via WebAssembly — no network calls, no API, no data leaving the browser.

### Content

**Internet Condom** - Local runnable models for filtering out crypto shill content, AI replies, and other undesirable content.

**Vision:** Local-first filtering system for all types of unwanted social media content.

**Current Categories:**
- 🪙 Crypto scams & pump-and-dump schemes (current focus)
- 🤖 AI-generated spam replies
- 📢 Promotional spam & engagement bait
- 🗳️ Political content & partisan rage-bait
- 😶‍🌫️ Vagueposting & attention-seeking posts
- 🔥 Rage-bait & outrage farming
- 🤬 Profanities & toxic language
- 👊 Online harassment & pile-ons

**Technical Details:**
- fastText model (122KB quantized) running via WebAssembly
- ~2,900 labeled samples (clean: 1,482, crypto: 1,249, scam: 572, promo: 368)
- Crypto recall: 89%, False positive rate: < 2%
- Chrome extension MV3, content scripts scan posts/DMs as you scroll

**Install:**
1. Clone/download repo
2. Open `chrome://extensions`, enable Developer mode
3. Click "Load unpacked" → select `extension/` folder
4. Pin to toolbar

**Built using OpenClaw** — open framework for personal AI assistants.
