# BESTE Renovate config

Shared Renovate presets for `beste/` repositories.

## Files

- `default.json` — base preset for most repos
- `github-actions.json` — GitHub Actions behavior for most repos
- `lang-php.json` — PHP umbrella preset
- `php-composer.json` — Composer behavior for PHP repos
- `php-platform.json` — PHP platform pin/ignore rules
- `renovate.json` — config used by Renovate when running on this repository

## Behavior

- Daily run during the `06:00 UTC` hour
- Auto-merge minor and patch updates for selected ecosystems
- Patch updates wait `1 day`; other updates keep `7 days`
- Release age checks use strict internal filtering
- Dependency Dashboard enabled
- Vulnerability alerts enabled
- Lock file maintenance enabled
- GitHub Actions pinned to immutable commit SHAs with exact SemVer comments
- GitHub Actions digest updates include commit-to-commit comparison links
- GitHub Actions minor/patch grouped and auto-merged
- PHP Composer minor/patch grouped and auto-merged through the PHP preset
- Common Composer virtual implementation packages are ignored to avoid lookup warnings
- Docs Python tooling minor/patch auto-merged

## Usage

Use the default preset for general repositories:

```json
{
  "extends": ["local>beste/renovate-config"]
}
```

Use the PHP umbrella preset for PHP repositories:

```json
{
  "extends": ["local>beste/renovate-config:lang-php"]
}
```

Use only the GitHub Actions behavior when composing a custom preset:

```json
{
  "extends": ["local>beste/renovate-config:github-actions"]
}
```

## Notes

- Major updates need Dependency Dashboard approval
- PHP platform package `php` is disabled in `php-platform.json`
- `default.json` is the exported default preset
- `renovate.json` can stay tiny; repo-specific overrides belong in child presets
