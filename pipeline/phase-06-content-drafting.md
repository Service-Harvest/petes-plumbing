# Phase 6 — Content Drafting

## Order
Draft premium pages first (homepage + the 3–7 priority pages from Phase 3),
then all remaining category/service pages, then About/Contact.

## Writing principles (every page)
- Friendly local expert voice. Direct, warm, no jargon (explain simply if
  necessary). Short paragraphs, one idea per paragraph. "We" for the business,
  "you" for the customer.
- Target roughly an 8th-grade reading level — genuinely easy to read without
  sounding dumbed-down or patronizing.
- No corporate phrases ("industry-leading," "world-class," "seamless,"
  "robust," "best-in-class," "look no further," etc.)
- No invented facts: no fake review counts, ratings, response times,
  guarantees, awards, years in business, license numbers, or statistics. Only
  what's in the intake or a cited outbound source.
- No keyword stuffing, no scare tactics, no generic "we pride ourselves" filler.
- Don't overuse the business name.

## Required page structure (category/service pages)
1. Hero: H1, subheadline, primary CTA, secondary CTA, trust badges.
2. Table of contents (short descriptive anchor labels).
3. Opening CTA banner.
4. 5 main H2 sections, chosen per service from: signs you need it, causes,
   what to do before calling, process, cost factors, local factors, repair
   vs. replace, prevention, when to call a pro. Pick what fits the specific
   service, but stay consistent within a service *type* across the site: all
   repair-type pages should tend toward the same subset/order (e.g., signs
   you need it → causes → what to do before calling → process → when to call
   a pro), all installation-type pages toward another consistent subset
   (e.g., process → cost factors → local factors → prevention → when to call
   a pro), and so on. This isn't a rigid template — swap in a section a page
   genuinely needs — but two pages of the same service type shouldn't read
   as structured by two different people.
5. Internal links to parent, services hub, relevant children, 2–4 related
   pages — placed inside body copy (paragraphs, bullets, explanatory text),
   never only in cards/grids/menus/footer.
6. One outbound authority link, in-body, from the approved domain list below.
7. Mid-page CTA after the 2nd or 3rd section.
8. 5–6 FAQs, specific to this service/area, not repeated from other pages.
   Wrap the FAQ section in `<section id="faq">` — `scripts/validate.js`
   uses this exact id to confirm visible FAQ content matches FAQPage schema
   (Phase 9) and vice versa.
9. Final CTA.
10. SEO elements: title tag, meta description, H1, H2s, internal links used,
    outbound link used.

