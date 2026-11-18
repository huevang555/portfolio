# DESIGN.md — Visual System

Read this before any UI work. Use the `frontend-design` skill (`.claude/skills/frontend-design`)
for *how* to design; this file decides *what this site looks like*. If they conflict, this file wins.

## 1. Brief

- **Subject:** a full-stack engineer who builds realtime systems that move real money
  (live dispatch, payments, ledgers) and ships fast with AI-assisted development.
- **Audience:** engineering leads and recruiters at tech / IT companies building apps and websites.
- **Primary job of the site:** in under 30 seconds, show "this person can own hard,
  money-critical backend + frontend work" → open a case study → contact.

## 2. Concept: "Dispatch & Ledger"

Two ideas from the user's real work drive every visual choice:

1. **Dispatch** — things moving and being matched in real time (orders ↔ riders).
   This is the one memorable element: a small live dispatch map in the hero.
2. **Ledger** — money that must always balance. Calm, precise, aligned numbers,
   clear rows. This drives the quiet rest of the page.

Color is drawn from Laos, not from tech templates: **indigo** (Lao natural-dye textiles)
as the ink, **marigold** (baci ceremony flowers) as the single signal color.

## 3. Color tokens

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg` | `#F3F4F7` | `#12162B` | Page background (cool paper / deep indigo night) |
| `--surface` | `#FFFFFF` | `#1B2140` | Raised areas: hero map, code/diagram panels |
| `--ink` | `#1B2140` | `#E9EBF3` | Body text and headings |
| `--muted` | `#5B6178` | `#A3A9C2` | Secondary text, captions |
| `--line` | `#D9DCE6` | `#2C3358` | Borders, map streets, table rules |
| `--indigo` | `#2B3A8C` | `#8C9CF0` | Links, focus ring, primary button |
| `--marigold` | `#E8A317` | `#F2B83B` | **Signal only**: live dots, matched route, active state. Never body text on light bg |

Rules:
- Marigold appears in at most 1–2 places per screen. Its rarity is what makes it read as "live".
- No gradients as decoration. No colored shadows.
- Verify AA contrast for every text/background pair during build.

## 4. Typography

| Role | Font | Notes |
|---|---|---|
| Everything (Latin) | **Schibsted Grotesk** (Google Fonts) | One family. Headlines 800, body 400, UI 500. Fallback: Instrument Sans |
| Numbers | same family, `font-variant-numeric: tabular-nums` | Ledger feel: figures align in columns. Verify tabular figures exist; else use fallback |
| Lao (later) | Noto Sans Lao | line-height ≥ 1.7 |

Scale (rem, ratio ~1.25): 0.875 · 1 · 1.25 · 1.563 · 1.953 · 2.441 · 3.815 (hero name only).
Body line length ≤ 70ch, line-height 1.6. Headlines tight (1.05–1.15), slight negative tracking.
Sentence case everywhere. No ALL-CAPS labels.

## 5. Layout

Left-aligned, asymmetric, generous whitespace. Max content width ~1120px, 16px mobile gutter.

**Home (desktop)**

```
┌──────────────────────────────────────────────────────────┐
│ Name                                  Work  About  Contact│
├───────────────────────────┬──────────────────────────────┤
│ Hue Vang                  │  ┌ live dispatch map ──────┐ │
│ Full-stack engineer.      │  │  · street grid           │ │
│ I build realtime systems  │  │  · orders appear,        │ │
│ that move real money.     │  │    nearest rider matched │ │
│                           │  │    (marigold route)      │ │
│ [View work] [Email me]    │  └──────────────────────────┘ │
├───────────────────────────┴──────────────────────────────┤
│ Selected work  (rows, not cards)                          │
│ ───────────────────────────────────────────────────────── │
│ Realtime rider dispatch        Socket.IO · Redis · Queue  │
│ Matching orders to riders live, surviving dropouts.       │
│ ───────────────────────────────────────────────────────── │
│ Atomic cash confirmation       Saga · Reconciliation      │
│ ...                                                       │
├──────────────────────────────────────────────────────────┤
│ How I build with AI   (concrete workflow, short)          │
├──────────────────────────────────────────────────────────┤
│ Stack   (plain grouped text, like ledger rows)            │
├──────────────────────────────────────────────────────────┤
│ Contact: large email link + GitHub                        │
└──────────────────────────────────────────────────────────┘
```

**Mobile (375px):** single column; the dispatch map sits under the intro at ~220px tall;
work rows stack (title → one line → tags).

**Case study page:** narrow reading column (≤ 70ch). Sections: Context, Problem, Constraints,
Approach (one simple diagram in the same map/ledger style), Result, What I learned.
A small sticky "at a glance" box on desktop (role, stack, duration).

## 6. Signature element — hero dispatch map

- Abstract street grid (not a real map, no real locations or data).
- Every few seconds: an order dot appears → the nearest rider is matched → a marigold
  route draws → both fade. One rider occasionally goes offline and the order is re-matched
  (nods to the real problem solved).
- SVG or canvas, < 15 KB JS, pauses when off-screen.
- `prefers-reduced-motion`: show one static, already-matched frame.
- `aria-hidden`, with a visually hidden sentence describing it.

## 7. Motion

- The hero map is the **only** ambient motion on the site.
- Interaction feedback only: link underline grow, button press, theme switch.
- No fade-up on scroll, no parallax, no hover-lift on rows.

## 8. Light / dark

Follow system preference by default, with a small toggle in the header. Both themes are
first-class (the dark theme is "night dispatch": deep indigo, not black).

## 9. Avoid

- Purple/blue gradients, glassmorphism, glow effects
- Emoji, tech-logo walls, skill progress bars or percentages
- Generic hero stock images or 3D blobs
- Identical rounded cards with soft grey shadows
- ALL-CAPS eyebrow labels, `01 / 02 / 03` numbering (unless real sequence, e.g. timeline)
- One highlighted word in a headline, `→` appended to every link/button
- Monospace for small labels, `A · B · C` meta strings as decoration
- Cream + terracotta, black + acid green (generic AI looks)
- Fade-and-slide-up on every section

## 10. Self-review against generic defaults

Checked the plan against what a generic "developer portfolio" prompt would produce:

- Generic: dark bg + neon accent + Inter + card grid of projects.
  **Changed to:** indigo/marigold palette from Lao textiles, single grotesk family with
  tabular numbers, case studies as ledger rows.
- Generic: animated gradient or typing effect in hero.
  **Changed to:** a dispatch simulation that shows the actual kind of system built.
- Generic: skill badges with logos. **Changed to:** grouped plain-text stack list.

## 11. References

TBD — user to add 3–5 sites they like (and why). Update this file when they do.
