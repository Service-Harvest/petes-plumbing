# Phase 10 — GHL Embed Integration

## Purpose
Insert the GHL-hosted functionality (chat widget, lead form, review widget,
GBP embed) into the finished static site. GHL remains the backend for these
specific features — only the embed snippets live in the static site; nothing
else about GHL integrates here.

## From intake, insert:
- Chat widget embed code (typically homepage + relevant service pages, or
  sitewide if the snippet is designed for that — confirm placement makes
  sense for a static, non-GHL-rendered page)
- Free estimate / lead form embed code (homepage + every category/service
  page, wherever a CTA currently points to a form)
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
