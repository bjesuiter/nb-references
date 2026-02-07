---
title: App Store Connect CLI Skills
anchor: Agent skills to automate iOS/macOS app publishing via App Store Connect CLI
tags: [ios, macos, app-store, automation, cli, asc, xcode]
description: Collection of Agent Skills for shipping apps using the App Store Connect CLI (asc)
source_url: https://github.com/rudrankriyam/app-store-connect-cli-skills
---

## Reference

### Summary
A collection of Agent Skills for automating the entire App Store deployment pipeline using the [App Store Connect CLI](https://github.com/rudrankriyam/App-Store-Connect-CLI). Covers builds, TestFlight, metadata, submissions, and signing.

### Available Skills

| Skill | Purpose |
|-------|----------|
| `asc-cli-usage` | asc command flags, pagination, output, auth |
| `asc-xcode-build` | Build/archival with xcodebuild for iOS/macOS |
| `asc-release-flow` | End-to-end TestFlight & App Store release |
| `asc-signing-setup` | Bundle IDs, certificates, provisioning profiles |
| `asc-id-resolver` | Resolve IDs for apps, builds, versions, testers |
| `asc-metadata-sync` | Metadata & localization sync (Fastlane format) |
| `asc-submission-health` | Preflight checks, review monitoring |
| `asc-testflight-orchestration` | Beta groups, testers, What to Test notes |
| `asc-build-lifecycle` | Build processing, resolution, cleanup |
| `asc-ppp-pricing` | Purchasing Power Parity pricing |
| `asc-notarization` | macOS notarization with Developer ID signing |

### Installation
```bash
npx add-skill rudrankriyam/app-store-connect-cli-skills
```

### Usage Examples
- "Build and upload my macOS app to App Store Connect"
- "Publish MyApp build 1.2.3 to TestFlight group Beta Testers"
- "Set up signing for bundle ID com.example.app"
- "Validate Fastlane metadata and sync to App Store Connect"
- "Submit iOS app version 2.0 to App Store review"
