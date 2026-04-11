# Profit Architect — CLAUDE.md

## Files
- `index.html` — HTML structure + inline IIFE JS (per-section animations)
- `style.css` — all styles (extracted from HTML)

## Design tokens (`:root` in style.css)
| Token      | Value   | Usage                        |
|------------|---------|------------------------------|
| --navy     | #1a2f5e | Primary dark blue            |
| --navy-dk  | #111f42 | Darkest navy, hero/cta bg    |
| --navy-lt  | #243570 | Lighter navy                 |
| --gold     | #f5b731 | Accent, CTAs, eyebrows       |
| --gold-dk  | #d99e1a | Gold hover                   |
| --white    | #ffffff | Page background              |
| --off      | #f4f6fb | Alternate section bg         |
| --text     | #1c2640 | Body text                    |
| --muted    | #6b7a9a | Secondary text               |
| --border   | #e2e8f4 | Dividers                     |

## Section order & backgrounds
| Selector      | Background       | Notes                                |
|---------------|------------------|--------------------------------------|
| nav           | navy-dk (fixed)  | Fixed top, z-index 500               |
| #hero         | navy gradient    | Hero + dash-card visual              |
| #driver-lift  | navy gradient    | Animated driver performance viz      |
| #problem      | --off            | 6 pain-cards grid (.pain-grid)       |
| #process      | --white          | 3-step layout (.steps-row)           |
| #value        | --off            | 6 value-cards (.value-grid)          |
| #why          | --white          | .why-list + sticky .quote-card       |
| #cta          | navy-dk gradient | Email + phone CTA                    |
| footer        | navy-dk          | Logo, tagline, copyright             |

## Key CSS patterns
- `.section` — `padding: 96px 60px` (responsive: 72px 20px)
- `.wrap` — `max-width: 1060px; margin: 0 auto`
- `.eyebrow` — gold bar + uppercase label; use before h2 in each section
- `.fi` / `.fi.on` — scroll fade-in; `.d1`–`.d5` = stagger (0.04s steps)
- `.btn-gold` — primary CTA; `.btn-border` — ghost on dark bg

## Wave dividers (SVG, viewBox="0 0 1440 72")
Dark section → light below (fill `#f4f6fb`, bottom shape):
```
M0,36 C240,72 480,0 720,36 C960,72 1200,0 1440,36 L1440,72 L0,72 Z
```
Light above → dark section (fill `#f4f6fb`, top shape):
```
M0,36 C240,0 480,72 720,36 C960,0 1200,72 1440,36 L1440,0 L0,0 Z
```

## Animated sections
### #driver-lift
- Inline IIFE JS, triggered by IntersectionObserver (threshold 0.2)
- 12 driver bubbles: `{ lbl, b (before%), a (after%), x (left%) }`
- `window._liftReplay()` → replay button
- Counter: 0 → +8% (230ms/step)
- Color thresholds: ≤-14 red, ≤-7 orange, ≤-1 amber, ≤5 yellow-green, ≤11 light green, >11 green

## Rules for working in this project
- Git: only on explicit user request
- New sections: navy dark bg → use wave dividers; light bg → just `.section` class
- Inline styles in HTML only for section-specific overrides (bg, color on dark sections)
- Section JS: always IIFE, always clean up (use `var`, not `const/let` for compat)

## When to update this file
Update after: new section added, new CSS class introduced, file structure changes, design token change.
Skip for: copy edits, minor tweaks within existing patterns, JS data-only changes.
