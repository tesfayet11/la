# LA Monorepo

A npm workspaces monorepo containing two AWS Amplify Gen 2 + Next.js applications.

## Structure

```
.
├── apps/
│   ├── inventory/   # Inventory management app
│   └── shop/        # Shop app
├── packages/
│   └── tsconfig/    # Shared TypeScript config
├── amplify.yml      # Amplify monorepo build spec
└── package.json     # Workspace root
```

## Getting Started

Install dependencies from the repository root:

```bash
npm install
```

Run an app locally:

```bash
# Inventory (http://localhost:3000)
npm run dev:inventory

# Shop (http://localhost:3001)
npm run dev:shop
```

For local Amplify backend development, run the sandbox from the app directory:

```bash
cd apps/inventory
npx ampx sandbox
```

## Deploying to AWS Amplify

This repo uses Amplify monorepo configuration. Create a separate Amplify app for each project and set the monorepo app root:

| App       | Monorepo app root  | Env variable value   |
|-----------|--------------------|----------------------|
| Inventory | `apps/inventory`   | `apps/inventory`     |
| Shop      | `apps/shop`        | `apps/shop`          |

Amplify sets `AMPLIFY_MONOREPO_APP_ROOT` automatically when you connect each app. The root `amplify.yml` defines build settings for both applications.

## Scripts

| Command              | Description                    |
|----------------------|--------------------------------|
| `npm run dev:inventory` | Start inventory dev server  |
| `npm run dev:shop`      | Start shop dev server       |
| `npm run build`         | Build all apps              |
| `npm run build:inventory` | Build inventory app       |
| `npm run build:shop`      | Build shop app            |
| `npm run lint`            | Lint all apps             |
