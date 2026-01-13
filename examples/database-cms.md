# Database and CMS Examples

## Astro DB

```bash
npm i -D @astrojs/db drizzle-orm
```

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import db from "@astrojs/db";

export default defineConfig({
  integrations: [
    db({
      // Database configuration
    }),
  ],
});
```

**Database Schema:**
```ts
// db/config.ts
import { defineDb, defineTable, column } from "astro:db";

const Users = defineTable({
  columns: {
    id: column.number({ primaryKey: true }),
    name: column.text(),
    email: column.text({ unique: true }),
  },
});

export default defineDb({
  tables: {
    Users,
  },
});
```

**Usage:**
```astro
---
// src/pages/users.astro
import { db, Users } from "astro:db";

const users = await db.select().from(Users);
---

<ul>
  {users.map((user) => (
    <li>{user.name} - {user.email}</li>
  ))}
</ul>
```

## Contentful CMS

```bash
npm i contentful
```

```ts
// src/lib/contentful.ts
import { createClient } from "contentful";

export const contentful = createClient({
  space: import.meta.env.CONTENTFUL_SPACE_ID,
  accessToken: import.meta.env.CONTENTFUL_ACCESS_TOKEN,
});
```

**Usage:**
```astro
---
// src/pages/blog/index.astro
import { contentful } from "../lib/contentful";

const entries = await contentful.getEntries({
  content_type: "blogPost",
  order: "-sys.createdAt",
});
---

<ul>
  {entries.items.map((entry) => (
    <li>
      <a href={`/blog/${entry.fields.slug}`}>
        {entry.fields.title}
      </a>
    </li>
  ))}
</ul>
```

## Sanity CMS

```bash
npm i @sanity/client
```

```ts
// src/lib/sanity.ts
import { createClient } from "@sanity/client";

export const sanity = createClient({
  projectId: import.meta.env.SANITY_PROJECT_ID,
  dataset: import.meta.env.SANITY_DATASET,
  useCdn: true,
  apiVersion: "2024-01-01",
});
```

**Usage:**
```astro
---
// src/pages/blog/index.astro
import { sanity } from "../lib/sanity";

const posts = await sanity.fetch(`
  *[_type == "post"] | order(_createdAt desc) {
    _id,
    title,
    slug,
    publishedAt
  }
`);
---

<ul>
  {posts.map((post) => (
    <li>
      <a href={`/blog/${post.slug.current}`}>
        {post.title}
      </a>
    </li>
  ))}
</ul>
```

## Strapi CMS

```bash
npm i @strapi/strapi
```

```ts
// src/lib/strapi.ts
const STRAPI_URL = import.meta.env.STRAPI_URL;

export async function getStrapiData(endpoint: string) {
  const response = await fetch(`${STRAPI_URL}/api${endpoint}`);
  return response.json();
}
```

**Usage:**
```astro
---
// src/pages/blog/index.astro
import { getStrapiData } from "../lib/strapi";

const { data } = await getStrapiData("/articles?populate=*");
---

<ul>
  {data.map((article) => (
    <li>
      <a href={`/blog/${article.attributes.slug}`}>
        {article.attributes.title}
      </a>
    </li>
  ))}
</ul>
```

## Prisma ORM

```bash
npm i @prisma/client
npm i -D prisma
```

```ts
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id    Int    @id @default(autoincrement())
  name  String
  email String @unique
}
```

**Usage:**
```ts
// src/lib/prisma.ts
import { PrismaClient } from "@prisma/client";

const prisma = new PrismaClient();

export default prisma;
```

```astro
---
// src/pages/users.astro
import prisma from "../lib/prisma";

const users = await prisma.user.findMany();
---

<ul>
  {users.map((user) => (
    <li>{user.name} - {user.email}</li>
  ))}
</ul>
```
