---
title: OctoStore - Leader Election & Distributed Locking as a Service
anchor: Single binary for consensus, leader election, and distributed locking
tags: [distributed-systems, locking, leader-election, consensus, rust, self-hosted]
description: Single binary distributed locking service with fencing tokens - no etcd/Consul/Kubernetes needed
source_url: https://github.com/octostore/octostore.io
---

## Summary

**OctoStore** is a single-binary leader election and distributed locking service. No Kubernetes, no etcd cluster, no Consul agents—just `./octostore` and you're running.

**Free hosted version:** https://api.octostore.io

## Why OctoStore?

Every existing solution requires running a consensus cluster (etcd, ZooKeeper, Consul) or using proprietary cloud services. OctoStore offers:

- **One binary** — MIT licensed, zero runtime dependencies
- **Simple HTTP API** — curl works, no client libraries needed
- **Fencing tokens** — actually safe distributed locking (not Redlock)
- **Self-hostable** — Runs anywhere, no cluster required
- **Free hosted** — GitHub OAuth sign-in, 30 seconds to start

## Architecture

| Component | Technology |
|-----------|------------|
| Language | Rust (Axum + Tokio) |
| Lock Storage | DashMap (concurrent in-memory) |
| Persistence | SQLite (user accounts + fencing tokens) |
| Auth | GitHub OAuth |
| Process | Single binary, no cluster, no consensus protocol |

**Simplicity philosophy:** If the server dies, all locks expire and clients re-acquire. No zombie locks.

## Quick Start

### Hosted Version
```bash
# Sign in with GitHub
open https://api.octostore.io/auth/github

# Acquire a lock
curl -X POST https://api.octostore.io/locks/my-service/acquire \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"ttl_seconds": 60}'
```

### Self-Host
```bash
# Download binary
curl -fsSL https://octostore.io/install.sh | bash

# Or build from source
cargo build --release

# Configure (GitHub OAuth)
cp .env.example .env

# Run
./target/release/octostore-lock
```

## API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/auth/github` | Start GitHub OAuth flow |
| POST | `/auth/token/rotate` | Rotate bearer token |
| POST | `/locks/{name}/acquire` | Acquire a lock |
| POST | `/locks/{name}/release` | Release a lock |
| POST | `/locks/{name}/renew` | Extend lock TTL |
| GET | `/locks/{name}` | Check lock status |
| GET | `/locks` | List active locks |
| GET | `/docs` | Interactive API docs (Scalar) |
| GET | `/openapi.yaml` | OpenAPI spec |

### Acquire Lock Response

**Success:**
```json
{
  "status": "acquired",
  "lease_id": "uuid",
  "fencing_token": 42,
  "expires_at": "2026-02-12T01:00:00Z"
}
```

**Already held:**
```json
{
  "status": "held",
  "holder_id": "other-user-uuid",
  "expires_at": "2026-02-12T00:55:00Z"
}
```

### Release / Renew
```bash
# Release
curl -X POST https://api.octostore.io/locks/leader/release \
  -H "Authorization: Bearer $TOKEN" \
  -d '{"lease_id": "your-lease-uuid"}'

# Renew (extend TTL)
curl -X POST https://api.octostore.io/locks/leader/renew \
  -H "Authorization: Bearer $TOKEN" \
  -d '{"lease_id": "your-lease-uuid", "ttl_seconds": 60}'
```

## Constraints

| Limit | Value |
|-------|-------|
| Locks per account | 100 |
| Max TTL | 1 hour (auto-expires) |
| Lock name format | alphanumeric + hyphens + dots, max 128 chars |
| Fencing tokens | Monotonically increasing |

## Fencing Tokens

This is what makes OctoStore's locking **actually safe** (unlike Redis/Redlock):

Every acquire returns a **fencing token** — a monotonically increasing integer. Use it to prevent stale lock holders from making writes:

```python
def write_with_fence(data, fencing_token):
    db.execute(
        "UPDATE state SET data=?, fence=? WHERE fence < ?",
        (data, fencing_token, fencing_token)
    )
```

## SDKs

Available for all major languages:

| Language | Package |
|----------|---------|
| Python | `sdks/python` |
| Go | `sdks/go` |
| Rust | `sdks/rust` |
| TypeScript | `sdks/typescript` |
| Java | `sdks/java` |
| C# | `sdks/csharp` |
| Ruby | `sdks/ruby` |
| PHP | `sdks/php` |

## Benchmark

```bash
cargo build --release
./target/release/octostore-bench \
  --token $TOKEN \
  --admin-key $KEY \
  --concurrency 100 \
  --duration 30
```

## Related Concepts

- Distributed locking patterns
- Leader election algorithms
- Fencing tokens (safe distributed locks)
- Single-binary deployment
- HTTP-based service discovery

## Links

- Repository: https://github.com/octostore/octostore.io
- Hosted API: https://api.octostore.io
- Docs: https://api.octostore.io/docs
- Self-host install: https://octostore.io/install.sh