Homepage follows the same spirit but with its own structure: hero, why-choose-
us (4 differentiators, drawn from the intake's unique selling points), reviews
placeholder (no invented review data), homepage-linked service/category
cards, local-service section, process section, trust/credentials section,
GBP embed placeholder, 6–8 FAQs (same `<section id="faq">` wrapper
convention as above), final CTA.

## Approved outbound source domains
**Trade-specific (prefer these first when one fits the page's topic):**
iaei.org (electrical), nachi.org (home inspection/general trades), nate.org
(HVAC technician certification), ahrinet.org (HVAC/refrigeration
standards), phccweb.org (plumbing/HVAC — the National Association; phcc.org
resolves to an unrelated Northern Virginia local chapter site, not the
national org, so don't use it), iapmo.org (plumbing codes), angi.com
(only for general contractor-selection guidance, not as a review/ratings
source), nari.org (remodeling), epa.gov/watersense (water efficiency).

**General (use when no trade-specific domain fits):**
epa.gov, energy.gov, energystar.gov, cdc.gov, fema.gov, osha.gov,
consumerreports.org, thisoldhouse.com, familyhandyman.com, nfpa.org,
ashrae.org, nahb.org, buildingscience.com, hud.gov, ftc.gov, usa.gov, nih.gov,
ncbi.nlm.nih.gov, mayoclinic.org, clevelandclinic.org, webmd.com,
healthline.com, cornell.edu, harvard.edu, mit.edu, stanford.edu, berkeley.edu,
psu.edu, umich.edu, wikipedia.org (only if no better authority fits),
bobvila.com, hgtv.com, bhg.com, aia.org, ul.com, asme.org, icc-es.org,
aceee.org, sciencedirect.com, bankrate.com, nerdwallet.com, investopedia.com,
forbes.com, nytimes.com, washingtonpost.com, apnews.com, reuters.com.

## The 6 Golden Rules of Internal Anchor Text (in-body links only)
1. Never repeat anchor text anywhere on the site — check `/ledgers/anchor-
   ledger.md` before finalizing any anchor, and add every new one to it.
2. Incorporate keywords naturally, never stuffed.
3. Anchor text describes the destination page, not the current page.
4. Descriptive yet concise — not a sentence, not "click here."
5. Links live in body content only. Nav/footer/header stay plain and
   functional, and are not subject to this ledger.
6. Never use the brand name as anchor text.

## Content ledger (cross-page redundancy prevention)
Before drafting each page, check `/ledgers/content-ledger.md` for which local
details, angles, and phrasings have already been used on other pages (e.g.,
"mature tree root intrusion" as the lead angle for one page shouldn't become
the lead angle for three more). After drafting, add this page's local
details/angles used to the ledger. The goal: pages that share a general
region and industry can share *facts* (the town has septic systems) without
sharing *angles* or *phrasing* — each page needs its own genuine differentiator,
not just a reworded repeat of the last page's hook.

## Services hub (/services) page structure
Nothing else in this pipeline defines this page's content, even though
Phase 3 requires it and Phase 9 schemas it — this is that definition:
1. H1 (e.g. "Our Services" — not keyword-stuffed).
2. A brief intro paragraph (2–4 sentences) explaining the range of services
   in plain language.
3. One short section per category, priority/homepage-linked categories
   first: a sentence or two of real body copy introducing the category,
   with in-body contextual links to that category's page and to 2–4 of its
   most relevant service pages woven into the prose — per the anchor ledger
   rules, same as every other page. A visual card/grid layer can sit on top
   for scannability, but it doesn't substitute for the body-copy links; this
   page is not exempt from the "links live in body content" rule just
   because it's a hub.
4. One CTA.
5. SEO elements: title tag, meta description, H1 — same as other pages.

## Writing the actual page file
Nothing before this point writes real HTML — this is where each page's file
first gets created. For each page, once its content above is drafted,
combine into a single file:
1. This page's drafted content (headings, body copy, FAQs, CTAs), placed
   into the Phase 4 page template's structure.
2. The shared header/nav/footer markup, copied verbatim from `/snippets/`.
3. A `<link rel="stylesheet" href="/assets/css/main.css">` reference to
   Phase 4a's stylesheet.
4. A placeholder for each image slot this page needs — a `data-slot`
   marker noting what the slot should depict (e.g.
   `<img data-slot="hero: technician repairing a tankless water heater">`),
   with no `src` or `alt` yet. Phase 7 generates the image and writes its
   alt text together, in the same step (alt text describes what was
   actually generated, not a guess made before the image exists), then
   fills in this exact slot.

Write this to `/site/[slug]/index.html` (or `/site/index.html` for the
homepage, `/site/services/index.html` for the hub, etc.), following the
file/directory convention in Phase 4 Task 1. This is a one-time write per
page — it is not regenerated from scratch later. Phase 7 (images), Phase 9
(schema), and Phase 10 (GHL embeds) each *edit* this same file to add their
own piece (filling in `src`/dimensions on the placeholder `<img>` tags,
inserting the JSON-LD `<script>` block in `<head>`, inserting embed
snippets) rather than writing a new file. Phase 11 (technical pass) mostly
works at the site level (`sitemap.xml`, `robots.txt`, `llms.txt`) but may
also edit an individual page file, and only that one, if its canonical
check finds a mismatch to fix.

## Output
Each page's full drafted content, in the same structured output format as the
architecture (title tag, meta description, H1, H2s, body copy, FAQs, CTAs,
internal/outbound links used) — ready for Phase 8 QA. The actual
`/site/[slug]/index.html` file exists by the end of this phase, per above.
