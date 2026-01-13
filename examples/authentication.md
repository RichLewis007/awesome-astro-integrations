# Authentication Examples

## Clerk Authentication

```bash
npm i @clerk/astro
```

```ts
// astro.config.mjs
import { defineConfig } from "astro/config";
import clerk from "@clerk/astro";

export default defineConfig({
  integrations: [
    clerk({
      afterSignInUrl: "/dashboard",
      afterSignUpUrl: "/onboarding",
    }),
  ],
});
```

**Environment Variables:**
```env
PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_...
CLERK_SECRET_KEY=sk_test_...
```

**Usage:**
```astro
---
// src/pages/dashboard.astro
import { getAuth } from "@clerk/astro/server";

const { userId } = await getAuth();

if (!userId) {
  return Astro.redirect("/sign-in");
}
---

<h1>Welcome to your dashboard!</h1>
```

**Client Component:**
```astro
---
// src/components/UserButton.astro
---

<clerk-user-button />
```

## Auth.js (NextAuth.js)

```bash
npm i @auth/astro
```

```ts
// src/auth.config.ts
import { defineConfig } from "@auth/astro/config";
import GitHub from "@auth/astro/providers/github";

export const { signIn, signOut, auth, handlers } = defineConfig({
  providers: [
    GitHub({
      clientId: import.meta.env.GITHUB_CLIENT_ID,
      clientSecret: import.meta.env.GITHUB_CLIENT_SECRET,
    }),
  ],
});
```

**API Route:**
```ts
// src/pages/api/auth/[...auth].ts
import { handlers } from "../../../auth.config";

export const { GET, POST } = handlers;
```

**Usage:**
```astro
---
// src/pages/dashboard.astro
import { auth } from "../auth.config";

const session = await auth();

if (!session) {
  return Astro.redirect("/api/auth/signin");
}
---

<h1>Welcome, {session.user.name}!</h1>
```

## Supabase Auth

```bash
npm i @supabase/supabase-js @supabase/auth-helpers-astro
```

```ts
// src/lib/supabase.ts
import { createClient } from "@supabase/supabase-js";

export const supabase = createClient(
  import.meta.env.PUBLIC_SUPABASE_URL,
  import.meta.env.PUBLIC_SUPABASE_ANON_KEY
);
```

**Server-side:**
```astro
---
// src/pages/dashboard.astro
import { createClient } from "@supabase/auth-helpers-astro";
import type { APIContext } from "astro";

const supabase = createClient(
  Astro.request,
  Astro.response,
  {
    supabaseUrl: import.meta.env.PUBLIC_SUPABASE_URL,
    supabaseKey: import.meta.env.PUBLIC_SUPABASE_ANON_KEY,
  }
);

const {
  data: { session },
} = await supabase.auth.getSession();

if (!session) {
  return Astro.redirect("/sign-in");
}
---

<h1>Welcome, {session.user.email}!</h1>
```

## Lucia Auth

```bash
npm i lucia @lucia-auth/adapter-astro
```

```ts
// src/lib/auth.ts
import { lucia } from "lucia";
import { astro } from "@lucia-auth/adapter-astro";
import { github } from "@lucia-auth/oauth/providers";

export const auth = lucia({
  adapter: astro(),
  env: import.meta.env.PROD ? "PROD" : "DEV",
});

export const githubAuth = github(auth, {
  clientId: import.meta.env.GITHUB_CLIENT_ID,
  clientSecret: import.meta.env.GITHUB_CLIENT_SECRET,
});
```
