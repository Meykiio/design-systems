# Clinical Care Design System

**System 04** — Medical Cyan & Coral

Design thesis: Clarity is care — information hierarchy that stays readable at 3am under stress.

What it rejects: Dark dashboards and decorative accent colors anywhere near patient data.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#0e7490` Medical Cyan (light) / `#22d3ee` (dark) |
| Secondary | `#f97316` Coral (actionable alerts) |
| Tertiary | `#a16207` Amber (caution) |
| Quaternary | `#8b5cf6` Lavender (informational links) |
| Base | Cool paper white `#f8fbfc` |
| Radius scale | 6, 8, 10, 12, 16, pill (gentle) |
| Spacing scale | Clinical 6-grid (4, 6, 12, 18, 24, 36) |
| Motion | Measured: `(.4,0,.2,1)`, .2s .35s .55s — no bounce |
| Density | Comfortable: 15px base, 1.6 lh |
| Default theme | Light |

## Fonts

- **Display**: Lora (Google Fonts)
- **Body**: Public Sans (Google Fonts)
- **Mono**: Roboto Mono (Google Fonts) — all lab values and dosages

## Signature Components

1. **Vital Tile** — mono value + reference range + state pill (in range / elevated / low)
2. **Medication Row** — checkable schedule rows with mono dosage
3. **Triage Status Card** — urgency via left border + tag (critical / urgent / routine)
4. **Appointment Card** — date block, clinic, provider, mono time
5. **Allergy Banner** — persistent, staff-only dismissal, never accidental

## Sections (24)

Hero, Accessibility Leads, Colors, Typography, Motion, Spacing, Radius, Elevation, Vitals Tiles, Medication Row, Triage Status, Appointment Card, Allergy Banner, Buttons, Chips, Intake Form, Lab Results, Care Plans, UX Principles, Engineering, Security, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Clinical Care" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example vitals, medications, lab values, plan copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (measured durations .2/.35/.55s, no bounce)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Safety-Critical Display / Error Prevention / Plain Language)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

---

## Audit Log — v0.4.1

Reviewed against `TEMPLATE-ANALYSIS.md` and `UNIQUENESS-MATRIX.md`. Fixed:

1. **WCAG contrast failure on the outline-coral button — the most serious issue found.** `.btn-outline-pill` rendered its text in `--secondary` (`#f97316`) directly on the light background: **2.7:1**, well under the 4.5:1 AA floor. This directly contradicted the system's own Accessibility Leads section, which states "4.5:1 normal text... verified on both themes and all status tints." The button's hover state also used `rgba(225,29,72,0.06)` — a rose/crimson value with no relationship to this system's coral hue, evidently leaked in from another system's palette. Fixed by retuning `--secondary-dim` (light theme) to `#c2410c`, a same-hue shade that hits 4.98:1, and using it for the button text and a corrected coral-toned hover fill. Dark mode was already compliant (8.23:1) and is unaffected.
2. **Malformed table row.** The Creatinine row in the Lab Results table had a stray extra `</div>` inside its status cell, which cascades into real tag-mismatch errors for everything downstream in a strict parser. Removed.
3. **A UX principle card missing its flip-back wrapper.** The "Look-Alike Names" card (Error Prevention group) was missing its entire `<div class="ux-card-face-back">` element — the rule text sat as a orphaned sibling instead of the card's back face, breaking the click-to-flip interaction for that one card and leaving the HTML structurally unbalanced from that point forward. Rebuilt to match the other 8 cards' structure. Also corrected its copy to the actual clinical term, "tall-man lettering" (e.g. hydrOXYzine vs. hydrALAZINE), in place of the vaguer original phrasing.
4. **Dead cross-contamination from the phone-feel systems**, identical to what was found in fintech-trust (03): ~700 bytes of unused `.bottom-nav`/`.bn-item`/`.bn-badge` CSS plus a whole duplicate, unused mobile-nav media-query block, both leaked in from the 02/05/06 template variants. Clinical-care is correctly top-bar-only per the matrix — the real, working top-bar block (still carrying a stray comment literally reading "fintech keeps a top bar," another copy-paste tell) is now the only mobile-nav block in the file.
5. **Undefined motion token.** `--ease-instant` was referenced 4 times in the real mobile-nav block but never defined in `:root`, so the menu toggle, sidebar backdrop, and nav-group reveal were silently falling back to default browser easing instead of this system's measured `(.4,0,.2,1)` curve. Added as the canonical token.
6. **Duplicate patient identifier.** Two different triage cards both read "Bed 7" (M. Ito and P. Naidoo) — a data slip in a patient-safety-themed demo where bed uniqueness matters. Changed one to Bed 3.
7. **Incomplete "Copy as MD" export**, same root cause as fintech-trust: `getMarkdown()` only handled typography rows and color swatches. Vitals, Medication Rows, Triage Cards, Appointment Cards, the Allergy Banner, Accessibility/Foundations cards, Buttons, Chips, UX Principles, Care Plans, and the Lab Results table were all exporting as an empty heading with no content. Added proper handlers for all of them.
8. **UTF-8 BOM** at the top of the file. Stripped.

Verified and left unchanged: token values (color, radius, spacing, motion durations) match this README exactly; section order matches the uniqueness matrix's registered opening trio (accessibility → colors → typography); all five signature components are present with real, clinically-specific content (not placeholder text); the rest of the palette (primary cyan, tertiary amber, muted text, error red) passes ≥4.5:1 on the light background; HTML tag balance and JS syntax both validated clean after fixes.