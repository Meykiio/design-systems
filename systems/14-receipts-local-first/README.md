# Receipts, Local-First Design System

**System 14** — Emerald & Saffron

Design thesis: Money records feel anxious when they live somewhere you do not control. The interface should read like a well-kept ledger sitting on your own desk — warm, quiet, and boring in the good sense.

What it rejects: Cloud-locked finance apps with a marketing dashboard bolted on, and decorative gradients wrapped around people's actual money.

---

## Audit Log — Reference Build 14

Audited against `TEMPLATE-ANALYSIS.md` and `UNIQUENESS-MATRIX.md`.

This system is an **imported real-product system** — it is the design system of the
Receipto app (GPL-3.0), added as-is rather than built from the whitelabel template.
Where it diverges from the strict collision rules, that is written down below instead
of papered over.

| # | Issue | Severity | Fix |
|---|-------|----------|-----|
| 1 | CRLF line endings throughout (2,709 lines) | Structural | Normalized to LF. Matches the rest of the repo and keeps diffs honest for tools that find/replace tokens. |
| 2 | All 57 decorative `<svg>` icons lacked `aria-hidden="true"` | Accessibility | Added. The glyphs are nav/theme/button icons, and the interactive parents already carry their own `aria-label`, so hiding the glyphs prevents duplicate announcements in screen readers. |

**Confirmed correct (checked, not assumed):**

- No UTF-8 BOM.
- Dark is the canonical theme (`<html data-theme="dark">`); the light variant at
  `[data-theme="light"]` defines a complete token set — no missing overrides.
- 111 CSS custom properties; the five accent tokens resolve in both themes.
- Interactive controls carry explicit `aria-label`s (menu toggle, theme toggle,
  sidebar, copy-as-Markdown).
- A "copy the whole system as Markdown" export ships inside the file.

**Known deviations from the Uniqueness Matrix (documented, deliberate):**

- Accent hue: emerald (~162°) sits within 30° of System 01's teal (170°).
- Font reuse: DM Sans (body) is also used by System 11.

Both are inherited from the shipped Receipto palette and are left intact on purpose —
recoloring or re-fonting it would stop it being the Receipto system. Systems 11–13 are
likewise imported real-product systems rather than matrix-built ones.

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#2fd6a3` Emerald-Teal (dark) · `#0b7e62` (light) |
| Secondary | `#f0b429` Saffron Gold (dark) · `#9a6b12` (light) |
| Tertiary | `#f28c6e` Coral (dark) · `#c2543c` (light) |
| Quaternary | `#a78bfa` Violet |
| Positive | `#4ade80` (dark) |
| Base hue | Warm ink-green tinted neutrals |
| Radius scale | 4, 8, 12, 16, 24, 9999 |
| Spacing scale | 4, 8, 16, 24, 48, 80 |
| Motion | `ease-out` cubic-bezier(.22,1,.36,1) · `ease-spring` cubic-bezier(.34,1.3,.64,1) |
| Durations | .18s · .3s · .55s |
| Density | Comfortable: 16px base, 1.5 line-height |
| Default theme | Dark |

## Fonts

- **Display**: Sora (Google Fonts)
- **Body**: DM Sans (Google Fonts)
- **Arabic**: Cairo (Google Fonts)

## Signature Components

1. **Receipt capture flow** — camera/file input, staged progress, review-before-save
2. **Money & receipts table** — tabular figures, right-aligned amounts, status chips
3. **RTL & Arabic panel** — Arabic is first-class here, not a mirror applied afterwards
4. **Tailwind & shadcn token map** — the live table mapping this palette onto the app's CSS variables

## Section Order (first 5)

Color Palette → Typography Scale → Spacing Scale → Border Radius Scale → Elevation & Depth
