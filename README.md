# Pantaz Co. — Site Catalog

Interactive sales tool for **Pantaz Co.**, Nick Pantazopoulos's side business building and managing websites for local trades (plumbers, cleaners, landscapers, contractors, HVAC, handymen, auto detailers) in Southwestern Ontario, run alongside a full-time engineering degree at Western University.

**Live:** https://pantaz.ca (catalog) · https://pantaz.ca/about.html (About)

A prospect picks their trade (six demos: Cleaning, Landscaping, General Contracting, HVAC, Handyman, Car Detailing), compares a Standard build against Premium in a live preview, reads real pricing, and sees which tier fits their business — all from one link, with nothing separate for Nick to send.

## Structure

Two self-contained files, no build step, no dependencies, no package manager:

- **`index.html`** — the catalog. Inline `<style>` for the shell, inline `<script>` for a vanilla-JS controller plus a `trades` data object (one entry per demo trade: copy, accent color, services, testimonials). Each picked trade/tier renders into a Shadow DOM host (`#demoHost`), so the demo site's CSS stays fully isolated from the shell around it — same technique a real deployed client site would use. "Open in new tab" builds a standalone blob URL of just the demo, matching what an actual client deploy would look like on its own.
- **`about.html`** — Nick's About page. Real bio, "how I work" values, honest credentials framing (no fabricated stats), founding pricing recap, contact CTA. Linked from the catalog's top nav (`Catalog` ↔ `About`).

Page section order on the catalog (numbered in the UI): **01** choose a tier → **02** choose a trade → live preview → **03** do you need Premium → **04** the retainer, explained → **05** why this works → **06** who's building this. Tier comes before trade — that was deliberately swapped from the original order.

## Running it locally

Plain static files — open directly in a browser, or serve the folder with any static file server if you'd rather not use `file://` (needed for some dev tools to get accurate mobile-width testing).

## Deploying

GitHub `main` → Netlify (`pantaz-catalog` project) → pantaz.ca, continuous deployment, no build command, publish directory is repo root.

**Every deploy costs 15 Netlify credits on the current plan, regardless of change size.** `netlify.toml`'s `ignore` rule skips a deploy for docs-only commits (README/CLAUDE.md/CHANGELOG with no `*.html` change), but any edit to either HTML file still costs a deploy — batch multiple edits into one push rather than pushing after every tweak.

## Brand quick reference

| Token | Value |
|---|---|
| Navy | `#2A487C` |
| Navy dark | `#1B3966` |
| Clay (single accent per screen) | `#C2542A` |
| Ink | `#1C1B19` |
| Paper | `#FAF8F4` |
| Paper tint | `#EFE8E4` |
| Display / body font | Source Sans 3 |
| Utility font (labels, prices, links) | IBM Plex Mono |
| Radius | 10px |
| Border | 1px, thin throughout |
| Shell max-width | 1080px (both pages) |

Logo mark: two stepped bars — a short solid bar (what's already there) and a taller outlined bar (what gets built on top). Never rotate, resize independently, or use one bar alone.

Full brand source: [Website Design Brand Development](https://claude.ai/code/artifact/5050bcb2-b0df-4327-a186-32d782f5ae30) (Claude Design Canvas — built under the project's original "Curbly" name; palette/type/mark carried over unchanged through the later rename to Pantaz Co.)

## Pricing & retainer (as reflected live — verify against the site before quoting a client, this has changed several times)

- **Standard** — $1,200 regular / **$200 founding price** (first 10 clients)
- **Premium** — $2,000 regular / **$500 founding price** (first 10 clients)
- **Founding client discount**: first 10 clients only, $1,000 off Standard or $1,500 off Premium. No retainer required to get this discount.
- **Retainer** (optional, either tier): $100/mo — includes hosting, support, and **2 free small edits/month**; extra edits beyond that are $15–$45 each.
- **Founding clients who take the retainer**: pay $40/mo for their first 6 months (then $100/mo), and get **unlimited small edits forever** as a signing bonus — that perk doesn't expire even after the rate reverts to $100/mo.
- **Skipping the retainer entirely**: $45 for a small edit, $150 for a large one, billed as needed. **Hosting is not included without the retainer** — the client is responsible for their own hosting arrangement (Nick will point them in the right direction, but it's not bundled).
- A "0 / 10 spots filled" progress badge on the founding banner is real and manually updated — it is not a placeholder, keep it honest as clients actually sign on.
- A referral program was discussed and drafted once, then explicitly removed — the terms weren't finalized. Don't re-add one unless asked; if asked, it's a new decision, not a restore.

## Full project context

For the complete story — decisions, deliverable links, contact info predating this repo's docs — see the standing handoff page:

**https://claude.ai/code/artifact/2339e765-8d40-4dd4-9186-2e129d3eb2f3**

(That page may lag behind this README/CHANGELOG for anything recent — this repo is the more current source for day-to-day work.)

See also `CLAUDE.md` (context for AI coding agents working in this repo) and `CHANGELOG.md` (durable decision history).

## Known open items

- **`trades-site-template`** (separate repo, used to build each real client's actual site) was lost when its drive became inaccessible, and — unlike this catalog — was never deployed publicly, so it can't be reconstructed from anything live. Status as of last check: possibly still recoverable from Nick's Calgary PC, which was powered off; ask Nick whether he's gotten it back before assuming it's gone for good.
- Job photos on the demo trades are still placeholder gray boxes (stock photography is an accepted permanent fix, not just a stopgap).
- Payment collection (Stripe vs. invoicing) isn't implemented anywhere on the site — Nick plans to sort this out once he has his first real client, not before.
- Netlify Pro / Claude Pro upgrades are planned once client #1 signs, not before — don't assume either is active.

## Resolved (kept here so nobody re-litigates them)

- Contact phone (825) 438-3626 is Nick's real personal number (Alberta area code, kept from before he moved to Ontario) — **not** a placeholder. Don't "fix" it.
- Contact email `Nick@Pantaz.ca` and the headshot photo are both real and live on both pages.
- Aerial/drone photography language was deliberately removed sitewide (commercial drone authorization was never confirmed) — don't reintroduce it without that being resolved first.
