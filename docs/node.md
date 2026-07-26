# Node.js / TypeScript CI Template

File: [`.github/workflows/ci-node.yml`](../.github/workflows/ci-node.yml)

## What it checks

| Step | Script | Fails on |
|------|--------|----------|
| Install | `npm ci` | Lockfile mismatch |
| Lint | `npm run lint` | Lint errors |
| Types | `npm run typecheck` or `npx tsc --noEmit` | Type errors |
| Tests | `npm test` | Test failures |
| Build | `npm run build` | Compilation errors |

All steps use `--if-present` — they're skipped silently if the corresponding `package.json` script doesn't exist.

## Customization

- **Node versions**: Edit the matrix strategy to match what you support.
- **Package manager**: Replace `npm ci` with `pnpm install --frozen-lockfile` or `yarn install --frozen-lockfile` and change the setup action accordingly.
- **Linter**: Make sure `package.json` has a `"lint"` script, or the step is skipped.

## Prerequisites

- A `package.json` + `package-lock.json` at the repo root
- For the release template: an `NPM_TOKEN` secret
