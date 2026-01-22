---
title: Satori - Dynamic OG Images with Static Site Generators
anchor: Generate dynamic open graph images with Satori for any static site generator (Astro, Nuxt, Next)
tags: [satori, og-image, opengraph, social-media, static-site-generator, astra, vercel]
description: Tutorial on using Satori to generate dynamic open graph images for static websites
source_url: https://knaap.dev/posts/dynamic-og-images-with-any-static-site-generator/
---

## Summary

**Satori** (by Vercel) generates Open Graph images from JSX templates. Works with any static site generator (Astro, Nuxt, Next.js).

## What are OG Images?

Open Graph images appear when links are shared on social media (Facebook, Twitter/X). They show a preview image alongside the title and description.

## Why Dynamic OG Images?

- Representative of each page's content
- Easy to update when design changes
- No manual maintenance per page

## Quick Start

```bash
npm install satori
# For PNG conversion
npm install @resvg/resvg-js
```

### Basic Example

```javascript
import satori from "satori";

const svg = await satori(
  <div style={{
    background: "rgb(24, 32, 47)",
    width: "100%",
    height: "100%",
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
    color: "white",
  }}>
    <h1 style={{ fontSize: "64px", fontWeight: "bold" }}>Hello World!</h1>
  </div>,
  {
    width: 1200,
    height: 630,
  }
);
```

## Convert to PNG

```javascript
import { Resvg } from "@resvg/resvg-js";

const resvg = new Resvg(svg);
const pngData = resvg.render();
const pngBuffer = pngData.asPng();
```

## Astro Implementation

Create `src/pages/[og].svg.ts`:

```typescript
import type { APIRoute } from "astro";
import { getCollection } from "astro:content";
import generateArticleOG from "@utils/generateArticleOG";

export const get: APIRoute = async ({ params }) => {
  const svg = await generateArticleOG(params.ogTitle);
  
  const resvg = new Resvg(svg);
  const pngData = resvg.render();
  const pngBuffer = pngData.asPng();

  return new Response(pngBuffer, {
    status: 200,
    headers: { "Content-Type": "image/png" },
  });
};

export function getStaticPaths() {
  const posts = await getCollection("blog");
  return posts
    .filter(({ data }) => !data.ogImage)
    .map(({ data }) => ({
      params: { ogTitle: data.title },
    }));
}
```

Then use in your page:
```html
<meta property="og:image" content={`/${postTitle}.png`} />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
```

## Resources

- [Satori GitHub](https://github.com/vercel/satori)
- [Satori Playground](https://og-playground.vercel.app/)
- [Vercel Edge OG](https://vercel.com/docs/concepts/functions/edge-functions/og-image-generation)
- [SvelteKit + ResVG implementation](https://www.leereamsnyder.com/blog/dynamic-social-media-images-with-sveltekit-and-resvg-js)
