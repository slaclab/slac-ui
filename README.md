# slac-ui

Shared SLAC frontend theme. Tailwind 4 only.

## Install

```bash
bun add github:slaclab/slac-ui#v0.1.0
```

```css
@import "tailwindcss";
@import "tw-animate-css";
@import "@slaclab/theme/slac.css";
```

Keep your own `@import "tailwindcss"`. Tailwind resolves source detection
relative to the file holding that import, so it cannot come from here.

Migrating an existing app: delete its `@custom-variant dark`, `@theme inline`,
`:root`, `.dark` and brand `@layer base` blocks. This package provides all five.
App-specific tokens stay in the app — Tailwind merges `@theme` blocks.

If you use [knip](https://knip.dev), add `@slaclab/theme` to
`ignoreDependencies`. knip does not follow CSS `@import`, so a CSS-only
dependency always reads as unused.

## Palette

Stanford's brand palette ([identity.stanford.edu](https://identity.stanford.edu/design-elements/color/)).

| Token | Light | Dark |
| --- | --- | --- |
| `primary`, `ring` | `#b1040e` Digital Red | `#b1040e` Digital Red |
| `accent` | `#dad7cb` Fog | `#53565a` Cool Grey |
| `background`, `card` | `oklch(1 0 0)` | `#25282b` |
| `foreground` | `oklch(0.145 0 0)` | `#dad7cb` Fog |
| `chart-1` | `#e98300` Poppy | `#4298b5` Sky |
| `chart-2` | `#007c92` Lagunita | `#279989` Palo Verde |
| `chart-3` | `#175e54` Palo Alto | `#fedd5c` Illuminating |
| `chart-4` | `#fedd5c` Illuminating | `#765e99` Lavender |
| `chart-5` | `#e04f39` Spirited | `#e98300` Poppy |

Logos are trademarks and are not distributed here.

## Editing

Every token in `:root` needs one in `.dark` except `--radius`, or dark mode
silently inherits the light value. Tag a release so consumers can pin it.
