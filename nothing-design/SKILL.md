# Nothing-Inspired UI/UX Design System

**When to apply:** Only when the user explicitly says "Nothing style", "Nothing design", or directly asks to use/apply the Nothing design system. NEVER trigger automatically for generic UI or design tasks.

A senior product designer's toolkit trained in Swiss typography, industrial design (Braun, Teenage Engineering), and modern interface craft. Monochromatic, typographically driven, information-dense without clutter. Dark and light mode with equal rigor.

**Before starting any design work, declare which Google Fonts are required and how to load them** (Section 6 — Typography). Never assume fonts are already available.

---

## 1. DESIGN PHILOSOPHY

- **Subtract, don't add.** Every element must earn its pixel. Default to removal.
- **Structure is ornament.** Expose the grid, the data, the hierarchy itself.
- **Monochrome is the canvas.** Color is an event, not a default — except when encoding data status (see Section 2.5).
- **Type does the heavy lifting.** Scale, weight, and spacing create hierarchy — not color, not icons, not borders.
- **Both modes are first-class.** Dark mode: OLED black. Light mode: warm off-white. Neither is "derived" — both get full design attention. Ask the user which mode to start with.
- **Industrial warmth.** Technical and precise, but never cold. A human hand should be felt.

---

## 2. CRAFT RULES — HOW TO COMPOSE

### 2.1 Visual Hierarchy: The Three-Layer Rule

Every screen has exactly **three layers of importance.** Not two, not five. Three.

| Layer | What | How |
|-------|------|-----|
| **Primary** | The ONE thing the user sees first. A number, a headline, a state. | Doto or Space Grotesk at display size. `--color-text-display`. `py-12`–`py-24` breathing room. |
| **Secondary** | Supporting context. Labels, descriptions, related data. | Space Grotesk at body/subheading. `--color-text-primary`. Grouped tight (`gap-2`–`gap-4`) to the primary. |
| **Tertiary** | Metadata, navigation, system info. Visible but never competing. | Space Mono at caption/label. `--color-text-secondary` or `--color-text-disabled`. ALL CAPS. Pushed to edges or bottom. |

**The test:** Squint at the screen. Can you still tell what's most important? If two things compete, one needs to shrink, fade, or move.

**Common mistake:** Making everything "secondary." Evenly-sized elements with even spacing = visual flatness. Be brave — make the primary absurdly large and the tertiary absurdly small. The contrast IS the hierarchy.

### 2.2 Font Discipline

Per screen, use maximum:
- **2 font families** (Space Grotesk + Space Mono. Doto only for hero moments.)
- **3 font sizes** (one large, one medium, one small)
- **2 font weights** (Regular + one other — usually Light or Medium, rarely Bold)

Think of it as a budget. Every additional size/weight costs visual coherence. Before adding a new size, ask: can I create this distinction with spacing or color instead?

| Decision | Size | Weight | Color |
|----------|:---:|:---:|:---:|
| Heading vs. body | Yes | No | No |
| Label vs. value | No | No | Yes |
| Active vs. inactive nav | No | No | Yes |
| Hero number vs. unit | Yes | No | No |
| Section title vs. content | Yes | Optional | No |

**Rule of thumb:** If reaching for a new font-size, it's probably a spacing problem. Add distance instead.

### 2.3 Spacing as Meaning

Spacing is the primary tool for communicating relationships.

```
Tight  (gap-1–gap-2 / p-1–p-2)    = "These belong together" (icon + label, number + unit)
Medium (gap-4 / p-4)               = "Same group, different items" (list items, form fields)
Wide   (gap-8–gap-12 / mt-8–mt-12) = "New group starts here" (section breaks)
Vast   (gap-16–gap-24 / py-16–py-24) = "This is a new context" (hero to content, major divisions)
```

**If a divider line is needed, the spacing is probably wrong.** Dividers are a symptom of insufficient spacing contrast. Use them only in data-dense lists where items are structurally identical.

### 2.4 Container Strategy (prefer top)

