# @whtsky/renovate-config

My [shareable config](https://docs.renovatebot.com/config-presets/) for [Renovate](https://renovatebot.com)

## ⚠️ Breaking Change: Migration Required

**As of v1.0.0**, this config has migrated from npm-hosted presets to GitHub-hosted presets.

If you were using:

```json
{
  "extends": ["@whtsky"]
}
```

You **must** update to:

```json
{
  "extends": ["github>whtsky/renovate-config"]
}
```

## Setup

Enable Renovate in your repo and add this to your `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>whtsky/renovate-config"]
}
```

## Available Presets

| Preset                             | Usage                                                            | Description                                                                               |
| ---------------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `default`                          | `github>whtsky/renovate-config`                                  | Full configuration with sensible defaults, semantic commits, and various auto-merge rules |
| `react-apolloMonorepo`             | `github>whtsky/renovate-config:react-apolloMonorepo`             | Groups packages from react-apollo monorepo together                                       |
| `celeryPackages`                   | `github>whtsky/renovate-config:celeryPackages`                   | Groups Python Celery-related packages (celery, amqp, billiard, kombu, vine)               |
| `autoMergeNonMajorDevDependencies` | `github>whtsky/renovate-config:autoMergeNonMajorDevDependencies` | Automerges minor and patch updates for devDependencies                                    |
| `autoMergeLockFileMaintenance`     | `github>whtsky/renovate-config:autoMergeLockFileMaintenance`     | Automerges lock file maintenance PRs                                                      |
| `autoMergeActions`                 | `github>whtsky/renovate-config:autoMergeActions`                 | Automerges GitHub Actions updates                                                         |

## Using Individual Presets

You can use presets individually or combine them:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": [
    "config:recommended",
    "github>whtsky/renovate-config:autoMergeActions",
    "github>whtsky/renovate-config:autoMergeLockFileMaintenance"
  ]
}
```

## What's in the Default Preset?

The default preset includes:

- **Base**: Extends `config:best-practices` (includes security features, merge confidence badges, workarounds)
- **Security**: OSV vulnerability alerts, pinned GitHub Action digests, 3-day npm release age
- **Semantic commits**: Uses `chore(dependencies):` prefix
- **Rebase strategy**: Rebases PRs when behind base branch
- **Rate limiting**: Max 2 PRs per hour, 10 concurrent PRs
- **Range strategy**: Bumps versions (doesn't widen ranges)
- **Separate minor/patch**: Creates separate PRs for minor and patch updates
- **Python support**: Enabled
- **Post-update options**: Runs `go mod tidy` and `npm dedupe`
- **Automerge**: Non-major devDependencies, GitHub Actions, lock file maintenance (branch strategy for speed)

## License

WTFPL
