<script setup lang="ts">
import { useSlideContext } from '@slidev/client';

// Frontmatter: kicker, value (the big number), label, was (optional "before" value).
const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout big-number">
    <div v-if="fm.kicker" class="eyebrow">{{ fm.kicker }}</div>
    <div class="value">{{ fm.value }}</div>
    <div v-if="fm.label" class="label">{{ fm.label }}</div>
    <div v-if="fm.was" class="was">{{ fm.was }}</div>
    <div class="more"><slot /></div>
  </div>
</template>

<style scoped>
.big-number { display: flex; flex-direction: column; justify-content: center; padding-inline: 5rem; }
.value {
  font-family: 'Instrument Serif', serif;
  font-size: 9rem;
  line-height: 0.95;
  letter-spacing: -0.03em;
  color: var(--bs-text);
}
.label { font-size: 1.35rem; color: var(--bs-text); margin-top: 0.75rem; }
.was { color: var(--bs-text-muted); margin-top: 0.25rem; }
.more { margin-top: 1.5rem; color: var(--bs-text-muted); max-width: 40rem; }
</style>
