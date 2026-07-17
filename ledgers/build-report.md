# Build Report — Pete's Plumbing

> Generated in Phase 2, updated by Phases 5, 7, 8, and read in full by
> Phase 13 for the final report to the user.

## Connection Status
- **DataforSEO**: Initially NOT CONNECTED — `mcp__dataforseo__business_data_business_listings_search` and `mcp__dataforseo__serp_locations` both returned HTTP 401 during the original Phase 1/Phase 2 checks (traced to missing `DATAFORSEO_USERNAME`/`DATAFORSEO_PASSWORD` env vars feeding the MCP server's Basic Auth header). User fixed the config; reconnection confirmed working as of 2026-07-16 — both endpoints now return real data. Phase 1/Phase 2 findings recorded before the fix are labeled "estimated — not DataforSEO-verified" and should be re-verified with live DataforSEO data before final sign-off, since the original research ran on the web-search fallback.
- **Gemini**: Initially NOT CONNECTED — `GEMINI_API_KEY` was unset during Phase 4a (favicon generation), confirmed via a direct test call returning HTTP 403 `PERMISSION_DENIED` ("unregistered caller," i.e. no key presented at all — not an invalid-key or quota error). The Phase 4a favicon used a hand-authored SVG mark (`/site/assets/img/favicon.svg`) as a placeholder fallback as a result. User set `GEMINI_API_KEY` before Phase 7 started; reconnection confirmed working as of 2026-07-16 via a direct test call to `gemini-2.5-flash-image` returning HTTP 200 with real image data. Phase 7 proceeds with real Gemini-generated images. The Phase 4a favicon placeholder remains in place (not retroactively regenerated) since Phase 4a has already completed — noting this in the Phase 13 final report as an optional follow-up if the client wants a Gemini-generated favicon instead of the hand-authored SVG mark.

## Research Takeaways
(Notable findings from Phase 2 and Phase 5 research, per category/page)
- Phase 2 (original pass): All signals estimated via general web search due to DataforSEO 401s at the time.
- Phase 2 (re-run with live DataForSEO, 2026-07-16): Real search volume, SERP, and AI/LLM signals replaced the estimates above. Key findings:
  - **Water Heater Installation**: 27,100/mo (US), low competition, keyword difficulty 8 — confirms this manual override is a strong pick.
  - **Drain Cleaning** ("drain cleaning near me"): 74,000/mo (US), very low competition (0.1) — strongly confirms Drainage Service priority.
  - **Gas Line Repair**: 2,900/mo (US), medium competition, kd 13. Real Armonk-area local-pack results are dominated by general Westchester plumbers (All Pipes Repair, VP's Plumbing, ABS Plumbing), not gas-only specialists — confirms Gasfitter is winnable territory for a full-service plumber. Note: "Gasfitter" itself is a weak/anomalous search term (mixed-language artifact in the data) — the category page should lead with "Gas Line Repair" and "Gas Water Heater Installation" language, not the word "Gasfitter," since that's not how customers actually search.
  - **Emergency Plumber / Emergency Plumber Near Me**: 60,500–90,500/mo (US), very low competition, transactional intent. Real Armonk-local SERP is dominated by general plumbers/drain companies (Reliable Drain Solutions, All Pipes Repair, Armonk Plumbing Services Inc, Roto-Rooter, Mr. Rooter, Bleakley) — winnable, not a specialist-dominated niche. **New recommendation: added Emergency Plumbing Repair as a 5th priority pick** (upgraded from Tier 3 to Tier 1 in architecture.md) — this was underweighted in the original web-search-only pass.
  - **Water Damage Restoration**: real national volume is substantial (135,000/mo) with a low PPC-competition score, but the real Armonk-local organic + local-pack SERP is 100% dominated by certified restoration specialists (Green Restoration, Green Island Group [IICRC-certified], ServiceMaster, UWRG Westchester) — zero general plumbers visible. Confirms the original recommendation: do not build this as a standalone page: high volume alone doesn't override a competitive field this client's intake can't credibly compete in.
  - **Bathroom Remodeling**: 135,000/mo (US), medium competition, kd 38. Real Armonk-local SERP dominated by dedicated remodeling firms (WLD Bathroom Remodeling, Bath Replacers, Raj Kitchen and Bath) — confirms standard (non-priority) page treatment.
  - **AI/LLM visibility** (ChatGPT/gpt-4o, web search on): asked "Who's the best emergency plumber in Armonk, NY?" — response cited 6 competitors, all sourced from Angi's Armonk plumbing directory listing (Mid-Westchester Sewer & Drain, Winners Sewer & Drain, Atomic Rooter, Aldos Plumbing, In Town Plumbing and Heating, NYC Plumbing). None is Pete's Plumbing (expected — pre-launch). Takeaway: getting/maintaining a strong Angi listing matters for AI-answer visibility on emergency-plumbing queries, independent of the site itself.
- Bathroom & Kitchen Remodeling and Septic Services remain real GBP categories with real demand, but both are dominated by specialists offering a broader scope than this client's intake supports — kept as standard pages, not homepage-linked priority.

## Content Quality Notes
(Notable QA findings from Phase 8, per page)
- Homepage, Contact: clean pass, no changes.
- Services Hub: **factual-accuracy fix** — removed an invented company-history claim ("this is where the company started") not supported by intake.
- About: reading-level fix — split two overly long, clause-stacked sentences in the local-experience section.
- Bathroom & Kitchen Remodeling (category): clean pass; scope-honesty disclaimer already solid.
- Bathroom Plumbing Remodeling, Kitchen Plumbing Remodeling: added an explicit "plumbing work only, not tile/cabinetry/design" sentence to each — the category page had this but the child pages only implied it.
- Water Heater Installation, Emergency Plumbing Repair (Tier 1): reading-level fixes — split overloaded/compound sentences given these pages' outsized traffic share.
- Hot Water System Repair, Water Line Replacement, Water Main Repair, Fixture Replacement, Water Softener Installation, Water Filtration System Installation, Slab Leak Repair, Frozen Pipe Repair, Low Water Pressure Repair, Sink Installation: clean pass, no changes.
- Sump Pump Installation: **claims-compliance fix** — removed an unsourced specific pump-lifespan figure ("7-10 years") not supported by intake.
- Bathtub Installation: grammar fix ("a acrylic" → "an acrylic" in an FAQ heading).
- Commercial Plumbing Services, Repiping, Plumbing Inspection, Appliance Hook-Up, Urinal Installation, Rainwater Tank Installation, Water Leak Sensor Installation, Plumbing Maintenance, Backflow Testing: clean pass, no changes.
- Boiler Installation: grammar fix (duplicated word "a a seasonal...").
- Laundry Room Plumbing: grammar fix (dangling modifier in hero subheadline).
- **Cross-cutting observation (not fixed, flagged for awareness)**: several installation-type "process" section openers across the Plumber-batch-B pages use a similar "We start by X. From there, we Y..." construction. Each page passes individually, but noted here in case a future copy refresh wants more variety.
- Drainage Service (category): reading-level fix — simplified a dense sentence about plumbing codes.
- Drain Cleaning, Clogged Drain Repair, Drain Snaking/Rooter Service, Hydro Jetting, Grease Trap Cleaning: clean pass, no changes.
- Sewer Line Repair: reading-level fix — simplified a long InterNACHI-sourced sentence.
- Sewer & Drain Camera Inspection: **fixed a missing required internal link** — the anchor ledger specified a body-copy link to `/drainage-service-armonk-ny` ("additional drain and sewer services") that was only present in breadcrumb/footer, not actual body copy. Added it.
- Gasfitter (category): fixed a broken outbound-citation sentence (treated "codes" as an organization name; now correctly names IAPMO). Confirmed no scope drift — still leads with "gas line repair"/"gas water heater" language over "Gasfitter."
- Gas Line Repair, Gas Water Heater Installation: clean pass, no changes.
- Septic Services (category): fixed a mangled internal-anchor sentence and a duplicated "EPA's EPA" outbound citation. Confirmed no literal duplication of local framing vs. child page.
- Septic Tank Service: fixed a near-verbatim duplicate FAQ answer shared with the category page (same disclosure, reworded for variation). Scope-honesty (plumbing-side-only, not a pumping company) confirmed intact on both septic pages.
- Plumber batch A (Tankless Water Heater Installation through Shower Valve Replacement): QA surfaced a systemic Phase 6 drafting issue — 5 of 12 pages had a fabricated or wrong-domain outbound citation URL (confirmed via live HTTP check, not just domain-name plausibility). Fixed: `leak-detection` (fake NACHI deep link), `pipe-repair` (wrong PHCC domain — archived local chapter vs. real phccweb.org), `burst-pipe-repair` (fabricated date-coded FEMA press-release URL), `outdoor-faucet-repair` (fake This Old House deep link), `shower-installation` (fake NAHB deep link). `garbage-disposal-repair` and `shower-valve-replacement` outbound links were unverifiable (403/bot-blocked even at domain root) and precautionarily downgraded to safe root-domain links.
- **Sitewide outbound-citation sweep** (triggered by the above finding — checked every one of the 39 unique outbound URLs across all 57 pages via live HTTP request, not just domain plausibility): found 7 MORE confirmed-fabricated/broken deep links beyond what the batch-A QA agent already caught, all fixed by replacing with verified-working root-domain URLs:
  - `water-softener-installation`: fake Consumer Reports water-softeners path → consumerreports.org/appliances/
  - `boiler-installation`: fake energy.gov furnaces-and-boilers path → energy.gov root
  - `hot-water-system-repair`: fake energy.gov water-heating path → energy.gov root
  - `grease-trap-cleaning`: fake EPA food-service-facilities path → epa.gov root
  - `urinal-installation`: fake EPA WaterSense toilets/urinals path → epa.gov/watersense (real page)
  - `plumbing-maintenance`: fake This Old House checklist path → thisoldhouse.com/plumbing (real page)
  - `water-leak-sensor-installation`: fake UL "ul-mark" resource path → ul.com root
  - After these fixes, re-verified all 39 outbound URLs: zero 404s remain. Remaining non-200 responses (angi.com, cdc.gov, familyhandyman.com, fema.gov, hgtv.com) are confirmed bot-blocking (403 even at bare domain root, not path-specific), not fabricated links — left as-is since they're legitimate approved domains.
  - Separately, confirmed via live page-content comparison that `phcc.org` (used by 3 pages) actually resolves to an unrelated Northern Virginia local chapter site, not the National Association — the real national org is `phccweb.org`. Updated all 4 PHCC citations sitewide to `phccweb.org` and corrected the approved domain list in `phase-06-content-drafting.md` to prevent this recurring on future edits.

## Phase 9 (Schema) + validator hardening
- Generated JSON-LD schema for all 57 pages via a script (not hand-authored per page, to guarantee sitewide `@id` consistency): LocalBusiness/WebSite on homepage, WebPage/CollectionPage/AboutPage/ContactPage + BreadcrumbList on every page, Service schema on all 53 category/service pages, ItemList on the hub, FAQPage on all 54 pages with visible FAQs. Verified: 0 invalid JSON, 0 prohibited schema types (Review/Product/Article), breadcrumb chains match the approved architecture and each page's actual visible breadcrumb.
- Caught and fixed a real bug in my own schema-generation script during this process: the meta-description regex stopped at the first apostrophe (mistaking a contraction like "home's" for a closing quote), truncating descriptions mid-word. Fixed and regenerated cleanly.
- **Found and fixed 3 real bugs in `scripts/validate.js` itself** (the reusable, cross-client validation gate) while running it as an early sanity check:
  1. The ledger-internal duplicate-anchor check used a raw substring search instead of comparing exact table-cell values, causing false-positive failures whenever one legitimate anchor text happened to contain a different, shorter legitimate anchor as a substring (e.g. "everything else we handle" vs. "everything else we handle for Armonk plumbing"). Fixed to compare exact parsed values.
  2. The markdown-table parser didn't strip the backticks used to format file paths as inline code (e.g. `` `/some-page` ``), so essentially every ledger-row lookup against real page content was silently failing — meaning the "every required link actually exists in body copy" check had never actually verified anything all build. Fixed, then found (and fixed) 2 real missing/mismatched required links this surfaced: `tankless-water-heater-installation` and `plumbing-maintenance` had the right links but slightly different wording (an added word, a capitalization difference) than the ledger recorded — reconciled the ledger to match the actual (correct, natural-reading) page text in both cases.
  3. A trailing-slash mismatch between how page URLs were stored (`/page-slug/`) vs. looked up (`/page-slug`, normalized) meant the same required-link check silently skipped every non-homepage page. Fixed by normalizing consistently at both write and read.
  4. Added a legitimate exemption: CTA buttons (`class="btn"`) intentionally repeat the same label sitewide ("Request a Free Estimate") as a UI/UX convention, not as SEO anchor text — updated the validator to treat them like nav/footer (structural, exempt from the anchor-uniqueness rule) rather than failing the whole site on this by design.
- **Fixed a real, sitewide structural bug found via browser inspection**: the header's site-nav `<ul>` never got its CSS applied (`.site-nav ul` selector targeted a nonexistent wrapper — the class is on the `<ul>` itself), so the nav rendered as a bulleted list on all 57 pages. Also moved the header's logo link inside the `<nav>` element (was a `<div>`) so it's correctly treated as navigation rather than a body-copy anchor repeating "Pete's Plumbing" as anchor text on every page.
- Fixed 3 real orphan pages (no incoming body-copy links): added one natural contextual link into each of Boiler Installation, Laundry Room Plumbing, and Rainwater Tank Installation from a genuinely related page.

## Phase 10 (GHL Embeds)
- **Chat widget**: inserted sitewide (all 57 pages + 404.html), placed just before `</body>` so it doesn't block rendering of page content. Verified in-browser: renders as a floating chat bubble, no layout shift to surrounding content.
- **Free estimate form**: **scope decision** — the client's embed code is configured `data-trigger-type="alwaysShow"` / `data-activation-type="alwaysActivated"`, which (confirmed via live browser test) makes it auto-open as a full-page modal popup immediately on load, not a passive inline form. Placing this on all 53 category/service pages as Phase 10's generic guidance suggests would mean every single page auto-pops a modal on load — a significant, unrequested UX change our CTA design (a plain link to `/contact`) never called for. Placed it **only on the Contact page**, replacing its placeholder, where a user arriving already has stated intent to request an estimate. Added a `<noscript>` fallback (phone/email) since the form itself can't render without JS. Flagging this for the client: if sitewide auto-popup is actually wanted, that's a one-line change (copy the same embed block into the other 52 pages), but it wasn't assumed by default given the intrusiveness.
- **Google review widget, GBP embed**: left as placeholders on the homepage, per explicit intake instruction ("leave as placeholders").

## Phase 11 (Sitemap + Technical Pass)
- Generated `sitemap.xml` with all 57 pages, `<lastmod>2026-07-17</lastmod>` (initial launch date).
- Generated a persistent 64-char hex IndexNow key at `site/indexnow-key.txt` — reuse this exact key on any future Phase 14 edit, never regenerate it.
- Expanded `llms.txt` with the complete 53-page listing grouped by category (was previously just the 4 core nav pages, per Phase 4's note that this would happen once all pages existed).
- Confirmed robots.txt/CNAME/sitemap domain all consistently reference `hexorasystems.com`.
- Re-ran `scripts/validate.js` with the sitemap now present: all sitemap-cross-check rules pass (every sitemap URL is a real page with a matching canonical, every real page is listed in the sitemap).

## Phase 12 (Validation Gate)
Final gate run: **0 hard failures, 86 non-blocking warnings** (all title/meta-description length guidance — every title/meta was pre-approved in the Phase 3 architecture checkpoint, so these are accepted as-is rather than rewritten purely to hit a character-count target). Clean to proceed to deploy.

## Phase 13 (Deploy)
- Created `Service-Harvest/petes-plumbing` on GitHub (public), pushed, set Pages source to GitHub Actions build.
- Deploy workflow run succeeded: both `validate` and `deploy` jobs green. IndexNow ping returned HTTP 202 (accepted).
- **Live URL**: https://service-harvest.github.io/petes-plumbing/ — confirmed reachable (200) and serving the real site.
- **Domain note**: the `CNAME` file references `hexorasystems.com` per intake ("for testing purposes"). That domain is a real, unrelated business's live site (Hexora Systems, IT consulting) — DNS was never pointed at this deployment, and GitHub's Pages API confirms no custom domain is actually verified/active (`cname: null`). The site is only genuinely live at the GitHub Pages URL above. A real client launch needs an actual domain the client owns, with DNS pointed at GitHub Pages, before the custom-domain step applies.
- Lighthouse spot-check (homepage + Drain Cleaning, a Tier-1 page): SEO 100/100 on both, Accessibility 95, Performance 87-88, Best Practices 73 (likely dragged down by the third-party GHL scripts, outside this build's control). Cumulative Layout Shift 0.24-0.27 — above Google's "good" threshold (0.1), worth a closer look in a future pass (candidate causes: image dimensions vs. rendered size, or the chat widget injecting late). on_page_instant_pages on the homepage: onpage_score 97.44, single clean H1, well-structured H2/H3 hierarchy, canonical/OG/Twitter tags all correct, 200 status, gzip-compressed, cacheable.

## Image Notes
(Generated vs. substituted images, from Phase 7)
- Gemini confirmed working as of 2026-07-16 (see Connection Status above). Generation batches completed so far, all succeeding on first attempt with zero SVG substitutions:
  - Homepage, Services Hub, About, Contact — 7 images
  - Gasfitter, Gas Line Repair, Gas Water Heater Installation, Septic Services, Septic Tank Service — 12 images
  - Bathroom & Kitchen Remodeling (+2 children), Water Heater Installation, Emergency Plumbing Repair — 11 images
  - Plumber service batch B (Hot Water System Repair through Sink Installation, 12 pages) — 24 images
  - Drainage Service (+7 children) — 18 images
  - Plumber service batch C (Boiler Installation through Backflow Testing, 11 pages) — 22 images (required one resume after an initial stalled status; verified all 11 pages have real images on disk before logging)
  - Plumber service batch A (Tankless Water Heater Installation through Shower Valve Replacement, 12 pages) — 24 images
  - **Final tally: 119 images across all 57 pages, zero permanent failures, zero SVG substitutions needed.** Verified sitewide: every page has exactly one hero/OG image, every `<img>` tag has alt/width/height, every `src` resolves to a real file on disk, no leftover temp files in `site/assets/img/`.
