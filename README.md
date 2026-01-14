<!--lint disable awesome-list-item awesome-badge awesome-contributing double-link-->
<div align="center">

<img src="images/awesome-astro-integrations-banner.jpg" alt="Awesome Astro Integrations" width="800">

# Awesome Astro Integrations [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

Extensions and plugins that add functionality to Astro web framework projects.

[![Astro](https://img.shields.io/badge/Astro-5.0+-FF5D01?logo=astro&logoColor=white)](https://astro.build)

_Updated with reviews and recommendations for your kind of project_

</div>

---

## Contents

- [About](#about)
- [Quick Start](#-quick-start)
- [Official Integrations](#-official-integrations)
  - [UI Frameworks](#ui-frameworks)
  - [Content & Documentation](#content--documentation)
  - [Adapters & Deployment](#adapters--deployment)
  - [Other Official Integrations](#other-official-integrations)
- [Community Integrations](#-community-integrations)
  - [Performance & Optimization](#performance--optimization)
  - [Styling & CSS](#styling--css)
  - [Images, Icons & Fonts](#images-icons--fonts)
  - [Authentication & Security](#authentication--security)
  - [Database & CMS](#database--cms)
  - [SEO & Analytics](#seo--analytics)
  - [Developer Experience](#developer-experience)
  - [Testing & Quality Assurance](#testing--quality-assurance)
  - [Accessibility](#accessibility)
- [Code Examples](#-code-examples)
- [Best Practices](#-best-practices)
- [Resources](#-resources)

---

## About

This repository is your go-to resource for discovering the best Astro integrations. Whether you're building a blog, documentation site, e-commerce platform, or web application, you'll find carefully curated integrations that deliver real impact.

**Curated by:** [Rich Lewis](https://RichLewis.com) ([@RichLewis007](https://github.com/RichLewis007))

**What makes an integration "AWESOME"?**

- ✅ Actively maintained
- ✅ Well-documented
- ✅ Production-ready
- ✅ Performance-conscious
- ✅ Developer-friendly

---

## ⚡ Quick Start

<details>
<summary><strong>Install an integration</strong></summary>

```bash
# Using Astro's automatic setup (recommended)
npx astro add react tailwind mdx

# Or install manually
npm install @astrojs/react @astrojs/tailwind @astrojs/mdx
```

Then add to your `astro.config.mjs`:

```ts
import { defineConfig } from "astro/config";
import react from "@astrojs/react";
import tailwind from "@astrojs/tailwind";
import mdx from "@astrojs/mdx";

export default defineConfig({
  integrations: [react(), tailwind(), mdx()],
});
```

</details>

<details>
<summary><strong>Quick picks by goal</strong></summary>

- **Make it feel instant**: `astro-critical-css` + `astro-compress`
- **Ship fewer bytes of CSS**: `UnoCSS` or `Tailwind CSS`
- **Keep analytics but remove jank**: `Partytown` + `Umami` or `Plausible`
- **Docs that don't fight you**: `Starlight` + `@astrojs/mdx`
- **Icons without bloat**: `astro-icon`
- **Add React/Vue/Svelte**: `@astrojs/react`, `@astrojs/vue`, `@astrojs/svelte`
- **Deploy anywhere**: `@astrojs/vercel`, `@astrojs/netlify`, `@astrojs/cloudflare`

</details>

---

## 🏢 Official Integrations

Integrations maintained by the Astro core team. These are battle-tested and production-ready.

### UI Frameworks

<details>
<summary><strong>@astrojs/react</strong> - Use React components in Astro</summary>

**Weekly Downloads:** ~1.2M | **Official** | **Most Popular**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/react/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/react)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/react)
- [📝 Code Examples](./examples/ui-frameworks.md#react-integration)

**Why it's awesome:** Seamlessly integrate React components as islands. Perfect for adding interactivity without shipping React to every page.

**Installation:**

```bash
npx astro add react
```

</details>

<details>
<summary><strong>@astrojs/vue</strong> - Use Vue components in Astro</summary>

**Weekly Downloads:** ~167K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/vue/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/vue)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/vue)
- [📝 Code Examples](./examples/ui-frameworks.md#vue-integration)

**Why it's awesome:** Vue 3 support with Composition API. Great for teams already using Vue.

**Installation:**

```bash
npx astro add vue
```

</details>

<details>
<summary><strong>@astrojs/svelte</strong> - Use Svelte components in Astro</summary>

**Weekly Downloads:** ~264K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/svelte/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/svelte)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/svelte)
- [📝 Code Examples](./examples/ui-frameworks.md#svelte-integration)

**Why it's awesome:** Svelte's compile-time approach pairs perfectly with Astro's zero-JS philosophy.

**Installation:**

```bash
npx astro add svelte
```

</details>

<details>
<summary><strong>@astrojs/preact</strong> - Use Preact components in Astro</summary>

**Weekly Downloads:** ~45K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/preact/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/preact)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/preact)
- [📝 Code Examples](./examples/ui-frameworks.md#preact-integration)

**Why it's awesome:** React-compatible but much smaller (3KB). Perfect for performance-critical apps.

**Installation:**

```bash
npx astro add preact
```

</details>

<details>
<summary><strong>@astrojs/solid-js</strong> - Use SolidJS components in Astro</summary>

**Weekly Downloads:** ~12K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/solid-js/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/solid-js)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/solid-js)
- [📝 Code Examples](./examples/ui-frameworks.md#solidjs-integration)

**Why it's awesome:** Fine-grained reactivity with no virtual DOM. Excellent performance characteristics.

**Installation:**

```bash
npx astro add solid-js
```

</details>

<details>
<summary><strong>@astrojs/alpinejs</strong> - Use Alpine.js in Astro</summary>

**Weekly Downloads:** ~25K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/alpinejs/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/alpinejs)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/alpinejs)
- [📝 Code Examples](./examples/ui-frameworks.md#alpinejs-integration)

**Why it's awesome:** Minimal JavaScript framework (15KB). Perfect for adding interactivity without a build step.

**Installation:**

```bash
npx astro add alpinejs
```

</details>

### Content & Documentation

<details>
<summary><strong>@astrojs/mdx</strong> - MDX support for Astro</summary>

**Weekly Downloads:** ~986K | **Official** | **Most Popular**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/mdx/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/mdx)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/mdx)
- [📝 Code Examples](./examples/content-management.md#mdx-integration)

**Why it's awesome:** Mix Markdown with JSX components. Keep authoring flow simple and use shortcodes everywhere.

**Installation:**

```bash
npx astro add mdx
```

</details>

<details>
<summary><strong>@astrojs/starlight</strong> - Official documentation theme</summary>

**Weekly Downloads:** ~85K | **Official**

- [📖 Documentation](https://starlight.astro.build/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/starlight)
- [💻 GitHub](https://github.com/withastro/starlight)
- [📝 Code Examples](./examples/content-management.md#starlight-documentation-theme)

**Why it's awesome:** Built-in search, i18n, strong a11y, and theming. Saves weeks for any docs site.

**Installation:**

```bash
npx astro add starlight
```

</details>

<details>
<summary><strong>@astrojs/markdoc</strong> - Markdoc support</summary>

**Weekly Downloads:** ~5K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/markdoc/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/markdoc)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/markdoc)

**Why it's awesome:** Structured Markdown with schema validation. Great for content that needs type safety.

**Installation:**

```bash
npx astro add markdoc
```

</details>

### Adapters & Deployment

<details>
<summary><strong>@astrojs/vercel</strong> - Deploy to Vercel</summary>

**Weekly Downloads:** ~241K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/deploy/vercel/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/vercel)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/vercel)
- [📝 Code Examples](./examples/adapters-deployment.md#vercel-adapter)

**Why it's awesome:** Zero-config deployment with edge functions support. Perfect for SSR and static sites.

**Installation:**

```bash
npx astro add vercel
```

</details>

<details>
<summary><strong>@astrojs/netlify</strong> - Deploy to Netlify</summary>

**Weekly Downloads:** ~148K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/deploy/netlify/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/netlify)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/netlify)
- [📝 Code Examples](./examples/adapters-deployment.md#netlify-adapter)

**Why it's awesome:** Netlify Functions and Edge Functions support. Great DX with Netlify Dev.

**Installation:**

```bash
npx astro add netlify
```

</details>

<details>
<summary><strong>@astrojs/cloudflare</strong> - Deploy to Cloudflare</summary>

**Weekly Downloads:** ~95K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/deploy/cloudflare/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/cloudflare)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/cloudflare)
- [📝 Code Examples](./examples/adapters-deployment.md#cloudflare-adapter)

**Why it's awesome:** Deploy to Cloudflare Workers/Pages. Edge computing with global distribution.

**Installation:**

```bash
npx astro add cloudflare
```

</details>

<details>
<summary><strong>@astrojs/node</strong> - Deploy to Node.js</summary>

**Weekly Downloads:** ~623K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/deploy/node/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/node)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/node)
- [📝 Code Examples](./examples/adapters-deployment.md#nodejs-adapter)

**Why it's awesome:** Deploy to any Node.js server. Flexible for custom hosting setups.

**Installation:**

```bash
npx astro add node
```

</details>

### Other Official Integrations

<details>
<summary><strong>@astrojs/sitemap</strong> - Automatic sitemap generation</summary>

**Weekly Downloads:** ~1.3M | **Official** | **Most Popular**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/sitemap/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/sitemap)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/sitemap)
- [📝 Code Examples](./examples/seo-analytics.md#sitemap-generation)

**Why it's awesome:** Automatically generates sitemaps for SEO. Zero configuration needed.

**Installation:**

```bash
npx astro add sitemap
```

</details>

<details>
<summary><strong>@astrojs/db</strong> - Built-in database with Drizzle ORM</summary>

**Weekly Downloads:** ~15K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/astro-db/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/db)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/db)
- [📝 Code Examples](./examples/database-cms.md#astro-db)

**Why it's awesome:** Built-in, managed SQL store. Perfect for small dynamic features without a separate backend.

**Installation:**

```bash
npx astro add db
```

</details>

<details>
<summary><strong>@astrojs/partytown</strong> - Offload third-party scripts to web workers</summary>

**Weekly Downloads:** ~45K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/partytown/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/partytown)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/partytown)
- [📝 Code Examples](./examples/performance-optimization.md#partytown)

**Why it's awesome:** Offload analytics and tag managers to web workers. Stops blocking the main thread.

**Installation:**

```bash
npx astro add partytown
```

</details>

---

## 🌟 Community Integrations

High-quality integrations built and maintained by the Astro community.

### Performance & Optimization

<details>
<summary><strong>astro-compress</strong> - Minify and compress HTML, CSS, JS, and images</summary>

**Weekly Downloads:** ~25K

- [📦 npm](https://www.npmjs.com/package/astro-compress)
- [💻 GitHub](https://github.com/kamranahmedse/astro-compress)
- [📝 Code Examples](./examples/performance-optimization.md#compression-and-minification)

**Why it's awesome:** One switch to minify everything. Put it last in your `integrations` array.

**Installation:**

```bash
npm i -D astro-compress
```

</details>

<details>
<summary><strong>astro-critters</strong> - Inline critical CSS</summary>

**Weekly Downloads:** ~8K

- [📦 npm](https://www.npmjs.com/package/astro-critters)
- [💻 GitHub](https://github.com/fariasf/astro-critters)
- [📝 Code Examples](./examples/performance-optimization.md#astro-critters)

**Why it's awesome:** Inlines above-the-fold CSS and lazy-loads the rest for faster first paint.

**Installation:**

```bash
npm i -D astro-critters
```

</details>

<details>
<summary><strong>astro-critical-css</strong> - Extract and inline critical CSS</summary>

**Weekly Downloads:** ~3K

- [📦 npm](https://www.npmjs.com/package/astro-critical-css)
- [💻 GitHub](https://github.com/rumaan/astro-critical-css)
- [📝 Code Examples](./examples/performance-optimization.md#astro-critical-css)

**Why it's awesome:** Alternative to astro-critters with different extraction strategy.

**Installation:**

```bash
npm i -D astro-critical-css
```

</details>

<details>
<summary><strong>UnoCSS</strong> - Utility-first CSS engine</summary>

**Weekly Downloads:** ~150K

- [📖 Documentation](https://unocss.dev/)
- [📦 npm](https://www.npmjs.com/package/unocss)
- [💻 GitHub](https://github.com/unocss/unocss)
- [📝 Code Examples](./examples/performance-optimization.md#unocss)

**Why it's awesome:** On-demand generation and presets. Usually lighter than shipping a full framework.

**Installation:**

```bash
npm i -D unocss @unocss/reset
```

</details>

### Styling & CSS

<details>
<summary><strong>@astrojs/tailwind</strong> - Tailwind CSS integration</summary>

**Weekly Downloads:** ~861K | **Official**

- [📖 Documentation](https://docs.astro.build/en/guides/integrations-guide/tailwind/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/tailwind)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/tailwind)

**Why it's awesome:** Official Tailwind CSS support. Utility-first styling with zero config.

**Installation:**

```bash
npx astro add tailwind
```

</details>

### Images, Icons & Fonts

<details>
<summary><strong>astro-icon</strong> - Icon component with Iconify support</summary>

**Weekly Downloads:** ~374K

- [📖 Documentation](https://www.astroicon.dev/)
- [📦 npm](https://www.npmjs.com/package/astro-icon)
- [💻 GitHub](https://github.com/natemoo-re/astro-icon)
- [📝 Code Examples](./examples/images-icons-fonts.md#astro-icon)

**Why it's awesome:** Local or Iconify icons with smart SVG inlining and sprite dedupe for tiny payloads.

**Installation:**

```bash
npm i -D astro-icon
```

</details>

<details>
<summary><strong>astro-font</strong> - Font optimization</summary>

**Weekly Downloads:** ~12K

- [📦 npm](https://www.npmjs.com/package/astro-font)
- [💻 GitHub](https://github.com/ayco/astro-font)
- [📝 Code Examples](./examples/images-icons-fonts.md#font-optimization)

**Why it's awesome:** Automates local and hosted font optimization with sensible defaults.

**Installation:**

```bash
npm i -D astro-font
```

</details>

### Authentication & Security

<details>
<summary><strong>@clerk/astro</strong> - Clerk authentication</summary>

**Weekly Downloads:** ~5K

- [📖 Documentation](https://clerk.com/docs/reference/astro/overview)
- [📦 npm](https://www.npmjs.com/package/@clerk/astro)
- [💻 GitHub](https://github.com/clerk/clerk-sdk-js)
- [📝 Code Examples](./examples/authentication.md#clerk-authentication)

**Why it's awesome:** Drop-in auth for accounts, sessions, and user management with SSR paths aligned for Astro.

**Installation:**

```bash
npm i @clerk/astro
```

</details>

<details>
<summary><strong>@auth/astro</strong> - Auth.js (NextAuth.js) for Astro</summary>

**Weekly Downloads:** ~8K

- [📖 Documentation](https://authjs.dev/getting-started/installation/adapters/astro)
- [📦 npm](https://www.npmjs.com/package/@auth/astro)
- [💻 GitHub](https://github.com/nextauthjs/next-auth)
- [📝 Code Examples](./examples/authentication.md#authjs-nextauthjs)

**Why it's awesome:** Popular authentication solution with many providers. Great for teams familiar with NextAuth.

**Installation:**

```bash
npm i @auth/astro
```

</details>

<details>
<summary><strong>@supabase/auth-helpers-astro</strong> - Supabase authentication</summary>

**Weekly Downloads:** ~15K

- [📖 Documentation](https://supabase.com/docs/guides/auth/auth-helpers/astro)
- [📦 npm](https://www.npmjs.com/package/@supabase/auth-helpers-astro)
- [💻 GitHub](https://github.com/supabase/auth-helpers)
- [📝 Code Examples](./examples/authentication.md#supabase-auth)

**Why it's awesome:** Open-source Firebase alternative. Includes auth, database, and storage.

**Installation:**

```bash
npm i @supabase/supabase-js @supabase/auth-helpers-astro
```

</details>

### Database & CMS

<details>
<summary><strong>Contentful</strong> - Headless CMS integration</summary>

- [📖 Documentation](https://www.contentful.com/developers/docs/javascript/tutorials/using-contentful-in-astro/)
- [📦 npm](https://www.npmjs.com/package/contentful)
- [💻 GitHub](https://github.com/contentful/contentful.js)
- [📝 Code Examples](./examples/database-cms.md#contentful-cms)

**Why it's awesome:** Popular headless CMS with great developer experience and content modeling.

**Installation:**

```bash
npm i contentful
```

</details>

<details>
<summary><strong>Sanity</strong> - Headless CMS with real-time collaboration</summary>

- [📖 Documentation](https://www.sanity.io/guides/astro)
- [📦 npm](https://www.npmjs.com/package/@sanity/client)
- [💻 GitHub](https://github.com/sanity-io/sanity)
- [📝 Code Examples](./examples/database-cms.md#sanity-cms)

**Why it's awesome:** Real-time collaboration, structured content, and powerful querying.

**Installation:**

```bash
npm i @sanity/client
```

</details>

<details>
<summary><strong>Strapi</strong> - Open-source headless CMS</summary>

- [📖 Documentation](https://strapi.io/integrations/astro-cms)
- [📦 npm](https://www.npmjs.com/package/@strapi/strapi)
- [💻 GitHub](https://github.com/strapi/strapi)
- [📝 Code Examples](./examples/database-cms.md#strapi-cms)

**Why it's awesome:** Self-hosted, open-source CMS with REST and GraphQL APIs.

**Installation:**

```bash
npm i @strapi/strapi
```

</details>

<details>
<summary><strong>Prisma</strong> - Next-generation ORM</summary>

- [📖 Documentation](https://www.prisma.io/docs/getting-started)
- [📦 npm](https://www.npmjs.com/package/@prisma/client)
- [💻 GitHub](https://github.com/prisma/prisma)
- [📝 Code Examples](./examples/database-cms.md#prisma-orm)

**Why it's awesome:** Type-safe database access with excellent developer experience.

**Installation:**

```bash
npm i @prisma/client
npm i -D prisma
```

</details>

### SEO & Analytics

<details>
<summary><strong>astro-seo</strong> - SEO component</summary>

**Weekly Downloads:** ~153K

- [📦 npm](https://www.npmjs.com/package/astro-seo)
- [💻 GitHub](https://github.com/jonasmerlin/astro-seo)
- [📝 Code Examples](./examples/seo-analytics.md#seo-component)

**Why it's awesome:** Makes it easy to add SEO-relevant tags to your Astro app.

**Installation:**

```bash
npm i -D astro-seo
```

</details>

<details>
<summary><strong>Plausible Analytics</strong> - Privacy-friendly analytics</summary>

- [📖 Documentation](https://plausible.io/docs)
- [💻 GitHub](https://github.com/plausible/analytics)
- [📝 Code Examples](./examples/seo-analytics.md#plausible-analytics)

**Why it's awesome:** Lightweight analytics with simple wiring. No cookies, GDPR compliant.

**Installation:**

```bash
# Manual setup - see code examples
```

</details>

<details>
<summary><strong>astro-umami</strong> - Umami analytics integration</summary>

**Weekly Downloads:** ~2K

- [📦 npm](https://www.npmjs.com/package/astro-umami)
- [💻 GitHub](https://github.com/yeskunall/astro-umami)
- [📝 Code Examples](./examples/seo-analytics.md#umami-analytics)

**Why it's awesome:** Privacy-friendly analytics with smooth integration. Works well with View Transitions and Partytown.

**Installation:**

```bash
npm i -D astro-umami
```

</details>

<details>
<summary><strong>@astrojs/rss</strong> - RSS feed generation</summary>

**Weekly Downloads:** ~45K

- [📖 Documentation](https://docs.astro.build/en/guides/rss/)
- [📦 npm](https://www.npmjs.com/package/@astrojs/rss)
- [💻 GitHub](https://github.com/withastro/astro/tree/main/packages/integrations/rss)
- [📝 Code Examples](./examples/seo-analytics.md#rss-feed)

**Why it's awesome:** Generate RSS for blogs or release notes. Keeps subscribers in sync.

**Installation:**

```bash
npm i -D @astrojs/rss
```

</details>

### Developer Experience

<details>
<summary><strong>astro-auto-import</strong> - Auto-import components</summary>

**Weekly Downloads:** ~8K

- [📦 npm](https://www.npmjs.com/package/astro-auto-import)
- [💻 GitHub](https://github.com/ElMassimo/astro-auto-import)

**Why it's awesome:** Automatically imports components in Astro projects. Reduces boilerplate.

**Installation:**

```bash
npm i -D astro-auto-import
```

</details>

<details>
<summary><strong>astro-expressive-code</strong> - Syntax highlighting engine</summary>

**Weekly Downloads:** ~12K

- [📦 npm](https://www.npmjs.com/package/astro-expressive-code)
- [💻 GitHub](https://github.com/expressive-code/astro-expressive-code)

**Why it's awesome:** Modular syntax highlighting & annotation engine for presenting source code.

**Installation:**

```bash
npm i -D astro-expressive-code
```

</details>

<details>
<summary><strong>eslint-plugin-astro</strong> - ESLint plugin for Astro</summary>

**Weekly Downloads:** ~85K

- [📦 npm](https://www.npmjs.com/package/eslint-plugin-astro)
- [💻 GitHub](https://github.com/ota-meshi/eslint-plugin-astro)
- [📝 Code Examples](./examples/testing-qa.md#eslint-for-astro)

**Why it's awesome:** Linting Astro components using ESLint. Find problems and apply consistent code style.

**Installation:**

```bash
npm i -D eslint @astrojs/eslint-config eslint-plugin-astro
```

</details>

### Testing & Quality Assurance

<details>
<summary><strong>Vitest</strong> - Unit testing</summary>

- [📖 Documentation](https://vitest.dev/)
- [📦 npm](https://www.npmjs.com/package/vitest)
- [💻 GitHub](https://github.com/vitest-dev/vitest)
- [📝 Code Examples](./examples/testing-qa.md#vitest-setup)

**Why it's awesome:** Fast unit test framework. Works great with Astro's Vite-based build.

**Installation:**

```bash
npm i -D vitest @testing-library/dom @testing-library/user-event
```

</details>

<details>
<summary><strong>Playwright</strong> - End-to-end testing</summary>

- [📖 Documentation](https://playwright.dev/)
- [📦 npm](https://www.npmjs.com/package/@playwright/test)
- [💻 GitHub](https://github.com/microsoft/playwright)
- [📝 Code Examples](./examples/testing-qa.md#playwright-e2e-testing)

**Why it's awesome:** Reliable end-to-end testing. Prevents regressions in layouts, routes, and interactive islands.

**Installation:**

```bash
npm i -D @playwright/test
npx playwright install
```

</details>

<details>
<summary><strong>@axe-core/playwright</strong> - Accessibility testing</summary>

- [📦 npm](https://www.npmjs.com/package/@axe-core/playwright)
- [💻 GitHub](https://github.com/dequelabs/axe-core)
- [📝 Code Examples](./examples/testing-qa.md#accessibility-testing-with-axe)

**Why it's awesome:** Automated accessibility testing. Prevents regressions and improves usability for everyone.

**Installation:**

```bash
npm i -D @axe-core/playwright
```

</details>

### Accessibility

<details>
<summary><strong>astro-a11y</strong> - Accessibility checks</summary>

**Weekly Downloads:** ~3K

- [📦 npm](https://www.npmjs.com/package/astro-a11y)
- [💻 GitHub](https://github.com/markteekman/astro-a11y)

**Why it's awesome:** Provides accessibility checks and improvements for Astro projects.

**Installation:**

```bash
npm i -D astro-a11y
```

</details>

---

## 📝 Code Examples

Detailed code examples and implementation guides are available in the [`examples/`](./examples/) directory:

- [Performance Optimization](./examples/performance-optimization.md) - Compression, critical CSS, Partytown, UnoCSS
- [Content Management](./examples/content-management.md) - MDX, Content Collections, Starlight
- [UI Frameworks](./examples/ui-frameworks.md) - React, Vue, Svelte, Preact, SolidJS, Alpine.js
- [Adapters & Deployment](./examples/adapters-deployment.md) - Vercel, Netlify, Cloudflare, Node.js
- [SEO & Analytics](./examples/seo-analytics.md) - Sitemap, SEO tags, Google Analytics, Plausible, Umami, RSS
- [Images, Icons & Fonts](./examples/images-icons-fonts.md) - Astro Icon, image optimization, font loading
- [Authentication](./examples/authentication.md) - Clerk, Auth.js, Supabase, Lucia
- [Database & CMS](./examples/database-cms.md) - Astro DB, Contentful, Sanity, Strapi, Prisma
- [Testing & QA](./examples/testing-qa.md) - Vitest, Playwright, ESLint, accessibility testing

---

## 💡 Best Practices

<details>
<summary><strong>Island Architecture</strong></summary>

- Prefer fewer, larger islands over many small ones to reduce hydration overhead
- Use `client:visible` or `client:idle` to delay hydration where possible
- Lazy-import heavy subcomponents inside hydrated islands
- Keep the rest of the site native so Astro can ship near-zero JS by default

</details>

<details>
<summary><strong>Performance</strong></summary>

- Put compression integrations last in your `integrations` array
- Use critical CSS inliners for faster first paint
- Offload third-party scripts to Partytown
- Optimize images using Astro's built-in image optimization

</details>

<details>
<summary><strong>SEO</strong></summary>

- Always set your `site` URL in `astro.config.mjs` for sitemap generation
- Use structured data (JSON-LD) for rich snippets
- Generate RSS feeds for blogs and changelogs
- Set up proper robots.txt

</details>

<details>
<summary><strong>Security</strong></summary>

- Use security headers (CSP, HSTS, etc.)
- Validate environment variables
- Sanitize user input
- Use HTTPS everywhere

</details>

---

## 📚 Resources

### Official Resources

- [Astro Documentation](https://docs.astro.build/)
- [Astro Integrations Guide](https://docs.astro.build/en/guides/integrations-guide/)
- [Astro Integration API Reference](https://docs.astro.build/en/reference/integrations-reference/)
- [Astro Integrations Directory](https://astro.build/integrations/)
- [Astro Discord Community](https://astro.build/chat)

### Community Resources

- [Astro Blog](https://astro.build/blog/)
- [Astro GitHub Discussions](https://github.com/withastro/astro/discussions)
- [r/astrojs](https://www.reddit.com/r/astrojs/) - Reddit community.
- [Stack Overflow - Astro](https://stackoverflow.com/questions/tagged/astro)

### Related Awesome Lists

- [Awesome Astro](https://github.com/one-aalam/awesome-astro)
- [Astro Themes](https://astro.build/themes/)

---

## 🤝 Contributing

Contributions are welcome! This repository aims to be a comprehensive resource for Astro integrations.

**Curator:** [Rich Lewis](https://RichLewis.com) ([@RichLewis007](https://github.com/RichLewis007))

**How to contribute:**

1. **Add a new integration**: Submit a pull request with the integration details
2. **Update existing entries**: Keep information current and accurate
3. **Improve examples**: Add or enhance code examples
4. **Fix issues**: Report bugs or suggest improvements

**Guidelines:**

- Only include integrations that are actively maintained
- Provide links to documentation, GitHub, and npm
- Include installation instructions
- Add code examples when possible
- Keep descriptions concise and helpful

---

## Footnotes

- Curated by [Rich Lewis](https://RichLewis.com) ([@RichLewis007](https://github.com/RichLewis007))
- [⭐ Star this repo](https://github.com/RichLewis007/awesome-astro-integrations) if you find it helpful!
