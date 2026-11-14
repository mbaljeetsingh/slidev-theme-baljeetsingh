<script setup lang="ts">
import { computed } from 'vue';
import { useNav, useSlideContext } from '@slidev/client';

// Footer on content slides: the talk title and the slide number.
const { $frontmatter: fm, $page: page } = useSlideContext();
const { total, slides } = useNav();
const title = computed(() => slides.value[0]?.meta?.slide?.frontmatter?.title ?? '');
const hidden = computed(() => ['cover', 'closing'].includes(fm.layout) || fm.footer === false);
</script>

<template>
  <footer v-if="!hidden" class="bs-footer">
    <span>{{ title }}</span>
    <span>{{ page }} / {{ total }}</span>
  </footer>
</template>

<style scoped>
.bs-footer {
  position: absolute;
  left: var(--bs-pad-x);
  right: var(--bs-pad-x);
  bottom: 1rem;
  display: flex;
  justify-content: space-between;
  font-size: 0.68rem;
  color: var(--bs-text-muted);
  letter-spacing: 0.02em;
}
</style>
