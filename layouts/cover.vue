<script setup lang="ts">
import { useSlideContext } from '@slidev/client';
import defaultAvatar from '../assets/avatar.png';

// Frontmatter: eyebrow, author, role, avatar (defaults to the theme's avatar), date.
const { $frontmatter: fm } = useSlideContext();
</script>

<template>
  <div class="slidev-layout cover">
    <div class="glow" aria-hidden="true" />
    <div class="body">
      <div v-if="fm.eyebrow" class="eyebrow">{{ fm.eyebrow }}</div>
      <div class="heading"><slot /></div>
    </div>
    <div class="foot">
      <div v-if="fm.author" class="who">
        <img :src="fm.avatar ?? defaultAvatar" :alt="fm.author" class="avatar">
        <div>
          <div class="name">{{ fm.author }}</div>
          <div v-if="fm.role" class="role">{{ fm.role }}</div>
        </div>
      </div>
      <div v-if="fm.date" class="date">{{ fm.date }}</div>
    </div>
  </div>
</template>

<style scoped>
.cover {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 3rem var(--bs-pad-x);
  overflow: hidden;
}
.glow {
  position: absolute;
  width: 620px;
  height: 620px;
  right: -180px;
  top: -260px;
  border-radius: 999px;
  background: radial-gradient(circle, color-mix(in oklch, var(--bs-primary) 22%, transparent) 0%, transparent 65%);
  pointer-events: none;
}
.body { position: relative; flex: 1; display: flex; flex-direction: column; justify-content: center; max-width: 46rem; }
.heading :deep(h1) { font-size: 4.4rem; line-height: 1; margin-bottom: 1rem; }
.heading :deep(p) { font-size: 1.15rem; color: var(--bs-text-muted); max-width: 36rem; }
.foot {
  position: relative;
  display: flex;
  align-items: end;
  justify-content: space-between;
  border-top: 1px solid var(--bs-border);
  padding-top: 1.1rem;
}
.who { display: flex; align-items: center; gap: 0.8rem; }
.avatar { width: 2.6rem; height: 2.6rem; border-radius: 999px; box-shadow: 0 0 0 1px var(--bs-border); }
.name { font-weight: 600; color: var(--bs-text); font-size: 0.95rem; }
.role, .date { color: var(--bs-text-muted); font-size: 0.82rem; }
</style>
