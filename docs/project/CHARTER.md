# Project Charter

> Drafted 2026-09-25 by the fleet charter sweep (Gemini) from README, git history, and open issues/PRs.
> The project-steward role keeps this current; owners should correct feature statuses.

## End Goal

Manage the catalog and content release workflow for all of D-sorganization's public web properties (GitHub Pages sites and public mirrors) to ensure public-facing sites stay reliably synchronized with their canonical source repositories. "Done" means all current and planned properties are registered in `registry/properties.json` with active schema validation in CI, release processes and cross-linking rules are documented, and release issues govern mirror updates without housing deployed application code directly.

## Non-Goals

- Hosting application or model source code (code remains in canonical repositories such as Tools, UpstreamDrift, and AffineDrift).
- Serving as an issue tracker for property bugs or content errors (defects belong in the property owner repository).
- Direct automated deployment execution or hosting build artifacts within this repository.

## Features

| ID | Feature | Status | Tracking | Notes |
| --- | --- | --- | --- | --- |
| F1 | Public web property registry | shipped | - | Central inventory of public web properties in registry/properties.json |
| F2 | Property schema and CI quality gate | shipped | #1 | Validation of property schema and link extraction in CI workflows |
| F3 | Content release process documentation | shipped | - | Standard operating procedures for deploying pages-sites and mirrors |
| F4 | Cross-linking conventions | shipped | - | Standards for cross-linking articles and interactive tools |
| F5 | Release issue tracking template | shipped | - | Issue template standardizing release sign-offs and execution |
| F6 | AffineDrift website property management | shipped | - | Tracking and deployment verification for primary Quarto site |
| F7 | Rate of Closure Explorer mirror resync | planned | #4 | Resyncing public mirror repository from private Tools web directory |
| F8 | Canonical development logging | shipped | #8 | Development history log under docs/development |
| F9 | Fleet agent standards synchronization | shipped | #18 | Centralized AGENTS.md rules synced from Repository_Management |

## Links

- Status (generated): [`STATUS.md`](STATUS.md)
- Steward playbook: Repository_Management `docs/fleet-project-steward.md`
