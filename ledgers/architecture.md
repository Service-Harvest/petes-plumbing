# Site Architecture — Pete's Plumbing (Armonk, NY)

> Generated in Phase 3. Permanent source of truth for every later phase.
> Do not regenerate from scratch on a later edit — only append/update.
>
> **APPROVED** by client 2026-07-16, including the 5-priority-pick revision
> (added Emergency Plumbing Repair) and the confirmed drop of Water Damage
> Restoration Service as a standalone page.

## Global conventions
- City/state used in all local URLs and titles: Armonk, NY
- URL pattern (category/service pages): `/[slug]-armonk-ny`
- Standard pages: `/`, `/services`, `/about`, `/contact`
- Nav bar: Home, Services, About, Contact — no dropdowns, no service links in nav. One CTA button in header ("Call Now", tel:+18555975391).
- Footer: main nav + all 4 secondary category pages + contact details + service areas (Armonk, Pleasantville, Mount Kisco, Yonkers, Bedford, Scarsdale, Greenwich). Footer links are plain/functional, not governed by the anchor ledger.
- No location/service-area pages in this initial build.
- "Water Damage Restoration Service" (a raw client category) is confirmed dropped as a standalone page — no unique service supports it, and it competes against certified restoration specialists on claims this client can't back. Not included in the page counts below.

## Content priority tiers
- **Tier 1 (Premium / homepage-linked):** Homepage, Drainage Service (category), Drain Cleaning, Gasfitter (category), Gas Line Repair, Water Heater Installation, Emergency Plumbing Repair (added after live DataForSEO data — see build-report.md Research Takeaways)
- **Tier 2 (Standard category/utility pages):** Septic Services, Bathroom & Kitchen Remodeling, Services Hub, About, Contact
- **Tier 3 (Standard service pages):** all other 45 individual service pages

## Design system (Phase 4a)
- Stylesheet: `/site/assets/css/main.css` (single file, no build step, no
  `@import` chains, system font stack — no webfont network requests).
- Palette (derived independently — no brand colors were provided): primary
  deep blue `#14497D` (header/buttons/links), accent rust-orange `#B3410C`
  (secondary CTA), slate text `#1F2937`, light section stripe `#F5F7FA`.
- Favicon: `/site/assets/img/favicon.svg` — hand-authored SVG mark (droplet
  + wrench), used in place of a Gemini-generated PNG set. Both Gemini
  (`GEMINI_API_KEY` unset) and local raster tools were unavailable when this
  ran. Flagged as a placeholder for the client to replace with a real logo.
- OG/Twitter image convention: each page's designated LCP/hero image slot
  doubles as its Open Graph/Twitter card image, sized 1200×630. Phase 7 fills
  this slot per page; until then, OG image tags reference a per-page path
  under `/assets/img/` that Phase 7 will create.

## Schema types by page type
- Homepage: `LocalBusiness` (Plumber subtype) + `WebSite` + `BreadcrumbList`
- Category pages: `Service` + `BreadcrumbList` + `FAQPage` (FAQ content added Phase 6, schema wired Phase 9)
- Service pages: `Service` + `BreadcrumbList` + `FAQPage` (same note)
- Services Hub: `CollectionPage` + `BreadcrumbList`
- About: `AboutPage` + `BreadcrumbList` (references LocalBusiness entity)
- Contact: `ContactPage` + `BreadcrumbList` (references LocalBusiness entity)

---

## Homepage

| Field | Value |
|---|---|
| URL | `/` |
| Title tag | Plumber in Armonk, NY \| Pete's Plumbing |
| Meta description | Licensed, insured plumber serving Armonk and Westchester County. Same-day and emergency service, upfront pricing, 15+ years of local experience. |
| H1 | Plumber in Armonk, NY |
| Parent | — (root) |
| Schema | LocalBusiness, WebSite, BreadcrumbList |
| Tier | 1 |

## Standard pages

