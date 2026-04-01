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
| **Primary** | The ONE thing the user sees first. A number, a headline, a state. | Doto or Space Grotesk at display size. `--color-text-display`. 48–96px breathing room. |
| **Secondary** | Supporting context. Labels, descriptions, related data. | Space Grotesk at body/subheading. `--color-text-primary`. Grouped tight (8–16px) to the primary. |
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
Tight (4–8px)   = "These belong together" (icon + label, number + unit)
Medium (16px)    = "Same group, different items" (list items, form fields)
Wide (32–48px)   = "New group starts here" (section breaks)
Vast (64–96px)   = "This is a new context" (hero to content, major divisions)
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
2. **Precision in the small things.** Letter-spacing, exact gray values, 4px gaps. Micro-decisions compound into craft.
3. **Data as beauty.** `36GB/s` in Space Mono at 48px IS the visual. No illustrations needed.
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
- No border-radius > 16px on cards. Buttons are pill (999px) or technical (4–8px).
- Data visualization: differentiate with **opacity** (100%/60%/30%) or **pattern** (solid/striped/dotted) before introducing color.

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

- **Duration:** 150–250ms micro, 300–400ms transitions
- **Easing:** `cubic-bezier(0.25, 0.1, 0.25, 1)` — subtle ease-out. No spring/bounce.
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

**Why these fonts:** Doto = variable dot-matrix (closest to NDot 57). Space Grotesk + Space Mono by Colophon Foundry — same foundry as Nothing's actual typefaces. Shared design DNA.

**Google Fonts import:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Doto:wght@400;700&family=Space+Grotesk:wght@300;400;500;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

### Type Scale

| Token | Size | Line Height | Letter Spacing | Use |
|-------|------|-------------|----------------|-----|
| `--display-xl` | 72px | 1.0 | -0.03em | Hero numbers, time displays |
| `--display-lg` | 48px | 1.05 | -0.02em | Section heroes, percentages |
| `--display-md` | 36px | 1.1 | -0.02em | Page titles |
| `--heading` | 24px | 1.2 | -0.01em | Section headings |
| `--subheading` | 18px | 1.3 | 0 | Subsections |
| `--body` | 16px | 1.5 | 0 | Body text |
| `--body-sm` | 14px | 1.5 | 0.01em | Secondary body |
| `--caption` | 12px | 1.4 | 0.04em | Timestamps, footnotes |
| `--label` | 11px | 1.2 | 0.08em | ALL CAPS monospace labels |

### Typographic Rules

- **Doto:** 36px+ only, tight tracking, never for body text
- **Labels:** Always Space Mono, ALL CAPS, 0.06–0.1em spacing, 11–12px ("instrument panel" labels)
- **Data/Numbers:** Always Space Mono. Units as `--label` size, slightly raised, adjacent
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
| `--color-accent-subtle` | `rgba(215,25,33,0.15)` | Accent tint backgrounds |
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

### Scale (8px base)

| Token | Value | Use |
|-------|-------|-----|
| `--spacing-2xs` | 2px | Optical adjustments only |
| `--spacing-xs` | 4px | Icon-to-label gaps, tight padding |
| `--spacing-sm` | 8px | Component internal spacing |
| `--spacing-md` | 16px | Standard padding, element gaps |
| `--spacing-lg` | 24px | Group separation |
| `--spacing-xl` | 32px | Section margins |
| `--spacing-2xl` | 48px | Major section breaks |
| `--spacing-3xl` | 64px | Page-level vertical rhythm |
| `--spacing-4xl` | 96px | Hero breathing room |

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

Dots 1–2px, uniform 12–16px grid. Opacity 0.1–0.2 for backgrounds, full for data. Never as container border or button style.

### Iconography

Monoline, 1.5px stroke, no fill. 24x24 base, 20x20 live area. Round caps/joins. Color inherits text color. Max 5–6 strokes. Preferred: Lucide (thin), Phosphor (thin). Never filled or multi-color.

---

## 9. COMPONENTS

### Cards / Surfaces
- Background: `--color-surface` or `--color-surface-raised`
- Border: `1px solid --color-border`, or none. Radius: 12–16px cards, 8px compact, 4px technical
- Padding: 16–24px. No shadows. Flat surfaces, border separation.

### Buttons

