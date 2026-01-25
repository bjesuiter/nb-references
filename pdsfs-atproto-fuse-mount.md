---
title: pdsfs - Mount ATProto PDS as FUSE Filesystem
anchor: Mount atproto PDS repository as a FUSE filesystem
tags: [atproto, bluesky, pds, fuse, filesystem, rust]
description: Tool to mount ATProto PDS repository as a read-only FUSE filesystem
source_url: https://tangled.org/did:plc:qfpnj4og54vl56wngdriaxug/pdsfs
---

## My Reference

### Summary
`pdsfs` is a Rust tool that mounts an ATProto PDS repository as a read-only FUSE filesystem, allowing exploration of Bluesky/atproto data as files.

### Installation
```bash
cargo install --git https://tangled.org/oppi.li/pdsfs
```

### Usage
```bash
# Foreground (ctrl-c to unmount)
pdsfs oppi.li

# Daemon mode (parent exits when mount is ready)
pdsfs -d oppi.li && ls mnt/
```

### Features
- Mount multiple repositories simultaneously
- Deserializes CBOR data to JSON automatically
- Explore collections like `app.bsky.feed.post`, `app.bsky.graph.follow`, etc.
- Access profile data, posts, likes, reposts, and custom collections

### Example Output
```
mnt/
  did:plc:qfpnj4og54vl56wngdriaxug/
    app.bsky.actor.profile/
    app.bsky.feed.post/
    app.bsky.graph.follow/
    sh.tangled.actor.profile/
    ...
```

### Use Cases
- Browse your Bluesky data locally
- Extract public keys from atproto repos for git signing
- Analyze listening habits (rocksky scrobbles)
- Backup/export PDS data via standard filesystem tools
