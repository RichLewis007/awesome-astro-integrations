# SEO and Analytics Examples

## Sitemap Generation

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import sitemap from "@astrojs/sitemap";

export default defineConfig({
  site: "https://example.com",
  integrations: [
    sitemap({
      // Options
      changefreq: "weekly",
      priority: 0.7,
      lastmod: new Date(),
      i18n: {
        defaultLocale: "en",
        locales: {
          en: "en-US",
          es: "es-ES",
        },
      },
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/sitemap
```

## SEO Component

### Using astro-seo

```bash
npm i -D astro-seo
```

```astro
---
// src/components/SEO.astro
import { SEO } from "astro-seo";

const { title, description, image } = Astro.props;
---

<SEO
  title={title}
  description={description}
  canonical={Astro.url.href}
  openGraph={{
    basic: {
      title: title,
      type: "website",
      image: image,
      url: Astro.url.href,
    },
    optional: {
      description: description,
    },
  }}
  twitter={{
    card: "summary_large_image",
    site: "@yourhandle",
  }}
/>
```

## Google Analytics

### Using @astrojs/google-analytics

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import googleAnalytics from "@astrojs/google-analytics";

export default defineConfig({
  integrations: [
    googleAnalytics({
      apiSecret: import.meta.env.GOOGLE_ANALYTICS_API_SECRET,
      measurementId: import.meta.env.GOOGLE_ANALYTICS_MEASUREMENT_ID,
    }),
  ],
});
```

**Installation:**
```bash
npm i -D @astrojs/google-analytics
```

### Manual Google Analytics Setup

```astro
---
// src/components/GoogleAnalytics.astro
const GA_MEASUREMENT_ID = import.meta.env.PUBLIC_GA_ID;
---

{GA_MEASUREMENT_ID && (
  <>
    <script
      async
      src={`https://www.googletagmanager.com/gtag/js?id=${GA_MEASUREMENT_ID}`}
    ></script>
    <script
      is:inline
      define:vars={{ GA_MEASUREMENT_ID }}
    >
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', GA_MEASUREMENT_ID);
    </script>
  </>
)}
```

## Plausible Analytics

```astro
---
// src/components/Plausible.astro
const PLAUSIBLE_DOMAIN = import.meta.env.PUBLIC_PLAUSIBLE_DOMAIN;
---

{PLAUSIBLE_DOMAIN && (
  <script
    defer
    data-domain={PLAUSIBLE_DOMAIN}
    src="https://plausible.io/js/script.js"
  ></script>
)}
```

## Umami Analytics

```bash
npm i -D astro-umami
```

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import umami from "astro-umami";

export default defineConfig({
  integrations: [
    umami({
      websiteId: import.meta.env.PUBLIC_UMAMI_WEBSITE_ID,
      src: "https://analytics.example.com/script.js",
    }),
  ],
});
```

## Robots.txt

```ts
// src/pages/robots.txt.ts
import type { APIRoute } from "astro";

const robotsTxt = `
User-agent: *
Allow: /

Sitemap: ${new URL("sitemap-index.xml", import.meta.env.SITE).href}
`.trim();

export const GET: APIRoute = () => {
  return new Response(robotsTxt, {
    headers: {
      "Content-Type": "text/plain; charset=utf-8",
    },
  });
};
```

## Structured Data (JSON-LD)

```astro
---
// src/components/StructuredData.astro
const { type, data } = Astro.props;

const schema = {
  "@context": "https://schema.org",
  "@type": type,
  ...data,
};
---

<script type="application/ld+json" set:html={JSON.stringify(schema)} />
```

**Usage:**
```astro
---
import { StructuredData } from "../components/StructuredData.astro";
---

<StructuredData
  type="Article"
  data={{
    headline: "My Article",
    author: {
      "@type": "Person",
      name: "John Doe",
    },
    datePublished: "2025-01-01",
  }}
/>
```

## RSS Feed

```ts
// src/pages/rss.xml.ts
import rss from "@astrojs/rss";
import type { APIRoute } from "astro";
import { getCollection } from "astro:content";

export const GET: APIRoute = async (context) => {
  const posts = await getCollection("blog");
  
  return rss({
    title: "My Blog",
    description: "A blog about web development",
    site: context.site!,
    items: posts.map((post) => ({
      title: post.data.title,
      description: post.data.description,
      pubDate: post.data.pubDate,
      link: `/blog/${post.slug}/`,
    })),
    customData: `<language>en-us</language>`,
  });
};
```

**Installation:**
```bash
npm i -D @astrojs/rss
```
