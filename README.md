# Nothing Design Skill

A design system prompt/skill inspired by Nothing's visual language. Monochrome, typographic, industrial. Works with any LLM that supports custom instructions or skill/context files.

I kept describing the same design rules over and over — Swiss typography, OLED blacks, segmented progress bars, dot-matrix motifs. So I packaged it into a reusable skill.

![Preview](preview.gif)

## What you get

Tell your LLM "Nothing style" or to use "Nothing design" and it generates UI following these principles:

- Three-layer visual hierarchy (display, body, metadata — that's it)
- Space Grotesk + Space Mono + Doto font stack
- Full dark and light mode token system
- Segmented progress bars, mechanical toggles, instrument-style widgets
- Output as HTML/Tailwind v4, SwiftUI, or React

## Install

### Claude Code

Copy the `nothing-design` folder into your Claude Code skills directory:

```sh
git clone https://github.com/adamdburton/nothing-design-skill.git
cp -r nothing-design-skill/nothing-design ~/.claude/skills/
```

### Other LLMs (ChatGPT, Gemini, Cursor, etc.)

Paste the contents of `nothing-design/SKILL.md` as a system prompt or custom instruction. Include the reference files as additional context when needed.

## What's inside

| File | |
|------|---|
| `SKILL.md` | Design philosophy, craft rules, workflow |
| `references/tokens.md` | Colors, fonts, spacing, Tailwind v4 `@theme` tokens, motion |
| `references/components.md` | Buttons, cards, lists, tables, overlays |
| `references/platform-mapping.md` | Tailwind v4 `@theme`, plain CSS, SwiftUI, React output mappings |

## License

MIT
