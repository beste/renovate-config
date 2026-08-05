# BESTE Renovate config

Shared Renovate presets for `beste/` repositories.

## Presets

- `base.json` — repository-wide PR, merge, status-check, and commit-message policy
- `default.json` — general schedule, release age, dashboard, vulnerability, lock-file, Docker, documentation, and GitHub Actions behavior
- `github-actions.json` — GitHub Actions SHA pinning, grouping, and targeted automerge rules
- `lang-php.json` — complete PHP preset combining `default`, `php-composer`, and `php-platform`
- `php-composer.json` — Composer grouping and targeted automerge rules
- `php-platform.json` — disables updates to the Composer `php` platform dependency
- `renovate.json` — configuration used by Renovate for this repository

`base.json` and the manager presets are composable fragments. Use `default.json` or `lang-php.json` when the complete repository policy is wanted.

## Repository-wide policy

The complete presets use the following behavior:

- Create pull requests before automerging
- Let Renovate perform the merge instead of GitHub platform-native auto-merge
- Rebase-merge automerge-enabled pull requests
- Require all status checks to pass before automerging
- Disable semantic prefixes for commit messages and pull-request titles
- Rebase pull requests whenever they fall behind their base branch
- Create normal update branches during the `06:00`–`06:59 UTC` window
- Limit creation to two pull requests per hour and ten concurrent pull requests

The schedule controls when Renovate may create branches; it does not guarantee that the hosted Renovate app runs at a particular minute.

## Update policy

| Category | Release age | Merge policy |
| --- | --- | --- |
| Composer minor and patch | 7 days | Automerge after checks |
| GitHub Actions minor and patch | 7 days | Group and automerge after checks |
| Docs Python tooling minor and patch | 7 days | Automerge after checks |
| Lock-file maintenance | Not supported by Renovate | Run daily before `04:00 UTC` and automerge after checks |
| Initial GitHub Action SHA pinning | Immediate | Group separately and automerge after checks |
| Major updates | 7 days when supported | Require Dependency Dashboard approval and manual merge |
| Digest updates | 7 days when supported | Manual merge |
| Other `pinDigest` updates | 7 days when supported | Manual merge |
| Ordinary version pinning | Not supported by Renovate | Manual merge |
| Vulnerability updates | Immediate | Manual merge |
| All other updates | 7 days when supported | Manual merge |

The seven-day age gate uses strict filtering. Releases without a usable timestamp are not considered old enough. Some update types and datasources cannot enforce release age; the table calls out the important exceptions.

Minor and patch automerge includes pre-`1.0` dependencies. There is no special `0.x` exclusion.

## Security and dependency details

- The Dependency Dashboard is enabled and includes the OSV vulnerability summary.
- GitHub vulnerability alerts and experimental OSV vulnerability alerts are enabled.
- Vulnerability pull requests bypass the normal schedule, rate limits, approval requirement, and release-age gate. They receive the `security` label and remain manual.
- Docker references are pinned to digests where supported.
- GitHub Actions are pinned to immutable commit SHAs while retaining exact SemVer comments.
- Subsequent GitHub Action digest updates include commit-to-commit comparison links and remain manual.
- Global dependency ranges use the `widen` strategy; vulnerability fixes use `bump`.
- Common Composer virtual implementation packages are ignored to avoid lookup warnings.
- The Composer `php` platform dependency is ignored by the PHP preset.

## Usage

Use the complete default preset for general repositories:

```json
{
  "extends": ["local>beste/renovate-config"]
}
```

Use the complete PHP preset for PHP repositories:

```json
{
  "extends": ["local>beste/renovate-config:lang-php"]
}
```

For a custom configuration, begin with the repository-wide base and add only the required manager fragments:

```json
{
  "extends": [
    "local>beste/renovate-config:base",
    "local>beste/renovate-config:github-actions"
  ]
}
```

Manager fragments do not enable the complete default schedule, seven-day release age, Dependency Dashboard, vulnerability alerts, or lock-file maintenance. Add those settings explicitly when constructing a custom policy.