1. **Spacing alone** (proximity groups items)
2. A single divider line
3. A subtle border outline
4. A surface card with background change

Each step down adds visual weight. Use the lightest tool that works. Never box the most important element — let it float on the background.

### 2.5 Color as Hierarchy

In a monochrome system, the gray scale IS the hierarchy. Max 4 levels per screen:

```
--color-text-display (100%) → Hero numbers. One per screen.
--color-text-primary (90%)  → Body text, primary content.
--color-text-secondary (60%) → Labels, captions, metadata.
--color-text-disabled (40%) → Disabled, timestamps, hints.
```

**Red (#D71921) is not part of the hierarchy.** It's an interrupt — "look HERE, NOW." If nothing is urgent, no red on the screen.

**Data status colors** (success green, warning amber, accent red) are exempt from the "one accent" rule when encoding data values. Apply color to the **value itself**, not labels or row backgrounds.

### 2.6 Consistency vs. Variance

**Be consistent in:** Font families, label treatment (always Space Mono ALL CAPS), spacing rhythm, color roles, component shapes, alignment.

**Break the pattern in exactly ONE place per screen:** An oversized number, a circular widget among rectangles, a red accent among grays, a Doto headline, a vast gap where everything else is tight.

This single break IS the design. Without it: sterile grid. With more than one: visual chaos.

### 2.7 Compositional Balance

**Asymmetry > symmetry.** Centered layouts feel generic. Favor deliberately unbalanced composition:
- **Large left, small right:** Hero metric + metadata stack.
- **Top-heavy:** Big headline near top, sparse content below.
- **Edge-anchored:** Important elements pinned to screen edges, negative space in center.

Balance heavy elements with more empty space, not with more heavy elements.

### 2.8 The Nothing Vibe

1. **Confidence through emptiness.** Large uninterrupted background areas. Resist filling space.
2. **Precision in the small things.** Letter-spacing, exact gray values, `gap-1` gaps. Micro-decisions compound into craft.
3. **Data as beauty.** `36GB/s` in Space Mono (`text-5xl`) IS the visual. No illustrations needed.
4. **Mechanical honesty.** Controls look like controls. A toggle = physical switch. A gauge = instrument.
5. **One moment of surprise.** A dot-matrix headline. A circular widget. A red dot. Restraint makes the one expressive moment powerful.
6. **Percussive, not fluid.** Imagine UI sounds: click not swoosh, tick not chime. Design transitions that feel mechanical and precise.

### 2.9 Visual Variety in Data-Dense Screens

When 3+ data sections appear on one screen, vary the visual form:

| Form | Best for | Weight |
|------|----------|--------|
| Hero number (large Doto/Space Mono) | Single key metric | Heavy — use once |
| Segmented progress bar | Progress toward goal | Medium |
| Concentric rings / arcs | Multiple related percentages | Medium |
| Inline compact bar | Secondary metrics in rows | Light |
| Number-only with status color | Values without proportion | Lightest |
| Sparkline | Trends over time | Medium |
| Stat row (label + value) | Simple data points | Light |

Lead section → heaviest treatment. Secondary → different form. Tertiary → lightest. The FORM varies, the VOICE stays the same.

---

## 3. ANTI-PATTERNS — WHAT TO NEVER DO

- No gradients in UI chrome
- No shadows. No blur. Flat surfaces, border separation.
- No skeleton loading screens. Use `[LOADING...]` text or segmented spinner.
- No toast popups. Use inline status text: `[SAVED]`, `[ERROR: ...]`
- No sad-face illustrations, cute mascots, or multi-paragraph empty states
- No zebra striping in tables
- No filled icons, multi-color icons, or emoji as UI
- No parallax, scroll-jacking, or gratuitous animation
- No spring/bounce easing. Use subtle ease-out only.
- No border-radius > `rounded-2xl` on cards. Buttons are pill (`rounded-full`) or technical (`rounded`–`rounded-lg`).
- Data visualization: differentiate with **opacity** (`opacity-100` / `opacity-60` / `opacity-30`) or **pattern** (solid/striped/dotted) before introducing color.

---

## 4. WORKFLOW

1. **Declare fonts** — tell the user which Google Fonts to load (Section 6)
2. **Ask mode** — dark or light? Neither is default.
3. **Sketch hierarchy** — identify the 3 layers before writing any code
4. **Compose** — apply craft rules (Sections 2.1–2.9)
5. **Check tokens** — Section 7 (colors), Section 6 (type), Section 8 (spacing)
6. **Build components** — Section 9 (component specs)
7. **Adapt to platform** — Section 10 (platform output)

---

## 5. MOTION & INTERACTION

- **Duration:** Micro interactions `duration-150`–`duration-200`, page/panel transitions `duration-300`–`duration-400`
- **Easing:** `ease-out` (Tailwind standard — maps to `cubic-bezier(0, 0, 0.2, 1)`). No spring/bounce.
- Prefer opacity over position. Elements fade, don't slide.
- Hover: border/text brightens. No scale, no shadows.
- No parallax, scroll-jacking, gratuitous animation.

---

## 6. TYPOGRAPHY

### Font Stack

| Role | Font | Fallback | Weight |
|------|------|----------|--------|
| **Display** | `"Doto"` | `"Space Mono", monospace` | 400–700, variable dot-size |
| **Body / UI** | `"Space Grotesk"` | `"DM Sans", system-ui, sans-serif` | Light 300, Regular 400, Medium 500, Bold 700 |
| **Data / Labels** | `"Space Mono"` | `"JetBrains Mono", "SF Mono", monospace` | Regular 400, Bold 700 |

**Google Fonts import:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Doto:wght@400;700&family=Space+Grotesk:wght@300;400;500;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

### Type Scale

All sizes except `label` and `btn` map directly to Tailwind defaults — use standard `text-*` utilities. Only `label` (11px → `text-2xs`) and `btn` (13px → `text-btn`) require custom tokens defined in `@theme`.

| Role | Size | Tailwind utility | Line Height | Letter Spacing | Use |
|------|------|-----------------|-------------|----------------|-----|
| `display-xl` | 72px | `text-7xl` | `leading-none` | `tracking-tighter` | Hero numbers, time displays |
| `display-lg` | 48px | `text-5xl` | `leading-[1.05]` | `tracking-tight` | Section heroes, percentages |
| `display-md` | 36px | `text-4xl` | `leading-[1.1]` | `tracking-tight` | Page titles |
| `heading` | 24px | `text-2xl` | `leading-tight` | `tracking-tight` | Section headings |
| `subheading` | 18px | `text-lg` | `leading-snug` | `tracking-normal` | Subsections |
| `body` | 16px | `text-base` | `leading-normal` | `tracking-normal` | Body text |
| `body-sm` | 14px | `text-sm` | `leading-normal` | `tracking-wide` | Secondary body |
| `caption` | 12px | `text-xs` | `leading-snug` | `tracking-wide` | Timestamps, footnotes |
| `label` | 11px | `text-2xs` | `leading-tight` | `tracking-widest` | ALL CAPS monospace labels |

### Typographic Rules

- **Doto:** `text-4xl`+ only, tight tracking, never for body text
- **Labels:** Always Space Mono, ALL CAPS, `tracking-wider` (0.06em) to `tracking-widest` (0.1em), `text-2xs`–`text-xs` ("instrument panel" labels)
- **Data/Numbers:** Always Space Mono. Units as `text-2xs`, slightly raised, adjacent
- **Hierarchy:** display (Doto) > heading (Space Grotesk) > label (Space Mono caps) > body (Space Grotesk). Four levels max.

---

## 7. COLOR SYSTEM

### Primary Palette (Dark Mode defaults)

| Token | Hex | Contrast on #000 | Role |
|-------|-----|-------------------|------|
| `--color-black` | `#000000` | — | Primary background (OLED) |
| `--color-surface` | `#111111` | 1.3:1 | Elevated surfaces, cards |
| `--color-surface-raised` | `#1A1A1A` | 1.5:1 | Secondary elevation |
| `--color-border` | `#222222` | — | Subtle dividers (decorative only) |
| `--color-border-visible` | `#333333` | — | Intentional borders, wireframe lines |
| `--color-text-disabled` | `#666666` | 4.0:1 | Disabled text, decorative elements |
| `--color-text-secondary` | `#999999` | 6.3:1 | Labels, captions, metadata |
| `--color-text-primary` | `#E8E8E8` | 16.5:1 | Body text |
| `--color-text-display` | `#FFFFFF` | 21:1 | Headlines, hero numbers |

### Accent & Status Colors (identical in both modes)

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-accent` | `#D71921` | Signal light: active states, destructive, urgent. One per screen. Never decorative. |
| `--color-accent-subtle` | `bg-accent/15` | Accent tint backgrounds (use Tailwind opacity modifier) |
| `--color-success` | `#4A9E5C` | Confirmed, completed, connected |
| `--color-warning` | `#D4A843` | Caution, pending, degraded |
| `--color-interactive` | `#007AFF` / `#5B9BF6` | Tappable text: links, picker values. Not for buttons. |

**Data status colors:** `--color-success` = good/in range, `--color-warning` = moderate/attention, `--color-accent` = bad/over limit, `--color-text-primary` = neutral. Apply color to **value**, not label or background. Labels stay `--color-text-secondary`. Trend arrows inherit value color.

### Dark / Light Mode Values

| Token | Dark | Light |
|-------|------|-------|
| `--color-black` | `#000000` | `#F5F5F5` |
| `--color-surface` | `#111111` | `#FFFFFF` |
| `--color-surface-raised` | `#1A1A1A` | `#F0F0F0` |
| `--color-border` | `#222222` | `#E8E8E8` |
| `--color-border-visible` | `#333333` | `#CCCCCC` |
| `--color-text-disabled` | `#666666` | `#999999` |
| `--color-text-secondary` | `#999999` | `#666666` |
| `--color-text-primary` | `#E8E8E8` | `#1A1A1A` |
| `--color-text-display` | `#FFFFFF` | `#000000` |
| `--color-interactive` | `#5B9BF6` | `#007AFF` |

**Dark feel:** Instrument panel in a dark room. OLED black, white data glowing.
**Light feel:** Printed technical manual. Off-white paper (#F5F5F5), black ink. Cards = `#FFFFFF` on off-white page = subtle elevation without shadows.

---

## 8. SPACING

| Semantic meaning | Value | Tailwind utilities | Use |
|-----------------|-------|--------------------|-----|
| `2xs` — optical adjust | 2px | `p-0.5`, `gap-0.5`, `m-0.5` | Optical adjustments only |
| `xs` — tight | 4px | `p-1`, `gap-1`, `m-1` | Icon-to-label gaps, tight padding |
| `sm` — internal | 8px | `p-2`, `gap-2`, `m-2` | Component internal spacing |
| `md` — standard | 16px | `p-4`, `gap-4`, `m-4` | Standard padding, element gaps |
| `lg` — group | 24px | `p-6`, `gap-6`, `m-6` | Group separation |
| `xl` — section | 32px | `p-8`, `gap-8`, `m-8` | Section margins |
| `2xl` — major break | 48px | `p-12`, `gap-12`, `m-12` | Major section breaks |
| `3xl` — page rhythm | 64px | `p-16`, `gap-16`, `m-16` | Page-level vertical rhythm |
| `4xl` — hero room | 96px | `p-24`, `gap-24`, `m-24` | Hero breathing room |

**Touch targets:** Use `min-h-11 min-w-11`. All interactive elements must meet this minimum.

**Common component sizes:**
- Row padding → `py-3`
- Button padding → `py-3 px-6`
- Cell padding → `py-3 px-4`
- Back button circle → `w-10 h-10` or `w-11 h-11`
- Edge inset → `top-4 left-4`

### Dot-Matrix Motif

**When to use:** Hero typography (Doto), decorative grid backgrounds, dot-grid data viz, loading indicators, empty state illustrations.

```css
.dot-grid {
  background-image: radial-gradient(circle, var(--color-border-visible) 1px, transparent 1px);
  background-size: 16px 16px;
}
.dot-grid-subtle {
  background-image: radial-gradient(circle, var(--color-border) 0.5px, transparent 0.5px);
  background-size: 12px 12px;
}
```

Dot diameters are 1–2px (set in `radial-gradient`, not a Tailwind utility). Grid spacing is set via `background-size` (12px / 16px in the CSS examples above). Opacity `opacity-10`–`opacity-20` for backgrounds, full for data. Never as container border or button style.

### Iconography

Monoline, 1.5px stroke, no fill. `size-6` (24×24) base, `size-5` (20×20) live area. Round caps/joins. Color inherits text color. Max 5–6 strokes. Preferred: Lucide (thin), Phosphor (thin). Never filled or multi-color.

---

## 9. COMPONENTS

### Cards / Surfaces
- Background: `bg-surface` or `bg-surface-raised`
- Border: `border border-border` or none. Radius: `rounded-xl`–`rounded-2xl` for cards, `rounded-lg` compact, `rounded` technical
- Padding: `p-4`–`p-6`. No shadows. Flat surfaces, border separation.

### Buttons

| Variant | Background | Border | Text | Radius |
|---------|-----------|--------|------|--------|
| Primary | `bg-text-display` (white) | none | `text-black` | `rounded-full` |
| Secondary | transparent | `border border-border-visible` | `text-text-primary` | `rounded-full` |
| Ghost | transparent | none | `text-text-secondary` | — |
| Destructive | transparent | `border border-accent` | `text-accent` | `rounded-full` |

All buttons: `font-mono text-btn uppercase tracking-wider py-3 px-6 min-h-11`.

### Inputs
- Underline preferred (`border-b border-border-visible`) or full border `rounded-lg`
- Label above: `font-mono text-2xs uppercase text-text-secondary`
- Focus: border → `border-text-primary`. Error: border → `border-accent`, message below in `text-accent`
- Data-entry fields: `font-mono` for input text

### Lists / Data Rows
- Dividers: `border-b border-border` full-width. Row padding: `py-3`–`py-4`
- Left: label (`font-mono uppercase text-2xs text-text-secondary`). Right: value (`text-text-primary`)
- Never alternating row backgrounds. Use dividers.

**Stat rows:** Label left (`font-mono uppercase text-2xs text-text-secondary`), value right (color = status color), unit adjacent in `text-2xs`. Trend arrow same color as value.

**Hierarchical rows:** Sub-items indented `pl-4`–`pl-6`, same divider treatment. No tree lines or expand/collapse — indentation IS the hierarchy.

### Tables / Data Grids
- Header: `font-mono uppercase text-2xs`, bottom `border-b border-border-visible`
- Cell text: `font-mono` numeric, `font-body` text. Cell padding: `py-3 px-4`
- Numbers right, text left. No zebra striping, no cell backgrounds.
- Active row: `bg-surface-raised` background, left `border-l-2 border-accent` indicator

### Navigation
- Bottom bar mobile, horizontal text bar desktop
- Labels: `font-mono uppercase`. Active: `text-text-display` + dot/underline. Inactive: `text-text-disabled`
- Bracket `[ HOME ]  GALLERY  INFO` or pipe `HOME | GALLERY | INFO`
- **Back button:** `w-10 h-10`–`w-11 h-11` circle, `bg-surface`, thin chevron `<`, `top-4 left-4` from edges

### Tags / Chips
- `border border-border-visible` no fill. Text: `font-mono text-xs uppercase`
- Radius: `rounded-full` (pill) or `rounded` (technical). Padding: `py-1 px-3`. Active: `text-text-display border-text-display`

### Segmented Control
- Container: `border border-border-visible`, `rounded-full` or `rounded-lg`
- Active: `bg-text-display text-black`. Inactive: `bg-transparent text-text-secondary`
- Text: `font-mono uppercase text-2xs`. Height: `h-9`–`h-11`. Transition: `duration-200 ease-out`
- Max 2–4 segments

### Date / Period Navigation
- Layout: `< LABEL >` — back arrow, label, forward arrow
- Label: `font-mono uppercase` or `font-body uppercase`. Arrows: thin chevrons, `text-text-secondary`, `min-w-11 min-h-11` touch target
- No calendar popovers — linear stepping IS the interaction

### Toggles / Switches
- Pill track, circle thumb. Off: `border-border-visible` track, `text-text-disabled` thumb
- On: `bg-text-display text-black` thumb. Min touch target: `min-h-11 min-w-11`

### Segmented Progress Bars

The signature data visualization. Discrete blocks — mechanical, instrument-like.

**Anatomy:** Label + value above, full-width bar of discrete rectangular segments with `gap-0.5` (2px) gaps below.

**Segments:** Square-ended blocks, no border-radius. Filled = solid status color. Empty = `bg-border` (dark) / `bg-neutral-200` (light).

| State | Fill | When |
|-------|------|------|
| Neutral | `--color-text-display` | Within normal range |
| Over limit | `--color-accent` | Exceeds target |
| Good | `--color-success` | Healthy range |
| Moderate | `--color-warning` | Caution zone |

**Overflow:** Filled segments continue past "full" mark in status color (typically red).
**Sizes:** Hero `h-4`–`h-5`, Standard `h-2`–`h-3`, Compact `h-1`–`h-1.5`.
Always pair with numeric readout. Bar = proportion, number = precision.

### Other Data Visualization
- **Bar charts:** Vertical, `bg-text-display` fill, `bg-border` remainder. Square ends.
- **Gauges:** Thin stroke circles + tick marks, numeric readout centered/adjacent.
- **Dot grids:** Vary opacity/size for heat maps. Uniform spacing.
- **Category differentiation:** Opacity → pattern → line style → color (last resort).
- Always show numeric value alongside any visual.

**Charts:** SVG line strokes: primary `stroke-[color-text-display]` (1.5–2px), average dashed `stroke-[color-text-secondary]` (1px). Axis labels: `font-mono text-xs`. Grid: `border-border`, horizontal only. No area fill, no legend boxes — label lines directly.

### Widgets (Dashboard Cards)
- `bg-surface rounded-2xl`. Hero metric: large `font-display` or `font-mono`, left-aligned
- Unit: `text-2xs`, adjacent. Category: `font-mono uppercase text-2xs` top-left
- Instrument gauges: compass, thermometer, dial motifs

### Overlays & Layering

No shadows. Layering through background contrast and borders.

- **Modals:** Backdrop `bg-black/80`, dialog `bg-surface border border-border-visible rounded-2xl`, centered `max-w-[30rem]`. Close: `[ X ]` top-right ghost button.
- **Bottom sheets:** `bg-surface`, `w-8 h-0.5` handle bar centered, `rounded-t-2xl`, drag-to-dismiss. Full-page sheets: title centered + dismiss button right, sections with `text-text-secondary` headings.
- **Dropdowns:** `bg-surface-raised border border-border-visible rounded-lg`, items `min-h-11`. Selected: left `border-l-2 border-accent`. No shadow.
- **Toasts:** None. Use inline status text: `[SAVED]`, `[ERROR: ...]`. `font-mono text-xs`, near trigger.

### State Patterns
- **Error:** Input `border-accent` + message below. Form-level: summary box `border border-accent`. Inline: `[ERROR]` prefix. Never red backgrounds or alert banners.
- **Empty:** Centered, `py-24`+. Headline `text-text-secondary`, 1 sentence description `text-text-disabled`. Optional dot-matrix illustration. No mascots.
- **Loading:** Segmented spinner (hardware-style), or segmented bar + percentage. No skeletons — use `[LOADING]` bracket text.
- **Disabled:** `opacity-40` or `text-text-disabled`. Borders fade to `border-border`.

---

## 10. Tailwind v4 Setup

Load fonts via Google Fonts (see Section 6). Define all tokens in a `@theme` block.

```css
@import "tailwindcss";

@theme {
  /* ── Fonts (always custom — no Tailwind defaults for these) ── */
  --font-display: "Doto", "Space Mono", monospace;
  --font-body:    "Space Grotesk", "DM Sans", system-ui, sans-serif;
  --font-mono:    "Space Mono", "JetBrains Mono", "SF Mono", monospace;

  --font-size-2xs: 0.6875rem;
  --font-size-btn: 0.8125rem;

  --tracking-tighter: -0.03em;
  --tracking-tight:   -0.02em;
  --tracking-wide:     0.04em;
  --tracking-wider:    0.06em;

  --color-black:          #000000;
  --color-surface:        #111111;
  --color-surface-raised: #1A1A1A;
  --color-border:         #222222;
  --color-border-visible: #333333;
  --color-text-disabled:  #666666;
  --color-text-secondary: #999999;
  --color-text-primary:   #E8E8E8;
  --color-text-display:   #FFFFFF;
  --color-accent:         #D71921;
  --color-success:        #4A9E5C;
  --color-warning:        #D4A843;
  --color-interactive:    #5B9BF6;
}
/* Light mode overrides */
@media (prefers-color-scheme: light) {
  @theme {
    --color-black:          #F5F5F5;
    --color-surface:        #FFFFFF;
    --color-surface-raised: #F0F0F0;
    --color-border:         #E8E8E8;
    --color-border-visible: #CCCCCC;
    --color-text-disabled:  #999999;
    --color-text-secondary: #666666;
    --color-text-primary:   #1A1A1A;
    --color-text-display:   #000000;
    --color-interactive:    #007AFF;
  }
}

/* Class-based light mode (.light on <html>) */
.light {
  --color-black:          #F5F5F5;
  --color-surface:        #FFFFFF;
  --color-surface-raised: #F0F0F0;
  --color-border:         #E8E8E8;
  --color-border-visible: #CCCCCC;
  --color-text-disabled:  #999999;
  --color-text-secondary: #666666;
  --color-text-primary:   #1A1A1A;
  --color-text-display:   #000000;
  --color-interactive:    #007AFF;
}
```

**Utility class conventions:**
- Colors: `bg-surface`, `bg-surface-raised`, `text-text-primary`, `text-text-secondary`, `text-text-display`, `text-text-disabled`, `border-border`, `border-border-visible`, `text-accent`, `text-success`, `text-warning`; accent tint: `bg-accent/15`
- Max widths: `max-w-[30rem]` for modals
- Fonts: `font-display` (Doto), `font-body` (Space Grotesk), `font-mono` (Space Mono)
- Type sizes: standard utilities — `text-7xl text-5xl text-4xl text-2xl text-lg text-base text-sm text-xs text-2xs`
- Letter spacing: `tracking-tighter tracking-tight tracking-normal tracking-wide tracking-wider tracking-widest`
- Line heights: `leading-none leading-[1.05] leading-[1.1] leading-tight leading-snug leading-normal`
- Spacing: `p-1 p-2 p-4 p-6 p-8 p-12 p-16 p-24` / `gap-*` / `m-*`
- Transitions: `transition-colors duration-150 ease-out` / `transition-all duration-300 ease-out`
- Opacity: `opacity-100` to `opacity-10`
- Touch targets: `min-h-11 min-w-11`

**React example:**

```tsx
export function StatRow({ label, value, unit }: StatRowProps) {
  return (
    <div className="flex justify-between items-baseline py-3 border-b border-border font-mono">
      <span className="text-xs uppercase tracking-widest text-text-secondary">{label}</span>
      <span className="text-text-primary">
        {value}
        <span className="text-xs text-text-secondary ml-1">{unit}</span>
      </span>
    </div>
  );
}
```

