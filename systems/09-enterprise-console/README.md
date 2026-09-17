# Enterprise Console Design System

**System 09** — Electric Violet & Cyan

Design thesis: Operate at scale — status, alerts, and control surfaces for teams managing fleets.

What it rejects: Consumer dashboards with toy aesthetics.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#a855f7` Electric Violet (dark canonical) / `#7c3aed` (light) |
| Secondary | `#c084fc` Deep Violet (interactive) |
| Tertiary | `#fbbf24` Amber (warnings) |
| Quaternary | `#67e8f9` Cyan (info) |
| Base | Neutral dark `#0d0a12`, violet whisper |
| Radius scale | 2, 4, 8, 10, 14, pill-for-badges |
| Spacing scale | Tight 4-steps (4, 8, 12, 16, 20, 24) |
| Motion | Utility: `(.2,.9,.3,1)`, `(.5,0,.5,1)`, linear; .1s .18s .3s |
| Density | Ultra-dense: 13px base, 1.35 lh |
| Default theme | Dark |

## Fonts

- **Display**: Archivo (Google Fonts)
- **Body**: Archivo (Google Fonts)
- **Mono**: Red Hat Mono (Google Fonts) — node IDs, versions, thresholds

## Signature Components

1. **Status Grid** — per-service health tiles with state word + figure
2. **Alert Row** — severity pill, mono metadata, one-tap ack
3. **Fleet Table** — multi-select rows with checkers, dense columns
4. **Audit Log** — who/what/when, immutable, greppable
5. **SLA Gauge** — availability bars with exact figures

## Sections (23)

Hero, Security First, Colors, Typography, Spacing, Radius, Elevation, Motion, Status Grid, Alert Row, Fleet Table, Audit Log, SLA Gauges, Buttons, Chips, Forms, Licensing, UX Principles, Engineering, Accessibility, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Enterprise Console" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example alerts, fleet rows, audit lines, licensing copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (utility durations .1/.18/.3s)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Operate at Scale / Control Surfaces / On-Call Rhythm)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

## Audit Notes (this pass)

The shipped file had copy-paste residue from other systems in the series. Fixed:
- Two malformed `rgba()` tokens in the light theme (`--primary-glow-sm`, `--toggle-border` were missing a color channel, silently breaking their opacity)
- `.btn-outline-pill:hover` was using a hardcoded rose/red hex left over from another system instead of this system's violet glow token
- Undefined `--ease-instant` used in 4 mobile-nav transitions (menu toggle, backdrop, nav stagger) — fell back to default browser easing, so mobile nav silently didn't match the "utility motion" signature. Replaced with the defined `--ease-out-soft` token
- 3 "Copy as MD" button icons (Responsive, Touch, Architecture sections) had a truncated SVG path and rendered a broken glyph
- Removed dead `.bottom-nav`/`.bn-*` CSS and a stray "fintech" comment carried over from another system's mobile nav — this system correctly uses a top app bar on mobile per the uniqueness matrix (it isn't one of the phone-feel systems), so that code was unused dead weight

No visual/structural changes beyond these fixes — palette, fonts, section set, and signature components are unchanged.
