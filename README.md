# renovate-config

Org-wide Renovate inheritance config for `StudistCorporation`.

## What this repo does

The Mend-hosted Renovate App auto-discovers `<org>/renovate-config/org-inherited-config.json` and applies it to every Renovate run across the org — no per-repo setup required.

The shared `default.json5` preset that every onboarded repo extends is hosted in `StudistCorporation/.github`.

```
       Mend                       this repo                    .github repo                each repo
  ┌────────────┐            ┌─────────────────────┐      ┌──────────────────┐        ┌──────────────────────┐
  │            │            │                     │      │                  │        │                      │
  │  Renovate  │ ──reads──▶ │ org-inherited-      │      │ default.json5    │◀extends│  .github/            │
  │  App       │            │   config.json       │      │  (shared preset) │        │    renovate.json5    │
  │  (hosted)  │            │                     │      │                  │        │                      │
  └─────┬──────┘            └─────────────────────┘      └──────────────────┘        └──────────┬───────────┘
        │                                                                                       ▲
        └──── onboards (opens initial Renovate onboarding PR) ──────────────────────────────────┘
```

When onboarded, each repo's `.github/renovate.json5` is auto-generated with:

```json5
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>StudistCorporation/.github:default.json5"],
}
```

Changes to `default.json5` are picked up on the next Renovate run on each repo (no per-repo action required).

## Conventions (Mend-hosted, non-negotiable)

- Repo name must be `renovate-config`
- File name must be `org-inherited-config.json`
- This repo does not need a Renovate onboarding PR
- The Renovate App must still be installed on this repo (otherwise Mend cannot read it)

## References

- [Mend-hosted Apps Configuration](https://docs.renovatebot.com/mend-hosted/hosted-apps-config/)
- [Renovate Configuration Overview](https://docs.renovatebot.com/config-overview/)
- [Inherited Config Schema](https://docs.renovatebot.com/renovate-inherited-schema.json)
- [`config:best-practices` preset](https://docs.renovatebot.com/presets-config/#configbest-practices)
