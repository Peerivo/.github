# Peerivo GitHub Actions optimization audit — 2026-09-27

Purpose: reduce GitHub-hosted Actions consumption without weakening project CI, fail-closed security, migration evidence, production gates or Peerivo Global Review.

## Applied or in flight

| Repository | Change | Status |
| --- | --- | --- |
| `Peerivo/factory` | PR-scoped superseded-run cancellation; unique non-PR concurrency; expensive Docker/PostgreSQL jobs depend on fast `check` | merged via #28 |
| `Peerivo/mercy-platform` | feature branches stop duplicating `push + pull_request`; PR supersession cancellation; Supabase integration waits for fast app gate | PR #103 |
| `Peerivo/happy` | PR supersession cancellation; non-PR runs unique | PR #3 |
| `Peerivo/postbazar` | cancel superseded PR runs only; protect every `master` run with unique non-PR group | PR #30 |
| `Peerivo/.github` | organization baseline + npm lockfile CI template | PR #2 |

## Highest-value remaining duplicate-trigger fixes

These repositories currently run CI on feature-branch pushes and also on pull requests, so the same candidate commit can execute twice.

| Repository | Observed pattern | Safe target |
| --- | --- | --- |
| `Peerivo/flow` | unfiltered `push` + `pull_request` | restrict `push` to default branch; keep PR CI |
| `Peerivo/marketing` | `push: [main, feat/**, fix/**]` + PR CI | restrict generic CI push to `main`; preserve effect-specific workflows separately |
| `Peerivo/publisher` | `push: [main, feat/**, fix/**]` + PR CI | restrict generic CI push to `main`; preserve production migration workflow |

Do not patch these on a second branch while their current security/CI PRs are active.

## Deferred because an open PR already changes the same CI workflow

- `Peerivo/daily` — current CI-changing security PR #9.
- `Peerivo/autocrm` — current CI-changing PR #11.
- `Peerivo/flow` — current CI-changing PR #5.
- `Peerivo/living-menaion` — current CI-changing PR #40.
- `Peerivo/origin` — current CI-changing PR #8.
- `Peerivo/marketing` — current CI-changing PR #28.
- `Peerivo/constitution` — current CI-changing PR #22.
- `Peerivo/publisher` — current CI-changing PR #18.
- `Peerivo/network` — current CI-changing PR #59.
- `Peerivo/ai-ceo` — current CI-changing PR #22.
- `Peerivo/artcompas` — multiple active CI-changing PRs including #17.

After each conflicting PR settles, create a fresh small branch from actual default branch and apply only the still-relevant cost controls.

## Governance / trust-boundary exclusions

- `Peerivo/reviewer`: do not cost-optimize around PR #45 by restoring the persistent shared self-hosted runner. Runner isolation is a security boundary.
- `Peerivo/global`: treat CI changes as governance changes. Review separately; do not bulk-edit with ordinary project CI patches.
- Persistent self-hosted runners must not be used as a cost workaround for contributor-controlled PR code where privileged jobs share the same machine.

## Canonical concurrency rule

Equivalent PR runs may supersede one another. Non-PR runs must be unique.

```yaml
concurrency:
  group: peerivo-ci-${{ github.repository }}-${{ github.workflow }}-${{ github.event.pull_request.number || github.run_id }}
  cancel-in-progress: ${{ github.event_name == 'pull_request' }}
```

Why `github.workflow`: concurrency groups are repository-wide; different required workflows must never cancel each other.

Why `github.run_id` for non-PR events: GitHub retains at most one running and one pending run per shared concurrency group, so using only a branch ref can discard an intermediate default-branch run.

## Fast-gate sequencing

Use `needs: check` (or the project's equivalent fast required gate) before expensive Docker, browser, database or full-stack integration jobs when all of the following are true:

1. the expensive job remains required before merge;
2. the fast gate does not remove required coverage;
3. a fast-gate failure already makes the candidate non-mergeable;
4. the expensive job does not provide evidence required to diagnose the fast gate itself.

## Review-minute discipline

Codex/Copilot review in private repositories consumes GitHub Actions minutes. Do not request advisory review after every intermediate commit. Prefer one review on a stabilized candidate HEAD, then re-request only when findings caused material code changes that need re-review.

This does not affect mandatory Peerivo Global Review or any project-required CI.


## Scheduled workflow optimization candidates

### Reviewer / Global Threat Radar

Current observed topology:

- `Peerivo/reviewer` authoritative Threat Radar worker: scheduled at minute **17** and **47** every hour.
- `Peerivo/global` Threat Radar guard: scheduled at minute **27** every hour and verifies freshness, authoritative completeness and dispatcher health.
- The Global Contract requires hourly active-production dependency scanning; the guard accepts authoritative status up to 90 minutes old.

The worker and guard are complementary, not duplicates. However, the second Reviewer worker run each hour is above the hourly contractual cadence.

**Deferred governance optimization:** after the active Reviewer runner/trust-boundary PR settles, evaluate changing the authoritative worker to one run per hour (for example `:17`) while retaining the Global guard shortly afterwards (for example `:27`). This can approximately halve worker executions while keeping an hourly authoritative scan plus independent fail-closed freshness verification.

Do not apply this as an ordinary bulk CI patch: Reviewer/Global schedule changes are governance/security changes and require their normal exact-HEAD review/approval path.

### Known failing scheduled jobs

Do not keep repeatedly failing scheduled workflows merely because they are historical. A recurring failure consumes minutes without producing useful evidence. Repair or explicitly pause it through the owning project's normal workflow.

Current examples are tracked separately where active project PRs already touch the same workflows; do not create overlapping CI branches.
