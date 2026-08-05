---
name: Content release
about: Track one content release of a public web property from source to live
title: 'Release: <property> — <what is being released>'
labels: release
---

**Property**: <!-- `name` from registry/properties.json, e.g. rate-of-closure-explorer -->
**Kind**: <!-- pages-site | pages-mirror -->
**Source change**: <!-- link the merged PR(s)/commit(s) in the canonical source repo -->

## Checklist

See [docs/RELEASE_PROCESS.md](../../blob/main/docs/RELEASE_PROCESS.md) for details.

- [ ] **Source merge** — change merged to canonical source `main`; source CI green
- [ ] **Sync / build** — sync procedure run (mirror: sync commit pushed via PR; site: deploy workflow triggered by merge)
- [ ] **Parity / deploy gates** — required checks green on the deploying repo's `main`; parity suite green where applicable (AffineDrift #3777 governance)
- [ ] **Verify live** — change visible at the property's `public_url`; no console errors or asset 404s
- [ ] **Announce / cross-link** — cross-links updated per [docs/LINKING.md](../../blob/main/docs/LINKING.md); release noted here

## Notes

<!-- deploy run links, verification screenshots, anything unusual -->
