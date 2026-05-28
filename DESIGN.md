# VIGIL — Design System

## Aesthetic Direction
**Editorial Brutalism.** Black and white. High contrast. No gradients. No color accents.
Think: a Bloomberg Terminal crossed with a 1990s financial newspaper. Every pixel is functional.
The only decoration is typography.

This is not "dark mode." This is a deliberate rejection of the AI startup aesthetic.
No purple. No glow. No rounded corners trying to feel friendly.
VIGIL is a tool for serious people.

---

## Color Palette

```css
:root {
  --bg:           #0a0a0a;    /* near-black background */
  --bg-raised:    #111111;    /* card / panel surface */
  --bg-border:    #1e1e1e;    /* subtle dividers */
  --text-primary: #f0f0f0;    /* main body text */
  --text-secondary:#888888;   /* metadata, timestamps, labels */
  --text-muted:   #444444;    /* disabled, placeholders */
  --accent:       #ffffff;    /* pure white — used sparingly */
  --negative:     #ff4444;    /* alerts, errors only */
  --positive:     #e0e0e0;    /* not green. just lighter white. */
  --rule:         #1e1e1e;    /* horizontal rules */
}
```

**Rule:** Never introduce a color outside this palette. No blues, no greens, no purples.
Red (`--negative`) is reserved for alerts and error states only.

---

## Typography

### Fonts
```css
/* Display / Headlines */
font-family: 'Bebas Neue', 'Impact', sans-serif;
/* Used for: H1, H2, section labels, the VIGIL wordmark */

/* Body / Reading */
font-family: 'IBM Plex Mono', 'Courier New', monospace;
/* Used for: all body text, article content, metadata */

/* UI Labels */
font-family: 'Space Mono', monospace;
/* Used for: nav items, tags, timestamps, captions */
```

Import via Google Fonts:
```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=IBM+Plex+Mono:wght@400;500&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

### Scale
```css
--text-xs:   0.7rem;    /* timestamps, metadata */
--text-sm:   0.85rem;   /* captions, labels */
--text-base: 1rem;      /* body */
--text-lg:   1.2rem;    /* lead paragraphs */
--text-xl:   1.5rem;    /* H3 */
--text-2xl:  2rem;      /* H2 */
--text-3xl:  3rem;      /* H1 */
--text-hero: 6rem;      /* VIGIL wordmark */
```

### Rules
- Line height for body: 1.7
- Line height for headlines: 1.0
- Letter spacing for headlines: 0.02em
- Letter spacing for labels/caps: 0.15em
- Max line length: 68ch

---

## Layout

### Grid
- 12-column grid, 24px gutter
- Max content width: 1200px
- Article column: 720px max (centered)

### Spacing Scale
```css
--space-1:  4px;
--space-2:  8px;
--space-3:  16px;
--space-4:  24px;
--space-5:  40px;
--space-6:  64px;
--space-7:  96px;
--space-8:  128px;
```

### Breakpoints
```css
--mobile:  480px;
--tablet:  768px;
--desktop: 1024px;
--wide:    1280px;
```

---

## Components

### Header / Wordmark
```
VIGIL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[AI AGENTS]  [MARKETS]  [RESEARCH]  [BRIEFS]
```
- VIGIL in Bebas Neue, 72px, white
- Nav in Space Mono, 11px, uppercase, letter-spacing 0.15em
- Full-width horizontal rule below (1px, #1e1e1e)

### Article Card
```
┌─────────────────────────────────────┐
│ DAILY BRIEF              2025-01-14 │  ← Space Mono, --text-xs, muted
│                                     │
│ TAO Breaks ATH as Subnet            │  ← Bebas Neue, --text-2xl
│ Activity Spikes 340%                │
│                                     │
│ On-chain data confirms institutional│  ← IBM Plex Mono, --text-sm
│ accumulation ahead of halving...    │
│                                     │
│ [READ →]                    4 MIN   │  ← Space Mono, xs
└─────────────────────────────────────┘
```
- Border: 1px solid #1e1e1e
- No border-radius (0px)
- Hover: border-color becomes #444444
- No box-shadow. No card elevation. Flat.

### Tag / Label
```css
.tag {
  font-family: 'Space Mono', monospace;
  font-size: var(--text-xs);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  padding: 2px 8px;
  border: 1px solid #1e1e1e;
  color: var(--text-secondary);
  background: transparent;
}
.tag--active {
  border-color: var(--accent);
  color: var(--accent);
}
```

### Horizontal Rule
```css
hr {
  border: none;
  border-top: 1px solid var(--rule);
  margin: var(--space-5) 0;
}
```

### Token Price Ticker
```
FET    $2.41   ▲ 3.2%     TAO    $487.22   ▼ 1.1%
```
- Space Mono, --text-xs
- Up: --text-primary (white)
- Down: --negative (red)
- Separator: 4-space gap, no border

---

## Page Templates

### Home Page Structure
```
[HEADER — VIGIL wordmark + nav]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[TICKER — live token prices, single line scrolling]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LATEST BRIEF                           ← full-width featured article

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[3-col grid of recent articles]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MARKET WATCH          |    RESEARCH
[token table]         |    [paper list]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[FOOTER — RSS link, source, last updated timestamp]
```

### Article Page Structure
```
[HEADER]
━━━━━━━━━━━━━━━━━━━━━━━━━

