# Cross-linking conventions

Rules for linking between affinedrift.com articles and the public tool sites,
so the estate reads as one connected body of work.

## Directions

- **Article → tool**: every affinedrift.com article that derives, reviews, or
  motivates a model behind a public tool links the tool's live site — once
  prominently near the top ("Try the interactive explorer") and optionally
  again in a closing "Tools" section. Link the *live* `public_url` from the
  registry, never a repo URL, unless the point is the source code.
- **Tool → article**: every tool site links back to the article(s) that
  derive its model — from an "About"/"Derivation" area, not buried in a
  footer. Use the article's canonical URL on `www.affinedrift.com`.
- **Tool → source**: tools may link their public source repo (the mirror repo
  for `pages-mirror` properties — never the private monorepo).

## URL rules

- Always `https://`, always the canonical host: `www.affinedrift.com` (not
  the apex) and `d-sorganization.github.io/<repo>/` (with trailing slash) for
  project Pages.
- No tracking parameters; no URL shorteners.
- Deep-link to article sections with their stable heading anchors rather than
  telling readers to scroll.

## Wording

- Refer to tools by their `display_name` from the registry on first mention.
- Prefer descriptive link text ("the Rate of Closure Impact Explorer") over
  "click here" or bare URLs in prose.

## Maintenance

- A release that adds or renames a page must update inbound links in the same
  release (see RELEASE_PROCESS.md step 5). If a URL must change, keep a
  redirect or stub at the old location.
- CI in this repo link-checks the docs and every `public_url` in the
  registry; broken links fail `quality-gate`.
