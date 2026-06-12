# AGENTS.md — demos

Live product demos — works on any device. Daniel's solo repo of static, self-contained
HTML demos for Cowbolt Register (non-custodial Bitcoin POS), served via GitHub Pages.

## Stack + run/verify

- Pure static HTML. No package.json, no Makefile, no README, no CI workflows, no build
  or test harness.
- Each demo is ONE self-contained `.html` file: all CSS and JS inline. Only external
  dependency is Google Fonts (Fraunces + Inter).
- Verify locally: open the file in a browser, or `python3 -m http.server` from the repo
  root and click through. Check both phone-width and desktop viewports — "works on any
  device" is the repo's promise.
- Deploy: GitHub Pages, legacy build from `main` branch root (`source: main /`). Every
  push to main goes live at https://nitton76.github.io/demos/ — there is no staging.
  After pushing, verify the live URL renders (cache-busted fetch).

## Layout

- `index.html` — the hub. Links ONLY `./cowbolt-pos-web/` (desktop/tablet web POS) and
  `./cowbolt-pos/` (mobile POS). Latest direction: "Hub = the POS system: web app +
  mobile app only" (commit fa7a87e).
- `cowbolt-mockup.html` — the Cowbolt App mockup; intentionally unlinked from the hub.
- `cowbolt-site/` — READ-ONLY mirror of the live cowbolt.com site (captured 2026-05-30;
  doubles as backup while cowbolt.com's TLS cert is expired — see `_MIRROR_README.md`).
- `assets/` — app screenshots + `cowbolt-transaction.mp4`, used by cowbolt-mockup.html.

## Conventions (hard)

1. Keep demos single-file: inline `<style>` and `<script>`, no external JS/CSS files.
2. Reuse the shared `:root` token block (duplicated per file): `--brand:#02CF0A` is the
   exact Cowbolt green from cowbolt.com; `--btc:#F68703`; `--usdt:#02BB83`. Never
   invent brand colors.
3. Fonts are Fraunces (display, `.serif`) + Inter (body) via Google Fonts — keep it.
4. Mobile-first: `viewport-fit=cover` meta on every page; demos must work on a phone.
5. Do NOT edit `cowbolt-site/` — it is a mirror/backup, not authored code.

## Gotchas

- No CI and no preview deploys: a bad push to main is immediately live. Verify locally
  before pushing.
- Hub links use trailing-slash directory paths (`./cowbolt-pos-web/`); keep that form
  so GitHub Pages resolves `index.html`.

## Git

Confirm before commit/push. Daniel handles git.

## State

- Cross-repo state + repo map: `GutenOS/Context/Guten_Group/coding-agent/CODING_STATE.md` (guten-coder skill).
- Last session: 2026-06-12 — AGENTS.md scaffolded (guten-coder GitHub sweep). Open work: none.
