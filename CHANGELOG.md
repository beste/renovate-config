# Changelog

## Unreleased

- Pin the Renovate validator used by CI.
- Stop persisting checkout credentials during validation.
- Analyze GitHub Actions workflows with actionlint and zizmor.
- Add the MIT license.
- Group npm updates separately from other ecosystems.
- Separate GitHub Action and reusable workflow updates from workflow runtime and tool updates.
- Run routine updates weekly.
- Remove the hourly PR limit so weekly runs can process the available batch.
- Stop forcing manual update PRs to rebase after every base-branch change.
- Add a shared base preset for PR-based, platform-managed rebase automerge with required status checks and semantic commits disabled.
- Replace broad minor automerge with explicit Composer, GitHub Actions, and npm rules.
- Require manual merge for pre-`1.0` minor updates.
- Disable lock-file maintenance in the default preset.
- Disable routine updates for `tools/**` in the PHP preset while keeping vulnerability alerts active.
- Pin GitHub Actions to immutable SHAs with exact SemVer comments and digest comparison links.
- Automerge initial GitHub Action SHA pinning immediately while keeping subsequent digest updates manual.
- Separate initial GitHub Action pinning from other digest-pinning updates.
- Scope `rangeStrategy: "widen"` to root Composer manifests and replace workflow runtime and tool versions.
- Support `--locked` flags in the Cargo workflow custom manager.
- Resolve internal presets relative to their repository and release tag.
- Keep vulnerability updates immediate but manual, add the `security 🔒` label alongside `dependencies 📦`, and drop the `[SECURITY]` commit/PR title suffix.
- Allow normal update branches whenever Renovate runs.
- Use strict seven-day release-age filtering for supported normal updates.
- Add dedicated GitHub Actions and Composer presets.
- Ignore common Composer virtual implementation packages.
- Validate all presets strictly as repository configuration.
