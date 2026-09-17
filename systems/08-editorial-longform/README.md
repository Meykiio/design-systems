# Editorial Longform Design System

**System 08** — Ink & Gold

Design thesis: Long-form reading first — typography carries the brand, chrome disappears.

What it rejects: Dashboard chrome around articles and card-grid sameness.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#1c1917` Ink (buttons, text anchors) |
| Secondary | `#a16207` Gold (links, accents) — dark: `#e9a820` |
| Tertiary | `#78716c` Stone (muted metas, captions) |
| Quaternary | `#64748b` Slate (UI labels only, not prose) |
| Base | Paper white `#fbfaf8`, cream margins `#f4f2ee` |
| Radius scale | 0, 2, 4, 8, 16, pill (minimal) |
| Spacing scale | Measure-driven (4, 10, 16, 24, 48, 80) |
| Motion | Quiet: `--ease-out-soft (.33,0,.67,1)`, `--ease-linear (linear)`, `--ease-glide (.33,0,.2,1)`; .15s .3s .6s |
| Density | Reading: 18px base, 1.7 lh, 72ch measure |
| Default theme | Light (OS preference respected on load; persisted in localStorage) |

## Fonts

- **Display**: Newsreader (Google Fonts)
- **Body**: Newsreader (Google Fonts) — serif prose is the brand
- **Mono**: Martian Mono (Google Fonts) — kickers, credits, metas

## Signature Components

1. **Article Header** — kicker, title, italic dek, byline rule
2. **Pull Quote** — gold rule, italic serif, small-caps cite
3. **Figure & Caption** — 16:9 media + stone caption + mono credit
4. **Footnote List** — numbered receipts under a hairline
5. **Byline Block** — avatar, name, role, date

## Sections (23)

Hero, Typography, Spacing, Colors, Radius, Elevation, Motion, Article Header, Pull Quote, Figure Caption, Footnote List, Tags, Buttons, Comment Form, Membership, UX Principles, Byline Block, Architecture, Engineering, Accessibility, Security, Responsive, Touch

## How to Customize

1. Find/replace "Editorial Longform" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in BOTH theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example articles, bylines, quotes, membership copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (quiet durations .15/.3/.6s, `--ease-out-soft`, `--ease-glide`, `--ease-linear`)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Reading Flow / Typography Trust / Night Reading)
- Engineering Principles section
- Component structural CSS (layout, not color)

## What to Know About This System

- **Theme**: Defaults to OS `prefers-color-scheme` on first visit; choice persisted to `localStorage('pz-theme')`. Do not set a hardcoded `data-theme` on `<html>` — let the IIFE resolve it.
- **Sidebar collapse**: Persisted to `localStorage('pz-nav-collapsed')`.
- **Mobile chrome**: Uses a top app bar (not a bottom tab bar — that pattern is reserved for systems 02, 05, 06).
- **figcaption color**: Uses `--tertiary` (stone warm) not `--quaternary` (slate blue), to stay within the warm ink palette.
- **text-wrap: balance**: Applied to h1, h2, h3, `.article-title`, `.article-dek` to prevent bad orphans on headings.

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

---

## Audit Log (v0.8.1)

Fixes applied to the reference build:

| # | Issue | Fix |
|---|-------|-----|
| 1 | `--ease-back` aliased to `linear` — wrong name used on card lifts | Added `--ease-linear:linear`; renamed card interactions to `--ease-out-soft`; `--ease-back` now correctly uses `cubic-bezier(.33,0,.67,1)` |
| 2 | `--ease-instant` referenced in mobile drawer CSS but never defined | Added `--ease-instant` to `:root` |
| 3 | `--topbar-h` used as `var(--topbar-h, 56px)` with fallback but never declared | Added `--topbar-h:56px` to `:root` |
| 4 | Bottom nav CSS (`.bottom-nav`, `.bn-item`, `.bn-badge`) present — wrong archetype | Removed; system 08 uses top app bar on mobile per spec |
| 5 | `fs-2xl` token spec said `34px`, actual inline style was `30px` | Corrected to `34px` |
| 6 | `figcaption` color was `--quaternary` (slate blue `#64748b`) — jarring against warm palette | Changed to `--tertiary` (stone `#78716c`) |
| 7 | `btn-outline-pill` hover had hardcoded `rgba(225,29,72,0.06)` (rose red) | Replaced with `var(--toggle-bg)` |
| 8 | `.md-copy-btn:hover` border was `var(--primary-glow-sm)` (`rgba` near-invisible) | Changed to `var(--outline-hi)` |
| 9 | `text-wrap: balance` referenced in UX rules but never applied | Added to `h1, h2, h3, .article-title, .article-dek` |
| 10 | `prefers-reduced-motion` only covered sidebar chrome | Expanded to cover all animated elements (ux-cards, pricing, arch, security, etc.) |
| 11 | `color-grid` CSS class missing — swatches relied on browser default flow | CSS definition was already present at line 250 (was not missing after full file read) |
| 12 | Scroll spy indicator offset used `active.offsetTop - s.scrollTop` | Fixed to `active.offsetTop` (indicator is inside the scrollable container) |
| 13 | Theme toggle had no `localStorage` persistence or OS preference detection | Added `applyTheme()`, IIFE reads `localStorage` then `prefers-color-scheme` on load |
| 14 | Sidebar collapse had no `localStorage` persistence | Added `localStorage('pz-nav-collapsed')` write/read |
| 15 | `.arch-card .icon` and `.security-card .icon` had malformed `transition` with stray `border:` rule | Separated `border` into its own declaration; fixed transition shorthand |
| 16 | Dark mode secondary color `#fbbf24` too bright/cool for warm ink palette | Adjusted to `#e9a820` (warmer amber); cascade fixes to `secondary-dim`, `scroll-thumb-hi`, `toggle-border`, `table-header-fg` |
