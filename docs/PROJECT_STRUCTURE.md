# Project Structure

```
/design-systems/
├── README.md                          # Gallery index — what each system is for
├── index.html                         # Live gallery page linking all 10 previews
├── _template/
│   └── design-system-whitelabel.html  # Reference implementation (DO NOT MODIFY)
├── systems/
│   ├── 01-saas-analytics/
│   │   ├── index.html                 # SaaS dashboard / analytics design system
│   │   └── README.md                  # Thesis, palette, fonts, research sources
│   ├── 02-commerce-storefront/
│   │   ├── index.html
│   │   └── README.md
│   ├── 03-fintech-trust/
│   │   ├── index.html
│   │   └── README.md
│   ├── 04-clinical-care/
│   │   ├── index.html
│   │   └── README.md
│   ├── 05-social-realtime/
│   │   ├── index.html
│   │   └── README.md
│   ├── 06-marketplace-booking/
│   │   ├── index.html
│   │   └── README.md
│   ├── 07-devtool-terminal/
│   │   ├── index.html
│   │   └── README.md
│   ├── 08-editorial-longform/
│   │   ├── index.html
│   │   └── README.md
│   ├── 09-enterprise-console/
│   │   ├── index.html
│   │   └── README.md
│   └── 10-expressive-brand/
│       ├── index.html
│       └── README.md
└── docs/
    ├── PROJECT_STRUCTURE.md           # This file
    ├── TEMPLATE-ANALYSIS.md           # Complete template extraction
    ├── UNIQUENESS-MATRIX.md           # Enforcement table for all 10 systems
    ├── FEATURES.md                    # What each system covers per archetype
    ├── CHANGELOG.md                   # Append after every system ships
    └── SYSTEM_INSTRUCTIONS.md         # How an AI agent should consume these files
```

## File Purposes

| File | Purpose |
|------|---------|
| `README.md` | Entry point for humans browsing the repo. Lists all 10 systems with thesis + palette preview. |
| `index.html` | Self-contained gallery page. Shows each system as a card with name, archetype, thesis, palette swatches, and font pairing. Links to system's `index.html` and README. |
| `_template/` | Reference implementation. Never modified. The canonical source of truth for structure, features, and conventions. |
| `systems/NN-slug/index.html` | Single-file design system for that archetype. Token-driven, self-contained, both themes complete. |
| `systems/NN-slug/README.md` | Short doc: thesis, palette summary, font pairing, research sources, what it refuses to do. |
| `docs/TEMPLATE-ANALYSIS.md` | Complete extraction of the template's tokens, sections, components, chrome, and JS systems. |
| `docs/UNIQUENESS-MATRIX.md` | Enforcement table: every system's thesis, hues, fonts, radius, spacing, motion, density, sections, signature components. Collision rules enforced. |
| `docs/FEATURES.md` | What each system covers, per archetype. Updated after each system ships. |
| `docs/CHANGELOG.md` | Chronological log of what shipped, when. |
| `docs/SYSTEM_INSTRUCTIONS.md` | How an AI agent should pick, re-theme, and use these files. |
