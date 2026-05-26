# BESTE Renovate config

Shared Renovate presets for `beste/` repositories.

## Files

- `renovate.json` — default entrypoint for repos using this config
- `default.json` — base preset for most repos
- `lang-php.json` — PHP-specific overrides

## Behavior

- Daily run at `06:00 UTC`
- Auto-merge minor updates for safe groups
- Dependency Dashboard enabled
- Vulnerability alerts enabled
- Lock file maintenance enabled
- Composer minor/patch grouped
- GitHub Actions minor/patch grouped
- Docs Python tooling minor/patch auto-merged

## Notes

- Major updates need Dependency Dashboard approval
- PHP platform package `php` is disabled in `lang-php.json`
- `renovate.json` can stay tiny; repo-specific overrides belong in child preset
