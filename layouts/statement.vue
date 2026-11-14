<script setup lang="ts">
import { useSlideContext } from '@slidev/client';

const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout statement">
    <div v-if="fm.kicker" class="eyebrow">{{ fm.kicker }}</div>
    <slot />
  </div>
</template>

<style scoped>
.statement { display: flex; flex-direction: column; justify-content: center; padding-inline: 5rem; }
.statement :deep(h1) { font-size: 3.6rem; line-height: 1.05; max-width: 22ch; }
.statement :deep(p) { color: var(--bs-text-muted); font-size: 1.1rem; margin-top: 1rem; max-width: 40rem; }
</style>
