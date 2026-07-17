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
