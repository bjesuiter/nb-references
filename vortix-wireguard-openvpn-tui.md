---
title: "Vortix — TUI for WireGuard and OpenVPN"
anchor: "Terminal UI for WireGuard and OpenVPN with real-time telemetry, leak detection, and kill switch"
tags: [wireguard, openvpn, vpn, tui, terminal, rust, security]
description: "Terminal UI for managing WireGuard and OpenVPN with real-time telemetry, leak detection, and built-in kill switch"
source_url: "https://github.com/Harry-kp/vortix"
---

## Reference

### Summary
Vortix is a terminal-based UI for managing WireGuard and OpenVPN connections. It provides real-time telemetry (throughput, latency, jitter, packet loss), leak detection (IPv6/DNS), and a built-in kill switch.

**Problem Solved:**
Single interface to manage VPN connections with visibility into connection health, without needing GUI clients or remembering CLI flags.

### Features
- **Multi-Protocol Support** — WireGuard & OpenVPN (auto-detects .conf and .ovpn files)
- **Real-Time Telemetry** — Throughput, latency, jitter, packet loss
- **Geo-Location** — Shows exit IP city and country
- **Leak Detection** — Monitors for IPv6 and DNS leaks in real-time
- **Kill Switch** — Built-in firewall management (macOS: pfctl, Linux: iptables/nftables)
- **Keyboard-Driven** — Full TUI navigation without mouse
- **SSH Compatible** — Works over SSH connections
- **Lightweight** — ~15MB memory, <100ms startup

### Installation

**From crates.io (Recommended):**
```bash
cargo install vortix
```

**Quick install (Binary):**
```bash
curl --proto '=https' --tlsv1.2 -LsSf https://github.com/Harry-kp/vortix/releases/latest/download/vortix-installer.sh | sh
```

**Static binary (Linux):**
Download from releases page for fully static binary with no dependencies.

### Requirements

**macOS:**
- macOS 12+
- Rust 1.75+
- WireGuard: `brew install wireguard-tools`
- OpenVPN: `brew install openvpn`

**Linux:**
- Linux kernel 3.10+
- iproute2, iptables or nftables
- Rust 1.75+

### Keybindings
| Key | Action |
|-----|--------|
| Tab | Cycle Focus (Panels) |
| 1-9 | Connect to Quick-Slot |
| Enter | Connect / Toggle Profile |
| d | Disconnect |
| r | Reconnect |
| i | Import Profile |
| v | View Config |
| y | Copy Public IP |
| K | Toggle Kill Switch |
| q | Quit |

### Compared to Alternatives
| Feature | Vortix | GUI Clients | CLI-only |
|---------|--------|-------------|----------|
| Memory | ~15MB | 200-500MB | ~5MB |
| Startup | <100ms | 2-5s | Instant |
| Real-time telemetry | ✅ | ✅ | ❌ |
| Leak detection | ✅ | Some | ❌ |
| Kill switch | ✅ | ✅ | Manual |
| Works over SSH | ✅ | ❌ | ✅ |

### Developer
[Harry-kp](https://github.com/Harry-kp) — Sponsor: https://github.com/sponsors/Harry-kp

### Links
- Crates.io: https://crates.io/crates/vortix
- Featured in Terminal Trove: https://terminaltrove.com/vortix/
