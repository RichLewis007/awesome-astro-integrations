# Images, Icons, and Fonts Examples

## Astro Icon

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import icon from "astro-icon";

export default defineConfig({
  integrations: [
    icon({
      // Options
      iconDir: "src/icons",
      include: {
        // Icon sets to include
        "heroicons": ["solid/*", "outline/*"],
        "lucide": ["*"],
      },
    }),
  ],
});
```

**Installation:**
```bash
npm i -D astro-icon
```

**Usage:**
```astro
---
import { Icon } from "astro-icon/components";
---

<Icon name="heroicons:heart" />
<Icon name="lucide:github" size={24} />
<Icon name="custom:my-icon" class="text-blue-500" />
```

## Astro Image Optimization

Astro has built-in image optimization. No integration needed!

```astro
---
import { Image } from "astro:assets";
import myImage from "../assets/image.jpg";
---

<Image
  src={myImage}
  alt="Description"
  width={800}
  height={600}
  format="webp"
  quality={80}
/>
```

**Responsive Images:**
```astro
---
import { Image, Picture } from "astro:assets";
import myImage from "../assets/image.jpg";
---

<Picture
  src={myImage}
  alt="Description"
  widths={[400, 800, 1200]}
  sizes="(max-width: 800px) 100vw, 800px"
  formats={["webp", "jpg"]}
/>
```

## Font Optimization

### Using astro-font

```bash
npm i -D astro-font
```

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import font from "astro-font";

export default defineConfig({
  integrations: [
    font({
      // Google Fonts
      google: {
        families: ["Inter", "Roboto"],
        display: "swap",
        preconnect: true,
      },
      // Local fonts
      local: {
        families: [
          {
            name: "Custom Font",
            src: "./src/fonts/custom.woff2",
          },
        ],
      },
    }),
  ],
});
```

### Manual Font Loading

```astro
---
// src/components/Fonts.astro
---

<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap"
  rel="stylesheet"
/>
```

**CSS:**
```css
/* src/styles/global.css */
@font-face {
  font-family: "Custom Font";
  src: url("/fonts/custom.woff2") format("woff2");
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}
```

## Iconify Integration

```bash
npm i -D @iconify-json/[collection-name]
```

```astro
---
import { Icon } from "@iconify-astro/icon";
---

<Icon icon="mdi:github" />
<Icon icon="carbon:email" width="24" height="24" />
```

## SVG Sprite Generation

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import svg from "astro-svg";

export default defineConfig({
  integrations: [
    svg({
      // Options
    }),
  ],
});
```
