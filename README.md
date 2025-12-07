

# Awesome Astro Integrations
Personally maintained reviews and examples of the very best, most useful Astro Integrations. Constantly updated with reviews and recommendations for your kind of project.

A curated, opinionated list of Astro integrations that deliver real impact on your project.

## Performance and DX boosters

* **astro-compress**
  One switch to minify and compress HTML, CSS, JS, and images in your build. Put it last in your `integrations` array.

* **Critical CSS inliners**
  Pick one: **astro-critical-css**, **astro-critters**, or PlayForm's **Inline**. They inline above-the-fold CSS and lazy-load the rest for faster first paint.

* **UnoCSS**
  Utility-first CSS engine with on-demand generation and presets. Usually lighter than shipping a full framework.

* **Partytown**
  Offload third-party scripts (analytics, tag managers) to a web worker so they stop blocking the main thread.

## Content and docs power

* **@astrojs/mdx**
  Mix Markdown and components. Keep authoring flow simple and use shortcodes everywhere.

* **Starlight**
  Astro's official docs theme with search, i18n, strong a11y, and theming. Saves weeks for any docs site.

## Images, icons, and fonts

* **Astro Icon**
  Local or Iconify icons with smart SVG inlining and sprite dedupe for tiny payloads.

* **astro-font** (directory pick)
  Automates local and hosted font optimization with sensible defaults.

## Auth and app features

* **Clerk for Astro**
  Drop-in auth for accounts, sessions, and user management with SSR paths aligned for Astro.

## Analytics that play nice with performance

* **Umami for Astro**
  Privacy-friendly analytics with smooth integration. Works well with View Transitions and Partytown.

* **Plausible**
  Lightweight analytics with simple wiring. Community guides and components make it tidy to adopt.

## Official ecosystem and what's new

* **Integrations Directory**
  The live source of truth. Filter by category and recency when starting a new site.

* **Astro DB**
  Built-in, managed SQL store with Drizzle ORM for small dynamic features without a separate backend.

---

## Quick picks by goal

* **Make it feel instant**: astro-critical-css or Inline + astro-compress
* **Ship fewer bytes of CSS**: UnoCSS
* **Keep analytics but remove jank**: Partytown + Umami or Plausible
* **Docs that don't fight you**: Starlight + @astrojs/mdx
* **Icons without bloat**: Astro Icon

---

## Example `astro.config.mjs`

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import mdx from "@astrojs/mdx";
import vue from "@astrojs/vue"; // if you use Vue islands
import starlight from "@astrojs/starlight"; // if building docs
// import critters from "astro-critters"; // or astro-critical-css
// import compress from "astro-compress";
export default defineConfig({
  integrations: [
    mdx(),
    vue(),
    // starlight(), // enable if using the docs theme
    // critters(),
    // compress(),
  ],
});
```

---

## Notes and good practices

* Prefer fewer, larger islands over many small ones to reduce hydration overhead.
* Use `client:visible` or `client:idle` to delay hydration where possible.
* Lazy-import heavy subcomponents inside hydrated islands.
* Keep the rest of the site native so Astro can ship near-zero JS by default.

---

## Reference snippets

Install common picks:

```bash
# MDX
npm i -D @astrojs/mdx

# Vue islands (optional)
npm i -D @astrojs/vue vue

# Critical CSS (choose one)
npm i -D astro-critters
# or
npm i -D astro-critical-css

# Compression
npm i -D astro-compress

# Icons
npm i -D astro-icon

# UnoCSS
npm i -D unocss @unocss/reset

