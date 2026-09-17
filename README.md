![palette](https://img.shields.io/badge/3B82F6-3B82F6?style=flat-square&labelColor=3B82F6) ![palette](https://img.shields.io/badge/D9480F-D9480F?style=flat-square&labelColor=D9480F) ![palette](https://img.shields.io/badge/047857-047857?style=flat-square&labelColor=047857) ![palette](https://img.shields.io/badge/0E7490-0E7490?style=flat-square&labelColor=0E7490) ![palette](https://img.shields.io/badge/818CF8-818CF8?style=flat-square&labelColor=818CF8) ![palette](https://img.shields.io/badge/FBBF24-FBBF24?style=flat-square&labelColor=FBBF24) ![palette](https://img.shields.io/badge/22C55E-22C55E?style=flat-square&labelColor=22C55E) ![palette](https://img.shields.io/badge/1C1917-1C1917?style=flat-square&labelColor=1C1917) ![palette](https://img.shields.io/badge/A855F7-A855F7?style=flat-square&labelColor=A855F7) ![palette](https://img.shields.io/badge/E04FA4-E04FA4?style=flat-square&labelColor=E04FA4)

# Ten design systems. Ten files.

No build step, no framework, nothing to install.

**Open one in your browser. Copy the tokens. Ship something that looks like yours.**

Most design systems look the same. These ten refuse to. Each one is built for a different kind of product, and every choice inside it — colors, fonts, radius, spacing, motion — serves that product. No two systems share a palette, a font pairing, a radius scale, or a spacing scale.

## Pick your world

| System | Built for | Palette | The one-line opinion |
|--------|-----------|---------|----------------------|
| [📊 **01 · SaaS Analytics**](systems/01-saas-analytics/index.html) | Dashboards, data-heavy apps | ![steel blue](https://img.shields.io/badge/steel%20blue-3B82F6?style=flat-square&labelColor=3B82F6) ![teal](https://img.shields.io/badge/teal-14B8A6?style=flat-square&labelColor=14B8A6) | Numbers first. The interface gets out of the way. |
| [🛍️ **02 · Commerce Storefront**](systems/02-commerce-storefront/index.html) | Online shops | ![burnt orange](https://img.shields.io/badge/burnt%20orange-D9480F?style=flat-square&labelColor=D9480F) ![berry](https://img.shields.io/badge/berry-E11D48?style=flat-square&labelColor=E11D48) | The photo sells. The UI yields. |
| [🏦 **03 · Fintech Trust**](systems/03-fintech-trust/index.html) | Banking, money apps | ![emerald](https://img.shields.io/badge/emerald-047857?style=flat-square&labelColor=047857) ![azure](https://img.shields.io/badge/azure-0369A1?style=flat-square&labelColor=0369A1) | Money wants calm. Trust comes from restraint. |
| [🩺 **04 · Clinical Care**](systems/04-clinical-care/index.html) | Patient and health tools | ![medical cyan](https://img.shields.io/badge/medical%20cyan-0E7490?style=flat-square&labelColor=0E7490) ![coral](https://img.shields.io/badge/coral-F97316?style=flat-square&labelColor=F97316) | Readable at 3am under stress. Clarity is care. |
| [💬 **05 · Social Realtime**](systems/05-social-realtime/index.html) | Feeds, chat, presence | ![indigo](https://img.shields.io/badge/indigo-818CF8?style=flat-square&labelColor=818CF8) ![presence green](https://img.shields.io/badge/presence%20green-4ADE80?style=flat-square&labelColor=4ADE80) | Feels alive in under 100ms. Presence is the product. |
| [🏝️ **06 · Marketplace Booking**](systems/06-marketplace-booking/index.html) | Stays, trips, listings | ![amber](https://img.shields.io/badge/amber-FBBF24?style=flat-square&labelColor=FBBF24) ![indigo](https://img.shields.io/badge/indigo-818CF8?style=flat-square&labelColor=818CF8) | Zero guessing about price or availability. Ever. |
| [⌨️ **07 · Devtool Terminal**](systems/07-devtool-terminal/index.html) | Developer tools | ![terminal green](https://img.shields.io/badge/terminal%20green-22C55E?style=flat-square&labelColor=22C55E) ![lime](https://img.shields.io/badge/lime-A3E635?style=flat-square&labelColor=A3E635) | Keyboard first. Dense. No marketing gloss. |
| [📰 **08 · Editorial Longform**](systems/08-editorial-longform/index.html) | Magazines, essays, reading | ![ink](https://img.shields.io/badge/ink-1C1917?style=flat-square&labelColor=1C1917) ![gold](https://img.shields.io/badge/gold-A16207?style=flat-square&labelColor=A16207) | Typography carries the brand. The chrome disappears. |
| [🖥️ **09 · Enterprise Console**](systems/09-enterprise-console/index.html) | Ops consoles, fleet control | ![electric violet](https://img.shields.io/badge/electric%20violet-A855F7?style=flat-square&labelColor=A855F7) ![cyan](https://img.shields.io/badge/cyan-67E8F9?style=flat-square&labelColor=67E8F9) | Built for teams on-call, not for demos. |
| [🎨 **10 · Expressive Brand**](systems/10-expressive-brand/index.html) | Brands that take risks | ![hot magenta](https://img.shields.io/badge/hot%20magenta-E04FA4?style=flat-square&labelColor=E04FA4) ![lime](https://img.shields.io/badge/lime-BEF264?style=flat-square&labelColor=BEF264) | Loud on purpose. Corporate-safe is banned. |

Every system also has its own [README](systems/01-saas-analytics/README.md) — thesis, full token table, fonts, signature components, and an audit log of everything that was checked and fixed.

## How to steal from it

1. Open the system's `index.html` in a browser — double-click, that's it
2. Find/replace the system name with your project name
3. Recolor the five color tokens in both theme blocks: `--primary` `--secondary` `--tertiary` `--quaternary` `--positive`
4. Swap the fonts if you want a different voice
5. Put your content in, delete the example content

Everything runs on CSS variables. Change a token, watch the whole system follow.

## Inside every file

- Dark **and** light themes, both complete
- The same skeleton: hero, colors, type, spacing, radius, elevation, motion, working components
- Written UX and engineering principles — not just styles
- App-like systems get a bottom tab bar, thumb-zone actions, and safe-area handling on mobile
- A "what this refuses to do" section, because a design system is as much about taste as it is about tokens

## What else is in the repo

- `systems/` — the ten systems, one folder each (`index.html` + `README.md`)
- `design-system-whitelabel.html` — the shared reference build every system is measured against (read-only)
- `docs/` — the rules: template analysis, the uniqueness matrix (the collision rules that keep the ten systems distinct), and project structure
