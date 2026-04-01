# Nothing Design System — Platform Mapping

## 1. HTML / CSS / WEB

### Tailwind v4 (preferred)

Load fonts via Google Fonts `<link>` or `@import`. Define all design tokens in a `@theme` block (Tailwind v4 CSS-first config). Dark/light via `prefers-color-scheme` media query or a `.dark` class toggled on `<html>`.

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

/* Class-based light mode (add .light to <html> for manual toggle) */
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

**Tailwind utility usage:** Tokens map directly to utilities. `bg-surface`, `text-text-primary`, `border-border-visible`, `font-mono`, `p-md`, `gap-sm`, etc. Spacing tokens map to `p-*`, `m-*`, `gap-*`.

### Plain CSS (no Tailwind)

Use the same variable names inside `:root` / dark-mode overrides:

```css
:root {
  --color-black:          #000000;
  --color-surface:        #111111;
  /* … same variables as @theme above … */
}
@media (prefers-color-scheme: light) {
  :root { --color-black: #F5F5F5; /* … */ }
}
```

---

## 2. SWIFTUI / iOS

Register fonts in Info.plist, bundle `.ttf` files. Use `@Environment(\.colorScheme)` for mode switching.

```swift
extension Color {
    static let ndBlack = Color(hex: "000000")
    static let ndSurface = Color(hex: "111111")
    static let ndSurfaceRaised = Color(hex: "1A1A1A")
    static let ndBorder = Color(hex: "222222")
    static let ndBorderVisible = Color(hex: "333333")
    static let ndTextDisabled = Color(hex: "666666")
    static let ndTextSecondary = Color(hex: "999999")
    static let ndTextPrimary = Color(hex: "E8E8E8")
    static let ndTextDisplay = Color.white
    static let ndAccent = Color(hex: "D71921")
    static let ndSuccess = Color(hex: "4A9E5C")
    static let ndWarning = Color(hex: "D4A843")
    static let ndInteractive = Color(hex: "5B9BF6")
}
```

Light mode values in tokens.md Dark/Light table. Derive Font extension from font stack table (trivial: `.custom("Doto"/"SpaceGrotesk-Regular"/"SpaceMono-Regular", size:)`).

---

## 3. REACT / TAILWIND V4

Install Tailwind v4 (`npm install tailwindcss@next @tailwindcss/vite` or `@tailwindcss/postcss`). Put the `@theme` block from Section 1 in your global CSS file (e.g. `globals.css`). No `tailwind.config.js` needed for token definitions.

**Example component:**

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

**Class conventions:**
- Colors: `bg-surface`, `bg-surface-raised`, `text-text-primary`, `text-text-secondary`, `text-text-display`, `text-text-disabled`, `border-border`, `border-border-visible`, `text-accent`, `text-success`, `text-warning`
- Fonts: `font-display` (Doto), `font-body` (Space Grotesk), `font-mono` (Space Mono)
- Spacing: `p-xs`, `p-sm`, `p-md`, `gap-lg`, `mt-2xl`, etc.

---

## 4. PAPER (DESIGN TOOL)

Use `get_font_family_info` to verify fonts before writing styles. Direct hex values (no CSS variables). Dark mode as default canvas, light mode as separate artboard.
