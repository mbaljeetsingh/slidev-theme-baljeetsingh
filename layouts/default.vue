<script setup lang="ts">
import { useSlideContext } from '@slidev/client';

// Optional `kicker` in frontmatter: a small pill above the title.
const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout default">
    <div v-if="fm.kicker" class="eyebrow">{{ fm.kicker }}</div>
    <slot />
  </div>
</template>
