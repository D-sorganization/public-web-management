# public-web-management

Release management for D-sorganization's public web properties — GitHub Pages
sites, public mirrors, and the content release process that keeps them in sync
with their canonical sources.

## What this repo is

- **The registry** of every public-facing web property the org runs
  ([`registry/properties.json`](registry/properties.json), validated against
  [`registry/properties.schema.json`](registry/properties.schema.json) in CI).
- **The release process** for content updates to those properties
  ([`docs/RELEASE_PROCESS.md`](docs/RELEASE_PROCESS.md)).
- **Cross-linking conventions** between affinedrift.com articles and the tool
  sites ([`docs/LINKING.md`](docs/LINKING.md)).
- **Release tracking** — one issue per content release, opened from the
  [release template](.github/ISSUE_TEMPLATE/release.md).

## What this repo is not

- **Not a home for programs.** Application and model code stays in its home
  repo (Tools, UpstreamDrift, AffineDrift, …). Nothing here is deployed.
- **Not an issue tracker for the properties themselves.** Bugs in a tool or
  article belong in the property's `owner_repo` (see the registry). Issues
  here track *releases* — the act of moving content from source to live.

## Map of the public estate

| Property | Kind | Live URL | Canonical source | Deploy |
|---|---|---|---|---|
| AffineDrift website | pages-site | <https://www.affinedrift.com/> | [`AffineDrift`](https://github.com/D-sorganization/AffineDrift) (Quarto site, repo root) | `deploy-website.yml` on merge to `main` |
| Rate of Closure Impact Explorer | pages-mirror | <https://d-sorganization.github.io/rate-of-closure-explorer/> | [`Tools`](https://github.com/D-sorganization/Tools) `src/rate_of_closure/web` (private) | manual sync → [`rate-of-closure-explorer`](https://github.com/D-sorganization/rate-of-closure-explorer) → `deploy-pages.yml` |

Two kinds of property:

- **pages-site** — the public repo *is* the canonical source; merging to its
  `main` deploys it.
- **pages-mirror** — the canonical source lives elsewhere (usually a private
  monorepo); a sync step copies the source into the public mirror repo, and
  the mirror's Pages workflow deploys it.

## Adding a property

1. Add an entry to `registry/properties.json` (CI validates it against the
   schema — every field is required).
2. Add a row to the estate map above.
3. Add a per-property section to `docs/RELEASE_PROCESS.md`.
4. Open the PR; `quality-gate` must pass before merge.