| Page | URL | Title tag | Meta description | H1 | Parent | Schema | Tier |
|---|---|---|---|---|---|---|---|
| Services Hub | `/services` | Plumbing Services in Armonk, NY \| Pete's Plumbing | Browse every plumbing, drainage, gas, and remodeling service Pete's Plumbing offers to homeowners across Armonk and Westchester County. | Our Services | Homepage | CollectionPage, BreadcrumbList | 2 |
| About | `/about` | About Pete's Plumbing \| Armonk, NY | Meet the locally owned plumbing team that's helped Armonk-area homeowners with honest, upfront plumbing service for over 15 years. | About Pete's Plumbing | Homepage | AboutPage, BreadcrumbList | 2 |
| Contact | `/contact` | Contact Pete's Plumbing \| Armonk, NY | Call, request a free estimate, or reach Pete's Plumbing directly — serving Armonk, Pleasantville, Mount Kisco, Yonkers, Bedford, Scarsdale, and Greenwich. | Contact Pete's Plumbing | Homepage | ContactPage, BreadcrumbList | 2 |

---

## Category: Drainage Service ⭐ PRIORITY

| Field | Value |
|---|---|
| URL | `/drainage-service-armonk-ny` |
| Title tag | Drainage Service in Armonk, NY \| Pete's Plumbing |
| Meta description | From routine drain cleaning to sewer line repair, Pete's Plumbing keeps Armonk-area drains clear and flowing — same-day appointments available. |
| H1 | Drainage Service in Armonk, NY |
| Parent | Homepage |
| Schema | Service, BreadcrumbList, FAQPage |
| Tier | 1 |

### Child service pages

| Service | URL | Title tag | Meta description | H1 | Tier |
|---|---|---|---|---|---|
| Drain Cleaning ⭐ | `/drain-cleaning-armonk-ny` | Drain Cleaning in Armonk, NY \| Pete's Plumbing | Slow or smelly drains? Pete's Plumbing clears clogs fast with upfront pricing and same-day appointments across Armonk and Westchester County. | Drain Cleaning in Armonk, NY | 1 |
| Clogged Drain Repair | `/clogged-drain-repair-armonk-ny` | Clogged Drain Repair in Armonk, NY \| Pete's Plumbing | A clogged drain that keeps coming back usually means something deeper. We diagnose and fix the real cause, not just the symptom. | Clogged Drain Repair in Armonk, NY | 3 |
| Drain Snaking / Rooter Service | `/drain-snaking-rooter-service-armonk-ny` | Drain Snaking & Rooter Service in Armonk, NY \| Pete's Plumbing | When a plunger won't cut it, our rooter service clears stubborn blockages and root intrusion from Armonk-area drain lines. | Drain Snaking & Rooter Service in Armonk, NY | 3 |
| Hydro Jetting | `/hydro-jetting-armonk-ny` | Hydro Jetting in Armonk, NY \| Pete's Plumbing | High-pressure hydro jetting clears grease, scale, and buildup that snaking alone can't reach — a deeper clean for stubborn pipes. | Hydro Jetting in Armonk, NY | 3 |
| Sewer Line Repair | `/sewer-line-repair-armonk-ny` | Sewer Line Repair in Armonk, NY \| Pete's Plumbing | Backups, slow drains, or soggy spots in the yard can point to a damaged sewer line. We diagnose it clearly before recommending any repair. | Sewer Line Repair in Armonk, NY | 3 |
| Sewer & Drain Camera Inspection | `/sewer-drain-camera-inspection-armonk-ny` | Sewer & Drain Camera Inspection in Armonk, NY \| Pete's Plumbing | See what's really going on inside your pipes. Our camera inspections pinpoint blockages, cracks, and root intrusion without guesswork. | Sewer & Drain Camera Inspection in Armonk, NY | 3 |
| Grease Trap Cleaning | `/grease-trap-cleaning-armonk-ny` | Grease Trap Cleaning in Armonk, NY \| Pete's Plumbing | Commercial kitchens rely on a clean grease trap to keep drains flowing. We service Armonk-area restaurants and small commercial properties. | Grease Trap Cleaning in Armonk, NY | 3 |

---

## Category: Septic Services

| Field | Value |
|---|---|
| URL | `/septic-services-armonk-ny` |
| Title tag | Septic Services in Armonk, NY \| Pete's Plumbing |
| Meta description | Plumbing support for septic-connected homes in Armonk — we handle the plumbing side of septic tank issues with clear, upfront communication. |
| H1 | Septic Services in Armonk, NY |
| Parent | Homepage |
| Schema | Service, BreadcrumbList, FAQPage |
| Tier | 2 |

### Child service pages

