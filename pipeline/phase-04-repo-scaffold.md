# Phase 4 — Repo Scaffold (Layer 1 Foundation)

## Purpose
Build the technical foundation so every Layer 1 requirement is structurally
guaranteed by the template, not something to remember per page. **"Layer 1"
means, specifically, every item in the Tasks list below** — this is the one
place that checklist is defined. Every other phase that refers to "Layer 1"
(Phase 10, Phase 12) means this exact list.

## Output format
`/site/` contains only final, plain static HTML files — no template
language (Nunjucks, Liquid, JSX, or otherwise), no build step, no
source/output split. Every `.html` file under `/site/` is exactly what
ships to the browser, exactly what `scripts/validate.js` reads, and exactly
what the deploy workflow (Task 14 below) publishes. No client-side
rendering of any page content, and no framework that renders content
client-side (no SPA behavior of any kind).

## Tasks

1. **Folder structure**: `/site/` contains the final site as flat HTML
   files, one directory per clean URL with an `index.html` inside it (e.g.
   the page at `/water-heater-repair-austin-tx` lives at
   `/site/water-heater-repair-austin-tx/index.html`) — this is what makes
   the clean URLs from Phase 3's URL structure actually resolve on GitHub
   Pages without a `.html` extension, and it's what `scripts/validate.js`
   assumes when matching sitemap/canonical URLs to real files. The
   homepage is `/site/index.html`; the 404 page is the one exception and
   lives flat at `/site/404.html` (GitHub Pages requires that exact path).
   A top-level `/snippets/` folder (outside `/site/` — never served,
   never read by `scripts/validate.js`) holds the canonical shared header/
   nav/footer HTML blocks: the authoring reference Claude Code copies
   verbatim into every real page file for sitewide consistency. If a
   sitewide nav/footer change is ever needed (including in Phase 14), update
   `/snippets/` first, then re-propagate the change into every affected page.
2. **robots.txt**: present, correct, and includes a deliberate AI-crawler
   policy (explicit allow/block decision for GPTBot, ClaudeBot, PerplexityBot,
   Google-Extended — a decision, not a default).
3. **llms.txt**: present, summarizing the site for AI crawlers.
4. **Favicon set**: complete (multiple sizes/formats) — the actual assets
   are produced in Phase 4a (Design System), which runs immediately after
   this phase; this scaffold just needs the `<link rel="icon">` etc. tags
   wired into the page template, ready to point at them.
5. **`<html lang="en">`, viewport meta, charset** on every page template.
6. **Open Graph + Twitter card tags** on every page template, populated
   per-page (unique title/description/image per page, not one static OG
   image sitewide) — Phase 4a establishes which image fills that slot per
   page; this scaffold just needs the tags wired to point at it.
7. **Self-referencing canonical tag** on every page, generated from the final
   domain (from intake), never a placeholder/preview domain.
8. **Single canonical hostname**: pick www or non-www, plan the 301 (this may
   be host-level, confirmed again in Phase 13 for GitHub Pages).
9. **HTML5 semantic sectioning**: header, `<nav>`, main, article/section,
   `<footer>` on every page template — use the literal `<nav>` / `<footer>`
   elements (not just visual styling), since `scripts/validate.js` relies on
   these exact tags to tell body-copy links apart from navigation/footer
   links when checking required contextual links.
10. **Real 404 handling**: a custom 404 page that actually returns 404, not a
    soft-200 fallback (verify this works correctly for GitHub Pages
    specifically once deployed in Phase 13).
11. **CNAME file** for the client's custom domain (used by GitHub Pages),
    placed at `/site/CNAME`.
12. **Image handling conventions**: explicit width/height on every `<img>`,
    `loading="lazy"` on below-the-fold images only (never on the LCP image),
    WebP format where practical, descriptive filenames (not generic IDs).
    These conventions get used in Phase 7.
13. **No render-blocking CSS/JS**: inline or minimal CSS, no `@import`,
    `font-display: swap` + preload on webfonts. Phase 4a builds the actual
    CSS on top of this constraint.
14. **Deploy workflow**: confirm `.github/workflows/deploy.yml` (shipped
    with this template — see the repo root) is present and unmodified. This
    is what actually validates and deploys `/site/` in Phase 13, since
    native GitHub Pages branch/folder settings can't serve an arbitrary
    `/site/` folder directly. Do not remove, rename, or hand-edit it per
    client.
15. **Git initialization**: run `git init -b main` (if this directory isn't
    already a git repository — and if it already is, confirm the current
    branch is actually named `main`, since the deploy workflow only triggers
    on pushes to `main`) and create an initial commit of the scaffold
    produced by this phase, so a real commit history exists before Phase 13
    ever tries to push or create the remote repo. Later phases don't need to
    commit as they go — Phase 13 commits and pushes everything accumulated
    since this initial commit.

## Output
A working, empty-of-content but fully wired site skeleton, with a real git
history behind it, ready for Phase 4a to apply the visual design system,
then Phase 5–6 to populate with real pages, and ready for Phase 12 to
validate against.
