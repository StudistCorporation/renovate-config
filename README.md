# renovate-config

Org-wide Renovate inheritance config and shared preset for `StudistCorporation`.

## What this repo does

The Mend-hosted Renovate App auto-discovers `<org>/renovate-config/org-inherited-config.json` and applies it to every Renovate run across the org — no per-repo setup required.

This repo also hosts the shared `default.json5` preset that every onboarded repo extends.

```
       Mend                       this repo                       each repo
  ┌────────────┐            ┌─────────────────────┐         ┌──────────────────────┐
  │            │            │ org-inherited-      │         │                      │
  │  Renovate  │ ──reads──▶ │   config.json       │         │  .github/            │
  │  App       │            │                     │         │    renovate.json5    │
  │  (hosted)  │            │ default.json5       │◀extends─│                      │
  │            │            │  (shared preset)    │         │                      │
  └─────┬──────┘            └─────────────────────┘         └──────────┬───────────┘
        │                                                              ▲
        └──── onboards (opens initial Renovate onboarding PR) ─────────┘
```

When onboarded, each repo's `.github/renovate.json5` is auto-generated with:

```json5
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>StudistCorporation/renovate-config:default.json5"],
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
