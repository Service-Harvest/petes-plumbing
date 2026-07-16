# Phase 12 — Build Validation Gate

## Purpose
One combined, reusable script (`/scripts/validate.js`) that checks both
technical/Layer-1 compliance (see `phase-04-repo-scaffold.md` for the full
Layer 1 checklist — this gate covers the subset listed below, not every
item) and content/SEO compliance, and blocks deploy on any failure. This is
the same script for every client — it reads the current client's `/site/`,
`/ledgers/anchor-ledger.md`, and `phase-06-content-drafting.md` (for the
approved outbound-domain list) to know what "correct" looks like for this
specific build. It does not read `/ledgers/architecture.md` directly — the
required per-page structure it needs (which links must exist, which pages
need an outbound link) is already fully captured in the anchor ledger and
the sitemap by the time this runs.

## Technical / Layer 1 checks (hard fail if any are true)
- Broken internal links anywhere on the site
- Orphan pages: zero internal links pointing to them *from body copy*
  (links inside `<nav>`/`<footer>` don't count — Phase 4 Task 9 requires
  those literal elements specifically so this distinction is checkable).
  The four main-nav pages (`/`, `/services`, `/about`, `/contact`) are
  exempt, since they're reachable from the global nav by design.
- Missing or duplicate title tags
- Missing or duplicate meta descriptions
- Missing canonical tag, or a canonical tag that doesn't resolve to
  `https://[domain from /site/CNAME][this page's own sitemap URL]`
- Missing alt text on any image
- Missing explicit width/height on any image
- Missing JSON-LD schema on any page (hard fail, not a warning), and every
  schema block present validates as well-formed JSON-LD
- Every URL in `sitemap.xml` corresponds to a real file in `/site/`, and
  that file's canonical tag matches the sitemap URL exactly (true live
  200-status is confirmed by the deploy workflow's own success/failure —
  this check is the static-file approximation available before deploy)

## Content / SEO checks (hard fail if any are true)
- Any anchor text string used more than once sitewide (checked against
  `/ledgers/anchor-ledger.md`)
- Any `/ledgers/anchor-ledger.md` row (source page → destination page,
  exact anchor text) not found as an actual link in that source page's body
  copy (outside `<nav>`/`<footer>`) — not just present in a card/grid/footer
- A page has FAQPage schema without a `<section id="faq">` present, or has
  a `<section id="faq">` without matching FAQPage schema (see Phase 6's FAQ
  convention and Phase 9's schema rules)
- Any category/service page (any page other than `/`, `/services`, `/about`,
  `/contact`) missing an outbound link to a domain from
  `phase-06-content-drafting.md`'s approved list

## Warnings (non-blocking, reported but don't stop deploy)
- Title tag outside ~50–60 characters
- Meta description outside ~150–160 characters

## Behavior
Run this script before Phase 13 (deploy) — the deploy workflow
(`.github/workflows/deploy.yml`) also runs it automatically as a hard gate
before publishing. If it fails:
- Report exactly which check(s) failed and on which page(s)
- Fix the specific issue(s)
- Re-run the full script — do not deploy on a partial pass

## Output
A clean validation report (all checks passed) is the gate to proceed to
Phase 13. Keep this script in the template repo so every client build (and
every Phase 14 edit, later) runs the same check.
