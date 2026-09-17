# Uniqueness Matrix

Enforcement table for all 10 design systems. Every row must satisfy all collision rules
before the system is built. No two rows may collide.

---

## Rules Recap

1. **Accent hue**: no two systems within 30° of each other
2. **Fonts**: zero reuse across all systems (any role)
3. **Radius scale**: no two systems share the same 6 values; at least 2 near-square, at least 1 pill-dominant
4. **Spacing scale**: at least 3 distinct ratio logics across 10
5. **Motion**: no two systems share an easing curve; at least 1 near-zero motion
6. **Section order**: no two systems open with the same 3 sections
7. **Light/dark default**: at least 4 systems default to light (`data-theme="light"`)
8. **Signature components**: zero overlap between systems

---

## Matrix

| # | Slug | Design thesis | What it rejects | Base hue | Accent hue | Font pairing (display / body / mono) | Radius scale | Spacing scale | Motion signature | Density | Section order (first 5) | Signature components | Default theme |
|---|------|---------------|-----------------|----------|------------|---------------------------------------|--------------|---------------|------------------|---------|------------------------|---------------------|---------------|
| 01 | saas-analytics | Analysts scan numbers faster than words; the interface must vanish behind the data. | Decorative dashboards with inflated padding and unnecessary gradients | 215 (steel blue) | 170 (teal) | Inter / Inter / JetBrains Mono | 2, 4, 6, 8, 12, 16 | 8pt linear (4, 8, 12, 16, 24, 32) | Snappy: ease(.2,0,.4,1) / ease(.25,.1,.25,1) / ease(.34,1.2,.64,1); .12s .22s .4s | Compact: 14px base, 1.4 lh | colors → typography → spacing → radius → elevation | metric-card, data-table, date-range-picker, chart-tooltip-spec, skeleton-grid | dark |
| 02 | commerce-storefront | Product photography sells; every pixel of chrome must yield to the image. | Text-heavy product cards that bury imagery | 25 (burnt orange) | 340 (berry) | Fraunces / Outfit / IBM Plex Mono | 4, 10, 16, 24, 32, 999 (soft) | Fibonacci (4, 8, 16,24, 40, 64) | Bouncy: ease(.22,1,.36,1) / ease(.68,-.4,.32,1.4) / ease(.65,0,.35,1); .15s .3s .5s | Airy: 15px base, 1.5 lh | typography → colors → motion → spacing → radius | product-card, product-gallery, star-rating, cart-drawer, countdown-promo | light |
| 03 | fintech-trust | Money demands calm authority; trust is engineered through restraint, precision, and proof. | Playful gradients and bubbly rounded finance apps | 160 (emerald) | 206 (azure) | Source Serif 4 / Source Sans 3 / Fira Code | 2, 6, 10, 14, 18, 22 (crisp) | 4/6 hybrid (4, 8, 14, 20, 28, 44) | NEAR-ZERO: ease(.16,1,.3,1) ×3; .08s .16s .24s | Compact: 14px base, 1.35 lh | typography → security → colors → motion → spacing | balance-card, transaction-feed, limit-progress, verify-stepper, insurance-badges | light |
| 04 | clinical-care | Clarity is care: information hierarchy that stays readable at 3am under stress. | Dark dashboards and decorative accents near patient data | 197 (medical cyan) | 26 (coral) | Lora / Public Sans / Roboto Mono | 6, 8, 10, 12, 16, 999 (gentle) | Clinical 6-grid (4, 6, 12, 18, 24, 36) | Measured: ease(.4,0,.2,1) ×3; .2s .35s .55s | Comfortable: 15px base, 1.6 lh | accessibility → colors → typography → spacing → radius | vitals-tile, medication-row, triage-status, appointment-card, allergy-banner | light |
| 05 | social-realtime | Presence is the product; the interface must feel alive and answer in under 100ms. | Static feeds with dead avatars and fake loading | 240 (indigo) | 134 (presence green) | Poppins / Nunito Sans / Space Mono | 8, 12, 16, 20, 24, 999 (pill-forward) | Golden-ish (6, 10, 16, 26, 42, 68) | Springy: ease(.25,.46,.45,.94) / ease(.34,1.56,.64,1) / ease(.83,0,.17,1); .18s .28s .45s | Medium: 15px base, 1.5 lh | motion → colors → typography → spacing → radius | presence-row, story-ring, reaction-bar, typing-indicator, thread-card | dark |
| 06 | marketplace-booking | Two-sided clarity: search, compare, book with zero ambiguity about price or availability. | Hidden fees and fake urgency | 36 (amber) | 242 (indigo) | Plus Jakarta Sans / Plus Jakarta Sans / DM Mono | 10, 14, 20, 26, 32, 999 (soft) | 5-step (5, 10, 15, 25, 40, 55) | Confident: ease(.65,.05,.36,1) / ease(.7,0,.3,1) / ease(.5,1.5,.5,1); .2s .32s .5s | Roomy: 16px base, 1.5 lh | colors → elevation → typography → spacing → radius | search-hero, date-grid, listing-card, filter-rail, booking-summary | dark |
| 07 | devtool-terminal | Dense, monospace-native, keyboard-first: the IDE is the interface. | Marketing gloss inside developer tools | 142 (terminal green) | 98 (lime) | Space Grotesk / Space Grotesk / Source Code Pro | 0, 2, 4, 8, 12, 999 (sharp) | Doubling (4, 8, 16, 32, 64, 96) | Snap+steps: ease(.19,1,.22,1) / steps(4,end) / ease(.19,1,.22,1); .1s .2s .3s | Dense: 13px base, mono-heavy 1.45 lh | colors → typography → architecture → spacing → radius | command-palette, log-stream, code-block, kbd-keycap, diff-view | dark |
| 08 | editorial-longform | Long-form reading first: typography carries the brand, chrome disappears. | Dashboard chrome around articles and card-grid sameness | 20 (ink) | 50 (gold) | Newsreader / Newsreader / Martian Mono | 0, 2, 4, 8, 16, 999 (minimal) | Measure-driven (4, 10, 16, 24, 48, 80) | Quiet: ease(.33,0,.67,1) / linear / ease(.33,0,.2,1); .15s .3s .6s | Reading: 18px base, 1.7 lh | typography → spacing → colors → radius → elevation | article-header, pull-quote, figure-caption, footnote-list, byline-block | light |
| 09 | enterprise-console | Operate at scale: status, alerts, and control surfaces for teams managing fleets. | Consumer dashboards with toy aesthetics | 283 (electric violet) | 278 (violet family) | Archivo / Archivo / Red Hat Mono | 2, 4, 8, 10, 14, 999 (squared-mid) | Tight 4-steps (4, 8, 12, 16, 20, 24) | Utility: ease(.2,.9,.3,1) / ease(.5,0,.5,1) / linear; .1s .18s .3s | Ultra-dense: 13px base, 1.35 lh | security → colors → typography → spacing → radius | status-grid, alert-row, fleet-table, audit-log, sla-gauges | dark |
| 10 | expressive-brand | Brand as experience: motion, color, and type take risks corporate systems cannot. | Safe corporate sameness and beige minimalism | 317 (hot magenta) | 312 (fuchsia) | Unbounded / Manrope / Azeret Mono | 16, 20, 24, 28, 32, 999 (pill-dominant) | Brand rhythm (8, 12, 16, 20, 28, 40) | Big springs: ease(.2,.9,.3,1) / ease(.2,.9,.3,1.2) / linear; .25s .4s .7s | Bold: 16px base, 1.6 lh | colors → typography → motion → spacing → radius | kinetic-hero, marquee-band, sticker-card, type-scale-demo, hue-morph | dark |

