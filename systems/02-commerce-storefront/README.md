# Commerce Storefront Design System

**System 02** — Burnt Orange & Berry

Design thesis: Product photography sells; every pixel of chrome must yield to the image.

What it rejects: Text-heavy product cards that bury imagery.

---

## Audit Log — Reference Build 02

Audited against the same standard as System 01: structural integrity, token-contract compliance, and internal data consistency across sections — not just visual correctness. Issues found and fixed:

| # | Issue | Severity | Fix |
|---|-------|----------|-----|
| 1 | UTF-8 BOM at file start + 28 mixed CRLF lines in an otherwise-LF file | Structural | Stripped BOM, normalized to LF throughout. Same issue as System 01 — likely from the same authoring/export step, worth checking the remaining 8 systems for it too. |
| 2 | Bottom-nav "Search" tab linked to `#forms` (the checkout form section: email, shipping address, discount code) | Broken reference | There's no dedicated search section in this file. Retargeted "Search" to `#product-gallery`, the closest thing to a browse/discover surface here. Flagging this rather than treating it as fully solved — if a future system adds real search/browse UI, this tab should point there instead. |
| 3 | `.bn-badge` (cart count badge on the bottom-nav Bag icon) used a hardcoded `color:#fff` instead of `var(--on-secondary)` | Rule violation | Replaced with the token. Same class of bug as System 01's chip fix — it happened to render fine in both themes here only because `--on-secondary` is white in both, but it was one recolor away from breaking. |
| 4 | Cart drawer free-shipping bar showed 86% fill, but the displayed numbers ($197.99 subtotal + "$12.00 more") imply a $209.99 threshold — that's 94%, not 86% | Data/logic bug | Corrected the fill to 94% so the bar actually matches the dollar amounts next to it. A demo whose own numbers don't agree with its own progress bar is exactly the kind of thing that gets copy-pasted wrong into a real build. |
| 5 | Engineering Principles: "Image Ratio Lock" rule read "Product media keeps a 1:1 ratio (4:3 in gallery)" — self-contradictory as written | Clarity bug | The underlying CSS is actually correct and intentional (`.pc-media` is 1:1, `.gallery-main` is 4:3) — the rule just garbled two true facts into one confusing sentence. Rewrote it to state both clearly: "Product card media is locked 1:1. The gallery's main image is locked 4:3." |
| 6 | All 133 decorative `<svg>` icons had no `aria-hidden="true"` (worse than System 01, which had none either — pattern confirmed across both files) | Accessibility | Added to all of them. Every nav item, button icon, star rating icon, and theme toggle glyph was previously exposed to screen readers as unlabeled graphics content. |

**Confirmed correct (checked, not assumed):**
- Section order matches the required opening trio for System 02 (`typography → colors → motion`) from the Uniqueness Matrix.
- `copyAllAsMarkdown()` reads section IDs directly from the live DOM instead of a hardcoded array (unlike System 01) — there's no way for this file's export tool to drift from its own section order. Worth carrying this pattern back into System 01 if you want one shared JS approach.
- Cart subtotal math: $89.99 (shirt, qty 1) + $108.00 (pour-over set, qty 2 combined) = $197.99. Correct.
- Cart item count ("3 items") = 1 + 2 units across 2 line items. Correct, not a bug.
- Star ratings: every filled/dim star count matches its displayed numeric rating (3.0 → 3 filled + 2 dim, 4.0 → 4 filled + 1 dim, etc.) across all rating blocks and review cards.
- 12-swatch color palette, both themes complete, no missing dark-mode overrides.
- Bottom tab bar, sticky add-to-bag, and safe-area padding (the "Phone Feelings" mobile-app directive specific to this system) are all actually implemented in CSS, not just described in prose.

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#d9480f` Burnt Orange (light) / `#fb923c` (dark) |
| Secondary | `#e11d48` Berry (sale flags) |
| Tertiary | `#b45309` Amber (star ratings) |
| Quaternary | `#0d9488` Teal (rare accents) |
| Base | Warm cream `#faf7f4`, low-chroma neutrals |
| Radius scale | 4, 10, 16, 24, 32, pill (soft) |
| Spacing scale | Fibonacci (4, 8, 16, 24, 40, 64) |
| Motion | out-soft `(.22,1,.36,1)`, back `(.68,-.4,.32,1.4)`, glide `(.65,0,.35,1)` |
| Durations | .15s .3s .5s |
| Density | Airy: 15px base, 1.5 lh |
| Default theme | Light |

## Fonts

- **Display**: Fraunces (Google Fonts)
- **Body**: Outfit (Google Fonts)
- **Mono**: IBM Plex Mono (Google Fonts) — all prices

## Phone Feelings (user directive)

On mobile (<1024px) this system behaves like an app:

- **Bottom tab bar** (Home / Shop / Bag / Search / Menu) replaces top navigation
- **Sticky add-to-bag** bar pinned above the tab bar on product pages
- **Safe-area padding** (`env(safe-area-inset-bottom)`) respected
- Thumb-zone: primary actions live in the bottom third

## Signature Components

1. **Product Card** — full-bleed media, brand line, title, stars, mono price, CTA
2. **Star Rating** — filled/dim stars + review count
3. **Product Gallery** — 4:3 main + active thumbnail ring + zoom hint
4. **Cart Drawer** — slide-in bag, free-shipping progress, qty steppers (live demo)
5. **Countdown Promo Bar** — berry band, live mono timer, pill CTA

## Sections (26)

Hero, Typography, Colors, Motion, Spacing, Radius, Elevation, Product Card, Star Rating, Product Gallery, Cart Drawer, Countdown Promo, Buttons, Chips, Reviews, Forms, Orders Table, Membership Pricing, UX Principles, Engineering, Accessibility, Security, Performance, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Commerce Storefront" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example products, prices, ratings, promo copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (`--ease-out-soft`, `--ease-back`, `--ease-glide`, `--dur-*`)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Conversion / Trust / Thumb-First Mobile)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` (Copy as MD buttons, scroll progress bar, their JS) is tooling for reading this reference — not a UI pattern.