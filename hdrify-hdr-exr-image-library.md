---
title: HDRify - HDR/EXR/JPEG-R Image Library
anchor: Pure JavaScript HDR image parsing and writing (HDR, EXR, Ultra HDR)
tags: [hdr, exr, image-processing, javascript, typescript, jpeg-r, gain-map]
description: Pure JS library for reading/writing HDR, EXR and Ultra HDR (JPEG-R) images
source_url: https://github.com/bhouston/hdrify
---

## Summary

HDRify is a pure JavaScript library for high dynamic range imaging with support for:
- **HDR** (Radiance RGBE)
- **EXR** (OpenEXR with multiple compression formats)
- **JPEG-R** (JPEG with gain maps / Ultra HDR)

Zero dependencies, works in Node.js and browsers.

## Key Features

### Format Support
- **Read/Write HDR** (Radiance RGBE files)
- **Read/Write EXR** (PIZ, PXR24, ZIP, ZIPS, RLE compression)
- **Write JPEG-R** (JPEG with gain maps) - highly compressible HDR format

### Universal Intermediate Format
All read functions return `FloatImageData`:
```typescript
interface FloatImageData {
  width: number;
  height: number;
  data: Float32Array;  // RGBA: [R, G, B, A, R, G, B, A, ...]
  metadata?: Record<string, unknown>;
}
```

### Additional Features
- Tone mapping utilities (Reinhard, etc.)
- Full TypeScript support
- Functional style (tree-shakeable)
- No DOM/Node dependencies

## Installation

```bash
pnpm add hdrify
```

## Main API

| Function | Description |
|----------|-------------|
| `readHdr(buffer)` | Parse Radiance RGBE HDR → FloatImageData |
| `writeHdr(imageData)` | Encode FloatImageData → HDR bytes |
| `readExr(buffer)` | Parse OpenEXR → FloatImageData |
| `writeExr(imageData, options?)` | Encode FloatImageData → EXR bytes |
| `writeJpegGainMap(encoding, options?)` | Encode HDR as JPEG-R |

## CLI Tool

```bash
pnpm add -g hdrify-cli

hdrify convert <input> <output>    # Convert between formats
hdrify info <file>                  # Display metadata
hdrify reference <output>           # Create synthetic reference images

# Examples
hdrify convert input.exr output.hdr
hdrify convert input.exr output.jpg  # JPEG-R with gain map
hdrify info input.exr
```

## Usage Examples

### Reading EXR
```typescript
import { readExr } from 'hdrify';
import * as fs from 'node:fs';

const buffer = fs.readFileSync('image.exr');
const imageData = readExr(new Uint8Array(buffer));
```

### Converting HDR → EXR
```typescript
import { readHdr, writeExr } from 'hdrify';

const hdrBuffer = fs.readFileSync('input.hdr');
const imageData = readHdr(new Uint8Array(hdrBuffer));
fs.writeFileSync('output.exr', writeExr(imageData));
```

### Converting to JPEG-R (compressible HDR)
```typescript
import { readExr, encodeGainMap, writeJpegGainMap } from 'hdrify';

const exrBuffer = fs.readFileSync('input.exr');
const imageData = readExr(new Uint8Array(exrBuffer));
const encoding = encodeGainMap(imageData, { toneMapping: 'reinhard' });
fs.writeFileSync('output.jpg', writeJpegGainMap(encoding, { quality: 90 }));
```

## Browser Demo

```bash
cd demos/web-converter
pnpm install
pnpm dev
# Open http://localhost:3000 - drag-and-drop EXR/HDR with exposure slider
```

## Author

Ben Houston ([benhouston3d@gmail.com](mailto:benhouston3d@gmail.com)), sponsored by Land of Assets

## Related

- [DASL specification](/references/webtiles-atproto-modular-ui.md) - For content addressing
- Image processing workflows