| Service | URL | Title tag | Meta description | H1 | Tier |
|---|---|---|---|---|---|
| Septic Tank Service | `/septic-tank-service-armonk-ny` | Septic Tank Service in Armonk, NY \| Pete's Plumbing | Noticing slow drains or backups in a septic-connected home? We handle the plumbing side of septic tank problems, explained clearly. | Septic Tank Service in Armonk, NY | 3 |

---

## Category: Gasfitter ⭐ PRIORITY

| Field | Value |
|---|---|
| URL | `/gasfitter-armonk-ny` |
| Title tag | Gasfitter in Armonk, NY \| Pete's Plumbing |
| Meta description | Licensed gas line and gas water heater work for Armonk-area homes, handled by a plumber who explains every step before starting. |
| H1 | Gasfitter in Armonk, NY |
| Parent | Homepage |
| Schema | Service, BreadcrumbList, FAQPage |
| Tier | 1 |

### Child service pages

| Service | URL | Title tag | Meta description | H1 | Tier |
|---|---|---|---|---|---|
| Gas Line Repair ⭐ | `/gas-line-repair-armonk-ny` | Gas Line Repair in Armonk, NY \| Pete's Plumbing | Smell gas or notice a pressure drop? Our licensed technicians diagnose and repair gas line issues safely, with upfront pricing. | Gas Line Repair in Armonk, NY | 1 |
| Gas Water Heater Installation | `/gas-water-heater-installation-armonk-ny` | Gas Water Heater Installation in Armonk, NY \| Pete's Plumbing | Replacing or installing a gas water heater? We handle the gas connection and plumbing safely, with clear pricing before we start. | Gas Water Heater Installation in Armonk, NY | 3 |

---

## Category: Bathroom & Kitchen Remodeling

| Field | Value |
|---|---|
| URL | `/bathroom-kitchen-remodeling-armonk-ny` |
| Title tag | Bathroom & Kitchen Remodeling Plumbing in Armonk, NY \| Pete's Plumbing |
| Meta description | Planning a bathroom or kitchen remodel? We handle the plumbing side — fixture moves, new supply lines, and drain rework — cleanly and on schedule. |
| H1 | Bathroom & Kitchen Remodeling Plumbing in Armonk, NY |
| Parent | Homepage |
| Schema | Service, BreadcrumbList, FAQPage |
| Tier | 2 |

### Child service pages

| Service | URL | Title tag | Meta description | H1 | Tier |
|---|---|---|---|---|---|
| Bathroom Plumbing Remodeling | `/bathroom-plumbing-remodeling-armonk-ny` | Bathroom Plumbing Remodeling in Armonk, NY \| Pete's Plumbing | Moving a toilet, adding a shower, or repiping for a bathroom remodel — we handle the plumbing work behind your renovation. | Bathroom Plumbing Remodeling in Armonk, NY | 3 |
| Kitchen Plumbing Remodeling | `/kitchen-plumbing-remodeling-armonk-ny` | Kitchen Plumbing Remodeling in Armonk, NY \| Pete's Plumbing | Relocating a sink, adding a dishwasher line, or repiping for a kitchen remodel — we handle the plumbing work your renovation needs. | Kitchen Plumbing Remodeling in Armonk, NY | 3 |

---

## Plumber — general service pages (parent: Homepage, no dedicated category page since Plumber is the primary GBP category)

