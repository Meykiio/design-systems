# Template Analysis — `design-system-whitelabel.html`

Complete extraction of the reference implementation. Every system built from this repo
must implement the same feature set, adapted to its archetype.

---

## 1. CSS Custom Properties

### `:root` (Dark Mode — canonical)

**Color tokens:**
- `--bg: #0c0d14` — page background
- `--bg-dim: #08090f` — dimmer background (hero, footer)
- `--surface: #121420` — card/panel surface
- `--surface-mid: #171a28` — mid surface (table headers, alt rows)
- `--surface-high: #1e2233` — raised surface (hover states, spacing ruler bg)
- `--surface-highest: #282d42` — highest surface (toast, tooltip)
- `--on-surface: #eef0f9` — primary text
- `--on-surface-muted: #9498b0` — secondary/muted text
- `--outline: #282d42` — borders
- `--outline-hi: #3f4664` — emphasized borders
- `--primary: #7c7fff` — accent (text/interactive)
- `--primary-solid: #7c7fff` — accent (fills/backgrounds)
- `--on-primary: #0c0d2e` — text on primary
- `--primary-glow: rgba(124,127,255,0.24)` — glow shadow
- `--primary-glow-sm: rgba(124,127,255,0.11)` — small glow
- `--brand-blue: #4fc3f7` — support blue
- `--secondary: #5eead4` — teal (dark)
- `--secondary-dim: #4bc2ab` — dimmed teal
- `--on-secondary: #06281f` — text on teal
- `--tertiary: #f5a623` — amber
- `--on-tertiary: #2e1a00` — text on amber
- `--quaternary: #f472b6` — rose
- `--on-quaternary: #2e0a1c` — text on rose
- `--positive: #34d399` — green/success
- `--on-positive: #04241a` — text on green
- `--error: #f87171` — error red

**Shadow tokens:**
- `--shadow-sm: 0 1px 3px rgba(0,0,0,0.5)`
- `--shadow-md: 0 8px 24px rgba(0,0,0,0.55)`
- `--shadow-lg: 0 20px 40px rgba(0,0,0,0.65)`

**Nav/scroll tokens:**
- `--nav-bg: #08090f`
- `--scroll-track: #121420`
- `--scroll-thumb: #2c3148`
- `--scroll-thumb-hi: #7c7fff`
- `--toggle-bg: rgba(124,127,255,0.09)`
- `--toggle-border: rgba(124,127,255,0.27)`

**Table tokens:**
- `--table-header-bg: #171a28`
- `--table-header-fg: #7c7fff`
- `--table-row-bg: #0c0d14`
- `--table-row-hover: #121420`
- `--table-border: #282d42`

**Section tokens:**
- `--section-alt: #0c0d14`

**Type tokens:**
- `--font-display: 'Sora', sans-serif`
- `--font-body: 'DM Sans', system-ui, sans-serif`

**Radius tokens:**
- `--r-xs: 4px`
- `--r-sm: 8px`
- `--r-md: 12px`
- `--r-lg: 16px`
- `--r-xl: 24px`
- `--r-full: 9999px`

**Space tokens:**
- `--s-xs: 4px`
- `--s-sm: 8px`
- `--s-md: 16px`
- `--s-lg: 24px`
- `--s-xl: 48px`
- `--s-2xl: 80px`

**Layout:**
- `--content-max: 1100px`
- `--transition: background .3s, color .3s, border-color .3s, box-shadow .3s`

**Motion tokens (in `:root` nested block):**
- `--ease-out: cubic-bezier(.22,1,.36,1)` — expo-out
- `--ease-spring: cubic-bezier(.34,1.3,.64,1)` — soft overshoot
- `--dur-fast: .18s`
- `--dur-med: .3s`
- `--dur-slow: .55s`

**Layout tokens (in `:root` nested block):**
- `--sidebar-w: 280px`
- `--topbar-h: 64px`

### `[data-theme="light"]`

All surface, text, accent, shadow, nav, table, and toggle tokens re-mapped for light mode.
Key differences: surfaces go from near-black to near-white, accents darken for AA contrast
on white backgrounds, shadows become much lighter (rgba(20,21,42,0.06–0.11)).

---

## 2. Sections (in order, with IDs)

