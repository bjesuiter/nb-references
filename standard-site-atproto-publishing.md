---
title: Standard.site Publishing on AT Protocol
anchor: AT Protocol lexicons for blog posts and long-form writing
tags: [atproto, bluesky, standard-site, publishing, lexicons]
description: Introduction to Standard.site lexicons for publishing long-form content on AT Protocol
source_url: https://standard.site/docs/introduction/
---

## Summary

Standard.site brings long-form writing into the social web by linking blog posts and articles to AT Protocol. It helps make published work easier to share and find while ensuring authors maintain ownership via records stored on their PDS (Personal Data Server).

## Core Lexicons

### Publications (`site.standard.publication`)
Represents a collection of documents published to the web. Includes location, theming, preferences.

### Documents (`site.standard.document`)
Metadata for individual documents including relation to publication, path, and full content.

### Subscriptions (`site.standard.graph.subscription`)
Tracks relationships between users and publications for follow functionality and personalized feeds.

## Design Philosophy

- Minimal requirements for adoptability
- Lightweight but extensible
- Existing properties are starting points, not constraints

## Related Lexicons

- Supporting lexicons for social features and utility
- Verification for domain linking

## Key Links

- [Quick Start Guide](https://standard.site/docs/quick-start/)
- [Publication Lexicon Schema](https://standard.site/docs/lexicons/publication/)
- [Document Lexicon Schema](https://standard.site/docs/lexicons/document/)
- [Implementations](https://standard.site/docs/implementations/)
