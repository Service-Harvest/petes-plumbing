# Phase 10 — GHL Embed Integration

## Purpose
Insert the GHL-hosted functionality (chat widget, lead form, review widget,
GBP embed) into the finished static site. GHL remains the backend for these
specific features — only the embed snippets live in the static site; nothing
else about GHL integrates here.

## From intake, insert:
- Chat widget embed code — sitewide (every page), placed once near the end
  of `<body>` so it doesn't block rendering of surrounding content.
- Free estimate / lead form embed code — the popup widget itself is
  included once per page, sitewide (same footprint as the chat widget), but
  configured as a **click-triggered** popup (`data-trigger-type="click"`,
  `data-trigger-value` set to a shared CSS selector, e.g.
  `.request-estimate-cta`) rather than an always-show popup. Every existing
  "Request a Free Estimate" (or equivalent free-estimate/lead-form) CTA
  button or link across the site — top-of-page hero CTA, mid-page CTA
  banners, and final CTA banners, on every page — gets that shared trigger
  class added, so clicking any of them opens the same popup in place. Keep
  each CTA's existing `href` (e.g. `/contact` or `#free-estimate`) as a
  graceful-degradation fallback destination in case the popup script fails
  to load — don't replace working links with a bare `#`.
- Google review widget embed code (homepage, and optionally category pages)
- Google Business Profile embed code (homepage, in the placeholder already
  present in the Phase 6 draft)

## Technical check on each embed (before accepting it)
- Does it block rendering of the surrounding page content? If so, load it
  async/deferred so it doesn't compromise the "no client-rendered content"
  requirement for everything around it.
- Does it introduce layout shift? If so, reserve space for it in the layout.
- Does it work without breaking the page if it fails to load (graceful
  degradation, since this is now the one piece of the site that depends on
  an external script)?

## Output
Finished pages with all embeds in place, each checked against the above
before being accepted — flag anything that can't be made to comply cleanly
rather than silently shipping something that violates Layer 1 rules (see
`phase-04-repo-scaffold.md` for the full Layer 1 checklist).
