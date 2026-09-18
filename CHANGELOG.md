# Changelog

Durable record of major decisions and milestones. Kept in the repo so it survives independently of any one chat session or Artifact.

## About page, sixth trade, retainer restructure, mobile fixes (2026-09)

- **Added `about.html`** — Nick's real bio ("From Alberta to Western — and finally starting it": Western University engineering student, from Alberta, moved for school), an honest credentials section (reframed from raw 0/0/0 stats — which read as a red flag — to "1st portfolio build / 100% of my attention / $1,500 max founding savings"), both tiers' founding pricing shown side by side, and a contact CTA. Linked to/from the catalog via a `Catalog` ↔ `About` top-nav link on both pages.
- **Added Car Detailing as a sixth demo trade** (Prestige Auto Detailing) — targeting this vertical for Instagram DM outreach.
- **Swapped the picker order**: tier selection now comes before trade selection (01/02 swapped). Added a new numbered section 04, "Want to keep it up and use my website?" — a dedicated retainer explainer styled like the existing "Do you need Premium?" decision-helper, pushing "Why this works" and "Who's building this" to 05/06.
- **Founding offer revised twice**: first changed from "first 5 clients, retainer required" to "first 10 clients, no retainer required" (to grow the client base faster before selling the retainer harder); then a discounted founding retainer was reintroduced — $40/mo for the founding client's first 6 months (then $100/mo) — as an optional add-on, not a requirement.
- **Per-edit / retainer pricing clarified after a couple of false starts**: settled structure is $100/mo retainer (2 free small edits/month, hosting, support included) → $15–$45 for extra edits beyond that; **or** no retainer at all → $45 small edit / $150 large edit, hosting becomes the client's own responsibility (this "hosting requires the retainer" detail wasn't disclosed clearly anywhere before and now is). Founding clients who take the retainer additionally get unlimited small edits *forever* as a signing bonus, not just during their discounted 6 months.
- **Founding pricing surfaced directly on the pricing cards** (struck-through regular price next to the founding price) instead of only in a paragraph below — was "too much reading to find the number."
- **Added a real headshot** (`headshot.png`) to both the About page and the catalog's "Who's building this" section, replacing the placeholder circle. Added the phone number and email to the catalog page's contact section and footer (previously only on About).
- **Clarified the founder's phone number, (825) 438-3626, is real** — not a leftover placeholder. It has an Alberta area code because Nick is from Alberta and kept the number after moving to Ontario for school; this matches his bio and doesn't need to change.
- **Removed aerial/drone photography language sitewide** (Premium tier bullet, a highlights card, the footer disclaimer, a demo placeholder, and several gallery captions) — commercial drone work needs authorization that was never confirmed, and none of these lines should promise more than "a website."
- **Fixed all five demo trades' placeholder phone numbers**, which used invalid NANP exchange codes starting with 0 (e.g. 019, 042) — moved to the `555-01XX` range reserved for fictional numbers.
- **Removed a leaked internal placeholder-note** that had accidentally shipped as live, visitor-facing text on the About page ("...swap it for a real one before this page goes live") — caught during a full site audit; a lesson to not leave TODO-style notes in rendered copy.
- **A referral program was drafted (a "$100 you / $100 them" structure) then explicitly removed** the same session — terms weren't finalized. Not currently on the site; treat re-adding it as a fresh decision requiring real terms, not a restore.
- **Two real mobile bugs found from user-supplied screenshots and fixed**: (1) the live-preview's browser-bar (domain + tier toggle + "Open in new tab") overflowed off-screen on narrow viewports instead of wrapping — added `flex-wrap` and made the wrapped row stretch full-width instead of clustering left with dead space on the right; (2) two icons (`.phone-pill`, `.mobile-call-bar`) rendered "massive" because the shared `svg()` helper never sets width/height on the raw tag and these two spots were missing their own sizing rule (see CLAUDE.md's icon-sizing note).
- **Widened prose text sitewide to match full-width card sections** — several paragraphs had ch-based reading-width caps that looked increasingly inconsistent (narrower than neighboring cards) after the About page's shell was widened from 780px to 1080px earlier. Most were simply uncapped; the About page's "My Story" section instead got a two-column treatment (heading in a narrow left column, paragraphs in the wider right column) so line length stays comfortable without looking narrower than the page around it.
- Netlify credits confirmed to cost 15 per deploy **regardless of file type** — the `netlify.toml` ignore-build rule only helps for genuinely docs-only commits (no `*.html` touched); any HTML change still costs a deploy, so batching real changes together still matters.
- `trades-site-template` status as of this update: possibly recoverable — it may still exist on Nick's Calgary PC, which was powered off. Not confirmed lost permanently; check with Nick before assuming.

## Recovery & infrastructure (2026-09)

- **Made the preview-bar tier badge clickable** — toggles Standard/Premium in sync with the pricing cards, no scroll required.
- **Linked GitHub repo to Netlify for continuous deployment** — pushes to `main` now auto-deploy to pantaz.ca. Previously deploys were manual (CLI upload).
- **Pushed recovered source to GitHub** (`nick-pantaz/Pantaz-Co.`) — first durable, version-controlled copy of this project.
- **Rebuilt the catalog from scratch** after the original source (in a Claude session's scratchpad) became unreachable when its drive was lost. Reconstructed by diffing the Claude Artifact copy (still "Curbly"-branded) against the live pantaz.ca DOM — only branding strings (title, meta tags, header wordmark) had drifted; everything else verified render- and behavior-identical to production.
- **`trades-site-template`** (the separate reusable template for building each client's real site) was lost in the same drive failure and, unlike the catalog, was never deployed publicly — not reconstructable. Treated as gone unless a backup surfaces.
- Corrected contact email to `Nick@Pantaz.ca` (previously `Nick@Pantaz.com`, which didn't match the live `.ca` domain).
- Clarified that stock photography is an accepted fix for the placeholder job photos on demo trades, not just a fallback.

## Launch (earlier)

- Connected the `pantaz.ca` domain (A record + www CNAME) — confirmed live with valid SSL.
- Rebranded the whole catalog from **"Curbly"** to **"Pantaz Co."** — same visual system, name only.
- Deployed to Netlify. Hit a snag: the whole Netlify account had visitor SSO required on all sites, traced to a setting cached on the individual site that didn't sync from the account-level toggle — fixed directly.
- Full review pass: rewrote the founding offer as a named discount with a 6-month minimum term, added a credibility section (name, city, photo placeholder, timeline, call-to-action), localized demo content to real Southwestern Ontario towns and 519/226 numbers, fixed a mobile scroll trap and a quirks-mode bug.

## Build (earliest)

- Discovered the real brand ("Curbly") via a linked Design Canvas and reskinned the catalog's outer shell to match — navy/clay/cream, Source Sans 3 + IBM Plex Mono, stepped-bar logo.
- Built **The Site Catalog**, an interactive single-link pitch tool: pick a trade, compare tiers, see live pricing. First version used placeholder "blueprint" styling and fictional towns.
- Built **trades-site-template**: a reusable Standard/Premium static template for cleaning, reskinned into landscaping, general contracting, HVAC, and handyman by editing one config file. *(Lost — see above.)*