| # | ID | Section Name | Purpose |
|---|-----|------|---------|
| 1 | `hero` | Overview | Hero banner with badge, title, description, CTAs |
| 2 | `colors` | Color Palette | Swatch grid with hex values |
| 3 | `typography` | Typography Scale | Type specimen rows (7 tiers) |
| 4 | `spacing` | Spacing Scale | Visual ruler with 6 values |
| 5 | `radius` | Border Radius Scale | 6 radius demos |
| 6 | `elevation` | Elevation & Depth | 4 shadow levels |
| 7 | `motion` | Motion & Transitions | 2 easing curves + 3 durations |
| 8 | `ux-principles` | UX Principles | 4 groups of flip-cards (20 principles) |
| 9 | `architecture` | Architecture & Files | 3 groups of flip-cards (14 principles) |
| 10 | `data-security` | Data & Security | 2 groups + pre-ship checklist table |
| 11 | `performance-scale` | Performance & Scale | 2 groups + complexity sanity table |
| 12 | `components` | Button Variants | 7 button variants |
| 13 | `chips` | Chips & Tags | 4 chip color variants |
| 14 | `cards` | Card Examples | 4 card types (base, stat, product, feature) |
| 15 | `forms` | Form Elements | 4 form controls |
| 16 | `responsive` | Responsive Behavior | Breakpoint table + notes |
| 17 | `touch` | Touch Targets | 3 touch target demos |
| 18 | `pricing` | Pricing Tiers | 3-tier pricing cards |

---

## 3. Component Classes

### Buttons (`.btn-*`)
- `.btn` — base button
- `.btn-primary` — solid primary fill
- `.btn-secondary` — outlined with secondary color
- `.btn-ghost` — transparent, no border
- `.btn-pill-primary` — pill shape, primary fill
- `.btn-pill-accent` — pill shape, accent/secondary fill
- `.btn-outline-pill` — pill shape, outlined primary
- `.btn-disabled` — disabled state
- `.btn-hero-primary` / `.btn-hero-secondary` — hero-specific buttons

### Chips (`.chip-*`)
- `.chip` — base chip
- `.chip-primary` — category/tag chip
- `.chip-active` — active/success state
- `.chip-tertiary` — info/warning
- `.chip-error` — error state
- `.chip-x` — dismissible chip close button
- `.dot-xs` — small status dot inside chip

### Cards (`.card-*`)
- `.card-demo` — base card wrapper
- `.card-tag` — category label
- `.card-title` — card heading
- `.card-text` — card body text
- `.card-link` — card link
- `.card-stat-label` / `.card-stat-value` — stat card
- `.card-cover` — cover image area
- `.card-product-row` — product card bottom row
- `.card-price` — product price
- `.card-icon` — icon container for feature cards
- `.card-feature` — feature card (hover border)

### Forms (`.form-*`)
- `.form-grid` — 2-column form layout
- `.form-group` — label + input wrapper
- `.form-input` — text input (44px height)
- `.form-select` — dropdown select
- `.form-textarea` — multi-line text area
- `.focused` — focus state class

### Pricing
- `.pricing-grid` — 3-column grid
- `.pricing-card` — individual card
- `.pricing-card.featured` — highlighted card
- `.pricing-badge` — "Most Popular" badge
- `.tier` / `.price` / `.price-sub` — pricing text
- `.pricing-features` — feature list
- `.pricing-cta-margin` — CTA spacing

### Table
- `.responsive-table` — scrollable table with rounded corners

### Toast
- `.toast` — fixed bottom toast notification
- `.t-dot` — status indicator dot
- `.show` — visible state

### UX Principle Cards (flip-cards)
- `.ux-card` — clickable card with `aria-expanded`
- `.ux-card-inner` — 3D flip container
- `.ux-card-face` — front face
- `.ux-card-face-front` / `.ux-card-face-back` — front/back sides
- `.ux-card-name` — principle name
- `.ux-card-def` — definition text
- `.ux-card-rule` — rule text (back)
- `.ux-card-flip-hint` — "Tap for the rule" hint

### Spacing/Radius/Elevation/Motion demos
- `.spacing-ruler` / `.spacing-block` / `.spacing-labels`
- `.radius-grid` / `.radius-item` / `.radius-box`
- `.elevation-grid` / `.elevation-card` / `.el-0..el-3`
- `.motion-grid` / `.motion-card` / `.motion-track` / `.motion-dot`

### Touch Targets
- `.touch-grid` / `.touch-item` / `.touch-target` / `.touch-label` / `.touch-input`

---

## 4. Chrome (Layout & Interactive Systems)

### Sidebar Navigation
- `.sidebar` — fixed left panel, 280px wide
- `.sidebar-header` — logo + close button
- `.sidebar-nav` — scrollable nav list
- `.nav-indicator` — sliding active indicator bar (accent color, 3px wide)
- `.nav-group` / `.nav-group-label` — section groups with uppercase labels
- `.nav-item` — individual nav links with SVG icons
- `.sidebar-footer` — theme toggle + collapse toggle
- `.sidebar-footer-tools` — "Copy entire doc as MD" button

