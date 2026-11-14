<script setup lang="ts">
// value: the headline number; label: what it is; was: the "before" value, shown struck through.
defineProps<{ value: string; label: string; was?: string; tone?: 'default' | 'good' | 'warn' }>();
</script>

<template>
  <div class="stat">
    <div class="value" :class="tone">{{ value }}</div>
    <div class="label">{{ label }}</div>
    <div v-if="was" class="was"><span>{{ was }}</span> today</div>
  </div>
</template>

<style scoped>
.stat {
  border: 1px solid var(--bs-border);
  border-radius: var(--bs-radius-lg);
  background: var(--bs-bg-muted);
  padding: 0.9rem 1.1rem 1rem;
}
.value {
  font-family: 'Instrument Serif', serif;
  font-size: 2.7rem;
  line-height: 1;
  letter-spacing: -0.02em;
  color: var(--bs-text);
}
.value.good { color: var(--bs-good); }
.value.warn { color: var(--bs-warn); }
.label { margin-top: 0.45rem; font-size: 0.85rem; color: var(--bs-text); font-weight: 500; }
.was { margin-top: 0.15rem; font-size: 0.78rem; color: var(--bs-text-muted); }
.was span { text-decoration: line-through; text-decoration-color: color-mix(in oklch, var(--bs-text-muted) 70%, transparent); }
</style>
