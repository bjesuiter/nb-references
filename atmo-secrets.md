---
title: Atmo - Time-locked Secrets on AT Protocol
anchor: Quick access when needing time-capsule style encrypted secrets app on atproto
tags: [atproto, bluesky, encryption, time-capsule, drand, web-app]
description: Encrypt messages that can only be decrypted after a specific time - powered by drand timelock encryption, stored on atproto PDS
source_url: https://secrets.atmo.social/
---

## Reference

### Summary
A decentralized time-capsule app for secrets. Users can encrypt messages that can only be decrypted after a specific time has passed. Powered by drand timelock encryption and stored on the user's AT Protocol PDS.

### How It Works
- Create a secret with a time lock (anywhere from 1 minute to years)
- The encrypted message is stored on your atproto PDS
- Until the timelock expires, the message cannot be decrypted (even by the server)
- Uses drand's timelock encryption - relies on VRF/vDF for cryptographic time locks

### Use Cases
- Future-dated predictions (e.g., "World Cup 2026 Winner")
- Time capsule messages
- Secrets to be revealed later
- Confessions that unlock after a period

### Tech Stack
- **Encryption**: drand timelock encryption
- **Storage**: AT Protocol (PDS)
- **Protocol**: Bluesky/ATproto

### Example Recent Secrets
- "Questions for AGI" - 10h lock
- "World Cup 2026 Winner" - 12h lock
- "10 year secret" - 1 year lock
- "my bank details and all my passwords" - 13h lock (ironic example)

### Source
- Website: https://secrets.atmo.social/
- Related: [drand timelock encryption](https://docs.drand.love/docs/timelock-encryption/)
- Related: [AT Protocol](https://atproto.com)
