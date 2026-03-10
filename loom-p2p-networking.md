---
title: Loom - Native Apple P2P Networking Library
anchor: When I need peer-to-peer Apple device networking with identity & trust management
tags: [swift, apple, networking, p2p, bonjour, multipeer, device-discovery]
description: Swift package for building Apple-native device-to-device features - discovery, direct connections, identity, trust, and remote reachability.
source_url: https://github.com/EthanLipnik/Loom
---

## Summary

Loom is a Swift package for apps that need to find other devices, connect directly, verify identity, make trust decisions, and keep working when the local network is not the whole story. Designed for Apple platforms (macOS 14+, iOS 17.4+, visionOS 26+).

## Why It's Nice

- **Nearby peer discovery** over Bonjour, including peer-to-peer support
- **Direct sessions** built on Network.framework
- **Stable device identity** and key management
- **Pluggable trust policy** and local trust storage
- **Remote reachability** support with relay presence and network probing
- **Diagnostics and instrumentation** hooks

## Use Cases

- Mac and iPhone companion apps
- Local-first collaboration tools
- Device control surfaces
- Host and client apps on the same network
- Pro apps that need to discover and connect to nearby machines
- Products that start local but eventually need remote coordination

## Compared to MultipeerConnectivity

Loom is better when you need:
- Identity, trust, diagnostics, and a path beyond the local network
- A durable multi-device architecture (not just nearby messaging)

MultipeerConnectivity is fine for:
- Quick local-first prototypes
- Simple nearby collaboration

## Installation

```swift
dependencies: [
 .package(url: "https://github.com/EthanLipnik/Loom.git", branch: "main")
]
```

## Basic Usage

```swift
import Loom

let node = LoomNode(
 configuration: LoomNetworkConfiguration(
   serviceType: "_myapp._tcp",
   enablePeerToPeer: true
 ),
 identityManager: LoomIdentityManager.shared
)
```

Then advertise your device, browse for peers, and open sessions.

## Requirements

- Swift 6.2+
- macOS 14+
- iOS 17.4+
- visionOS 26+

## Links

- [Loom Documentation](https://ethanlipnik.github.io/Loom/documentation/loom/)
- [LoomShell Documentation](https://ethanlipnik.github.io/Loom/documentation/loomshell/)
