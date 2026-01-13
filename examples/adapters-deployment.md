# Adapters and Deployment Examples

## Cloudflare Adapter

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import cloudflare from "@astrojs/cloudflare";

export default defineConfig({
  output: "server",
  adapter: cloudflare({
    // Cloudflare-specific options
    platformProxy: {
      enabled: true,
    },
  }),
});
```

**Installation:**
```bash
npm i -D @astrojs/cloudflare
```

**Cloudflare Workers Usage:**
```ts
// src/pages/api/hello.ts
export async function GET() {
  return new Response(JSON.stringify({ message: "Hello from Cloudflare!" }), {
    headers: { "Content-Type": "application/json" },
  });
}
```

## Vercel Adapter

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import vercel from "@astrojs/vercel/serverless";

export default defineConfig({
  output: "server",
  adapter: vercel({
    // Vercel-specific options
    webAnalytics: {
      enabled: true,
    },
  }),
});
```

**Installation:**
```bash
npm i -D @astrojs/vercel
```

**Vercel Edge Functions:**
```ts
// astro.config.mjs
import vercel from "@astrojs/vercel/edge";

export default defineConfig({
  output: "server",
  adapter: vercel(),
});
```

## Netlify Adapter

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import netlify from "@astrojs/netlify/functions";

export default defineConfig({
  output: "server",
  adapter: netlify({
    // Netlify-specific options
    binaryMediaTypes: ["image/*"],
  }),
});
```

**Installation:**
```bash
npm i -D @astrojs/netlify
```

**Netlify Edge Functions:**
```ts
// astro.config.mjs
import netlify from "@astrojs/netlify/edge-functions";

export default defineConfig({
  output: "server",
  adapter: netlify(),
});
```

## Node.js Adapter

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import node from "@astrojs/node";

export default defineConfig({
  output: "server",
  adapter: node({
    mode: "standalone", // or "middleware"
  }),
});
```

**Installation:**
```bash
npm i -D @astrojs/node
```

**Standalone Server:**
```ts
// server.js
import { handler as ssrHandler } from "./dist/server/entry.mjs";
import express from "express";

const app = express();
app.use(express.static("dist/client"));
app.use(ssrHandler);

app.listen(3000, () => {
  console.log("Server running on http://localhost:3000");
});
```

## Static Site Generation (SSG)

For static sites, no adapter is needed:

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";

export default defineConfig({
  output: "static", // Default
  // No adapter needed for static sites
});
```

## Hybrid Rendering

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import vercel from "@astrojs/vercel/serverless";

export default defineConfig({
  output: "hybrid",
  adapter: vercel(),
});
```

**Page-level configuration:**
```astro
---
// src/pages/static-page.astro
// This page will be statically generated
---

<h1>Static Page</h1>
```

```astro
---
// src/pages/dynamic-page.astro
export const prerender = false; // This page will be server-rendered
---

<h1>Dynamic Page</h1>
```
