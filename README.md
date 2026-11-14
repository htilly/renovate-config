# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for my repositories.

Use it from a repo's `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>htilly/renovate-config"]
}
```

## What it does

- **Security fixes** (GitHub/Dependabot alerts and OSV): PR right away, any day. No release-age delay, and merged automatically when all checks pass.
- **Minor/patch updates**: grouped into one PR every Monday morning (Europe/Stockholm), merged automatically when all checks pass.
- **Lock file maintenance**: weekly, so transitive dependencies get their fixes too. Merged automatically when all checks pass.
- **Major updates and 0.x minor bumps**: separate PRs that are never merged automatically. npm `overrides` get no major bumps at all, since they only exist to force patched transitive versions.
- **Supply chain**: new releases must be 3 days old before Renovate proposes them (security fixes are exempt). GitHub Actions are pinned to commit digests.
- **Automerge safety**: `platformAutomerge` is off, so Renovate itself waits for every status check to be green before it merges. That holds even on repos without required status checks.
- A **Dependency Dashboard** issue in each repo lists everything that's pending.

Override anything per repo in that repo's `renovate.json`.
