# Phase 13 — Deploy + Final Report

## Deploy steps
1. Confirm `scripts/validate.js` has been run locally and passed with zero
   failures. (The deploy workflow re-runs this as a hard gate before
   publishing — see step 3 — but confirm it locally first rather than
   relying on CI to be the first place a failure surfaces.)
2. Confirm `.github/workflows/deploy.yml` is present and unmodified (it
   ships with the template — see Phase 4 Task 14). This is what actually
   publishes the site, since GitHub Pages' native branch/folder settings
   can't serve an arbitrary `/site/` folder directly.
3. Push to the client's GitHub repo, creating it first if needed:
   - All client repos live under the GitHub organization `Service-Harvest`.
   - Check whether the repo already exists remotely under that org, e.g.
     `gh repo view Service-Harvest/[repo-name]`.
   - If it does not exist yet, create it (using the "GitHub repo name" value
     from that client's completed intake file for `[repo-name]`):
     `gh repo create Service-Harvest/[repo-name] --public --source=. --push`
   - If it already exists (e.g. this is a later deploy for the same client,
     not the first one), just commit and push normally instead of trying to
     create it again.
4. Set the repo's Pages source to "GitHub Actions" (a one-time setting per
   repo — skip if already set on a later deploy):
   `gh api repos/Service-Harvest/[repo-name]/pages -X POST -f build_type=workflow`
   Check first with `gh api repos/Service-Harvest/[repo-name]/pages` if
   unsure whether this has already been done; the create call will error
   harmlessly if a Pages site already exists.
5. Confirm the workflow run triggered by the push succeeded — both the
   `validate` job and the `deploy` job (`gh run list`, `gh run view`, or the
   Actions tab). If `validate` fails, `deploy` never runs: fix the specific
   issue(s) it reported, commit, push again, and re-check.
6. Confirm the `CNAME` file (from Phase 4) matches the client's domain
   exactly.
7. Once the site is live (custom domain or the default
   `*.github.io` URL), spot-check real technical SEO/Core Web Vitals with
   the connected DataforSEO MCP tools rather than relying only on the
   static-file checks in Phase 12:
   - `mcp__dataforseo__on_page_lighthouse` on the homepage and at least one
     priority page, for performance/SEO/accessibility scores.
   - `mcp__dataforseo__on_page_instant_pages` on the homepage, to confirm
     the live page renders/crawls as expected (catches anything a static
     file check can't, like a server-level redirect or header issue).
   Report notable scores/issues in the final report below — this is a
   spot-check, not a blocking gate; don't hold up deploy on it, but do flag
   anything that looks clearly wrong (e.g. a failing performance score).
8. Note the DNS records the domain registrar needs (this step happens
   outside the repo — report it clearly rather than attempting it, since it
   requires the domain registrar account, not GitHub).

## Final report to the user
Read the full `/ledgers/build-report.md` and present it to the user in the
final report, alongside everything below.

Report, plainly:
- Total pages built and deployed
- Live GitHub Pages URL (and custom domain URL once DNS is connected)
- Any DNS steps still required on the user's end, spelled out clearly
- Confirmation that the validation gate passed with zero failures
- Any warnings (non-blocking) surfaced during validation, for the user's
  awareness
- The Phase 7 image-substitutions list (if non-empty), so the user knows
  exactly which image slots got an SVG substitution instead of a generated
  image and can decide whether to regenerate them later
- Confirmation that the deploy workflow's IndexNow ping succeeded (check the
  workflow run logs), or a note that it was skipped and why
- The Lighthouse/on-page spot-check results from step 7, and anything
  flagged as worth a closer look
- A short pointer to Phase 14 for any future edits, so the user knows this
  isn't a one-and-done static file — it's an editable repo with a repeatable
  process behind it
