---
title: Deno Sandbox - Code Isolation Runner
anchor: Lightweight Linux microVMs for running untrusted LLM-generated code with network egress control and secret protection
tags: [deno, sandbox, code-isolation, security, ai, runners, deno-deploy]
description: Deno Sandbox provides secure code execution for untrusted LLM-generated code with secrets protection and network egress control. Competes with sprites.dev and Daytona.
source_url: https://deno.com/blog/introducing-deno-sandbox
docs_url: https://docs.deno.com/sandbox/
---

## My Reference

### Summary
Deno Sandbox is a code isolation platform for running untrusted LLM-generated code securely. Provides lightweight Linux microVMs with defense-in-depth security: network egress control, secret protection, and direct deployment to Deno Deploy.

### Key Features

**Security**
- **Secrets That Can't Be Stolen:** Secrets enter as placeholders, only materialize for approved hosts
- **Network Egress Control:** Whitelist allowed hosts, block unlisted connections
- **Defense-in-depth:** VM-level + runtime-level permissions

**Technical Specs**
| Spec | Value |
|------|-------|
| Regions | Amsterdam, Chicago |
| vCPUs | 2 |
| Memory | 768 MB - 4 GB |
| Boot time | < 1 second |
| Max lifetime | 30 minutes |
| Persistence | Volumes + Snapshots |

**Sandbox to Production**
- Deploy directly from sandbox to Deno Deploy
- No rebuilding, no re-authentication

**Use Cases**
- AI agents executing code
- Vibe-coding environments
- Secure plugin systems
- Ephemeral CI runners
- Customer-supplied code execution

### Pricing (Deno Deploy Plan)

- Compute: $0.05/h CPU time (40h included with Pro)
- Memory: $0.016/GB-h (1000 GB-h included with Pro)
- Storage: $0.20/GiB-month (5 GiB included with Pro)

### SDKs

- JavaScript/TypeScript: `jsr.io/@deno/sandbox` or `npm @deno/sandbox`
- Python: `pypi.org/project/deno-sandbox`

### Resources

- **Landing Page:** https://deno.com/sandbox
- **Docs:** https://docs.deno.com/sandbox/
- **Blog:** https://deno.com/blog/introducing-deno-sandbox

### Competitors

- sprites.dev
- Daytona
