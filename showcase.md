---
theme: ./
title: Theme showcase
info: Every layout and component in slidev-theme-baljeetsingh.
colorSchema: dark
transition: slide-left
layout: cover
eyebrow: slidev-theme-baljeetsingh
author: Baljeet Singh
role: Theme showcase
date: Every layout and component
---

# Slides in the *site’s style*

Cover layout: `eyebrow`, `author`, `role`, `date`, optional `avatar`. Italic in a heading renders as the muted serif accent.

---
kicker: default layout
---

# Default, with a *kicker*

The subtitle paragraph right after the heading is muted.

- Bullets use a short dash marker
- **Bold** is full-strength text; body text is toned down
- Inline `code` gets a chip
- Helpers: <span class="accent">.accent</span>, <span class="good">.good</span>, <span class="warn">.warn</span>, <span class="muted">.muted</span>, <span class="serif">.serif</span>

<div class="card mt-4">A <code>.card</code> div: bordered, rounded, muted background.</div>

---
layout: statement
kicker: statement layout
---

# One big idea, *said plainly*

A supporting line under the statement.

---
layout: section
number: '02'
---

# Section layout

`number` in frontmatter draws the large serif numeral.

---
layout: big-number
kicker: big-number layout
value: $0.00046
label: per new question
was: ~$0.010–0.013 today
---

Frontmatter `value`, `label`, `was`; the slot holds the supporting text.

---
kicker: Stat · Chip · Callout
---

# Numbers and labels

<div class="grid grid-cols-3 gap-3">
  <Stat value="3.7 s" label="to answer" was="10–14 s" />
  <Stat value="93–97%" label="relevant" tone="good" />
  <Stat value="57–83%" label="faithful" tone="warn" />
</div>

<div class="flex gap-2 mt-5">
  <Chip>default</Chip><Chip tone="primary">primary</Chip><Chip tone="good">good</Chip><Chip tone="warn">warn</Chip>
</div>

<div class="grid grid-cols-3 gap-3 mt-5">
  <Callout title="primary">Default tone.</Callout>
  <Callout tone="good" title="good">Something that worked.</Callout>
  <Callout tone="warn" title="warn">Something to watch.</Callout>
</div>

---
kicker: Step
---

# Steps, *revealed one by one*

<div class="grid grid-cols-2 gap-2 mt-4">
<v-clicks>
<Step n="1" title="Exact cache" tag="Redis" tone="good">same question → answer in ms</Step>
<Step n="2" title="Semantic cache" tag="pgvector" tone="good">reworded question → reuse</Step>
<Step n="3" title="AI call" tag="Haiku" tone="primary">only for new questions</Step>
<Step title="No number">omit <code>n</code> for a plain card</Step>
</v-clicks>
</div>

---
kicker: Compare
---

# Before and after

<Compare class="mt-4" before-label="Before" after-label="After" :rows="[
  { label: 'Cost', before: '~1¢', after: '$0.00046' },
  { label: 'Time', before: '10–14 s', after: '3.7 s' },
  { label: 'Calls', before: '~5', after: '2 + 1' },
]" />

---
kicker: Bars
---

# A quick bar chart

<Bars class="mt-6" :highlight="1" :items="[
  { label: 'Option A', value: 100, display: '100' },
  { label: 'Option B', value: 62, display: '62', note: 'highlighted' },
  { label: 'Option C', value: 25, display: '25' },
]" />

---
kicker: Code and marks
---

# Code, *highlighted per click*

```ts {1|2-3|all}
const exact = await getExact(version, norm)
if (exact)
  return served('exact', exact)
```

Hand-drawn marks: <span v-mark.underline.orange="1">underline</span>, <span v-mark.circle.blue="2">circle</span>.

---
layout: closing
kicker: closing layout
links:
  - label: baljeetsingh.in
  - label: github.com/mbaljeetsingh
---

# Thank *you*

Optional `links` render as pills.
