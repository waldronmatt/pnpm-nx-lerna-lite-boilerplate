# Architecture

## Introduction

The repository setup and folder structure is heavily inspired by the turborepo [kitchen sink starter monorepo templates](https://github.com/vercel/turbo/tree/main/examples/kitchen-sink) and the [design system monorepo template](https://github.com/vercel/turbo/tree/main/examples/design-system).

## Folder Structure

```bash
apps/
configs/
docs/
packages/
...
package.json
pnpm-workspace.yaml
```

**`apps`** - Contains standalone applications / SPAs that can consume modules in `packages`

**`configs`** - Contains linters / configurations such as `eslint` / `tsconfig` shared across the monorepo

**`docs`** - Contains documentation for ui components and other documentation

**`packages`** - Contains utilities and tools published to `npm` that are used across the monorepo

## Turborepo Differences

- Tooling and configurations such as `eslint` and `tsconfig` are included in their own `config` folder. This is a personal preference to separate from the `packages` folder where reusable packages and utilities shared across projects are stored.
- Configurations such as `eslint` and `tsconfig` in the `config` folder do not reference other shareable configurations, for example, my own personal `eslint` config I use across projects. This is a personal preference so that configuration complexity and inheritence is kept to a minimum. This keeps configuration code more readable and self contained to the monorepo.
- Package naming for public packages published to `npm` have the `@` alias scoping while private packages do not have an alias. This is a personal preference to maintain the distinction between published and non-published packages more easily.
- The `apps` and `docs` folders remain separate and both are top-level folders. This is a personal preference to make the distinction between SPA and UI component documentation code / other documentation. I opt for more top-level folders.

## Turborepo Similarities

- Under `docs` is where `storybook` component code is stored, however it is common to house this along with the UI component for simplicity. If kept together, you would need to update the project to ignore `storybook` files when building and publishing the UI components to `npm`.