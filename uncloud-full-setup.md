---
title: Uncloud - Full Cluster Setup Guide
anchor: How to set up a complete Uncloud cluster with WireGuard mesh, service discovery, and ingress
tags: [uncloud, cluster, wireguard, container-orchestration, self-hosted, docker]
description: Complete tutorial for setting up Uncloud cluster - lightweight container orchestration with automatic WireGuard mesh networking
source_url: https://labs.iximiuz.com/tutorials/uncloud-create-cluster-ebebf72b
---

# Uncloud Full Setup Reference

**What it is:** Lightweight clustering and container orchestration tool. Creates secure WireGuard mesh between Docker hosts with automatic service discovery, load balancing, and HTTPS ingress — without Kubernetes complexity.

Website: https://uncloud.run/docs/

---

## Installation

### CLI (uc) Installation

```bash
# Install Uncloud CLI
curl -sSf https://uncloud.run/install.sh | bash

# Verify
uc --version
```

### SSH Setup

Ensure SSH access to target machines with your key:
```bash
ssh-copy-id -i ~/.ssh/id_ed25519 user@server-1
ssh-copy-id -i ~/.ssh/id_ed25519 user@server-2
```

---

## Initialize Cluster

### Step 1: Add First Machine (Control + Worker)

```bash
uc machine init user@server-1
```

**Options explained:**
- `--public-ip auto` (default) — Configure for ingress
- `--public-ip none` — Skip ingress config (for NAT environments)
- `--no-dns` — Skip *.uncld.dev subdomain reservation

### Step 2: Add Second Machine

```bash
uc machine add user@server-2
```

### Step 3: Rename Machines (Optional)

```bash
uc machine rename machine-incv server-1
uc machine rename machine-m4wy server-2
```

### Verify Cluster

```bash
uc machine ls
```

**Output:**
```
NAME     STATE  ADDRESS       PUBLIC IP  WIREGUARD ENDPOINTS                   MACHINE ID
server-1 Up     10.210.0.1/24 -           172.16.0.3:51820, 65.109.107.161:51820 42866c...
server-2 Up     10.210.1.1/24 -           172.16.0.4:51820, 65.109.107.161:51820 4c453f...
```

**Columns:**
- **ADDRESS** — Private IP in WireGuard mesh (/24 subnet per machine)
- **WIREGUARD ENDPOINTS** — How other machines reach this one
- **MACHINE ID** — Unique, never changes

---

## What Gets Installed

On each machine:
- **Docker** — Container runtime
- **uncloudd** — Uncloud daemon
- **Corrosion** — State sync + service discovery

---

## Context Management

### List Contexts

```bash
uc ctx ls
```

**Config file:** `~/.config/uncloud/config.yaml`

```yaml
current_context: default
contexts:
  default:
    connections:
      - ssh: user@server-1
        ssh_key_file: ~/.ssh/id_ed25519
      - ssh: user@server-2
        ssh_key_file: ~/.ssh/id_ed25519
```

### Switch Contexts

```bash
uc ctx use <context-name>
```

---

## Deploy Services

### Quick Deploy (uc run)

```bash
# Deploy Excalidraw as example
uc run --name excalidraw --publish excalidraw.internal:80/http excalidraw/excalidraw
```

**What it does:**
1. Picks a random machine
2. Pulls Docker image
3. Creates service with container
4. Exposes on hostname:port via Caddy

### Check Services

```bash
uc ls                    # List all services
uc inspect <service>     # Detailed view
```

**Output:**
```
NAME        MODE       REPLICAS IMAGE                     ENDPOINTS
caddy       global     2        caddy:2.10.2
excalidraw  replicated 1        excalidraw/excalidraw      http://excalidraw.internal → :80
```

### Service Modes

| Mode | Description |
|------|-------------|
| **global** | One replica per node (e.g., Caddy) |
| **replicated** | N replicas on any nodes |

### Scale Service

```bash
uc scale excalidraw 2
```

---

## Access Services

### Via Internal Hostname

```bash
# From any cluster machine
curl --header 'Host: excalidraw.internal' server-1
```

**Internal hostnames:**
- `<service>.internal` — Resolves on all nodes
- Caddy routes requests to correct container

### Via Published Port

```bash
uc run --name myapp --publish myapp.example.com:80/http myimage:latest
```

---

## Publishing to Internet

### With Managed DNS

```bash
uc machine init user@server-1 --public-ip auto
# *.uncld.dev subdomain auto-assigned

# Or with custom domain
uc dns add mydomain.com
```

### With Custom Domain

```bash
# Point DNS to server public IP
uc machine update server-1 --public-ip 1.2.3.4
```

---

## Docker Compose Deployments

```bash
uc deploy -f docker-compose.yml
```

---

## WireGuard Mesh Network

**Automatically created between all nodes:**
- Each machine gets /24 subnet (10.210.0.0/24, 10.210.1.0/24, etc.)
- Containers get IPs from machine's subnet
- Cross-machine communication via WireGuard

**Endpoints include:**
- Private IP (for same network machines)
- Public IP (for remote machines)

---

## Managing Caddy (Ingress)

Caddy runs in "global" mode by default, providing:
- Automatic routing to services
- Load balancing
- HTTPS (when configured)

### View Caddy Config

```bash
uc caddy config
```

---

## Common Commands

| Command | Description |
|---------|-------------|
| `uc machine ls` | List cluster machines |
| `uc machine init user@host` | Add first machine |
| `uc machine add user@host` | Add machine to cluster |
| `uc machine rename <old> <new>` | Rename machine |
| `uc machine update <name> --public-ip X.X.X.X` | Update public IP |
| `uc ls` | List services |
| `uc run --name <name> <image>` | Deploy service |
| `uc scale <service> <n>` | Scale replicas |
| `uc ctx ls` | List contexts |
| `uc ctx use <name>` | Switch context |
| `uc deploy -f compose.yml` | Deploy from compose |

---

## Next Steps

1. **Scale services:** `uc scale excalidraw 2`
2. **HTTPS ingress:** Configure custom domains with TLS
3. **Multi-region:** Add machines in different data centers
4. **Monitoring:** Add observability stack

---

## Playground

Try in browser: https://labs.iximiuz.com/playgrounds/uncloud-cluster-64523f7c

---

## Resources

- **Docs:** https://uncloud.run/docs/
- **CLI Reference:** https://uncloud.run/docs/cli-reference/
- **GitHub:** https://github.com/tonyo/uncloud-labs/
