# slidev-theme-baljeetsingh

Slidev theme in the style of baljeetsingh.in. Consumed by the decks in the sibling `talks` repo as the npm package `slidev-theme-baljeetsingh` (`theme: baljeetsingh` in a deck's headmatter).

`showcase.md` shows every layout and component. Run it after any theme change:

```bash
pnpm dev
```

## Files

- `styles/tokens.css`: the only place colours, radius and padding are defined. Mirrors the site: Nuxt UI primary `blue`, neutral `zinc` (`app/app.config.ts`); Tailwind v4 oklch values. If the site's colours change, change them here.
- `styles/layout.css`: base styles for `.slidev-layout` (type, lists, code, tables) and the helpers below.
- `layouts/*.vue`: theme layouts; Slidev's built-in layouts (`two-cols`, `image-right`, …) still work.
- `components/*.vue`: auto-available in every slide, no imports.
- `slide-bottom.vue`: footer with the talk title and slide number (hidden on `cover` and `closing`, or with `footer: false`).
- `setup/shiki.ts`: code themes (vitesse dark/light).
- `assets/avatar.png`: default cover avatar (same image as the site).

## Look

- Dark by default (`colorSchema: dark` in the deck); light works too.
- Headings: Instrument Serif, normal weight, tight tracking. `*italic*` in a heading renders as the muted serif accent: `# Ask Khalis AI, *built to scale*`.
- Body: Public Sans. Code: JetBrains Mono.
- Thin vertical rails at the slide edges, like the site's container lines.

## Layouts

| Layout | Frontmatter | Use for |
|---|---|---|
| `cover` | `eyebrow`, `author`, `role`, `date`, `avatar?` | first slide |
| `default` | `kicker?` (small pill above the title) | most slides |
| `statement` | `kicker?` | one big sentence |
| `section` | `number` (e.g. `'02'`) | section dividers |
| `big-number` | `kicker?`, `value`, `label`, `was?`; slot = supporting text | one headline figure |
| `closing` | `kicker?`, `links?: [{ label }]` | last slide |

## Components

```html
<Stat value="3.7 s" label="to answer" was="10–14 s" tone="good|warn" />
<Chip tone="primary|good|warn">Redis</Chip>
<Callout tone="primary|good|warn" title="Optional title">Body</Callout>
<Step n="1" title="Exact cache" tag="Redis" tone="good">description</Step>
<Compare before-label="Today" after-label="Rebuild" :rows="[{ label, before, after }]" />
<Bars :highlight="2" :items="[{ label, value, display, note? }]" />
```

Helper classes: `.card`, `.eyebrow`, `.muted`, `.accent`, `.good`, `.warn`, `.serif`. Layout with UnoCSS utilities (`grid grid-cols-2 gap-4 mt-4`).

## Rules

- Colours only through the `--bs-*` tokens; no hex values in layouts or slides.
- Reveal lists with `<v-clicks>` placed **inside** the flex/grid wrapper, so each child is its own click.
- Emphasis on a number: `<span v-mark.underline.orange="2">…</span>`.
- If a slide overflows, cut text first; `zoom: 0.9` in the slide frontmatter as a last resort.
- Speaker notes in `<!-- -->` at the end of each slide; `[click]` lines match the reveals.
- Add a component only when a talk needs it, then add it to `showcase.md` and the table above.
