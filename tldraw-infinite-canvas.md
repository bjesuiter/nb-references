---
title: tldraw SDK - Infinite Canvas for React (v4.x)
anchor: TypeScript library for building infinite canvas experiences on the web - v4.3
tags: [tldraw, infinite-canvas, react, whiteboard, typescript, ui, sdk]
description: tldraw is a TypeScript library for creating infinite canvas experiences in React. v4.0+ requires license for production use.
source_url: https://tldraw.dev/
source_url_alt: https://github.com/tldraw/tldraw
---

## Summary

**tldraw** is a TypeScript library for building infinite canvas applications in React. Powers the popular tldraw.com whiteboard and used by 70,000+ weekly installs.

## Quick Start

```bash
# Create new tldraw project
npm create tldraw@latest

# Install manually
npm install tldraw
```

```tsx
import { Tldraw } from 'tldraw'
import 'tldraw/tldraw.css'

export default function App() {
  return <Tldraw />
}
```

## Key Features

- **Infinite canvas** — Pan, zoom, create unlimited workspace
- **Drawing tools** — Shapes, arrows, lines, freehand
- **Text & sticky notes** — Quick annotations
- **Images & links** — Embed external content
- **Multiplayer ready** — Built-in sync with tldraw sync
- **Export options** — PNG, SVG, JSON

## v4.0+ New Features

### Starter Kits

| Kit | Purpose |
|-----|---------|
| **agent** | Cursor-style AI chatbot on canvas |
| **workflow** | React-flow style node-and-wire apps |
| **branching chat** | Branching AI conversations |
| **chat** | Image annotation + chat |
| **multiplayer** | Real-time collaboration starter |

### npm create tldraw

```bash
npm create tldraw@latest my-canvas-app
```

### Accessibility

v4.0+ is WCAG 2.2 AA compliant (via Sarah Fossheim's contributions)

## Licensing (Important!)

**v4.0+ changed license:**

- **Development:** Free, no license needed
- **Production:** Requires license (free 100-day trial available)
- **Hobby/Commercial:** Paid licenses available

```bash
# Get free trial license
# https://tldraw.dev/get-a-license/trial
```

## Use Cases

- **Whiteboard apps** — Collaborative thinking tools
- **AI interfaces** — Agent-style chatbots on canvas (agent starter kit)
- **Workflow tools** — Node-based programming, pipelines
- **Design tools** — Canvas-based UIs
- **Games** — Canvas-based multiplayer games

## Example: Custom Tool

```tsx
import { Tldraw, createShapeId } from 'tldraw'
import 'tldraw/tldraw.css'

function CustomShapeExample() {
  return (
    <Tldraw>
      <MyCustomTool />
    </Tldraw>
  )
}

// Custom tool implementation
const MyCustomTool = () => {
  // Implements custom shape creation
}
```

## Related

- **Docs:** https://tldraw.dev/docs
- **GitHub:** https://github.com/tldraw/tldraw
- **Starter kits:** https://tldraw.dev/starter-kits/overview
- **tldraw sync:** Multiplayer backend: https://tldraw.dev/docs/sync
- **Pricing:** https://tldraw.dev/pricing

## For Skills Integration

Perfect for creating **visual workflow skills** or **AI agent canvas interfaces**:

- `tldraw-agent-chat` — Agent chatbot on infinite canvas
- `tldraw-workflow-builder` — Node-based workflow skills
- `tldraw-whiteboard` — Collaborative whiteboard skill

## Stats (as of v4.0)

- **40,000+ GitHub stars**
- **70,000+ weekly npm installs**
- **8,000+ Discord members**
