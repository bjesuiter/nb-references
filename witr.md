---
title: witr - Why Is This Running?
anchor: Debug process causality chains and find why something is running
tags: [debugging, processes, system-tools, diagnostics, tracing]
description: Tool to explain why a process is running and trace its startup chain
source_url: https://github.com/pranshuparmar/witr
---

## Summary

witr answers: **"Why is this running?"**

It traces the causality chain of running processes—explaining where something came from, how it was started, and what chain of systems is responsible. Unlike `ps`, `top`, `lsof`, `ss`, `systemctl`, or `docker ps` which only show state/metadata, witr makes causality explicit.

## Core Concept

Existing tools expose *what* is running but leave you to infer *why*. witr connects the dots across layers:
- Supervisors
- Containers
- Services
- Shells

## Installation

### Script (Linux, macOS, FreeBSD)

```bash
curl -fsSL https://raw.githubusercontent.com/pranshuparmar/witr/main/install.sh | bash
```

### Windows (PowerShell)

```powershell
irm https://raw.githubusercontent.com/pranshuparmar/witr/main/install.ps1 | iex
```

### Package Managers

```bash
# Homebrew (macOS/Linux)
brew install witr

# Conda/mamba/pixi
conda install -c conda-forge witr
mamba install -c conda-forge witr
pixi global install witr

# Arch Linux (AUR)
yay -S witr-bin

# Windows winget
winget install -e --id PranshuParmar.witr

# FreeBSD
pkg install witr
```

## Supported Targets

- Processes
- Services
- Ports
- Containers

## Output

Single, human-readable output explaining:
- Where the running thing came from
- How it was started
- What chain of systems is responsible

## Platforms

- Linux
- macOS
- FreeBSD
- Windows

## Use Cases

- Debug mystery processes
- Trace service dependencies
- Find root cause of port conflicts
- Understand systemd/supervisor chains
