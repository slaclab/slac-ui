# slac-ui

Shared SLAC frontend theme, as a [shadcn registry](https://ui.shadcn.com/docs/registry).

## Install

Add to `components.json`, then run the command. Requires Tailwind 4.

```json
"registries": { "@slac": "https://slaclab.github.io/slac-ui/r/{name}.json" }
```

```bash
npx shadcn add @slac/theme
```

Migrating an existing app: delete its `:root`, `.dark` and brand `@layer base`
rules first. `shadcn add` appends rather than replaces.

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

`r/theme.json` is the whole registry. Every token in `light` needs one in `dark`
except `radius`, or dark mode silently inherits the light value.
