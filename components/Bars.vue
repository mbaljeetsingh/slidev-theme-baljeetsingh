<script setup lang="ts">
import { computed } from 'vue';

// Horizontal bars. items: [{ label, value, display }]; highlight: index to colour.
const props = defineProps<{
  items: { label: string; value: number; display: string; note?: string }[];
  highlight?: number;
}>();

const max = computed(() => Math.max(...props.items.map((i) => i.value)));
</script>

<template>
  <div class="bars">
    <div v-for="(item, i) in items" :key="item.label" class="row" :class="{ hi: i === highlight }">
      <div class="label">{{ item.label }}</div>
      <div class="track">
        <div class="bar" :style="{ width: `${(item.value / max) * 100}%`, animationDelay: `${i * 90}ms` }" />
      </div>
      <div class="value">
        {{ item.display }}
        <span v-if="item.note" class="note">{{ item.note }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bars { display: flex; flex-direction: column; gap: 0.7rem; }
.row { display: grid; grid-template-columns: 6.5rem 1fr 11rem; align-items: center; gap: 1rem; }
.label { font-size: 0.85rem; color: var(--bs-text-muted); }
.track { height: 1.6rem; border-radius: 0.4rem; background: var(--bs-bg-muted); overflow: hidden; }
.bar {
  height: 100%;
  border-radius: 0.4rem;
  background: var(--bs-bar, color-mix(in oklch, var(--bs-text-muted) 45%, transparent));
  transform-origin: left;
  animation: grow 900ms cubic-bezier(0.2, 0.8, 0.2, 1) both;
}
@keyframes grow { from { transform: scaleX(0); } }
.hi .bar { background: var(--bs-primary); }
.hi .label { color: var(--bs-text); font-weight: 600; }
.value { font-family: 'Instrument Serif', serif; font-size: 1.4rem; color: var(--bs-text); line-height: 1; }
.note { font-family: 'Public Sans', sans-serif; font-size: 0.72rem; color: var(--bs-text-muted); margin-left: 0.35rem; }
</style>
