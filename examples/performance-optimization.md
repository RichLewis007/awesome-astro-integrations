# Performance Optimization Examples

## Compression and Minification

### astro-compress

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import compress from "astro-compress";

export default defineConfig({
  integrations: [
    compress(), // Put this last in your integrations array
  ],
});
```

**Installation:**
```bash
npm i -D astro-compress
```

## Critical CSS

### astro-critters

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import critters from "astro-critters";

export default defineConfig({
  integrations: [
    critters({
      // Options: external, inline, preload, noscriptFallback
    }),
  ],
});
```

**Installation:**
```bash
npm i -D astro-critters
```

### astro-critical-css

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import criticalCSS from "astro-critical-css";

export default defineConfig({
  integrations: [
    criticalCSS(),
  ],
});
```

**Installation:**
```bash
npm i -D astro-critical-css
```

## Partytown

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import partytown from "@astrojs/partytown";

export default defineConfig({
  integrations: [
    partytown({
      config: {
        forward: ["dataLayer.push"],
      },
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/partytown
```

**Usage in component:**
```astro
---
// src/components/Analytics.astro
---
<script type="text/partytown">
  // Third-party scripts run in web worker
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

## UnoCSS

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import UnoCSS from "unocss/astro";

export default defineConfig({
  integrations: [
    UnoCSS({
      // UnoCSS options
    }),
  ],
});
```

**Installation:**
```bash
npm i -D unocss @unocss/reset
```

**UnoCSS config:**
```ts
// uno.config.ts
import { defineConfig } from "unocss";

export default defineConfig({
  // Your UnoCSS configuration
});
```
