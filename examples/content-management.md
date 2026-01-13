# Content Management Examples

## MDX Integration

### Basic MDX Setup

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import mdx from "@astrojs/mdx";

export default defineConfig({
  integrations: [
    mdx({
      // MDX options
      remarkPlugins: [],
      rehypePlugins: [],
    }),
  ],
});
```

**Installation:**

```bash
npm i -D @astrojs/mdx
```

**Usage:**

```mdx
---
// src/pages/blog/post.mdx
import { Button } from '../components/Button.astro';
---

# My MDX Post

This is a post written in MDX. I can use **Markdown** and <Button>components</Button>!
```

## Content Collections

### Setting Up Content Collections

```ts
// src/content/config.ts
import { defineCollection, z } from "astro:content";

const blog = defineCollection({
  type: "content",
  schema: z.object({
    title: z.string(),
    description: z.string(),
    pubDate: z.coerce.date(),
    updatedDate: z.coerce.date().optional(),
    heroImage: z.string().optional(),
    tags: z.array(z.string()).default([]),
    draft: z.boolean().default(false),
  }),
});

export const collections = {
  blog,
};
```

### Using Content Collections

```astro
---
// src/pages/blog/index.astro
import { getCollection } from "astro:content";

const allPosts = await getCollection("blog", ({ data }) => {
  return import.meta.env.PROD ? data.draft !== true : true;
});

// Sort posts by date
const sortedPosts = allPosts.sort((a, b) =>
  b.data.pubDate.valueOf() - a.data.pubDate.valueOf()
);
---

<ul>
  {sortedPosts.map((post) => (
    <li>
      <a href={`/blog/${post.slug}`}>
        <h2>{post.data.title}</h2>
        <p>{post.data.description}</p>
        <time>{post.data.pubDate.toLocaleDateString()}</time>
      </a>
    </li>
  ))}
</ul>
```

### Rendering Content Collection Entry

```astro
---
// src/pages/blog/[slug].astro
import { getCollection } from "astro:content";

export async function getStaticPaths() {
  const posts = await getCollection("blog");
  return posts.map((post) => ({
    params: { slug: post.slug },
    props: { post },
  }));
}

const { post } = Astro.props;
const { Content } = await post.render();
---

<article>
  <h1>{post.data.title}</h1>
  <time>{post.data.pubDate.toLocaleDateString()}</time>
  <Content />
</article>
```

## Starlight Documentation Theme

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import starlight from "@astrojs/starlight";

export default defineConfig({
  integrations: [
    starlight({
      title: "My Documentation",
      social: {
        github: "https://github.com/username/repo",
      },
      sidebar: [
        {
          label: "Guides",
          items: [
            { label: "Getting Started", link: "/guides/getting-started/" },
          ],
        },
      ],
    }),
  ],
});
```

**Installation:**

```bash
npm i -D @astrojs/starlight
```