### Mobile Drawer
- `.topbar` — fixed top bar (hidden on desktop)
- `.menu-toggle` — hamburger button
- `.sidebar-backdrop` — overlay backdrop
- Drawer slides from left, backdrop fades in
- Staggered reveal of nav groups on open
- Escape key closes drawer

### Collapse Toggle (Desktop)
- `html.nav-collapsed` — shrinks sidebar to 78px icon rail
- Logo becomes single letter, labels hidden, items centered
- Persisted in `localStorage('pz-nav-collapsed')`
- Floating `.nav-tooltip` appears on hover in collapsed mode

### Theme Toggle
- Multiple `.theme-toggle` buttons (mobile topbar + sidebar footer)
- Animated icon swap (spin out, glyph change, spring back)
- Persisted in `localStorage('pz-theme')`
- Respects `prefers-color-scheme: dark`

### Scroll Progress Bar
- `.scroll-progress` — fixed bar at top, right of sidebar
- `.bar` — fills proportionally to scroll position

### Scroll-Spy
- `IntersectionObserver` watches all `section[id]`
- Active `.nav-item` gets `.active` class
- `.nav-indicator` slides to active item position
- Click suppression during smooth-scroll to avoid indicator flicker

### Scroll Reveal
- `[data-reveal]` elements animate in on scroll
- IntersectionObserver with threshold 0.12
- `.revealed` class triggers opacity/transform transition
- `.draw-target` underline animation on reveal

---

## 5. The `.agent-tool` Markdown Export System

### Per-Section Copy
- `.md-copy-btn.agent-tool` buttons with `data-copy-section="sectionId"`
- Click calls `sectionToMarkdown(section)` which converts the section's HTML
  structure to clean Markdown:
  - Color swatches → bullet list with hex + name
  - Type specimens → bullet list with token name + spec + sample
  - UX cards → grouped by `.ux-group-title`, each card as Name/Def/Rule
  - Tables → Markdown table with headers
  - Buttons → bullet list with class + label
  - Chips → comma-separated list
  - Cards → title + tag + text
  - Pricing → tier + price + feature list
  - Forms → label text

### Global Copy
- `#copyAllMd` button in `.sidebar-footer-tools`
- Calls `fullDocMarkdown()` which:
  1. Adds title heading
  2. Adds table of contents from nav links
  3. Iterates all `section[id]`, calling `sectionToMarkdown()` on each

### Feedback
- Toast notification confirms copy
- Button gets `.copied` class for 1.4s visual feedback
- Uses `navigator.clipboard.writeText` with fallback to `document.execCommand('copy')`

### Exclusion Rule
- All elements with `.agent-tool` class are excluded from replication
- The comment block explicitly states: never copy "Copy as MD" buttons into a built website
- The `sectionToMarkdown()` / `fullDocMarkdown()` JS is tooling, not a product pattern

---

## 6. Header Comment Block (Agent-Instruction Contract)

Located in the `<style>` block as a CSS comment, the header contains:

1. **WHAT TO CHANGE PER PROJECT** — 5 items (name, recolor, fonts, copy, footer)
2. **WHAT TO KEEP VERBATIM** — 5 items (motion tokens, scales, principles, engineering, structural CSS)
3. **HOW TO USE THIS FILE AS A CODING AGENT** — instruction to pull tokens + principles before building UI
4. **EXCLUDED FROM REPLICATION** — `.agent-tool` class and markdown export system
5. **TOKEN SYSTEM** — the default palette description (Slate & Indigo-Violet)
6. **RECYCLABLE TEMPLATE** — instructions for creating new systems

---

## 7. What the Template Proves About the Format

- Single self-contained `.html` file, no build step
- Only external dependency: Google Fonts (preconnect + stylesheet link)
- All CSS in one `<style>` block, all JS in one `<script>` block at end
- No hardcoded colors outside theme blocks + Colors section
- Dark mode canonical, light mode derived (both complete)
- Agent-instruction comment block at top
- Works offline (minus fonts), opens by double-click
- Both themes must be complete and tested
- Responsive at 360px, 768px, 1280px, 1920px
- `prefers-reduced-motion` respected
- Visible `:focus-visible` on interactive elements
- Semantic HTML with `aria-*` attributes
- All interactive targets ≥44×44px
- Keyboard-operable nav and theme toggle
- No meaning carried by colour alone
