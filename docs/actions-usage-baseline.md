# GitHub Actions usage baseline

Use this baseline when creating or repairing Peerivo project CI.

## Required cost controls

1. **Do not duplicate feature-branch CI.** Use `pull_request` for feature work and restrict `push` CI to the repository default branch unless a separate branch-specific effect is genuinely required.
2. **Cancel superseded pull-request runs.** Use a concurrency group bound to repository + PR and `cancel-in-progress` only for pull requests. Do not cancel default-branch release/deployment runs.
3. **Fail fast before expensive jobs.** Lint/typecheck/unit/contract/security gates should run before Docker, database, browser, Supabase or other expensive integration jobs. Expensive jobs should use `needs` on the fast gate when that preserves the required test contract.
4. **Keep required coverage.** Cost optimization must not remove project-required CI, fail-closed security/privacy tests, migration replay, production gates or Peerivo Global Review.
5. **Avoid repeated advisory reviews.** Codex/Copilot review in private repositories consumes GitHub Actions minutes. Request it on a stabilized candidate HEAD rather than on every intermediate commit.
6. **Use path filters only when ownership is explicit.** A path filter must not make a required gate disappear for changes that can affect its behavior transitively.
7. **Do not fall back to a persistent shared self-hosted runner for untrusted PR code.** Runner isolation is a security boundary; cost pressure must not weaken it.

## Recommended concurrency

```yaml
concurrency:
  group: peerivo-ci-${{ github.repository }}-${{ github.workflow }}-${{ github.event.pull_request.number || github.run_id }}
  cancel-in-progress: ${{ github.event_name == 'pull_request' }}
```

## Recommended triggers

```yaml
on:
  push:
    branches: [main] # replace with the actual default branch
  pull_request:
```

For repositories whose default branch is not `main`, use the actual default branch. Organization workflow templates can use `$default-branch`.

## Expensive-job sequencing

```yaml
jobs:
  check:
    # fast required checks

  integration:
    needs: check
    # DB/browser/container integration

  e2e:
    needs: check
    # expensive E2E
```

This changes scheduling only: every required downstream job still has to succeed before merge.
