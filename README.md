# renovate-config

Org-wide Renovate inheritance config for `StudistCorporation`.

## What this repo does

The Mend-hosted Renovate App auto-discovers `<org>/renovate-config/org-inherited-config.json` and applies it to every Renovate run across the org — **no per-repo setup required**.

```
┌──────────────────────────────┐
│  Mend-hosted Renovate App    │
└──────────────┬───────────────┘
               │ reads on every run
               ▼
┌──────────────────────────────┐
│ org-inherited-config.json    │  ← this repo
└──────────────┬───────────────┘
               │ controls onboarding PR shape
               ▼
┌──────────────────────────────┐
│  any repo in the org         │
│  → .github/renovate.json5    │
└──────────────────────────────┘
```

## Current config

| Setting | Value | Effect |
| --- | --- | --- |
| `onboardingConfigFileName` | `.github/renovate.json5` | Onboarding PR creates config at `.github/renovate.json5` instead of repo root |
| `onboardingConfig.extends` | `github>StudistCorporation/.github:default.json5` | Onboarding PR pre-extends our shared preset |

## Conventions (Mend-hosted, non-negotiable)

- **Repo name** must be `renovate-config` (cannot be changed)
- **File name** must be `org-inherited-config.json` (cannot be changed)
- Repo does not need to be onboarded
- App must be installed on this repo for it to be read

## Editing

1. Edit `org-inherited-config.json`
2. Commit to default branch
3. Mend picks it up on the next run — no deploy step

The `$schema` reference at the top of the file enables editor validation/completion in VS Code and most modern editors.

## References

- [Mend-hosted Apps Configuration](https://docs.renovatebot.com/mend-hosted/hosted-apps-config/)
- [Renovate Configuration Overview](https://docs.renovatebot.com/config-overview/)
- [Inherited Config Schema](https://docs.renovatebot.com/renovate-inherited-schema.json)
