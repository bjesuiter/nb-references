---
title: Tangled - Decentralized Git on ATProto
anchor: Decentralized Git hosting and collaboration platform built on ATProto
tags: [atproto, bluesky, git, decentralized, self-hosted, collaboration]
description: Decentralized Git hosting platform built on the ATProtocol
source_url: https://tangled.org/
---

## My Reference

### Summary
Tangled is a decentralized Git hosting and collaboration platform built on ATProto. Developers own their code, open source communities can self-govern.

### Key Features

**Lightweight Git Repo Hosting**
- Host repos on your own infrastructure using "knots" (headless servers)
- Add friends to your knot or invite collaborators
- Fine-grained role-based access control
- SSH for push/pull

**Improved Pull Request Model**
- Round-based PR flow with inter-diffing between rounds
- Stacked pull requests using Jujutsu's change IDs
- Paste git diff/format-patch for quick drive-by changes

**Run Pipelines with Spindles**
- CI runners on your own infrastructure
- Native Nix support
- Extensible execution backends

### Related
- pdsfs: Mount PDS as FUSE filesystem (for accessing data)
