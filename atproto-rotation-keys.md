---
title: ATProto Rotation Keys Guide
anchor: When I need to understand atproto rotation keys for Bluesky account migration/recovery
tags: [atproto, bluesky, rotation-key, decentralized, pds, migration]
description: Guide explaining what rotation keys are, how they work, and how to use them for adversarial PDS migrations.
source_url: https://marvins-guide.leaflet.pub/3m4qzoj6ubc2h
---

## Summary

Explains what rotation keys are in the ATProto/Bluesky decentralized identity system and how they enable account migration even when your PDS is down.

## Key Concepts

### What is a Rotation Key?

A rotation key is like a password that allows the PLC (Public Ledger of Credential) to update your PDS address. It's needed when:
- Moving to a new PDS (account migration)
- Performing an "adversarial migration" when your current PDS is unresponsive

### Why It Matters

If your PDS goes down or the admin is unresponsive:
- Normal migration via email code won't work
- But with your own rotation key, you can submit PLC changes without the PDS
- This lets you recover your account in typically less than an hour

### PLC (Public Ledger of Credential)

- Global address book for Bluesky/ATProto accounts
- Applications use it to find where your data is hosted
- When you migrate, you're submitting a change to the PLC to update your PDS location

## Use Cases

- PDS server goes down / admin unresponsive
- Want full control over your identity independent of PDS
- Account recovery when normal migration isn't possible
