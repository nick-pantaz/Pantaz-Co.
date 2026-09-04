# Pantaz Co. — Site Catalog

Interactive sales tool for **Pantaz Co.**, Nick Pantazopoulos's side business building and managing websites for local trades (plumbers, cleaners, landscapers, contractors, HVAC, handymen) in Southwestern Ontario.

**Live:** https://pantaz.ca

A prospect picks their trade (five demos: Cleaning, Landscaping, General Contracting, HVAC, Handyman), compares a Standard build against Premium in a live preview, reads real pricing, and sees which tier fits their business — all from one link, with nothing separate for Nick to send.

## Structure

This is a single self-contained file: `index.html`. No build step, no dependencies, no package manager.

- Inline `<style>` — the Pantaz Co. brand shell (header, pricing cards, page sections)
- Inline `<script>` — a small vanilla-JS controller plus a `trades` data object (one entry per demo trade: copy, pricing-page accent color, services, testimonials). The controller renders the picked trade/tier into a Shadow DOM host (`#demoHost`), so the demo site's CSS stays fully isolated from the shell around it — same technique a real deployed client site would use.
- "Open in new tab" builds a standalone blob URL of just the demo site, matching what an actual client deploy would look like on its own.

## Running it locally

It's a plain static file — open `index.html` directly in a browser, or serve the folder with any static file server if you'd rather not use `file://`.

## Deploying

This repo is linked to Netlify (`pantaz-catalog` project) for continuous deployment: **any push to `main` auto-deploys to pantaz.ca**, no manual steps. No build command is set — publish directory is the repo root.

**Each deploy costs Netlify credits on the current plan (15 per deploy) regardless of how small the change is.** Batch multiple edits into one commit/push rather than pushing after every tweak.

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

Logo mark: two stepped bars — a short solid bar (what's already there) and a taller outlined bar (what gets built on top). Never rotate, resize independently, or use one bar alone.

Full brand source: [Website Design Brand Development](https://claude.ai/code/artifact/5050bcb2-b0df-4327-a186-32d782f5ae30) (Claude Design Canvas — built under the project's original "Curbly" name; palette/type/mark carried over unchanged through the later rename to Pantaz Co.)

## Pricing (as reflected live)

- **Standard** — $1,200 one-time
- **Premium** — $2,000 one-time
- Retainer optional on full-price builds — $100/mo covers hosting, edits, and support. Without it, changes are billed $45–150 each.
- **Founding client discount** (first five clients only): $1,000 off Standard (pay $200 upfront) or $1,500 off Premium (pay $500 upfront). Requires the $100/mo retainer, with a 6-month minimum term.

## Full project context

This repo covers the product only. For the complete story — decisions, open items, deliverable links, contact info — see the standing handoff page:

**https://claude.ai/code/artifact/2339e765-8d40-4dd4-9186-2e129d3eb2f3**

See also `CLAUDE.md` (context for AI coding agents working in this repo) and `CHANGELOG.md` (durable decision history).

## Known open items

- Contact email (`Nick@Pantaz.ca`) not yet confirmed to actually receive mail
- Founder phone number on the site is still an Alberta placeholder — (825) 438-3626
- Headshot photo placeholder needs a real photo
- Demo trades use placeholder gray boxes for job photos (stock photography is an accepted fix, not just real photos)
- The separate `trades-site-template` repo (used to build each real client's actual site) was lost when its drive became inaccessible and was never deployed publicly, so — unlike this catalog — it can't be reconstructed from anything live. Check for a backup (old zip, cloud sync, email attachment, GitHub Desktop cache) before treating it as gone for good.
