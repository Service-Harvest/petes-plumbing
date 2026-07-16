# Local SEO Website Build Pipeline — Master Instructions

You are building a complete, production-ready local SEO website for a home-service
business, entirely inside this repo, with no external hosting/CMS dependencies
beyond DataforSEO (research) and Gemini (image generation).

This file is the entry point. Read it fully before doing anything else, then work
through the phase files in `/pipeline/` **in numeric order**. Do not skip a phase
or jump ahead. Do not ask the user for approval between phases except at the one
checkpoint explicitly marked below.

## How this repo is organized

```
/intake/intake-completed.md      <- filled-in client intake (input, provided by user)
/pipeline/phase-00-intake.md     <- what the intake must contain, and how to validate it
/pipeline/phase-01-category-audit.md
/pipeline/phase-02-research.md
/pipeline/phase-03-architecture-checkpoint.md   <- THE ONE HUMAN CHECKPOINT
/pipeline/phase-04-repo-scaffold.md
/pipeline/phase-04a-design-system.md
/pipeline/phase-05-per-page-research.md
/pipeline/phase-06-content-drafting.md
/pipeline/phase-07-images.md
/pipeline/phase-08-qa-pass.md
/pipeline/phase-09-schema.md
/pipeline/phase-10-ghl-embeds.md
/pipeline/phase-11-sitemap-technical.md
/pipeline/phase-12-validation-gate.md
/pipeline/phase-13-deploy.md
/pipeline/phase-14-post-launch/14a-single-page-edit.md
/pipeline/phase-14-post-launch/14b-add-new-page.md
/pipeline/phase-14-post-launch/14c-sitewide-fact-update.md

/ledgers/anchor-ledger.md        <- every internal anchor text ever used, generated in Phase 3, updated forever after
/ledgers/content-ledger.md       <- every local detail/angle used per page, generated in Phase 6, updated forever after
/ledgers/architecture.md         <- the approved site architecture from Phase 3 (source of truth for all later phases)
/ledgers/build-report.md         <- connection status and research/QA takeaways, generated in Phase 2, updated forever after

/site/                           <- the actual static site files (final output — plain final HTML, no build step)
/snippets/                       <- shared header/nav/footer reference markup (Phase 4), copied into pages, never served
/.github/workflows/deploy.yml    <- validates then deploys /site/ to GitHub Pages on push (Phase 4/Phase 13)
/scripts/validate.js             <- the Phase 12 build-validation gate, reusable across all clients
```

## Non-negotiable global rules (apply to every phase)

- **No invented facts, ever.** Reviews, ratings, license numbers, years in business,
  pricing, credentials, statistics — only what's in the intake or on the approved
  live content. If something is missing, flag it as a gap, don't fill it in.
- **No client-rendered content.** Output must be plain static HTML with the full
  content present in the initial response — no JS required to see any text, price,
  or CTA. This is the entire reason this pipeline exists (the prior GHL pipeline
  had this problem). Treat any violation of this as a Phase 12 hard failure.
- **Anchor text is never repeated sitewide**, and lives in body copy, not nav/
  footer/headers. See the 6 Golden Rules in `phase-06-content-drafting.md`.
- **Writing voice**: friendly local expert, direct, warm, no jargon, short
  paragraphs, one idea per paragraph, "we"/"you," no corporate-speak, ~8th-grade
  reading level, never patronizing.
- **DataforSEO informs decisions, it does not make them.** Every category/service/
  content decision needs four inputs weighed together: search-volume signal,
  competitive-landscape signal, client-fit signal (from the intake), and
  AI/LLM visibility signal (see `phase-02-research.md`). Never rank-order
  purely by volume.
- **One outbound authoritative link per page**, in-body, from the approved domain
  list in `phase-06-content-drafting.md`.
- **Ledgers are real files, updated as you go, never held only in working memory.**
  Every later phase (including everything in Phase 14, used months after launch)
  depends on these files being current and complete.

## Execution model

1. Confirm `/intake/intake-completed.md` exists and is complete (Phase 0). If
   incomplete, stop and list exactly what's missing — do not guess or proceed.
2. Run Phases 1–3 and produce the Phase 3 checkpoint output. **Stop here and wait
   for explicit human approval.** This is the only planned interruption in the
   entire pipeline.
3. Once approved, run Phases 4–13 to completion without further check-ins
   (this includes Phase 4a, which runs immediately after Phase 4 and before
   Phase 5), reporting only at the end (Phase 13's final report).
4. Phase 14 sub-flows are invoked separately, on demand, long after initial launch.

## A note on session continuity

This build is long-running. If the session is interrupted (computer sleep,
shutdown, crash), files already written to `/site/`, `/ledgers/`, and this repo
are safe — resume by re-reading `/ledgers/architecture.md` and checking which
pages in `/site/` already exist against it, rather than restarting from Phase 1.
