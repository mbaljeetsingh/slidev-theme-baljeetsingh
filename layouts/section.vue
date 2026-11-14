<script setup lang="ts">
import { useSlideContext } from '@slidev/client';

// Frontmatter: number (e.g. "02").
const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout section">
    <div v-if="fm.number" class="num">{{ fm.number }}</div>
    <div class="content"><slot /></div>
  </div>
</template>

<style scoped>
.section { display: flex; align-items: end; padding-bottom: 4.5rem; }
.num {
  position: absolute;
  right: 3rem;
  top: 0.5rem;
  font-family: 'Instrument Serif', serif;
  font-size: 15rem;
  line-height: 1;
  color: var(--bs-bg-elevated);
}
.content { position: relative; max-width: 36rem; }
.content :deep(h1) { font-size: 3.6rem; }
.content :deep(p) { color: var(--bs-text-muted); }
</style>
