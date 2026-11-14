# slidev-theme-baljeetsingh

A [Slidev](https://sli.dev) theme in the style of [baljeetsingh.in](https://baljeetsingh.in): Instrument Serif headlines with an italic accent, Public Sans body, zinc neutrals and a blue accent. Dark by default, light works too.

## Use

```bash
pnpm add github:mbaljeetsingh/slidev-theme-baljeetsingh
```

```md
---
theme: baljeetsingh
colorSchema: dark
---
```

## Layouts

`cover`, `default`, `statement`, `section`, `big-number`, `closing`. Slidev's built-in layouts still work.

## Components

`Stat`, `Chip`, `Callout`, `Step`, `Compare`, `Bars`. Available in every slide without imports.

Frontmatter options and usage for each are in [AGENTS.md](AGENTS.md).

## Develop

```bash
pnpm install
pnpm dev      # opens showcase.md with every layout and component
```

Colours, radius and padding live in `styles/tokens.css` only.
