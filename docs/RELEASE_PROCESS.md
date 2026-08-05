# Release process

One content release = one tracked pass of: **source merge → sync/build →
gates → verify live → announce/cross-link**. Open a release issue from the
[release template](../.github/ISSUE_TEMPLATE/release.md) before starting and
check items off as you go.

Programs are never released from this repo — a "release" here means moving
already-merged content from its canonical source to the live public site.

## General checklist (all properties)

1. **Source merge** — the content change is merged to `main` of the canonical
   source repo (see `registry/properties.json` → `source`). Its CI is green.
2. **Sync / build** — run the property's `sync_procedure`. For `pages-site`
   properties this is automatic on merge; for `pages-mirror` properties it is
   a manual sync commit in the mirror repo.
3. **Parity / deploy gates** — all required checks pass on the deploying
   repo's `main` (mirror repos: the sync commit's CI; site repos: the deploy
   workflow run). For mirrored tools with dual implementations, the parity
   suite (TS pinned test-for-test against Python) must be green in the source
   repo before syncing — see the parity governance epic,
   [AffineDrift #3777](https://github.com/D-sorganization/AffineDrift/issues/3777).
4. **Verify live** — load the `public_url`, hard-refresh, and confirm the
   released change is visible. Spot-check the browser console for errors and
   that no asset 404s.
5. **Announce / cross-link** — add or update cross-links per
   [LINKING.md](LINKING.md) (article ↔ tool), note the release in the tracking
   issue, and close it.

## Per-property notes

### affinedrift-website (pages-site)

- **Source merge**: PR into `D-sorganization/AffineDrift` `main`.
- **Sync/build**: none — `deploy-website.yml` builds the Quarto site and
  deploys Pages on merge.
- **Gates**: AffineDrift CI (`ci-standard.yml`, `spec-check.yml`,
  `link-checker.yml`) plus the deploy workflow run itself.
- **Verify**: <https://www.affinedrift.com/> — check the changed article
  renders, nav/TOC intact, and the apex redirect (affinedrift.com → www)
  still works.
- **Cross-link**: new articles that discuss a tool must link its live site;
  see LINKING.md.

### rate-of-closure-explorer (pages-mirror)

- **Source merge**: PR into `D-sorganization/Tools` `main` touching
  `src/rate_of_closure/web`. Python↔TS parity tests green (per #3777
  governance).
- **Sync**: in a `rate-of-closure-explorer` checkout, run
  `./scripts/sync-from-tools.ps1 -ToolsPath <Tools checkout>`, review
  `git status`, commit (`chore: sync from Tools @<short-sha>`), push via PR.
- **Gates**: mirror repo CI + `deploy-pages.yml` run.
- **Verify**: <https://d-sorganization.github.io/rate-of-closure-explorer/> —
  exercise the changed feature, confirm the derivation panel and canvas load.
- **Cross-link**: update the corresponding affinedrift.com article if the
  tool's behavior or UI changed materially.
