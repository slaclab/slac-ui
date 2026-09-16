# slac-ui

Shared SLAC frontend theme and tooling config. Tailwind 4, Biome 2, TypeScript.

```bash
bun add github:slaclab/slac-ui#v0.2.0
```

## Theme

```css
@import "tailwindcss";
@import "tw-animate-css";
@import "@slaclab/ui/slac.css";
```

Keep your own `@import "tailwindcss"`. Tailwind resolves source detection
relative to the file holding that import, so it cannot come from here.

Migrating: delete the app's `@custom-variant dark`, `@theme inline`, `:root`,
`.dark` and brand `@layer base` blocks. This package provides all five.
App-specific tokens stay in the app — Tailwind merges `@theme` blocks.

## Biome

```json
{
  "extends": ["@slaclab/ui/biome"],
  "files": { "includes": ["**", "!**/dist/**/*"] }
}
```

`files.includes` stays local; the paths are project-specific.

## TypeScript

```json
{
  "extends": "@slaclab/ui/tsconfig.json",
  "compilerOptions": { "paths": { "@/*": ["./src/*"] } },
  "include": ["src"],
  "references": [{ "path": "./tsconfig.node.json" }]
}
```

`paths` and `include` must stay local. TypeScript resolves both relative to the
file that declares them, so inheriting them would point into `node_modules` —
`@/*` fails with TS2307 if you try.

`@slaclab/ui/tsconfig.node.json` is the matching base for the Vite config project.

## Not shareable

`components.json` (shadcn) and `knip.json` have no `extends` mechanism, so their
duplication stays. If you use knip, add `@slaclab/ui` to `ignoreDependencies` —
knip does not follow CSS `@import`, so a CSS dependency always reads as unused.

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
