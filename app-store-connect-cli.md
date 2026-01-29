---
title: App Store Connect CLI
anchor: Nice CLI for releasing iOS apps to the App Store (current: v0.16)
tags: [ios, app-store, cli, release, automation, xcode]
description: Command-line tool for uploading and releasing iOS apps to the App Store
source_url: https://github.com/rudrankriyam/App-Store-Connect-CLI
---

## App Store Connect CLI

### Summary
A user-friendly command-line interface for uploading and releasing iOS applications to the Apple App Store. Current version: 0.16.

### Key Features
- **CLI-first:** Release iOS apps without leaving terminal
- **Authentication:** App Store Connect API integration
- **Upload:** Binary upload and processing
- **Release management:** Submit for review, release scheduling
- **Automation-friendly:** Scriptable workflows

### Use Cases
- CI/CD pipelines for iOS apps
- Automated release workflows
- Scripted beta deployments
- Scheduled App Store releases
- Reducing manual Work portal clicks

### Commands (example)
```bash
# Upload binary
asc-cli upload --path App.ipa

# Submit for review
asc-cli submit --version 1.2.0

# Release immediately
asc-cli release --version 1.2.0

# Schedule release
asc-cli release --version 1.2.0 --scheduled "2026-02-01T10:00:00Z"
```

### Links
- GitHub: https://github.com/rudrankriyam/App-Store-Connect-CLI
- Current version: 0.16
