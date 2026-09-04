# CLAUDE.md

Context for Claude Code (or any AI agent) working in this repo. Read this before editing `index.html`.

## What this is

The sales catalog for **Pantaz Co.**, Nick Pantazopoulos's side business building websites for local trades in Southwestern Ontario. One interactive page: pick a trade, compare Standard vs. Premium, see real pricing. Live at **pantaz.ca**.

## Why this file exists

The original project source was lost when the drive holding a Claude session's scratchpad became inaccessible — the catalog only survived because it had also been published as a Claude Artifact and was live on Netlify, so it could be reconstructed by diffing the two. A second, earlier-stage project (`trades-site-template`, the reusable template for actually building each client's real site) had no such backup and was lost for good.

**The lesson this file is here to enforce: never let this repo be the only copy, and never treat a Claude session's scratchpad/temp directory as durable storage for anything that matters.** This repo on GitHub, linked to Netlify, is the durable source now — keep it that way.

## Architecture

Single self-contained file: `index.html`. No build step, no package.json, no dependencies. Inline `<style>` for the shell, inline `<script>` for logic and the `trades` data object. Each demo trade renders into a Shadow DOM host so its CSS never leaks into (or is affected by) the Pantaz Co. shell around it — treat that isolation as load-bearing, not incidental, if you're touching the render logic.

## Brand system — do not deviate without being asked

- Navy `#2A487C` carries brand identity. Clay `#C2542A` is spent on exactly **one** ask per screen (a button, a phone number, "book now") — never more than one accent element visible at a time.
- Fonts: Source Sans 3 (display/body), IBM Plex Mono (labels, prices, status, links).
- Radius 10px, borders 1px, consistently.
- Logo mark is two stepped bars (short solid + tall outlined). Never rotate, resize independently, or use one bar alone.
- Each of the five demo trades keeps its own distinct branding (colors, business name, town) — those are hypothetical *client* sites, separate from the Pantaz Co. shell. Don't blend the two palettes.

Full brand source: https://claude.ai/code/artifact/5050bcb2-b0df-4327-a186-32d782f5ae30

## Business rules encoded in the copy — treat as data, verify before changing

- Standard $1,200 / Premium $2,000, one-time.
- Retainer optional: $100/mo (hosting, edits, support) or $45–150 per change without it.
- Founding client discount (first five clients only): $1,000 off Standard / $1,500 off Premium, **requires** the retainer with a 6-month minimum. This replaced an earlier "$400 flat, no retainer" option that was deliberately dropped — don't reintroduce it without being asked.
- Any Standard build can move to Premium later for the price difference, same content/structure.

If a request implies changing pricing, the founding-discount terms, or the retainer structure, treat that as a real business decision worth confirming rather than a copy edit.

## Deployment

GitHub `main` → Netlify (`pantaz-catalog` project, linked for continuous deployment) → pantaz.ca. No build command; publish directory is repo root.

**Every deploy costs Netlify credits (15 per deploy) on the current plan, regardless of change size.** Batch edits into one commit/push rather than pushing after each small tweak — don't push-fix-push-fix on typos.

## Current known-placeholder content (see README for the full list)

Phone number, headshot, and job photos on the live site are all still placeholders. Don't "fix" these unilaterally — they're open items pending real assets from Nick, not bugs.

## Full context

This file covers repo-local conventions only. For the complete project history, decisions log, and every deliverable link: https://claude.ai/code/artifact/2339e765-8d40-4dd4-9186-2e129d3eb2f3
