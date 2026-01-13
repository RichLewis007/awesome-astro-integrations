# Testing and QA Examples

## Vitest Setup

```bash
npm i -D vitest @testing-library/dom @testing-library/user-event
```

```ts
// vitest.config.ts
import { defineConfig } from "vitest/config";

export default defineConfig({
  test: {
    environment: "happy-dom",
    globals: true,
  },
});
```

**Test Example:**
```ts
// src/components/__tests__/Button.test.ts
import { describe, it, expect } from "vitest";
import { render } from "@testing-library/dom";

describe("Button", () => {
  it("renders correctly", () => {
    const { container } = render(`
      <button>Click me</button>
    `);
    expect(container.textContent).toBe("Click me");
  });
});
```

## Playwright E2E Testing

```bash
npm i -D @playwright/test
npx playwright install
```

```ts
// playwright.config.ts
import { defineConfig, devices } from "@playwright/test";

export default defineConfig({
  testDir: "./tests",
  projects: [
    {
      name: "chromium",
      use: { ...devices["Desktop Chrome"] },
    },
  ],
  webServer: {
    command: "npm run dev",
    url: "http://localhost:4321",
    reuseExistingServer: !process.env.CI,
  },
});
```

**E2E Test:**
```ts
// tests/home.spec.ts
import { test, expect } from "@playwright/test";

test("home page loads", async ({ page }) => {
  await page.goto("http://localhost:4321");
  await expect(page.getByRole("heading", { name: "Welcome" })).toBeVisible();
});
```

## Accessibility Testing with Axe

```bash
npm i -D @axe-core/playwright
```

```ts
// tests/a11y.spec.ts
import { test, expect } from "@playwright/test";
import AxeBuilder from "@axe-core/playwright";

test("should not have any automatically detectable accessibility issues", async ({
  page,
}) => {
  await page.goto("http://localhost:4321");
  const accessibilityScanResults = await new AxeBuilder({ page }).analyze();
  expect(accessibilityScanResults.violations).toEqual([]);
});
```

## ESLint for Astro

```bash
npm i -D eslint @astrojs/eslint-config
```

```js
// .eslintrc.cjs
module.exports = {
  extends: ["@astrojs/eslint-config"],
  rules: {
    // Your custom rules
  },
};
```

## Lighthouse CI

```yaml
# .github/workflows/lighthouse.yml
name: Lighthouse CI
on: [push]
jobs:
  lhci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm run build
      - run: npx lhci autorun --upload.target=temporary-public-storage
```

## Visual Regression Testing

```bash
npm i -D @playwright/test
```

```ts
// tests/visual.spec.ts
import { test, expect } from "@playwright/test";

test("homepage visual regression", async ({ page }) => {
  await page.goto("http://localhost:4321");
  await expect(page).toHaveScreenshot("homepage.png");
});
```
