# Phase 4a — Design System

## Purpose
Nothing before this phase turns the intake's Aesthetic Direction into an
actual look — Phase 4 builds the technical skeleton, Phase 5 onward builds
content. This phase closes that gap: it produces the site's real CSS/
layout, favicon set, and Open Graph image convention, so pages already look
like the client's brand by the time content gets written into them.

Runs once per client, immediately after Phase 4, before Phase 5.

## Task 1 — CSS / layout system
1. Read the intake's Aesthetic Direction section (overall feel, brand
   colors/fonts/logo file, reference sites liked/disliked).
2. Produce a small, consistent design system: color palette (derived from
   the brand colors, with sufficient contrast for body text — WCAG AA
   minimum), typography (heading/body font pairing and a sizing scale),
   spacing/layout grid, and button/CTA/card/section styling used across
   every page template.
3. Implement this as a single stylesheet at `/site/assets/css/main.css`,
   linked identically from every page's `<head>` (a plain `<link
   rel="stylesheet">` reference — no build step needed to share one static
   file across many pages). Never page-specific inline styling that would
   have to be maintained separately per page. Keep the nav/footer markup in
   `/snippets/` (Task 1's structure) and this stylesheet's classes in sync.
4. Keep it render-blocking-free per Phase 4 Task 13: inline critical CSS or
   a single minimal stylesheet, no heavy framework, no `@import` chains.
5. If "liked" reference sites were listed in intake, use them for
   directional inspiration only (layout rhythm, tone, spacing) — never copy
   their actual content, code, or distinctive visual identity.

## Task 2 — Favicon set
1. If a logo file was provided in intake, derive the favicon set from it:
   export the standard sizes/formats (16×16, 32×32, 180×180 apple-touch-icon,
   plus a web app manifest icon set if applicable).
2. If no logo file was provided, generate a simple, brand-appropriate icon
   via Gemini (e.g., a monogram or simple mark using the palette from Task
   1) instead. Flag this in the Phase 13 final report as a placeholder — a
   generated favicon is not a substitute for the client's real brand mark,
   and the client should replace it once a logo exists.
3. Place the complete set where the Phase 4 template's `<link rel="icon">`
   tags already point.

## Task 3 — Open Graph image convention
1. Establish, per page type (homepage, category, service, about, contact),
   which image slot serves as that page's Open Graph/Twitter card image.
   Default convention: each page's designated LCP/hero image doubles as its
   OG image, sized/cropped to 1200×630.
2. Record this convention (a short note is enough — it doesn't need its own
   ledger) so that Phase 7 generates/sizes that specific image slot with OG
   usage in mind on every page, and Phase 4's OG tags have a real image to
   point to once Phase 7 runs.

## Output
A working CSS/layout system applied across every Phase 4 template partial,
a complete favicon set in place, and a documented OG-image convention —
ready for Phase 5 research and Phase 6 content to be dropped into a site
that already looks and feels like the client's brand.
