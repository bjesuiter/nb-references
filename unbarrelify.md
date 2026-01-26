---
title: unbarrelify - Barrel File Removal Tool
anchor: Barrel file removal tool for JavaScript & TypeScript projects by the author of knip
tags: [typescript, javascript, refactoring, barrel, exports, cli, tool, esm]
description: Barrel file removal tool for JavaScript & TypeScript projects (ESM-only) by webpro, author of knip
source_url: https://github.com/webpro/unbarrelify
---

## Overview

**unbarrelify** is a barrel file removal tool for JavaScript & TypeScript projects (ESM-only). Created by **webpro**, the author of [knip](https://github.com/webpro-nl/knip).

## What are Barrel Files?

Barrel files are index files that only contain re-exports from other modules:

```typescript
export { formatDate } from "./date.ts";
export { formatCurrency } from "./currency.ts";
export { capitalize } from "./string.ts";
```

## Why Avoid Barrel Files?

- **Performance and memory**: They artificially inflate the module graph and slow down startup times, HMR, and CI pipelines
- **Tree-shaking failures**: They often confuse tree-shakers, risk entire libraries to be bundled when only a single function is needed
- **Circular dependencies**: They frequently create "import cycles", crashing bundlers or causing confusing errors

## Features

- Automated rewiring of consumers to import directly from source
- Preserves path aliases
- Skips barrel files that are entry points (package.json#exports etc.)
- Auto-detects or enforces file extensions to match project style
- Optional `--organize-imports` to dedupe and clean up after rewrites
- Granular control with `--skip`, `--only` or add `--barrel-like` files
- Use `--check` for CI to fail if barrel files are detected
- Go all out with `--unsafe-namespace` to namespace imports

## Installation

### npx (no install)

```bash
npx unbarrelify
npx unbarrelify --help
```

### npm

```bash
npm install -D unbarrelify
```

## CLI Usage

```
Options:
 -c, --cwd <dir>        Working directory (default: ".")
 -o, --only <file>      Process only selected barrel file (can be repeated)
 -s, --skip <pattern>   Barrel files to skip (glob, can be repeated)
 -b, --barrel <pattern> Extra files to treat as barrels (glob, can be repeated)
 -f, --files <pattern>  Set file coverage (glob, can be repeated, default: use tsconfig.json)
 -e, --ext <ext>        Extension for rewritten imports (default: auto-detect)
 -w, --write            Write changes to disk (default: false/dry-run)
 --organize-imports     Run TypeScript's "Organize Imports" after rewrites
 --check, --ci          Check mode for CI; non-zero exit if there are changes
 --unsafe-namespace     Rewrite namespace imports (may include types - use with caution)
 -h, --help             Show help
```

### Examples

```bash
# Dry-run (default)
unbarrelify

# Write changes to disk
unbarrelify --write

# Process only specific barrel file
unbarrelify --only ./src/utils/index.ts

# Skip certain barrel files
unbarrelify --skip ./public-api.ts

# CI check mode
unbarrelify --check

# Organize imports after rewrites
unbarrelify --write --organize-imports
```

## Programmatic API

```typescript
import { unbarrelify } from "unbarrelify";

const result = await unbarrelify({
  cwd: "./src",
  files: ["**/*.ts"],
  skip: [],
  ext: ".ts",
  write: false,
});

console.log(`Modified ${result.modified.length} files`);
console.log(`Deleted ${result.deleted.length} barrel files`);
```

## Resources

- [Speeding up the JavaScript ecosystem - The barrel file debacle](https://marvinh.dev/blog/speeding-up-javascript-ecosystem-part-7/)
- [How we optimized package imports in Next.js](https://vercel.com/blog/how-we-optimized-package-imports-in-next-js)
- [A practical guide against barrel files for library authors](https://dev.to/thepassle/a-practical-guide-against-barrel-files-for-library-authors-118c)
- [Please Stop Using Barrel Files](https://tkdodo.eu/blog/please-stop-using-barrel-files)
