# UI Framework Integration Examples

## React Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import react from "@astrojs/react";

export default defineConfig({
  integrations: [
    react({
      // React options
      include: ["**/react/**"],
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/react react react-dom
```

**Usage:**
```astro
---
// src/pages/index.astro
import { Counter } from "../components/react/Counter.tsx";
---

<Counter client:load />
```

**React Component:**
```tsx
// src/components/react/Counter.tsx
import { useState } from "react";

export function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

## Vue Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import vue from "@astrojs/vue";

export default defineConfig({
  integrations: [
    vue({
      // Vue options
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/vue vue
```

**Usage:**
```astro
---
// src/pages/index.astro
import { Counter } from "../components/vue/Counter.vue";
---

<Counter client:visible />
```

**Vue Component:**
```vue
<!-- src/components/vue/Counter.vue -->
<script setup>
import { ref } from "vue";

const count = ref(0);
</script>

<template>
  <button @click="count++">Count: {{ count }}</button>
</template>
```

## Svelte Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import svelte from "@astrojs/svelte";

export default defineConfig({
  integrations: [
    svelte({
      // Svelte options
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/svelte svelte
```

**Usage:**
```astro
---
// src/pages/index.astro
import { Counter } from "../components/svelte/Counter.svelte";
---

<Counter client:idle />
```

**Svelte Component:**
```svelte
<!-- src/components/svelte/Counter.svelte -->
<script>
  let count = 0;
</script>

<button on:click={() => count++}>Count: {count}</button>
```

## Preact Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import preact from "@astrojs/preact";

export default defineConfig({
  integrations: [
    preact({
      // Preact options
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/preact preact
```

## SolidJS Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import solid from "@astrojs/solid-js";

export default defineConfig({
  integrations: [
    solid({
      // SolidJS options
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/solid-js solid-js
```

## Alpine.js Integration

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import alpinejs from "@astrojs/alpinejs";

export default defineConfig({
  integrations: [
    alpinejs(),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/alpinejs alpinejs
```

**Usage:**
```astro
---
// src/pages/index.astro
---

<div x-data="{ count: 0 }">
  <button @click="count++" x-text="`Count: ${count}`"></button>
</div>
```

## Client Directives

All framework components support these client directives:

- `client:load` - Load immediately
- `client:idle` - Load when browser is idle
- `client:visible` - Load when element is visible
- `client:media` - Load based on media query
- `client:only` - Only load on client (skip SSR)

```astro
---
import { Counter } from "../components/react/Counter.tsx";
---

<!-- Load immediately -->
<Counter client:load />

<!-- Load when browser is idle -->
<Counter client:idle />

<!-- Load when visible in viewport -->
<Counter client:visible />

<!-- Load only on client (no SSR) -->
<Counter client:only="react" />
```