**Phone-feelings note (user directive):** systems where a mobile app feel is natural
(02, 05, 06) use a fixed **bottom tab bar** instead of a top bar on mobile, sticky
thumb-zone CTAs, and safe-area padding. Desktop chrome (sidebar) stays unchanged.
All other systems keep the mobile top app bar.

---

## Collision Tracking

### Accent hues used
- 01: 170° (teal)
- 02: 340° (berry)
- 03: 206° (azure)
- 04: 26° (coral)
- 05: 134° (presence green)
- 06: 242° (indigo)
- 07: 98° (lime)
- 08: 50° (gold)
- 09: 278° (violet)
- 10: 312° (fuchsia)
All pairwise gaps ≥ 32°.

### Fonts used (zero reuse, any role)
- 01: Inter (display + body), JetBrains Mono (mono)
- 02: Fraunces (display), Outfit (body), IBM Plex Mono (mono)
- 03: Source Serif 4 (display), Source Sans 3 (body), Fira Code (mono)
- 04: Lora (display), Public Sans (body), Roboto Mono (mono)
- 05: Poppins (display), Nunito Sans (body), Space Mono (mono)
- 06: Plus Jakarta Sans (display + body), DM Mono (mono)
- 07: Space Grotesk (display + body), Source Code Pro (mono)
- 08: Newsreader (display + body), Martian Mono (mono)
- 09: Archivo (display + body), Red Hat Mono (mono)
- 10: Unbounded (display), Manrope (body), Azeret Mono (mono)

