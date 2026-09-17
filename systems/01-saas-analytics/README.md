# SaaS Analytics Design System

**System 01** — Steel Blue & Teal

Design thesis: Analysts scan numbers faster than words; the interface must vanish behind the data.

What it rejects: Decorative dashboards with inflated padding and unnecessary gradients.

---

## Audit Log — Reference Build 01

Audited against `TEMPLATE-ANALYSIS.md` and `UNIQUENESS-MATRIX.md`. Section order, token set, component classes, and JS export map were all checked line-by-line against the spec. Issues found and fixed:

| # | Issue | Severity | Fix |
|---|-------|----------|-----|
| 1 | UTF-8 BOM at file start | Structural | Stripped. A BOM before `<!DOCTYPE html>` risks quirks-mode parsing in some tools/editors and has no reason to be there in a hand-authored template. |
| 2 | Mixed line endings (28 CRLF lines mixed into an otherwise-LF file) | Structural | Normalized to LF throughout. Matters because this file gets find/replaced and diffed by coding agents — mixed endings cause noisy diffs and inconsistent tooling behavior. |
| 3 | `.chip.filled:hover` used a hardcoded hex (`#2d6fdb`) instead of a token | Rule violation | Replaced with `filter:brightness(0.88)` on the existing token-driven background — now correctly darkens in both themes instead of only working (by coincidence) in dark mode. This was a direct violation of the system's own "CSS variables only, never hardcode colors" engineering principle. |
| 4 | Churn Rate metric card contradicted itself and the Data Table | Data/logic bug | The metric card showed `+0.3pp` with a red down-arrow (`.metric-delta.down`), implying churn got worse. The Data Table section — same page — shows churn actually improved from 2.8% → 2.1% (`-0.7pp`, green). Fixed the metric card to `-0.7pp` with `.metric-delta.up` (green, matches "improvement" semantics), so the number, color, arrow direction, sparkline shape, and the table row all now tell the same story. This is exactly the kind of inconsistency that makes a reference file untrustworthy to build from. |
| 5 | 71 decorative `<svg>` icons had no `aria-hidden="true"` | Accessibility | Added to all of them. These are purely decorative (nav icons, button icons, theme toggle glyphs) — without `aria-hidden`, screen readers may announce blank/confusing icon nodes on every nav item and button. |

**Confirmed correct (checked, not assumed):**
- Section order in HTML exactly matches the `copyAllAsMarkdown()` id array (26/26) — no drift between the live page and the export tool.
- 12-swatch color palette (5 gray, 3 hue, 4 functional) — matches spec.
- Motion tokens (`--ease-snappy/smooth/spring`, `--dur-fast/med/slow`) are defined once and referenced consistently everywhere they're used — no orphaned or mismatched values.
- Both themes (dark default, light variant) have complete token sets — no missing light-mode overrides.
- Radius scale (2/4/6/8/12/16, near-square) and spacing scale (8pt linear) match the Uniqueness Matrix row for System 01, no collisions with other systems' scales.

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#3b82f6` Steel Blue |
| Secondary | `#14b8a6` Teal |
| Tertiary | `#f59e0b` Amber |
| Quaternary | `#ec4899` Rose |
| Base hue | Neutral gray, no tint |
| Radius scale | 2, 4, 6, 8, 12, 16px (near-square) |
| Spacing scale | 8pt linear (4, 8, 12, 16, 24, 32) |
| Motion | ease-snappy, ease-smooth, ease-spring |
| Durations | .12s .22s .4s |
| Density | Compact: 14px base, 1.4 lh |
| Default theme | Dark |

## Fonts

- **Display**: Inter (Google Fonts)
- **Body**: Inter (Google Fonts)
- **Mono**: JetBrains Mono (Google Fonts)

## Signature Components

1. **Metric Card** — delta arrows + sparkline bars + tabular-nums
2. **Dense Data Table** — sort indicators, status dots, avatar cells
3. **Date Range Picker** — dropdown calendar + preset chips
4. **Chart Tooltip** — color-coded rows, mono-aligned values
5. **Skeleton Grid** — shimmer loading placeholders

## Sections (26)

Hero, Colors, Typography, Spacing, Radius, Elevation, Motion, Buttons, Pricing, Cards, Chips, Forms, Table, Metric Card (Signature Components), Dense Data Table, Date Range Picker, Chart Tooltip, Skeleton Loading, UX Principles, Engineering, Accessibility, Security, Performance, Responsive, Touch Targets, Architecture

## How to Customize

1. Find/replace "SaaS Analytics" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example copy (metric values, table rows, chart labels)
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (`--ease-snappy`, `--ease-smooth`, `--ease-spring`, `--dur-*`)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` (Copy as MD buttons and their JS) is tooling for reading this reference — not a UI pattern.
