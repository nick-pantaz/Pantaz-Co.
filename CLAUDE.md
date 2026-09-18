# CLAUDE.md

Context for Claude Code (or any AI agent) working in this repo. Read this before editing `index.html` or `about.html`.

## What this is

The sales catalog + About page for **Pantaz Co.**, Nick Pantazopoulos's side business building websites for local trades in Southwestern Ontario, run alongside a full-time engineering degree at Western University. Pick a trade, compare Standard vs. Premium, see real pricing. Live at **pantaz.ca** and **pantaz.ca/about.html**.

## Why this file exists

The original project source was lost once already when the drive holding a Claude session's scratchpad became inaccessible — the catalog only survived because it had also been published as a Claude Artifact and was live on Netlify, so it could be reconstructed by diffing the two. A second, earlier-stage project (`trades-site-template`, the reusable template for actually building each client's real site) had no such backup and was lost. It may or may not still exist on a personal machine — check with Nick rather than assuming either way.

**The lesson this file enforces: never let this repo be the only copy, and never treat a Claude session's scratchpad/temp directory as durable storage for anything that matters.** This repo on GitHub, linked to Netlify, is the durable source — keep it that way.

## Architecture

Two self-contained files, no build step, no package.json, no dependencies:
- `index.html` — the catalog. Inline `<style>` for the shell, inline `<script>` for logic and the `trades` data object (six entries: Cleaning, Landscaping, General Contracting, HVAC, Handyman, Car Detailing). Each demo trade renders into a Shadow DOM host so its CSS never leaks into (or is affected by) the Pantaz Co. shell around it — treat that isolation as load-bearing, not incidental.
- `about.html` — real bio content, not a template. Shares the brand shell CSS pattern but is its own file.

Section order on the catalog is intentional and numbered in the UI (01 tier → 02 trade → preview → 03 premium-or-not → 04 retainer explainer → 05 why-this-works → 06 who's-building-this) — tier before trade was a deliberate swap from the original order. Don't reorder without being asked.

**Icon sizing gotcha:** the shared `svg(name)` helper outputs a bare `<svg viewBox="0 0 24 24">` with no `width`/`height` — every icon usage needs its own CSS rule to size it (e.g. `.service-icon svg { width: 20px; height: 20px; }`), or the browser falls back to its default ~300×150px replaced-element size and it renders massive. This has bitten two icons already (`.phone-pill svg`, `.mobile-call-bar svg`). When adding any new `${svg(...)}` usage, add a matching sized selector in the same commit.

## Brand system — do not deviate without being asked

- Navy `#2A487C` carries brand identity. Clay `#C2542A` is spent on exactly **one** ask per screen (a button, a phone number, "book now") — never more than one accent element visible at a time.
- Fonts: Source Sans 3 (display/body), IBM Plex Mono (labels, prices, status, links).
- Radius 10px, borders 1px, consistently. Shell max-width 1080px on both pages.
- Logo mark is two stepped bars (short solid + tall outlined). Never rotate, resize independently, or use one bar alone.
- Each of the six demo trades keeps its own distinct branding (colors, business name, town) — those are hypothetical *client* sites, separate from the Pantaz Co. shell. Don't blend the two palettes.
- Prose paragraphs generally run full-width now, matching card/box widths on the same page (Nick's explicit preference, after ch-based reading-width caps looked inconsistent next to full-width sections). The one deliberate exception: About page's "My Story" section uses a two-column layout (kicker+heading in a narrow left column, paragraphs in the wider right column) specifically to keep body text at a comfortable line length *without* looking narrower than neighboring full-width cards — that's the pattern to reach for if a similar "text looks too narrow/wide" complaint comes up elsewhere, not a blanket ch-cap.
- Aerial/drone photography language was deliberately scrubbed sitewide — commercial drone authorization was never confirmed. Don't reintroduce "aerial," "drone," etc. without that being resolved first.

Full brand source: https://claude.ai/code/artifact/5050bcb2-b0df-4327-a186-32d782f5ae30

## Business rules encoded in the copy — treat as data, verify against the live site before changing (this has been revised several times already)

- Standard $1,200 / Premium $2,000 regular price, one-time build.
- **Founding discount** (first 10 clients, not five): $1,000 off Standard ($200 upfront) or $1,500 off Premium ($500 upfront). No retainer required to get this discount. A "0 / 10 spots filled" badge on the founding banner is real and hand-updated as clients sign on — never fabricate a higher number.
- **Retainer** (optional, either tier, either founding or not): $100/mo — hosting, support, 2 free small edits/month included; extra edits beyond that are $15–$45 each.
- **Founding clients who also take the retainer**: $40/mo for their first 6 months (then reverts to $100/mo), *and* get unlimited small edits forever as a signing bonus — the unlimited part doesn't expire when the price reverts.
- **No retainer at all**: $45 for a small edit, $150 for a large one, billed per request. Hosting is NOT included without the retainer — that's the client's own responsibility (Nick points them in the right direction but doesn't bundle it). This is a real, deliberate distinction — don't blend the "skip retainer" rate with the "retainer extra-edit" rate; they're different numbers for different situations.
- Any Standard build can move to Premium later for the price difference, same content/structure.
- No referral program exists currently — one was drafted, then explicitly pulled because terms weren't finalized. If asked to add one, treat it as a fresh decision (ask for the actual terms), not a restore of something removed.

**If a request implies changing any of the above, treat it as a real business decision worth a quick confirmation rather than a copy edit** — this project's pricing/retainer terms have been revised multiple times in-session, usually because an earlier version turned out to be unclear or inconsistent once written out. Reread the current live copy before assuming you know the terms; this file can lag the site by a commit or two.

## Deployment

GitHub `main` → Netlify (`pantaz-catalog` project, linked for continuous deployment) → pantaz.ca. No build command; publish directory is repo root.

**Every deploy costs 15 Netlify credits, regardless of change size.** `netlify.toml`'s `ignore` rule skips a deploy when a commit touches no `*.html` file (so docs-only commits are free) — but any edit to `index.html` or `about.html`, however small, still costs one. Batch edits into a single commit/push; don't push-fix-push-fix on typos. When testing, use a local static server (a simple PowerShell `HttpListener` loop has worked fine in this environment — no Node/Python required) and verify visually (including at mobile width, e.g. 375px) before pushing.

## Known-real vs. known-placeholder content

**Real, live, do not treat as placeholder:** the headshot (`headshot.png`), the phone number (825) 438-3626 (Nick's actual personal number — Alberta area code because he's from Alberta, not a leftover placeholder), the email `Nick@Pantaz.ca`, the "My Story" bio content on the About page.

**Still placeholder / open:** job photos on the demo trades (gray boxes — stock photography is an accepted permanent fix, not just a stopgap). Payment collection (Stripe vs. invoice) isn't built into the site and isn't planned until client #1 signs.

## Full context

This file covers repo-local conventions only. For the complete project history predating this repo, and a decisions log: https://claude.ai/code/artifact/2339e765-8d40-4dd4-9186-2e129d3eb2f3 (may lag — `CHANGELOG.md` in this repo is more current for anything recent).
