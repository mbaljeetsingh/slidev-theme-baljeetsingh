<script setup lang="ts">
import { useSlideContext } from '@slidev/client';

// Frontmatter: kicker, links: [{ label, href }]
const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout closing">
    <div class="glow" aria-hidden="true" />
    <div v-if="fm.kicker" class="eyebrow">{{ fm.kicker }}</div>
    <slot />
    <div v-if="fm.links?.length" class="links">
      <span v-for="l in fm.links" :key="l.label" class="link">{{ l.label }}</span>
    </div>
  </div>
</template>

<style scoped>
.closing { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; overflow: hidden; }
.glow {
  position: absolute;
  width: 700px;
  height: 700px;
  bottom: -420px;
  left: 50%;
  translate: -50% 0;
  border-radius: 999px;
  background: radial-gradient(circle, color-mix(in oklch, var(--bs-primary) 22%, transparent) 0%, transparent 65%);
}
.closing .eyebrow { align-self: center; position: relative; }
.closing :deep(h1) { font-size: 4.2rem; position: relative; }
.closing :deep(p) { color: var(--bs-text-muted); position: relative; }
.closing :deep(ol) { position: relative; text-align: left; margin-top: 1.25rem; }
.links { display: flex; gap: 0.6rem; margin-top: 1.5rem; position: relative; }
.link { font-size: 0.8rem; border: 1px solid var(--bs-border); border-radius: 999px; padding: 0.2rem 0.75rem; }
</style>
