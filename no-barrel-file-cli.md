---
title: no-barrel-file CLI
anchor: CLI tool to remove barrel file imports from TypeScript/JavaScript projects
tags: [typescript, javascript, refactoring, barrel, exports, cli, tool]
description: CLI tool for removing barrel file imports by replacing them with full paths
source_url: https://github.com/Nergie/no-barrel-file
---

## Overview

**no-barrel-file** is a CLI tool for removing barrel file imports in JavaScript/TypeScript projects. It efficiently replaces barrel imports with full paths and helps improve runtime, build-time, and test-time performance.

## Features

- **Display Barrel Files**: List all barrel files in your project
- **Replace Barrel Imports**: Automatically replace barrel file imports with full paths
- **Count Barrel Files**: Get the total number of barrel files
- **Customizable**: Supports root path, alias configurations, gitignore rules, file extensions
- **Scalable**: Handles large projects with complex barrel structures (nested, circular)

## Installation

### Go (Recommended)

```bash
go install github.com/nergie/no-barrel-file@latest
```

### Docker

```bash
docker pull nergie42/no-barrel-file:latest
```

## Usage

### Commands

| Command | Description |
|---------|-------------|
| `no-barrel-file count` | Count barrel files in project |
| `no-barrel-file display` | List all barrel files |
| `no-barrel-file replace` | Replace barrel imports with full paths |

### Flags

| Flag | Description | Default |
|------|-------------|---------|
| `--root-path, -r` | Root path of project | Required |
| `--extensions, -e` | File extensions to process | .ts,.js,.tsx,.jsx |
| `--gitignore-path, -g` | .gitignore file path | .gitignore |
| `--ignore-paths, -i` | Directories/files to ignore | None |
| `--alias-config-path, -a` | Path to tsconfig.json for alias resolution | None |
| `--barrel-path, -b` | Specific barrel file to replace | All |
| `--target-path, -t` | Target path for replacements | Current dir |

### Example

```bash
# Count barrel files
no-barrel-file count --root-path ./src

# Replace all barrel imports
no-barrel-file replace --root-path ./src

# Replace specific barrel file
no-barrel-file replace --root-path ./src --barrel-path ./src/components/index.ts
```

## Why Remove Barrel Files?

- **Faster builds**: Atlassian achieved 75% build time reduction by removing barrel files
- **Better tree-shaking**: Explicit imports allow bundlers to eliminate unused code
- **Improved IDE performance**: Less indirection means faster navigation
- **Clearer dependency graphs**: Direct imports show actual dependencies

## Related

- [Barrel files and why you should STOP using them now](https://dev.to/tassiofront/barrel-files-and-why-you-should-stop-using-them-now-bc4)
- [Speeding up the JavaScript ecosystem - The barrel file debacle](https://marvinh.dev/blog/speeding-up-javascript-ecosystem-part-7/)
