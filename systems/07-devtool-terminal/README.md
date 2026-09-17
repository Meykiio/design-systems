# Devtool Terminal Design System

**System 07** — Phosphor Green & Lime

Design thesis: Dense, monospace-native, keyboard-first — the IDE is the interface.

What it rejects: Marketing gloss inside developer tools.

---

## Token Summary

| Token | Value |
|-------|-------|
| Primary | `#22c55e` Terminal Green (dark canonical) / `#16a34a` (light) |
| Secondary | `#a3e635` Lime (added lines, highlights) |
| Tertiary | `#fbbf24` Amber (warnings) |
| Quaternary | `#67e8f9` Cyan (info values) |
| Base | Near-black `#0a0f0b` with green whisper |
| Radius scale | 0, 2, 4, 8, 12, pill (sharp) |
| Spacing scale | Doubling (4, 8, 16, 32, 64, 96) |
| Motion | Snap + steps: `(.19,1,.22,1)`, `steps(4)`, .1s .2s .3s |
| Density | Dense: 13px base, mono-heavy, 1.45 lh |
| Default theme | Dark |

## Fonts

- **Display**: Space Grotesk (Google Fonts)
- **Body**: Space Grotesk (Google Fonts)
- **Mono**: Source Code Pro (Google Fonts) — all commands, hashes, durations

## Signature Components

1. **Command Palette** — keyboard-first launcher with keybinding twins
2. **Log Stream** — timestamped levels, color + word redundancy
3. **Code Block** — header copy affordance, mono syntax colors
4. **Keycap Keycaps** — physical bottom-edge keycaps for shortcuts
5. **Diff View** — lime added / red removed / dim context, counts in header

## Sections (24)

Hero, Colors, Typography, Architecture, Spacing, Radius, Elevation, Motion, Command Palette, Log Stream, Code Block, Keycaps, Diff View, Buttons, Chips, Forms, Build History, Pricing, UX Principles, Accessibility, Security, Responsive, Touch, Footer

## How to Customize

1. Find/replace "Devtool Terminal" with your project name
2. Recolor `--primary`, `--secondary`, `--tertiary`, `--quaternary`, `--positive` in both theme blocks
3. Swap Google Fonts imports + font tokens if needed
4. Replace example commands, logs, diffs, pricing copy
5. Update footer tagline

## What to Keep Verbatim

- Motion tokens (snap durations .1/.2/.3s, steps(4))
- Spacing/radius/elevation scale (values, not colors)
- UX Principles section (Keyboard First / Signal Density / Debug Flow)
- Engineering Principles section
- Component structural CSS (layout, not color)

## Excluded from Replication

Every element with class `agent-tool` is tooling for reading this reference — not a UI pattern.
