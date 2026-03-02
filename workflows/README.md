# GenFeed Reusable Workflows

Org-level reusable GitHub Actions for all GenFeed repos. One source of truth for quality gates.

## Available Workflows

| Workflow | What it does | Timeout |
|----------|-------------|---------|
| `reusable-lint.yml` | Biome format check + lint | 10min |
| `reusable-typecheck.yml` | TypeScript type check (affected-only on PRs) | 15min |
| `reusable-build.yml` | Build with Turbo cache | 25min |
| `reusable-test.yml` | Run tests + optional Codecov upload | 30min |

## Usage

### Minimal (new app, gets everything)

Create `.github/workflows/ci.yml` in your repo:

```yaml
name: CI
on:
  pull_request:
    branches: [main, develop]
  push:
    branches: [staging]

jobs:
  lint:
    uses: genfeedai/.github/.github/workflows/reusable-lint.yml@main

  type-check:
    uses: genfeedai/.github/.github/workflows/reusable-typecheck.yml@main

  build:
    needs: [lint, type-check]
    uses: genfeedai/.github/.github/workflows/reusable-build.yml@main
```

### With custom commands

```yaml
jobs:
  lint:
    uses: genfeedai/.github/.github/workflows/reusable-lint.yml@main
    with:
      lint-command: 'bunx biome check .'
      format-command: 'bunx biome format --check .'

  type-check:
    uses: genfeedai/.github/.github/workflows/reusable-typecheck.yml@main
    with:
      typecheck-command: 'bun tsc --noEmit'

  build:
    needs: [lint, type-check]
    uses: genfeedai/.github/.github/workflows/reusable-build.yml@main
    with:
      build-command: 'bun run build'
      node-options: '--max-old-space-size=4096'

  test:
    needs: [lint, type-check]
    uses: genfeedai/.github/.github/workflows/reusable-test.yml@main
    with:
      coverage: true
      coverage-flag: 'my-app'
    secrets:
      CODECOV_TOKEN: ${{ secrets.CODECOV_TOKEN }}
```

### Cloud monorepo (custom — calls reusable jobs internally)

The `cloud` repo has complex path filtering and multi-service logic, so it calls reusable 
workflows for setup/bun/cache steps but keeps its own job orchestration.

## Branch Protection (enforce it)

In GitHub → Settings → Branches → Add rule for `main`/`develop`/`staging`:
- ✅ Require status checks to pass
- Required checks: `lint`, `type-check`, `build` (exact job names from the reusable workflows)
- ✅ Require branches to be up to date
- ✅ Restrict deletions

## Adding a new repo

1. Copy the minimal usage above into `.github/workflows/ci.yml`
2. Enable branch protection on `main` requiring `lint`, `type-check`, `build`
3. Done — new PRs are gated automatically

## Updating the workflows

Changes to `reusable-*.yml` apply immediately to all repos calling `@main`. 
Test in a branch with `@your-branch` before merging.
