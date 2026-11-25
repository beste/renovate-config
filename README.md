# BESTE Renovate config

Shared [Renovate](https://docs.renovatebot.com/) presets for general and PHP repositories.

## Usage

General repositories:

```json
{
  "extends": ["github>beste/renovate-config"]
}
```

PHP repositories:

```json
{
  "extends": ["github>beste/renovate-config:lang-php"]
}
```

Custom composition:

```json
{
  "extends": [
    "github>beste/renovate-config:base",
    "github>beste/renovate-config:github-actions"
  ]
}
```

Use `local>` instead of `github>` when extending from the same forge instance.

## Presets

Complete presets:

- `default.json` - general repositories
- `lang-php.json` - PHP repositories

Composable fragments:

- `base.json` - repository-wide automerge and commit policy
- `github-actions.json` - GitHub Actions and workflow tooling
- `npm.json` - npm dependencies
- `php-composer.json` - Composer dependencies
- `php-platform.json` - ignore Composer `php` platform updates

## Notifications

Presets do not set assignees. To assign manual and failed automerge PRs to a maintainer:

```json
{
  "extends": [
    "github>beste/renovate-config",
    ":assignee([USERNAME])"
  ]
}
```
