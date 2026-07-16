# Build Report — Pete's Plumbing

> Generated in Phase 2, updated by Phases 5, 7, 8, and read in full by
> Phase 13 for the final report to the user.

## Connection Status
- **DataforSEO**: Initially NOT CONNECTED — `mcp__dataforseo__business_data_business_listings_search` and `mcp__dataforseo__serp_locations` both returned HTTP 401 during the original Phase 1/Phase 2 checks (traced to missing `DATAFORSEO_USERNAME`/`DATAFORSEO_PASSWORD` env vars feeding the MCP server's Basic Auth header). User fixed the config; reconnection confirmed working as of 2026-07-16 — both endpoints now return real data. Phase 1/Phase 2 findings recorded before the fix are labeled "estimated — not DataforSEO-verified" and should be re-verified with live DataforSEO data before final sign-off, since the original research ran on the web-search fallback.
- **Gemini**: not yet used (first call happens in Phase 7).

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

## Image Notes
(Generated vs. substituted images, from Phase 7)