# Partytown
npm i -D @builder.io/partytown
```

---

## Sources and references

* [Astro Integrations Guide](https://docs.astro.build/en/guides/integrations-guide/)
* [Astro Integration API Reference](https://docs.astro.build/en/reference/integrations-reference/)
* [@astrojs/mdx docs](https://docs.astro.build/en/guides/integrations-guide/mdx/)
* [Starlight docs](https://starlight.astro.build/)
* [UnoCSS site](https://unocss.dev/)
* [Partytown docs](https://partytown.qwik.dev/)
* [Umami for Astro (integration example)](https://github.com/yeskunall/astro-umami)
* [Plausible + Astro guide](https://decaster.dev/using-plausible-analytics-in-gatsby-js-or-astro-js/)
* [Clerk Astro SDK](https://clerk.com/docs/reference/astro/overview)
* [Astro DB guide](https://docs.astro.build/en/guides/astro-db/)
* [Astro Icon docs](https://www.astroicon.dev/getting-started/)
* [astro-critical-css](https://github.com/rumaan/astro-critical-css)
* [astro-critters](https://github.com/fariasf/astro-critters)
* [PlayForm Inline](https://github.com/PlayForm/Inline)
* [astro-compress](https://github.com/kamranahmedse/astro-compress)

---

## Next picks backlog

* Data fetching best practices with islands (e.g., TanStack Query)
* Security headers and CSP patterns
* Accessibility linting and automated checks
* RSS feeds for blogs and changelogs
* Deploy-time image optimization and caching strategies

---

## Backlog details (starting)

### Table of contents

* [@astrojs/image and image pipelines](#astrojsimage-and-image-pipelines)
* [View Transitions API patterns for Astro](#view-transitions-api-patterns-for-astro)
* [i18n options for Astro sites](#i18n-options-for-astro-sites)
* [Adapters: Cloudflare, Vercel, Netlify](#adapters-cloudflare-vercel-netlify)
* [SEO helpers: sitemap, robots, structured data](#seo-helpers-sitemap-robots-structured-data)
* [Content Collections and CMS bridges](#content-collections-and-cms-bridges)
* [Rich code rendering: Shiki and Code Hike](#rich-code-rendering-shiki-and-code-hike)
* [Testing and QA: Vitest and Playwright](#testing-and-qa-vitest-and-playwright)
* [Performance and monitoring bundle](#performance-and-monitoring-bundle)
* [Security headers and CSP patterns](#security-headers-and-csp-patterns)
* [Accessibility linting and automated checks](#accessibility-linting-and-automated-checks)
* [Data fetching with TanStack Query](#data-fetching-with-tanstack-query)
* [RSS feeds and changelog wiring](#rss-feeds-and-changelog-wiring)
* [Deploy-time image optimization and caching](#deploy-time-image-optimization-and-caching)

### @astrojs/image and image pipelines

* **What it is:** Official image optimization and responsive pipelines for Astro.
* **Why it matters:** Automatic `srcset`, format conversion, and on-demand transforms keep pages sharp and fast.
* **Docs:** [https://docs.astro.build/en/guides/images/](https://docs.astro.build/en/guides/images/)
* **Quick start:**

  ```ts
  // astro.config.mjs
  import { defineConfig } from "astro/config";
  import image from "@astrojs/image";
  export default defineConfig({ integrations: [image()] });
  ```

  ```astro
  ---
  import { Image } from "@astrojs/image/components";
  ---
  <Image src="/hero.jpg" widths={[400, 800, 1200]} sizes="(max-width: 800px) 100vw, 800px" alt="Hero" />
  ```

### View Transitions API patterns for Astro

* **What it is:** Native browser API to animate page-to-page changes; Astro supports it via the built-in View Transitions feature.
* **Why it matters:** Adds polish with minimal JS and keeps the SSR/MPA model.
* **Docs:** [https://docs.astro.build/en/guides/view-transitions/](https://docs.astro.build/en/guides/view-transitions/)
* **Quick start:**

  ```ts
  // astro.config.mjs
  export default { experimental: { viewTransitions: true } };
  ```

  ```css
  /* global.css */
  ::view-transition-old(root), ::view-transition-new(root) { animation-duration: .25s; }
  ```

### i18n options for Astro sites

* **What it is:** Internationalization via Starlight i18n, route-based i18n, or community integrations.
* **Why it matters:** Localized content with clean URLs and minimal overhead.
* **Docs:**

  * Starlight i18n: [https://starlight.astro.build/guides/i18n/](https://starlight.astro.build/guides/i18n/)
  * Core routing patterns: [https://docs.astro.build/en/guides/internationalization/](https://docs.astro.build/en/guides/internationalization/)

### Adapters: Cloudflare, Vercel, Netlify

* **What it is:** Server adapters to run SSR or islands on your target platform.
* **Docs:**

  * Cloudflare: [https://docs.astro.build/en/guides/deploy/cloudflare/](https://docs.astro.build/en/guides/deploy/cloudflare/)
  * Vercel: [https://docs.astro.build/en/guides/deploy/vercel/](https://docs.astro.build/en/guides/deploy/vercel/)
  * Netlify: [https://docs.netlify.com/build/frameworks/framework-setup-guides/astro/](https://docs.netlify.com/build/frameworks/framework-setup-guides/astro/)
* **Tip:** Prefer SSG where possible; use SSR only where a dynamic route actually needs it.

### SEO helpers: sitemap, robots, structured data

* **What it is:** Official and community integrations for SEO basics.
* **Docs:**

  * Sitemap: [https://docs.astro.build/en/guides/integrations-guide/sitemap/](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
  * Robots: [https://docs.astro.build/en/guides/seo/#robots-txt](https://docs.astro.build/en/guides/seo/#robots-txt)
  * Structured data: [https://docs.astro.build/en/guides/seo/#structured-data](https://docs.astro.build/en/guides/seo/#structured-data)
* **Snippet:**

  ```ts
  import sitemap from "@astrojs/sitemap";
  export default { site: "https://example.com", integrations: [sitemap()] };
  ```

### Content Collections and CMS bridges

* **What it is:** Astro Content Collections provide typed frontmatter and fast lookups for Markdown/MDX, JSON, and YAML content. CMS bridges sync or fetch content from a headless CMS.
* **Why it matters:** Schemas catch content mistakes at build time; bridges let non-devs edit without touching the repo.
* **Docs:**

  * Content Collections: [https://docs.astro.build/en/guides/content-collections/](https://docs.astro.build/en/guides/content-collections/)
  * Sanity: [https://www.sanity.io/guides/astro](https://www.sanity.io/guides/astro)
  * Contentful: [https://www.contentful.com/developers/docs/javascript/tutorials/using-contentful-in-astro/](https://www.contentful.com/developers/docs/javascript/tutorials/using-contentful-in-astro/)
  * Storyblok: [https://www.storyblok.com/mp/astro-cms](https://www.storyblok.com/mp/astro-cms)
* **Quick start (collections):**

  ```ts
  // src/content/config.ts
  import { defineCollection, z } from "astro:content";
  const posts = defineCollection({
    type: "content",
    schema: z.object({
      title: z.string(),
      date: z.string().transform((s) => new Date(s)),
      tags: z.array(z.string()).default([]),
      draft: z.boolean().default(false),
    }),
  });
  export const collections = { posts };
  ```

  ```ts
  // astro.config.mjs
  export default { integrations: [], markdown: { shikiConfig: { theme: "github-light" } } };
  ```

  ```astro
  ---
  import { getCollection } from "astro:content";
  const posts = await getCollection("posts", ({ data }) => !data.draft);
  ---
  <ul>{posts.map(p => <li><a href={p.slug}>{p.data.title}</a></li>)}</ul>
  ```
* **CMS bridge pattern:** fetch at build time via an API client, write to `src/content/` JSON, or pull at request time on specific routes. Cache aggressively.

### Rich code rendering: Shiki and Code Hike

* **What it is:** Shiki is a fast, accurate syntax highlighter; Code Hike adds rich code UI (scrolly code, diff, focus lines).
* **Why it matters:** Developer blogs and docs look pro, with accessible color contrast and copyable blocks.
* **Shiki quick start:**

  ```ts
  // astro.config.mjs
  import { defineConfig } from "astro/config";
  export default defineConfig({
    markdown: {
      syntaxHighlight: "shiki",
      shikiConfig: { theme: "github-dark", wrap: true },
    },
  });
  ```
* **Code Hike sketch:**

  ```bash
  npm i -D codehike
  ```

  ```mdx
  ---
  setup: |
    import { CH } from "codehike/mdx";
  ---
  <CH.Code code={`console.log('hi')`} lang="js" />
  ```

  Tip: keep number of heavy MDX plugins low to avoid slow builds.

### Testing and QA: Vitest and Playwright

* **What it is:** Unit tests with Vitest and component tests for islands; Playwright drives real browser E2E.
* **Why it matters:** Prevent regressions in layouts, routes, and interactive islands.
* **Vitest quick start:**

  ```bash
  npm i -D vitest @testing-library/dom @testing-library/user-event
  ```

  ```ts
  // vitest.config.ts
  import { defineConfig } from "vitest/config";
  export default defineConfig({ test: { environment: "happy-dom" } });
  ```
* **Playwright quick start:**

  ```bash
  npm i -D @playwright/test
  npx playwright install
  ```

  ```ts
  // tests/home.spec.ts
  import { test, expect } from "@playwright/test";
  test("home loads", async ({ page }) => {
    await page.goto("http://localhost:4321");
    await expect(page.getByRole("heading", { name: "Hello" })).toBeVisible();
  });
  ```

  CI tip: build once, run both Playwright and Lighthouse CI against the same build output.

### Performance and monitoring bundle

* **What it is:** Automate perf checks and production monitoring.
* **Why it matters:** Catch regressions before they ship; see real user metrics in prod.
* **Lighthouse CI (GitHub Actions):**

  ```yaml
  name: lhci
  on: [push]
  jobs:
    lhci:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v4
        - uses: actions/setup-node@v4
          with: { node-version: 20 }
        - run: npm ci
        - run: npm run build
        - run: npx lhci autorun --upload.target=temporary-public-storage
  ```
* **Core Web Vitals in prod:** use a tiny script to send CLS, LCP, INP to your analytics endpoint.

  ```html
  <script type="module">
    import { onLCP, onINP, onCLS } from "https://unpkg.com/web-vitals@3/dist/web-vitals.attribution.js";
    const send = (m) => navigator.sendBeacon("/vitals", JSON.stringify(m));
    onLCP(send); onINP(send); onCLS(send);
  </script>
  ```
* **Error and trace monitoring:** Sentry or OpenReplay for client errors; platform logs for SSR adapters. Remember to scrub PII.
* **Cloudflare insights:** If deploying to Pages, enable Analytics and Logs; set long cache headers for static assets.

---

### Security headers and CSP patterns

* **What it is:** HTTP response headers that harden your site: `Content-Security-Policy`, `Strict-Transport-Security`, `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`.
* **Why it matters:** Blocks common injection vectors and mixed content; reduces blast radius if a script is compromised.
* **Docs:**

  * CSP: [https://developer.mozilla.org/docs/Web/HTTP/CSP](https://developer.mozilla.org/docs/Web/HTTP/CSP)
  * Security headers overview: [https://developer.mozilla.org/docs/Web/HTTP/Headers](https://developer.mozilla.org/docs/Web/HTTP/Headers)
  * Astro adapters guidance: [https://docs.astro.build/en/guides/deploy/](https://docs.astro.build/en/guides/deploy/)
* **Cloudflare Pages/Workers example (wrangler.toml):**

  ```toml
  [vars]
  SECURITY_HEADERS = "true"
  ```

  ```js
  // functions/_middleware.js (Workers)
  export async function onRequest({ next }) {
    const res = await next();
    res.headers.set("X-Content-Type-Options", "nosniff");
    res.headers.set("Referrer-Policy", "strict-origin-when-cross-origin");
    res.headers.set("Permissions-Policy", "camera=(), microphone=(), geolocation=()");
    res.headers.set("X-Frame-Options", "DENY");
    res.headers.set("Strict-Transport-Security", "max-age=31536000; includeSubDomains; preload");
    res.headers.set("Content-Security-Policy", [
      "default-src 'self'",
      "img-src 'self' data: https:",
      "script-src 'self' 'unsafe-inline' https:",
      "style-src 'self' 'unsafe-inline' https:",
      "connect-src 'self' https:",
      "font-src 'self' https: data:",
    ].join("; "));
    return res;
  }
  ```

  Tip: start with `report-only` for CSP during rollout and inspect violations in your logs.

### Accessibility linting and automated checks

* **What it is:** Static checks and runtime scans to catch a11y issues.
* **Why it matters:** Prevents regressions and improves usability for everyone.
* **Tools:**

  * ESLint a11y: `eslint-plugin-jsx-a11y` for JSX islands; `astro-eslint-parser` for .astro files.
  * Playwright Axe: integrate Axe-core in E2E scans.
* **Snippets:**

  ```bash
  npm i -D eslint @astrojs/eslint-config eslint-plugin-jsx-a11y
  ```

  ```js
  // .eslintrc.cjs
  module.exports = { extends: ["@astrojs/eslint-config", "plugin:jsx-a11y/recommended"] };
  ```

  ```ts
  // tests/a11y.spec.ts
  import { test, expect } from "@playwright/test";
  import AxeBuilder from "@axe-core/playwright";
  test("a11y", async ({ page }) => {
    await page.goto("http://localhost:4321");
    const results = await new AxeBuilder({ page }).analyze();
    expect(results.violations).toEqual([]);
  });
  ```

### Data fetching with TanStack Query

* **What it is:** Client-side fetching, caching, and background updates inside hydrated islands.
* **Why it matters:** Smooth UX for dashboards and editors without hand-rolled fetch state.
* **Docs:** [https://tanstack.com/query/latest](https://tanstack.com/query/latest)
* **Vue island example:**

  ```bash
  npm i @tanstack/vue-query
  ```

  ```vue
  <!-- src/components/UsersPane.vue -->
  <script setup>
  import { VueQueryPlugin, useQuery } from "@tanstack/vue-query";
  const { data, isLoading, error } = useQuery({
    queryKey: ["users"],
    queryFn: () => fetch("/api/users").then(r => r.json()),
    staleTime: 60_000,
  });
  </script>
  <template>
    <div v-if="isLoading">Loading...</div>
    <div v-else-if="error">Error</div>
    <ul><li v-for="u in data" :key="u.id">{{ u.name }}</li></ul>
  </template>
  ```

  ```astro
  ---
  import UsersPane from "../components/UsersPane.vue";
  ---
  <UsersPane client:visible />
  ```

  Tip: co-locate server endpoints with `src/pages/api/*.ts`; cache at the edge when possible.

### RSS feeds and changelog wiring

* **What it is:** Generate RSS for blogs or release notes; keeps subscribers in sync.
* **Docs:** [https://docs.astro.build/en/guides/rss/](https://docs.astro.build/en/guides/rss/)
* **Quick start:**

  ```bash
  npm i -D @astrojs/rss
  ```

  ```ts
  // src/pages/rss.xml.ts
  import rss from "@astrojs/rss";
  import { getCollection } from "astro:content";
  export async function GET(context) {
    const posts = await getCollection("posts", ({ data }) => !data.draft);
    return rss({
      title: "My Blog",
      stylesheet: true,
      items: posts.map(p => ({ link: `/${p.slug}/`, title: p.data.title, pubDate: p.data.date })),
      site: context.site,
    });
  }
  ```

### Deploy-time image optimization and caching

* **What it is:** Optimize and cache images at build or edge.
* **Patterns:**

  * Build-time via `@astrojs/image` static generation.
  * Edge transforms on Cloudflare Images or Vercel OG/Image; set `Cache-Control` and immutable fingerprints.
* **Headers tip:**

  ```plain
  Cache-Control: public, max-age=31536000, immutable
  ```
* **Cloudflare Pages _headers example:**

  ```
  /assets/*
    Cache-Control: public, max-age=31536000, immutable
  ```