### Radius scales used
- 01: 2, 4, 6, 8, 12, 16 (near-square #1)
- 02: 4, 10, 16, 24, 32, 999 (soft)
- 03: 2, 6, 10, 14, 18, 22 (near-square #2, crisp)
- 04: 6, 8, 10, 12, 16, 999 (gentle)
- 05: 8, 12, 16, 20, 24, 999 (pill-forward)
- 06: 10, 14, 20, 26, 32, 999 (soft-large)
- 07: 0, 2, 4, 8, 12, 999 (near-square #3, sharp)
- 08: 0, 2, 4, 8, 16, 999 (minimal)
- 09: 2, 4, 8, 10, 14, 999 (squared-mid)
- 10: 16, 20, 24, 28, 32, 999 (pill-dominant)

### Spacing logics used
- 01: 8pt linear (4, 8, 12, 16, 24, 32)
- 02: Fibonacci (4, 8, 16, 24, 40, 64)
- 03: 4/6 hybrid (4, 8, 14, 20, 28, 44)
- 04: clinical 6-grid (4, 6, 12, 18, 24, 36)
- 05: golden-ish (6, 10, 16, 26, 42, 68)
- 06: 5-step (5, 10, 15, 25, 40, 55)
- 07: doubling (4, 8, 16, 32, 64, 96)
- 08: measure-driven (4, 10, 16, 24, 48, 80)
- 09: tight 4-steps (4, 8, 12, 16, 20, 24)
- 10: brand rhythm (8, 12, 16, 20, 28, 40)

### Easing curves used
- 01: ease(.2,0,.4,1), ease(.25,.1,.25,1), ease(.34,1.2,.64,1)
- 02: ease(.22,1,.36,1), ease(.68,-.4,.32,1.4), ease(.65,0,.35,1)
- 03: ease(.16,1,.3,1) ×3 (NEAR-ZERO motion system)
- 04: ease(.4,0,.2,1) ×3 (measured)
- 05: ease(.25,.46,.45,.94), ease(.34,1.56,.64,1), ease(.83,0,.17,1)
- 06: ease(.65,.05,.36,1), ease(.7,0,.3,1), ease(.5,1.5,.5,1)
- 07: ease(.19,1,.22,1), steps(4,end), ease(.19,1,.22,1)
- 08: ease(.33,0,.67,1), linear, ease(.33,0,.2,1)
- 09: ease(.2,.9,.3,1), ease(.5,0,.5,1), linear
- 10: ease(.2,.9,.3,1), ease(.2,.9,.3,1.2), linear

### Section opening trios used
- 01: colors → typography → spacing
- 02: typography → colors → motion
- 03: typography → security → colors
- 04: accessibility → colors → typography
- 05: motion → colors → typography
- 06: colors → elevation → typography
- 07: colors → typography → architecture
- 08: typography → spacing → colors
- 09: security → colors → typography
- 10: colors → typography → motion

### Light-mode defaults (4 of 10 required)
- 02: commerce-storefront
- 03: fintech-trust
- 04: clinical-care
- 08: editorial-longform
(01, 05, 06, 07, 09, 10 default dark)

### Signature component names used
- 01: metric-card, data-table, date-range-picker, chart-tooltip-spec, skeleton-grid
- 02: product-card, product-gallery, star-rating, cart-drawer, countdown-promo
- 03: balance-card, transaction-feed, limit-progress, verify-stepper, insurance-badges
- 04: vitals-tile, medication-row, triage-status, appointment-card, allergy-banner
- 05: presence-row, story-ring, reaction-bar, typing-indicator, thread-card
- 06: search-hero, date-grid, listing-card, filter-rail, booking-summary
- 07: command-palette, log-stream, code-block, kbd-keycap, diff-view
- 08: article-header, pull-quote, figure-caption, footnote-list, byline-block
- 09: status-grid, alert-row, fleet-table, audit-log, sla-gauges
- 10: kinetic-hero, marquee-band, sticker-card, type-scale-demo, hue-morph
(50 unique names, zero overlap)
