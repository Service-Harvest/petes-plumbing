# Local SEO Website Build Pipeline — Template Repo

This is the reusable template for building a client's local SEO website
entirely through Claude Code, with no CMS/hosting dependency beyond
DataforSEO (research) and Gemini (image generation), hosted on GitHub Pages.

## How to start a new client build

1. Duplicate this template into a new repo (named for the client).
2. Copy `/intake/intake-template.md` to `/intake/intake-completed.md` and fill
   it in completely — see `/pipeline/phase-00-intake.md` for what each field
   needs.
3. Open Claude Code in the new repo and point it at `CLAUDE.md`. It will read
   the phase files in order, validate the intake (Phase 0), and run Phases
   1–3, stopping at the Phase 3 checkpoint for your review.
4. Review the proposed GBP + site structure output, correct anything needed,
   and approve.
5. Claude Code runs Phases 4–13 (including Phase 4a, the design system pass
   right after Phase 4) to completion and reports back with a deployed site
   and a final summary.
6. For any edits after launch, use the relevant Phase 14 sub-flow
   (`/pipeline/phase-14-post-launch/`) rather than re-running the full
   pipeline.

## What's reusable vs. per-client

**Reusable across every client (do not edit per-build):**
- `CLAUDE.md`
- `/pipeline/*` (all phase files)
- `/scripts/validate.js`
- `/.github/workflows/deploy.yml` (validates then deploys `/site/` on push)
- Shared header/nav/footer reference markup in `/snippets/` (see Phase 4)

**Per-client (created fresh each build):**
- `/intake/intake-completed.md`
- `/ledgers/*` (architecture, anchor ledger, content ledger, build report)
- `/site/*` (the actual pages — plain final HTML, no build step)

## Prerequisites
- [GitHub CLI](https://cli.github.com/) (`gh`), authenticated, for repo
  creation/pushes and Pages setup in Phase 13.
- Node.js (any reasonably current LTS version), to run
  `node scripts/validate.js` locally in Phase 12/13 — the deploy workflow
  runs it again in CI, but local Node is what lets Claude Code catch a
  failure before ever pushing.

## Open items to resolve before first real client run

- **DataforSEO**: account/API key not yet set up. Until connected, Phase 2
  and Phase 5 fall back to web search and label findings as
  "estimated — not DataforSEO-verified." Set this up once, store the key as
  an environment variable, and every future client build benefits
  automatically.
- **Gemini API**: confirm key is stored as an environment variable / repo
  secret before Phase 7 runs on a real client build.
- **GitHub Pages custom domain**: DNS changes for each client's domain happen
  outside this repo, at the domain registrar, once Phase 13 reports what's
  needed.
