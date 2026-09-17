# Expressive Brand Design System

**System 10** — Ink & Magenta

Design thesis: Brand as experience — motion, color, and type take risks corporate systems cannot.

What it rejects: Safe corporate sameness and beige minimalism.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#e04fa4` Hot Magenta (dark canonical) / `#c2185b` (light) |
| Secondary | `#d946ef` Fuchsia (kinetic accents) |
| Tertiary | `#bef264` Lime (energy marks) |
| Quaternary | `#fde047` Yellow (highlights) |
| Base | Ink black `#0d0b10`, warm charcoal surfaces |
| Radius scale | 16, 20, 24, 28, 32, pill (pill-dominant) |
| Spacing scale | Brand rhythm (8, 12, 16, 20, 28, 40) |
| Motion | Big springs: `(.2,.9,.3,1)`, `(.2,.9,.3,1.2)`, linear; .25s .4s .7s |
| Density | Bold: 16px base, 1.6 lh |
| Default theme | Dark |

## Fonts

- **Display**: Unbounded (Google Fonts)
- **Body**: Manrope (Google Fonts)
- **Mono**: Azeret Mono (Google Fonts) — version marks, meta labels

## Signature Components

1. **Kinetic Hero** — display type with highlight flips
2. **Marquee Band** — infinite ticker, pauses on hover
3. **Sticker Card** — rounded, tilted, tactile; two per page max
4. **Type Scale Demo** — three sizes, one voice
5. **Hue Morph Button** — magenta-to-fuchsia morph with tilt on hover

## Sections (23)

Hero, Colors, Typography, Motion, Spacing, Radius, Elevation, Kinetic Hero, Marquee Band, Sticker Card, Type Scale, Hue Morph, Buttons, Chips, Forms, Pricing, UX Principles, Engineering, Accessibility, Security, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Expressive Brand" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example copy, manifesto lines, sticker copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (big springs with overshoot)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Risk With Discipline / Motion As Asset)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

## Audit Notes (this pass)

Like the other systems in this series, the shipped file had copy-paste residue and a few genuine bugs. Fixed:
- **22 of 23** "Copy as MD" button icons had a truncated SVG path and rendered a broken glyph — only the sidebar's global copy button had the correct path
- `.btn-outline-pill:hover` used a hardcoded rose/red hex left over from another system instead of this system's magenta glow token
- Undefined `--ease-instant` used in 4 mobile-nav transitions (menu toggle, backdrop, nav stagger) — fell back to default browser easing instead of this system's big-spring motion signature. Replaced with the defined `--ease-out-soft` token
- Removed dead `.bottom-nav`/`.bn-*` CSS and a stray "fintech" comment carried over from another system's mobile nav — this system correctly uses a top app bar on mobile per the uniqueness matrix (it isn't one of the phone-feel systems)
- Two mojibake encoding artifacts (a mangled em dash in a CSS comment, and five mangled middle-dots in the typography spec strings)
- A duplicate `@keyframes mq` declaration (the second silently overrode the first — harmless but sloppy, removed)
- The Sticker Card section's copy button referenced `sticker-cards` (plural) while the section's actual id is `sticker-card` (singular), so the button silently did nothing — fixed the id reference
- The Colors section claimed "light theme is canonical for this build" — this contradicts the file's actual dark-canonical default (`data-theme="dark"`, the token comment, and this README all agree on dark). Corrected the copy
- The Responsive section's copy and mockup described a bottom tab bar ("Home / Work / Ship / Menu") that this build doesn't have — the system correctly implements a top app bar on mobile (per the uniqueness matrix, expressive-brand isn't a phone-feel system), so the description and mockup didn't match the actual implementation. Corrected both to reflect the top bar
- The Forms section markup (`.form-grid`, `.form-group`, `.form-input`, `.form-select`, `.form-textarea`) had **no CSS rules at all** — every form control rendered as unstyled browser-default HTML with labels running straight into inputs. Added the missing rules to match the section's own spec copy ("42px rounded inputs, 4px magenta focus glow"): pill-radius inputs, Manrope body font, magenta focus glow, styled select caret

No visual/structural changes beyond these fixes — palette, fonts, section set, and signature components are unchanged.