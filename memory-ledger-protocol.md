---
title: Memory Ledger Protocol (MLP) - Sovereign Memory for AI
anchor: Protocol for portable, verifiable, consent-aware AI memory across platforms - fixes trapped AI memories
tags: [memory, protocol, decentralization, ai, sovereignty, portable-memory]
description: MLP separates content, verification, and access for sovereign AI memory across platforms
source_url: https://github.com/Riley-Coyote/memory-ledger-protocol-v0.2
---

## Summary

**Memory Ledger Protocol (MLP)** is a portable, verifiable, consent-aware memory format and persistence workflow for digital intelligence across platforms.

### The Problem MLP Solves

AI memories are trapped on platforms:
- ChatGPT memories live on OpenAI's servers
- Claude memories on Anthropic's servers
- Gemini memories on Google's servers
- **You don't control any of it**

### What MLP Does

Separates three things platforms bundle together:

| Layer | Today (Bundled) | MLP (Unbundled) |
|-------|-----------------|-----------------|
| Content | Platform stores | Encrypted blobs you control |
| Verification | Platform vouches | Public ledger with proofs |
| Access | Platform decides | Your keys, your control |

### Core Components

- **MemoryEnvelope** - Ledger-facing record with pointers and attestations
- **MemoryBlob** - Encrypted payload with your memories
- **AccessPolicy** - Machine-readable consent rules
- **IdentityKernel** - Minimal portable "I am" (values, boundaries, preferences)
- **ContextPack** - Runtime bundle for session initialization

### Trust Model

- **You** → Trusted (control your keys)
- **Your AI Agent** → Partial (signs when enabled)
- **Platform** → Untrusted (never sees decryption keys)
- **Storage Network** → Untrusted (only holds ciphertext)
- **Ledger Nodes** → Untrusted (only holds pointers)

### Conformance Levels

| Profile | Requirements |
|---------|--------------|
| MLP-CORE | Envelope + blob + user signature, access policy |
| MLP-PLUS | Core + agent signature, kernel + context packs |
| MLP-ADV | Plus + witness signatures, privacy commitments |

### Continuity Framework

Reflection system that transforms passive memory logging into active development:
- **Reflect** - Analyze conversations after sessions end
- **Extract** - Pull structured memories with 7 types + confidence scores
- **Score** - Assign 0.0-1.0 confidence based on evidence
- **Question** - Generate follow-up questions from gaps
- **Surface** - Present relevant questions when user returns

### The Guardian Pattern

An AI that understands your patterns:
- When you think best
- What triggers breakthroughs
- Where your blind spots are
- How you've evolved over time

> "It's 2 AM and your cognitive patterns suggest you're burning out. The insight you're chasing will come faster after sleep."

### Integration Options

**Claude Code:**
- Copy `skills/claude-code/SKILL.md` to project
- Stores memories locally in `~/clawd/memory/`

**OpenClaw:**
- `skills/openclaw/continuity/` - Local markdown storage only
- `skills/openclaw/full-stack/` - + IPFS/Pinata encrypted storage

### Token: $POLYPHONIC

Enables coordination without centralization:
- **Payment** - Storage nodes, verification nodes
- **Governance** - Protocol upgrades voting
- **Alignment** - Stakeholders want network success

### Resources
- **Spec:** [MLP-0.2.md](https://github.com/Riley-Coyote/memory-ledger-protocol-v0.2/blob/main/spec/MLP-0.2.md)
- **Continuity Framework:** [continuity-framework.md](https://github.com/Riley-Coyote/memory-ledger-protocol-v0.2/blob/main/docs/continuity-framework.md)
- **Polyphonic (reference impl):** polyphonic.chat
