# Social Realtime Design System

**System 05** — Indigo & Presence Green

Design thesis: Presence is the product; the interface must feel alive and answer in under 100ms.

What it rejects: Static feeds with dead avatars and fake loading states.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#818cf8` Indigo (dark canonical) / `#4f46e5` (light) |
| Secondary | `#4ade80` Presence green (online, active) |
| Tertiary | `#e879f9` Fuchsia (reactions) |
| Quaternary | `#fbbf24` Amber (streaks, badges) |
| Base | Deep neutral `#0d0d14` with violet whisper |
| Radius scale | 8, 12, 16, 20, 24, pill (pill-forward) |
| Spacing scale | Golden-ish (6, 10, 16, 26, 42, 68) |
| Motion | Springs: `(.25,.46,.45,.94)`, `(.34,1.56,.64,1)`, `(.83,0,.17,1)`; .18s .28s .45s |
| Density | Medium: 15px base, 1.5 lh |
| Default theme | Dark |

## Fonts

- **Display**: Poppins (Google Fonts)
- **Body**: Nunito Sans (Google Fonts)
- **Mono**: Space Mono (Google Fonts) — handles, counts, streak numbers, timestamps

## Phone Feelings (user directive)

- **Bottom tab bar** (Home / Feed / Post / Chat / Menu) on mobile
- Floating compose lives in the thumb zone
- Safe-area padding respected

## Signature Components

1. **Presence Row** — pulsing online dots, amber away, dim offline
2. **Story Ring** — conic-gradient ring for unseen, plus badge for own
3. **Reaction Bar** — SVG icons + mono counts, one-tap toggles
4. **Typing Indicator** — three staggered bouncing dots under 100ms
5. **Thread Card** — avatar with live dot, body, mono counts

## Sections (23)

Hero, Motion, Colors, Typography, Spacing, Radius, Elevation, Presence, Story Ring, Reactions, Typing, Thread Card, Buttons, Chips, Compose, Creator Tiers, UX Principles, Engineering, Accessibility, Security, Responsive, Touch, Architecture

## How to Customize

1. Find/replace "Social Realtime" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example handles, counts, reactions, thread copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (springs with overshoot)
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Liveness / Feed Reading / Thumb-First)
- Engineering Principles section
- Component structural CSS (layout, not color)
- The `prefers-reduced-motion` block (covers animation + transition globally, not just nav)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.

---

## Audit Log — 2026-09-17

Full read-through against the archetype's own thesis and the repo-wide template
contract. Six real bugs found and fixed, none cosmetic-only:

1. **Invalid CSS custom property (light theme).** `--primary-glow-sm` was
   `rgba(4f,46,229,0.07)` — a hex digit leaked into an `rgb()` arg, which is
   invalid and gets dropped by the parser. Every focus ring, hover glow, and
   the `.md-copy-btn` hover state in light mode silently lost that glow.
   Fixed to `rgba(79,70,229,0.07)`.

2. **Off-palette hover color.** `.btn-outline-pill:hover` used
   `rgba(225,29,72,0.06)` — a berry/rose value that exists in no token in
   this system (it belongs to a different archetype's accent family). Fixed
   to the system's actual presence-green tint, `rgba(74,222,128,0.1)`.

3. **Off-palette shadow tint, duplicated.** The mobile bottom-nav shadow used
   `rgba(60,30,10,...)` / `rgba(20,10,5,...)` — warm brown/amber values on a
   cool indigo-based dark UI. Worse, the entire `.bottom-nav`/`.bn-item`
   block was **defined twice**: once correctly inside
   `@media(max-width:1023px)`, and again, verbatim with the bad color,
   dangling unscoped at the end of the stylesheet — meaning it applied at
   every breakpoint, not just mobile. Removed the duplicate, fixed the tint
   on the original to a neutral indigo-black shadow.

4. **`prefers-reduced-motion` didn't do what the copy claims.** The
   Accessibility section states "All springs disabled under
   prefers-reduced-motion," but the actual media query only killed
   transitions on the sidebar/nav — not the presence-dot pulse (infinite
   animation), typing-dot bounce, story-ring hover scale, reaction hover,
   or the UX-card 3D flip. Rewrote the query to zero out animation and
   transition duration globally and explicitly stop the presence-dot pulse,
   so the claim is now true.

5. **"Copy as MD" silently dropped most sections.** The export function only
   knew how to read two shapes (`.type-row`, `.color-swatch`); everything
   else — Creator Tiers pricing cards, all 20 UX-principle flip-cards, the
   6 accessibility rules, engineering principles, architecture/security
   cards, chips, and the button gallery — fell through to a `<p>`-only
   fallback and exported almost nothing. Since the whole point of the
   `.agent-tool` system is that an agent can pull accurate section content,
   this was a functional dead end for over half the doc. Added real
   handlers for pricing cards, flip-cards (grouped by their group title),
   icon cards, chip lists, the button gallery, and generic tables.

6. **Housekeeping.** Stripped a stray UTF-8 BOM at the top of the file and
   normalized mixed CRLF/LF line endings to LF; removed a dead duplicate
   `:root{--sidebar-w:264px}` declaration that had been appended onto an
   unrelated selector.

Everything else held up: all 23 nav anchors resolve to real section IDs
(sidebar and bottom-nav both), the radius/spacing/motion scales in the CSS
match what the Uniqueness Matrix specifies for this system, both themes
define a complete token set, and the JS has no syntax errors. Content
quality (thesis, UX principles, engineering rules) was already strong —
nothing there needed rewriting, only the plumbing around it.
