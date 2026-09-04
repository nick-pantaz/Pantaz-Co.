# Changelog

Durable record of major decisions and milestones. Kept in the repo so it survives independently of any one chat session or Artifact.

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
