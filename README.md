# BESTE Renovate config

Shared Renovate presets for general and PHP repositories.

The configuration files define behavior. This README covers preset selection and summarizes the effective update policy.

## Presets

- `base.json` - repository-wide policy
- `default.json` - complete default preset
- `github-actions.json` - GitHub Actions policy
- `lang-php.json` - complete PHP preset
- `php-composer.json` - Composer policy
- `php-platform.json` - ignores updates to the Composer `php` platform dependency
- `renovate.json` - this repository's Renovate configuration

`base.json` and the manager presets are composable fragments. Use `default.json` or `lang-php.json` for a complete configuration.

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

Strict filtering blocks releases without a usable timestamp. Renovate cannot apply the seven-day age gate to every update type or datasource; the table lists the relevant exceptions.

Minor and patch automerge includes pre-`1.0` dependencies. No rule excludes `0.x` releases.

## Usage

For general repositories:

```json
{
  "extends": ["github>beste/renovate-config"]
}
```

For PHP repositories:

```json
{
  "extends": ["github>beste/renovate-config:lang-php"]
}
```

For a custom configuration, start with the base and add the required manager fragments:

```json
{
  "extends": [
    "github>beste/renovate-config:base",
    "github>beste/renovate-config:github-actions"
  ]
}
```

The examples use `github>` because this repository is hosted on GitHub.com. Use `local>` for a mirror hosted on the same forge instance as the target repository.

Manager fragments do not include the seven-day release age, Dependency Dashboard, vulnerability alerts, or lock-file maintenance. Add those settings separately.
