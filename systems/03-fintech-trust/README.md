# Fintech Trust Design System

**System 03** — Emerald & Azure

Design thesis: Money demands calm authority; trust is engineered through restraint, precision, and proof.

What it rejects: Playful gradients and bubbly rounded finance apps that feel unserious.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#047857` Emerald (light) / `#34d399` (dark) |
| Secondary | `#0369a1` Azure (links, info) |
| Tertiary | `#a16207` Amber (pending, holds) |
| Quaternary | `#6d28d9` Violet (rare) |
| Base | Cool mint-tinted white `#f7faf9` |
| Radius scale | 2, 6, 10, 14, 18, 22px (crisp) |
| Spacing scale | 4/6 hybrid (4, 8, 14, 20, 28, 44) |
| Motion | NEAR-ZERO: instant `(.16,1,.3,1)`, .08s .16s .24s |
| Density | Compact: 14px base, 1.35 lh |
| Default theme | Light |

## Fonts

- **Display**: Source Serif 4 (Google Fonts)
- **Body**: Source Sans 3 (Google Fonts)
- **Mono**: Fira Code (Google Fonts) — all money figures

## Signature Components

1. **Balance Card** — mono figures, masked account number, status chip
2. **Transaction Feed** — category icons, mono amounts, status metas
3. **Credit Limit Progress** — three utilization states (ok / warn / critical)
4. **Verification Stepper** — persistent 4-step identity verification
5. **Insurance Badge Row** — FDIC / SOC 2 / SIPC proof badges with links

## Sections (24)

Hero, Typography, Colors, Security First, Motion, Spacing, Radius, Elevation, Balance Card, Transaction Feed, Limit Progress, Verify Stepper, Insurance Badges, Buttons, Chips, Forms, Ledger Table, Account Tiers, UX Principles, Engineering, Accessibility, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Fintech Trust" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example balances, transactions, fee copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (near-zero durations .08/.16/.24s)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Security Perception / Data Display / Error Prevention)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

---

## Audit Log — v0.3.1

Reviewed against `TEMPLATE-ANALYSIS.md` and `UNIQUENESS-MATRIX.md`. Fixed:

1. **Stray text leaking into the rendered page.** A raw `:root{--sidebar-w:264px;--topbar-h:56px}` sat in the HTML body (outside any `<style>` tag), between the Security and Motion sections — it would have rendered as literal visible text on the page. Removed.
2. **Dead cross-contamination from the phone-feel systems.** ~700 bytes of `.bottom-nav`/`.bn-item`/`.bn-badge` CSS (a fixed bottom tab bar) had leaked in from the 02/05/06 template variants, alongside a duplicate, unused mobile-nav media query block using non-canonical easing var names. Fintech-trust is correctly a top-bar system per the matrix's phone-feelings note — the dead CSS never had matching markup, but it bloated the file and risked confusion for future edits. Removed entirely; the real, working top-bar mobile block (correctly commented `/* fintech keeps a top bar on mobile — contrast with commerce/social */`) is now the only one.
3. **Undefined motion token.** The header comment and mobile chrome both reference `--ease-instant`, but `:root` only defined `--ease-out-soft` / `--ease-back` / `--ease-glide` — so every mobile topbar/menu/backdrop transition was silently falling back to the browser default `ease` instead of the intended near-zero curve. Added `--ease-instant` as the canonical token (kept the other three as aliases so nothing else breaks).
4. **Incomplete "Copy as MD" export.** `getMarkdown()` only handled typography rows and color swatches — Buttons, Chips, Ledger Table, Account Tiers, UX Principles, Balance Card, Transaction Feed, Security, and Forms sections silently exported as just a heading + description, with no actual content. Added proper handlers for button variants, chips, UX flip-cards (grouped by principle category), balance/security cards, the ledger table (real Markdown table), and form labels.
5. **UTF-8 BOM at the top of the file.** Some parsers/build tools choke on a leading BOM before `<!DOCTYPE html>`. Stripped.

Verified and left unchanged: token values match this README (radius, spacing, motion durations, hex codes), section order matches the uniqueness matrix's registered opening trio (typography → security → colors), all five signature components are present and content-accurate (not placeholder text), WCAG contrast checked at ≥4.5:1 for primary/secondary/tertiary/muted text on the light-theme background, and HTML tag balance / JS syntax both validated clean.