[CATEGORY TAG]    [DATE]

[TITLE — Bebas Neue, large]

[LEAD PARAGRAPH — IBM Plex Mono, slightly larger]

━━━━━━━━━━━━━━━━━━━━━━━━━

[BODY CONTENT]

━━━━━━━━━━━━━━━━━━━━━━━━━

*Published by VIGIL — automated AI agent intelligence.*
[← BACK]        [RSS FEED]
```

---

## Animation & Motion

**Principle: motion serves information, never decoration.**

Allowed:
```css
/* Fade in on load */
@keyframes vigil-in {
  from { opacity: 0; transform: translateY(8px); }
  to   { opacity: 1; transform: translateY(0); }
}
.card { animation: vigil-in 0.3s ease forwards; }

/* Stagger cards */
.card:nth-child(1) { animation-delay: 0ms; }
.card:nth-child(2) { animation-delay: 60ms; }
.card:nth-child(3) { animation-delay: 120ms; }

/* Ticker scroll */
@keyframes ticker {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
```

Not allowed:
- Parallax effects
- Glitch effects (too cliché)
- Pulsing glow or bloom
- Particle systems
- Spinning loaders (use a blinking cursor `_` instead)

---

## Iconography

No icon libraries. Use typographic symbols only:
```
→   navigation, "read more"
←   back
↑↓  sorting
▲▼  price up/down (small, inline)
×   close
—   separator
[·] loading state
_   cursor / awaiting
```

---

## Do & Don't

| ✓ DO | ✗ DON'T |
|---|---|
| High contrast black/white | Any color outside palette |
| Sharp 0px corners | Rounded corners (border-radius > 0) |
| Monospace for all body text | Sans-serif body fonts |
| Thin 1px borders | Drop shadows or elevation |
| Uppercase labels + tracking | Title case for labels |
| Dense information layout | Empty hero sections with taglines |
| Bebas Neue for headlines | Inter, Space Grotesk, or system fonts |
| Blinking underscore for loading | Spinner animations |
| Static background (#0a0a0a) | Gradients, noise textures, blurs |

---

## File Structure (docs/)
```
docs/
├── index.html           ← homepage
├── articles/
│   ├── index.html       ← article listing
│   └── [slug].html      ← individual articles
├── market/
│   └── index.html       ← token watch page
├── research/
│   └── index.html       ← paper digest listing
├── style.css            ← single global stylesheet (this design system)
├── feed.xml             ← RSS feed
└── assets/
    └── (no images — text only)
```
