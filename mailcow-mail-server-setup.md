---
title: Mailcow High-Quality Mail Server Setup (jusec Tutorial)
anchor: How to set up a complete mail server with Mailcow - tutorial by jusec
tags: [mail-server, mailcow, self-hosted, email, docker, smtp]
description: Complete guide for setting up a production-ready mail server using Mailcow Dockerized suite
source_url: https://youtu.be/Oi4VOW_g0rM
---

# Mailcow Mail Server Setup Reference

**Tutorial:** jusec YouTube video
**Video:** https://youtu.be/Oi4VOW_g0rM

---

## What is Mailcow?

**Mailcow** is a Dockerized email server suite with a modern web UI. It combines:

| Component | Function |
|-----------|----------|
| **Postfix** | SMTP (mail transfer) |
| **Dovecot** | IMAP/POP3 (mail retrieval) |
| **Rspamd** | Spam filtering |
| **ClamAV** | Virus scanning |
| **SOGo** | Webmail & groupware |
| **Acme.sh** | Let's Encrypt certificates |
| **MySQL** | Configuration storage |

---

## Prerequisites

### Domain Requirements

- **Registered domain** with DNS access
- **SPF, DKIM, DMARC** records capability
- **Reverse DNS (PTR)** for server IP

### Server Requirements

| Resource | Minimum | Recommended |
|----------|---------|-------------|
| **CPU** | 1 vCPU | 2+ vCPU |
| **RAM** | 2 GB | 4+ GB |
| **Storage** | 10 GB SSD | 50+ GB SSD |
| **IP** | Dedicated | Dedicated |

### Ports Required

```
25  - SMTP (incoming mail)
143 - IMAP
465 - SMTPS
587 - Submission
993 - IMAPS
995 - POP3S
443 - Web UI (HTTPS)
```

---

## Setup Steps (jusec Tutorial Flow)

### 1. Prepare Server

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y curl git

# Set hostname
sudo hostnamectl set-hostname mail.yourdomain.com
```

### 2. Install Docker & Docker Compose

```bash
# Docker
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker $USER

# Docker Compose (v2)
sudo mkdir -p /usr/local/lib/docker/cli-plugins
curl -SL https://github.com/docker/compose/releases/download/v2.24.0/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose
chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
```

### 3. Clone Mailcow Repository

```bash
sudo git clone https://github.com/mailcow/mailcow-dockerized.git /opt/mailcow-dockerized
cd /opt/mailcow-dockerized
```

### 4. Generate Configuration

```bash
./generate_config.sh
```

**Key questions answered:**
- Mail server hostname (e.g., `mail.yourdomain.com`)
- Timezone
- Web server port (443)

### 5. Configure DNS

Add these records to your domain's DNS:

| Type | Host | Value |
|------|------|-------|
| **A** | mail | SERVER_IP |
| **MX** | @ | mail.yourdomain.com |
| **TXT** | @ | v=spf1 ip4:SERVER_IP -all |
| **TXT** | dkim._domainkey | (from Mailcow DKIM key) |

### 6. Start Mailcow

```bash
docker compose up -d
```

### 7. Access Web UI

**URL:** https://mail.yourdomain.com
**Default user:** admin
**Default password:** moohoo (change immediately!)

---

## Post-Setup Configuration

### 1. Create Domain & Mailboxes

In Mailcow UI:
1. **E-Mail → Domains** → Add your domain
2. **E-Mail → Mailboxes** → Add users

### 2. Enable DKIM

```bash
cd /opt/mailcow-dockerized
docker exec $(docker compose ps -q postfix-mailcow) amavisd-new showkeys
```

Copy the DKIM record to your DNS.

### 3. Configure RDNS

Set reverse DNS for your server's IP to `mail.yourdomain.com` (via hosting provider).

### 4. Test Setup

```bash
# Check SMTP
telnet mail.yourdomain.com 25

# Check ports
nc -zv mail.yourdomain.com 25 143 465 587 993 995
```

---

## Common Issues & Fixes

### Port 25 Blocked

Many VPS providers block port 25. Solutions:
- Contact provider to unblock
- Use a mail-friendly provider (Hetzner, Contabo)

### IP Blacklisting

Check if IP is blacklisted:
- https://mxtoolbox.com/blacklists.aspx

If blacklisted, request delisting or use different IP.

### Let's Encrypt Issues

```bash
# Renew certificates manually
docker compose exec acme-mailcow docker-entrypoint.sh
```

---

## Security Best Practices

1. **Strong passwords** for all mailboxes
2. **2FA** for admin UI (Mailcow 2024+)
3. **Fail2ban** enabled by default
4. **Regular updates**:
   ```bash
   cd /opt/mailcow-dockerized
   git pull
   docker compose pull
   docker compose up -d
   ```
5. **Rate limiting** in Postfix config
6. **Separate VLAN** for mail server

---

## Mailcow UI Features

- **Webmail** (SOGo)
- **Email filters** (Sievelang)
- **Quarantine** (spam/virus)
- **DKIM/ARC/DMARC** reports
- **Mail queue** monitoring
- **DKIM signing** per domain
- **Alias management**
- **Public folders**

---

## Alternative Tutorials

| Source | Link |
|--------|------|
| Official Docs | https://mailcow.github.io/mailcow-dockerized-docs/ |
| Mailcow Website | https://mailcow.org/ |
| Docker Hub | https://hub.docker.com/r/mailcow/ |

---

## Related Tools

- **Mailu** — Similar Dockerized mail server
- **iRedMail** — Full mail server installer
- **Postfix/Dovecot from scratch** — Maximum control
