---
title: Chartli - ASCII Charts in Terminal
anchor: Quick access when needing to render charts in terminal from numeric data
tags: [cli, terminal, charts, ascii, visualization, nodejs]
description: CLI tool that turns plain numbers into terminal charts - ascii, spark, bars, columns, heatmap, unicode, braille, svg
source_url: https://github.com/ahmadawais/chartli
---

## Reference

### Summary
CLI tool that turns plain numbers into terminal charts. Supports multiple chart types: ascii, spark, bars, columns, heatmap, unicode, braille, and SVG.

### Installation
```bash
# Run instantly
npx chartli --help

# Or install globally
pnpm add -g chartli
```

### Usage
```bash
chartli [file] [options]

# Chart types: svg, ascii, unicode, braille, spark, bars, columns, heatmap
chartli data.txt -t ascii -w 24 -h 8
```

### Chart Types
- **ascii** - ASCII line charts
- **spark** - Sparklines
- **bars** - Horizontal bars
- **columns** - Vertical columns
- **heatmap** - Heatmap visualization
- **unicode** - Unicode block charts
- **braille** - Braille dot charts
- **svg** - SVG output

### Example Output
```
# Sparklines
S1 ▁▂▃▄▅▆
S2 ▁▄▂▇▅█

# Columns
 ▓
 ▓ ░
█ ▓ ░
```

### Source
- GitHub: https://github.com/ahmadawais/chartli
- npm: `pnpm add -g chartli`