| Service | URL | Title tag | Meta description | Tier |
|---|---|---|---|---|
| Emergency Plumbing Repair ⭐ | `/emergency-plumbing-repair-armonk-ny` | Emergency Plumbing Repair in Armonk, NY \| Pete's Plumbing | A plumbing emergency can't wait. We offer same-day and emergency response across Armonk and Westchester County. | 1 |
| Water Heater Installation ⭐ | `/water-heater-installation-armonk-ny` | Water Heater Installation in Armonk, NY \| Pete's Plumbing | New water heater or replacing an old one? We help Armonk homeowners choose the right size and install it correctly, with upfront pricing. | 1 |
| Tankless Water Heater Installation | `/tankless-water-heater-installation-armonk-ny` | Tankless Water Heater Installation in Armonk, NY \| Pete's Plumbing | Considering a tankless water heater? We walk you through the tradeoffs and install it right, whether gas or electric. | 3 |
| Toilet Repair | `/toilet-repair-armonk-ny` | Toilet Repair in Armonk, NY \| Pete's Plumbing | Running, leaking, or clogged toilet? We diagnose the actual problem before recommending a repair or replacement. | 3 |
| Toilet Installation | `/toilet-installation-armonk-ny` | Toilet Installation in Armonk, NY \| Pete's Plumbing | Upgrading to a new or more efficient toilet? We install it cleanly and make sure it's sealed and working right the first time. | 3 |
| Leak Detection | `/leak-detection-armonk-ny` | Leak Detection in Armonk, NY \| Pete's Plumbing | A rising water bill or damp spot can mean a hidden leak. We find the source before it causes real damage to your home. | 3 |
| Pipe Repair | `/pipe-repair-armonk-ny` | Pipe Repair in Armonk, NY \| Pete's Plumbing | From small leaks to corroded joints, we repair damaged pipes so your home's plumbing works the way it should. | 3 |
| Pipe Replacement | `/pipe-replacement-armonk-ny` | Pipe Replacement in Armonk, NY \| Pete's Plumbing | Old or failing pipes causing recurring problems? We replace them with durable materials built for Armonk's climate. | 3 |
| Burst Pipe Repair | `/burst-pipe-repair-armonk-ny` | Burst Pipe Repair in Armonk, NY \| Pete's Plumbing | A burst pipe is a true emergency. We respond quickly to stop the water and repair the damage before it spreads. | 3 |
| Faucet Installation | `/faucet-installation-armonk-ny` | Faucet Installation in Armonk, NY \| Pete's Plumbing | Upgrading a kitchen or bathroom faucet? We install it cleanly, with no leaks and no surprises on the bill. | 3 |
| Outdoor Faucet Repair | `/outdoor-faucet-repair-armonk-ny` | Outdoor Faucet Repair in Armonk, NY \| Pete's Plumbing | A leaking or frozen outdoor spigot can waste water and damage your home's exterior. We repair it before winter makes it worse. | 3 |
| Garbage Disposal Repair | `/garbage-disposal-repair-armonk-ny` | Garbage Disposal Repair in Armonk, NY \| Pete's Plumbing | Jammed, leaking, or dead garbage disposal? We repair or replace it so your kitchen sink is back in working order fast. | 3 |
| Shower Installation | `/shower-installation-armonk-ny` | Shower Installation in Armonk, NY \| Pete's Plumbing | Installing a new shower or converting a tub? We handle the plumbing so the finished result works as good as it looks. | 3 |
| Shower Valve Replacement | `/shower-valve-replacement-armonk-ny` | Shower Valve Replacement in Armonk, NY \| Pete's Plumbing | Inconsistent water temperature or a stuck shower valve? We replace it so your shower is reliable again. | 3 |
| Hot Water System Repair | `/hot-water-system-repair-armonk-ny` | Hot Water System Repair in Armonk, NY \| Pete's Plumbing | No hot water or inconsistent temperatures? We diagnose the actual cause before recommending a repair. | 3 |
| Water Line Replacement | `/water-line-replacement-armonk-ny` | Water Line Replacement in Armonk, NY \| Pete's Plumbing | An aging or damaged water line puts your whole home's water supply at risk. We replace it before a small issue becomes a big one. | 3 |
| Water Main Repair | `/water-main-repair-armonk-ny` | Water Main Repair in Armonk, NY \| Pete's Plumbing | A damaged water main affects your entire home. We diagnose and repair it quickly to restore full water service. | 3 |
| Sump Pump Installation | `/sump-pump-installation-armonk-ny` | Sump Pump Installation in Armonk, NY \| Pete's Plumbing | Protect your Armonk basement from flooding with a properly sized, correctly installed sump pump. | 3 |
| Bathtub Installation | `/bathtub-installation-armonk-ny` | Bathtub Installation in Armonk, NY \| Pete's Plumbing | New tub or replacing an old one? We handle the plumbing connections so it's watertight and ready to use. | 3 |
| Fixture Replacement | `/fixture-replacement-armonk-ny` | Fixture Replacement in Armonk, NY \| Pete's Plumbing | Worn-out fixtures waste water and look dated. We replace them cleanly, matching your home's existing plumbing. | 3 |
| Water Softener Installation | `/water-softener-installation-armonk-ny` | Water Softener Installation in Armonk, NY \| Pete's Plumbing | Hard water can damage pipes and appliances over time. We install a water softener sized right for your Armonk home. | 3 |
| Water Filtration System Installation | `/water-filtration-system-installation-armonk-ny` | Water Filtration System Installation in Armonk, NY \| Pete's Plumbing | Want cleaner water straight from the tap? We install filtration systems suited to your home's actual water quality. | 3 |
| Slab Leak Repair | `/slab-leak-repair-armonk-ny` | Slab Leak Repair in Armonk, NY \| Pete's Plumbing | A leak under your foundation is serious. We locate it precisely and repair it with minimal disruption to your home. | 3 |
| Frozen Pipe Repair | `/frozen-pipe-repair-armonk-ny` | Frozen Pipe Repair in Armonk, NY \| Pete's Plumbing | Cold snaps can freeze and crack exposed pipes. We thaw and repair them fast to prevent further damage. | 3 |
| Low Water Pressure Repair | `/low-water-pressure-repair-armonk-ny` | Low Water Pressure Repair in Armonk, NY \| Pete's Plumbing | Weak water pressure has a real cause — from buildup to a hidden leak. We find it and fix it, not just mask it. | 3 |
| Sink Installation | `/sink-installation-armonk-ny` | Sink Installation in Armonk, NY \| Pete's Plumbing | New kitchen or bathroom sink? We install it with clean connections and no leaks under the counter. | 3 |
| Boiler Installation | `/boiler-installation-armonk-ny` | Boiler Installation in Armonk, NY \| Pete's Plumbing | Replacing an aging boiler? We help you choose the right unit for your home and install it correctly. | 3 |
| Commercial Plumbing Services | `/commercial-plumbing-services-armonk-ny` | Commercial Plumbing Services in Armonk, NY \| Pete's Plumbing | We support small commercial properties in the Armonk area with the same upfront pricing and clear communication as our residential work. | 3 |
| Repiping | `/repiping-armonk-ny` | Repiping in Armonk, NY \| Pete's Plumbing | Recurring leaks or corrosion across multiple pipes usually means it's time to repipe. We walk you through the process clearly. | 3 |
| Plumbing Inspection | `/plumbing-inspection-armonk-ny` | Plumbing Inspection in Armonk, NY \| Pete's Plumbing | Buying a home or just want peace of mind? A full plumbing inspection catches small issues before they become expensive ones. | 3 |
| Appliance Hook-Up | `/appliance-hook-up-armonk-ny` | Appliance Hook-Up in Armonk, NY \| Pete's Plumbing | New dishwasher, washing machine, or fridge with a water line? We connect it correctly so it works from day one. | 3 |
| Urinal Installation | `/urinal-installation-armonk-ny` | Urinal Installation in Armonk, NY \| Pete's Plumbing | Installing a urinal for a commercial property? We handle the plumbing connections cleanly and to code. | 3 |
| Rainwater Tank Installation | `/rainwater-tank-installation-armonk-ny` | Rainwater Tank Installation in Armonk, NY \| Pete's Plumbing | Want to collect and reuse rainwater at your Armonk property? We install a tank system that fits your setup. | 3 |
| Laundry Room Plumbing | `/laundry-room-plumbing-armonk-ny` | Laundry Room Plumbing in Armonk, NY \| Pete's Plumbing | Setting up or fixing laundry room plumbing? We handle the supply and drain lines so your washer runs without leaks. | 3 |
| Water Leak Sensor Installation | `/water-leak-sensor-installation-armonk-ny` | Water Leak Sensor Installation in Armonk, NY \| Pete's Plumbing | Catch a leak before it becomes a disaster. We install leak sensors that alert you the moment water shows up where it shouldn't. | 3 |
| Plumbing Maintenance | `/plumbing-maintenance-armonk-ny` | Plumbing Maintenance in Armonk, NY \| Pete's Plumbing | Regular plumbing maintenance catches small problems early. We check the things homeowners usually don't think to check. | 3 |
| Backflow Testing | `/backflow-testing-armonk-ny` | Backflow Testing in Armonk, NY \| Pete's Plumbing | Required annual backflow testing, done right and documented, to keep your property's water supply safe and compliant. | 3 |

---

## Page count summary
- Homepage: 1
- Standard pages: 3 (Services Hub, About, Contact)
- Category pages: 4 (Drainage Service, Septic Services, Gasfitter, Bathroom & Kitchen Remodeling)
- Service pages: 49 (37 under Plumber/homepage, 7 under Drainage, 1 under Septic, 2 under Gasfitter, 2 under Bathroom & Kitchen Remodeling)
- **Total: 57 pages**
