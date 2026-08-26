# Changelog

## Unreleased

- Add a shared base preset for PR-based, Renovate-managed rebase automerge with required status checks and semantic commits disabled.
- Replace broad minor automerge with explicit Composer, GitHub Actions, and docs Python tooling rules.
- Keep lock-file maintenance automerge explicit.
- Pin GitHub Actions to immutable SHAs with exact SemVer comments and digest comparison links.
- Automerge initial GitHub Action SHA pinning immediately while keeping subsequent digest updates manual.
- Separate initial GitHub Action pinning from other digest-pinning updates.
- Keep vulnerability updates immediate but manual and apply the `security` label correctly.
- Allow normal update branches whenever Renovate runs.
- Use strict seven-day release-age filtering for supported normal updates.
- Add dedicated GitHub Actions and Composer presets.
- Ignore common Composer virtual implementation packages.
- Validate all presets strictly as repository configuration.
- Document complete-preset and custom-composition behavior.