| Variant | Background | Border | Text | Radius |
|---------|-----------|--------|------|--------|
| Primary | `--color-text-display` (#FFF) | none | `--color-black` | 999px (pill) |
| Secondary | transparent | `1px solid --color-border-visible` | `--color-text-primary` | 999px |
| Ghost | transparent | none | `--color-text-secondary` | 0 |
| Destructive | transparent | `1px solid --color-accent` | `--color-accent` | 999px |

All buttons: `Space Mono`, 13px, ALL CAPS, letter-spacing 0.06em, padding 12px 24px. Min height 44px.

### Inputs
- Underline preferred (`1px solid --color-border-visible` bottom) or full border 8px radius
- Label above: Space Mono, ALL CAPS, `--color-text-secondary`, 11px
- Focus: border → `--color-text-primary`. Error: border → `--color-accent`, message below in `--color-accent`
- Data-entry fields: `Space Mono` for input text

### Lists / Data Rows
- Dividers: `1px solid --color-border`, full-width. Row padding: 12–16px vertical
- Left: label (Space Mono caps, `--color-text-secondary`). Right: value (`--color-text-primary`)
- Never alternating row backgrounds. Use dividers.

**Stat rows:** Label left (Space Mono, ALL CAPS, `--color-text-secondary`), value right (color = status color), unit adjacent in label size. Trend arrow same color as value.

**Hierarchical rows:** Sub-items indented 16–24px, same divider treatment. No tree lines or expand/collapse — indentation IS the hierarchy.

### Tables / Data Grids
- Header: Space Mono ALL CAPS 11px, bottom border `--color-border-visible`
- Cell text: `Space Mono` numeric, `Space Grotesk` text. Cell padding: 12px 16px
- Numbers right, text left. No zebra striping, no cell backgrounds.
- Active row: `--color-surface-raised` background, left `2px solid --color-accent` indicator

### Navigation
- Bottom bar mobile, horizontal text bar desktop
- Labels: Space Mono, ALL CAPS. Active: `--color-text-display` + dot/underline. Inactive: `--color-text-disabled`
- Bracket `[ HOME ]  GALLERY  INFO` or pipe `HOME | GALLERY | INFO`
- **Back button:** Circular 40–44px, `--color-surface` bg, thin chevron `<`, top-left 16px from edges

### Tags / Chips
- Border: `1px solid --color-border-visible`, no fill. Text: Space Mono, 12px, ALL CAPS
- Radius: 999px (pill) or 4px (technical). Padding: 4px 12px. Active: `--color-text-display` border+text

### Segmented Control
- Container: `1px solid --color-border-visible`, pill or 8px rounded
- Active: `--color-text-display` bg, `--color-black` text (inverted). Inactive: transparent, `--color-text-secondary`
- Text: Space Mono, ALL CAPS, 11px. Height: 36–44px. Transition: 200ms ease-out
- Max 2–4 segments

### Date / Period Navigation
- Layout: `< LABEL >` — back arrow, label, forward arrow
- Label: Space Mono/Grotesk, ALL CAPS. Arrows: thin chevrons, `--color-text-secondary`, 44px touch
- No calendar popovers — linear stepping IS the interaction

### Toggles / Switches
- Pill track, circle thumb. Off: `--color-border-visible` track, `--color-text-disabled` thumb
- On: `--color-text-display` track, `--color-black` thumb. Min touch target: 44px

### Segmented Progress Bars

The signature data visualization. Discrete blocks — mechanical, instrument-like.

**Anatomy:** Label + value above, full-width bar of discrete rectangular segments with 2px gaps below.

**Segments:** Square-ended blocks, no border-radius. Filled = solid status color. Empty = `--color-border` (dark) / `#E0E0E0` (light).

| State | Fill | When |
|-------|------|------|
| Neutral | `--color-text-display` | Within normal range |
| Over limit | `--color-accent` | Exceeds target |
| Good | `--color-success` | Healthy range |
| Moderate | `--color-warning` | Caution zone |

**Overflow:** Filled segments continue past "full" mark in status color (typically red).
**Sizes:** Hero 16–20px, Standard 8–12px, Compact 4–6px height.
Always pair with numeric readout. Bar = proportion, number = precision.

### Other Data Visualization
- **Bar charts:** Vertical, white fill, `--color-border` remainder. Square ends.
- **Gauges:** Thin stroke circles + tick marks, numeric readout centered/adjacent.
- **Dot grids:** Vary opacity/size for heat maps. Uniform spacing.
- **Category differentiation:** Opacity → pattern → line style → color (last resort).
- Always show numeric value alongside any visual.

**Charts:** Line 1.5–2px `--color-text-display`, average dashed 1px `--color-text-secondary`. Axis labels: Space Mono, 12px. Grid: `--color-border`, horizontal only. No area fill, no legend boxes — label lines directly.

### Widgets (Dashboard Cards)
- `--color-surface` bg, 16px radius. Hero metric: large Doto/Space Mono, left-aligned
- Unit: label size, adjacent. Category: ALL CAPS Space Mono top-left
- Instrument gauges: compass, thermometer, dial motifs

### Overlays & Layering

No shadows. Layering through background contrast and borders.

- **Modals:** Backdrop `rgba(0,0,0,0.8)`, dialog `--color-surface` + `1px solid --color-border-visible` + 16px radius, centered max 480px. Close: `[ X ]` top-right ghost button.
- **Bottom sheets:** `--color-surface`, 2px handle bar centered, 16px top radius, drag-to-dismiss. Full-page sheets: title centered + dismiss button right, sections with `--color-text-secondary` headings.
- **Dropdowns:** `--color-surface-raised`, `1px solid --color-border-visible` 8px radius, 44px items. Selected: left 2px accent bar. No shadow.
- **Toasts:** None. Use inline status text: `[SAVED]`, `[ERROR: ...]`. Space Mono, 12px, near trigger.

### State Patterns
- **Error:** Input border → `--color-accent` + message below. Form-level: summary box `1px solid --color-accent`. Inline: `[ERROR]` prefix. Never red backgrounds or alert banners.
- **Empty:** Centered, 96px+ padding. Headline `--color-text-secondary`, 1 sentence description `--color-text-disabled`. Optional dot-matrix illustration. No mascots.
- **Loading:** Segmented spinner (hardware-style), or segmented bar + percentage. No skeletons — use `[LOADING]` bracket text.
- **Disabled:** Opacity 0.4 or `--color-text-disabled`. Borders fade to `--color-border`.

---

## 10. PLATFORM OUTPUT

### Tailwind v4 (preferred for web/React)

Load fonts via Google Fonts (see Section 6). Define all tokens in a `@theme` block — no `tailwind.config.js` needed.

```css
@import "tailwindcss";

@theme {
  /* Fonts */
  --font-display: "Doto", "Space Mono", monospace;
  --font-body:    "Space Grotesk", "DM Sans", system-ui, sans-serif;
  --font-mono:    "Space Mono", "JetBrains Mono", "SF Mono", monospace;

  /* Colors — dark mode defaults */
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
  --color-accent-subtle:  rgba(215, 25, 33, 0.15);
  --color-success:        #4A9E5C;
  --color-warning:        #D4A843;
  --color-interactive:    #5B9BF6;

  /* Spacing */
  --spacing-2xs: 2px;
  --spacing-xs:  4px;
  --spacing-sm:  8px;
  --spacing-md:  16px;
  --spacing-lg:  24px;
  --spacing-xl:  32px;
  --spacing-2xl: 48px;
  --spacing-3xl: 64px;
  --spacing-4xl: 96px;
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
- Colors: `bg-surface`, `bg-surface-raised`, `text-text-primary`, `text-text-secondary`, `text-text-display`, `text-text-disabled`, `border-border`, `border-border-visible`, `text-accent`, `text-success`, `text-warning`
- Fonts: `font-display` (Doto), `font-body` (Space Grotesk), `font-mono` (Space Mono)
- Spacing: `p-xs`, `p-sm`, `p-md`, `gap-lg`, `mt-2xl`, etc.

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

### Plain CSS (no Tailwind)

```css
:root {
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
  --color-accent-subtle:  rgba(215,25,33,0.15);
  --color-success:        #4A9E5C;
  --color-warning:        #D4A843;
  --color-interactive:    #5B9BF6;
  --spacing-xs: 4px; --spacing-sm: 8px; --spacing-md: 16px;
  --spacing-lg: 24px; --spacing-xl: 32px; --spacing-2xl: 48px;
  --spacing-3xl: 64px; --spacing-4xl: 96px;
}
@media (prefers-color-scheme: light) {
  :root {
    --color-black: #F5F5F5; --color-surface: #FFFFFF; --color-surface-raised: #F0F0F0;
    --color-border: #E8E8E8; --color-border-visible: #CCCCCC;
    --color-text-disabled: #999999; --color-text-secondary: #666666;
    --color-text-primary: #1A1A1A; --color-text-display: #000000;
    --color-interactive: #007AFF;
  }
}
```

### SwiftUI / iOS

Register fonts in Info.plist, bundle `.ttf` files. Use `@Environment(\.colorScheme)` for mode switching.

```swift
extension Color {
    static let ndBlack          = Color(hex: "000000")
    static let ndSurface        = Color(hex: "111111")
    static let ndSurfaceRaised  = Color(hex: "1A1A1A")
    static let ndBorder         = Color(hex: "222222")
    static let ndBorderVisible  = Color(hex: "333333")
    static let ndTextDisabled   = Color(hex: "666666")
    static let ndTextSecondary  = Color(hex: "999999")
    static let ndTextPrimary    = Color(hex: "E8E8E8")
    static let ndTextDisplay    = Color.white
    static let ndAccent         = Color(hex: "D71921")
    static let ndSuccess        = Color(hex: "4A9E5C")
    static let ndWarning        = Color(hex: "D4A843")
    static let ndInteractive    = Color(hex: "5B9BF6")
}
```

Light mode values from the Dark/Light table in Section 7. Fonts via `.custom("Doto"/"SpaceGrotesk-Regular"/"SpaceMono-Regular", size:)`.

### Paper (Design Tool)

Direct hex values (no CSS variables). Dark mode as default canvas, light mode as separate artboard. Values from Section 7.

