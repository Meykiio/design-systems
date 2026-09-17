# Marketplace Booking Design System

**System 06** — Amber & Indigo

Design thesis: Two-sided clarity — search, compare, book with zero ambiguity about price or availability.

What it rejects: Hidden fees and fake urgency.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#fbbf24` Amber (dark canonical) / `#b45309` (light) |
| Secondary | `#818cf8` Indigo (interactive accents) |
| Tertiary | `#34d399` Mint (confirmed states) |
| Quaternary | `#f472b6` Pink (wishlist) |
| Base | Warm dark charcoal `#12100d` |
| Radius scale | 10, 14, 20, 26, 32, pill (soft) |
| Spacing scale | 5-step (5, 10, 15, 25, 40, 55) |
| Motion | Confident glides: `(.65,.05,.36,1)`, `(.7,0,.3,1)`, `(.5,1.5,.5,1)`; .2s .32s .5s |
| Density | Roomy: 16px base, 1.5 lh |
| Default theme | Dark |

## Fonts

- **Display**: Plus Jakarta Sans (Google Fonts)
- **Body**: Plus Jakarta Sans (Google Fonts)
- **Mono**: DM Mono (Google Fonts) — nightly prices, dates, totals

## Phone Feelings (user directive)

- **Bottom tab bar** (Home / Explore / Trip / Filters / Menu) on mobile
- Sticky confirm button above the tab bar
- Safe-area padding respected

## Signature Components

1. **Search Hero** — where, when, who in one row; price never hidden
2. **Date Grid** — nightly prices printed on open nights, sold-out explicit
3. **Listing Card** — photo, rating, mono price, wishlist heart
4. **Filter Rail** — active filters show their values inline
5. **Booking Summary** — all-in total before checkout, cancellation cutoff visible

## Sections (23)

Hero, Colors, Elevation, Typography, Spacing, Radius, Motion, Search Hero, Date Grid, Listing Card, Filter Rail, Booking Summary, Buttons, Chips, Forms, Host Tiers, UX Principles, Engineering, Accessibility, Security, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Marketplace Booking" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example listings, dates, prices, cities
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (confident glide curves)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Price Clarity / Search Flow / Trust Surfaces)
- Engineering Principles section
- Component structural CSS (layout, not color)
- The `prefers-reduced-motion` block (covers animation + transition globally, not just nav)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

---

## Audit Log — 2026-09-17

Same base template as System 05 (Social Realtime), so two of the bugs found here are
the same defect inherited from the shared scaffold, not independent mistakes —
worth knowing if you're patching across all 10 systems rather than one at a time.

1. **Off-palette hover color (template-level bug).** `.btn-outline-pill:hover` used
   `rgba(225,29,72,0.06)` — the exact same stray berry/rose value found in System
   05, on a button whose actual color is `var(--secondary)` (indigo, `#818cf8`
   here). Confirms this leaked in from whatever archetype originated the base
   template, not from a one-off copy-paste in this file. Fixed to an indigo tint,
   `rgba(129,140,248,0.12)`.

2. **Duplicated `.bottom-nav` block (template-level bug).** Same pattern as
   System 05: the mobile bottom-nav rules were defined correctly once inside
   `@media(max-width:1023px)`, then defined again — verbatim, unscoped — dangling
   at the end of the stylesheet, so it applied at every breakpoint instead of
   just mobile. Also carried a dead `:root{--sidebar-w:264px}` tacked onto its
   last line. Removed the duplicate block entirely; the media-query-scoped
   original was already correctly colored in this file (unlike System 05, the
   warm brown shadow tint here is actually on-palette for an amber/charcoal
   system, so nothing needed recoloring — just de-duplicating).

3. **`prefers-reduced-motion` too narrow.** Same gap as System 05: the query
   only killed transitions on sidebar/nav elements, leaving every card hover
   lift, button glide, and the UX-card 3D flip animating regardless of the
   user's OS setting. This system has no infinite `@keyframes` animations to
   worry about (no pulsing dots here), so the fix was simpler than System 05:
   broadened the query to zero out animation and transition duration on every
   element. The flip cards stay fully functional — only the animation speed
   changes, not the toggle logic.

4. **"Copy as MD" missed every signature component.** Bigger gap here than
   System 05: this system's whole point is Search Hero, Date Grid, Listing
   Card, Filter Rail, and Booking Summary — none of which the generic export
   function recognized. All five would previously export as just their intro
   sentence, dropping the destination input, the actual per-night prices, the
   listing details, the active filter pills, and the full price breakdown.
   Added dedicated handlers for all five, plus carried over the pricing-card,
   flip-card, icon-card, chip, and button handlers already fixed in System 05.

5. **Housekeeping.** Stripped the UTF-8 BOM and normalized CRLF/LF to LF, same
   as System 05.

What held up without changes: the `:root` token blocks in both themes are
internally consistent with no invalid CSS (unlike System 05's light-theme
`rgba` typo — this file didn't have that particular bug). Radius, spacing, and
motion scales match the Uniqueness Matrix spec for this system exactly. All 23
sidebar nav anchors and all bottom-nav links resolve to real section IDs. Tags
balance, JS has no syntax errors. The Security and Engineering section content
makes no claims the code contradicts — unlike System 05's false "springs
disabled" line, there was nothing here to correct on the copy side.
