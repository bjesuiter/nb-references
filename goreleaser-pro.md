---
title: GoReleaser Pro - Software Release Automation
anchor: Paid tool for simplifying releases ($15/month) - macOS .app, npm, and more
tags: [goreleaser, release, automation, ci-cd, macos, npm, devops]
description: GoReleaser Pro simplifies software releases for .app, npm packages, and more - $15/month
source_url: https://goreleaser.com/pro/
---

## Summary

**GoReleaser Pro** is a paid, closed-source distribution of GoReleaser with additional features for professional software releases. Costs **~$15/month**.

## Key Pro Features

### macOS
- **Native App Bundles** — Build .app bundles with signing
- **DMG Creation** — Create macOS disk images
- **Notarization** — Apple notarization support

### Package Management
- **NPM registries** — Publish to npm registries
- **CloudSmith integration** — Alpine, apt, yum repositories
- **fury.io integration** — apt and yum repositories

### Release Features
- **AI changelog** — Improve/format release notes with AI
- **Template entire files** — Include templated files in releases
- **Split and merge builds** — Speed up CI with partial builds
- **Prepare/publish/announce separate** — Split release workflow

### Advanced
- **Cross-publish** — Release to GitLab, push Homebrew to GitHub
- **Monorepo support** — Use in monorepos
- **Include configuration** — Reuse config files
- **Podman support** — Rootless Docker builds

## Pricing

- **~$15/month**
- Low pricing likely to increase as features are added
- Discounts available for sponsors

## Is It Worth It?

**Worth it if you:**
- Regularly release macOS .app files
- Publish to npm registries
- Need notarization for macOS apps
- Want AI-generated changelogs
- Build multi-platform releases

**Free alternative:** GoReleaser free has most core features (binaries, Docker, Homebrew).

## Install

```bash
# Pro binary is separate
brew install goreleaser/tap/goreleaser-pro

# Or set GORELEASER_KEY env var
export GORELEASER_KEY="your-license-key"
```

## Related

- GoReleaser free: https://goreleaser.com
- Gumroad purchase: https://gum.co/goreleaser
