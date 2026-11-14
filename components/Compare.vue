<script setup lang="ts">
// Rows of "before → after". rows: [{ label, before, after }]
defineProps<{
  rows: { label: string; before: string; after: string }[];
  beforeLabel?: string;
  afterLabel?: string;
}>();
</script>

<template>
  <div class="compare">
    <div class="head" />
    <div class="head">{{ beforeLabel ?? 'Today' }}</div>
    <div class="head" />
    <div class="head after-head">{{ afterLabel ?? 'Rebuild' }}</div>
    <template v-for="r in rows" :key="r.label">
      <div class="label">{{ r.label }}</div>
      <div class="before">{{ r.before }}</div>
      <div class="arrow" aria-hidden="true">→</div>
      <div class="after">{{ r.after }}</div>
    </template>
  </div>
</template>

<style scoped>
.compare {
  display: grid;
  grid-template-columns: 11rem 1fr 1.5rem 1fr;
  column-gap: 1rem;
  align-items: baseline;
}
.head { font-size: 0.72rem; color: var(--bs-text-muted); padding-bottom: 0.4rem; border-bottom: 1px solid var(--bs-border); }
.after-head { color: var(--bs-primary); }
.label, .before, .arrow, .after { padding: 0.55rem 0; border-bottom: 1px solid var(--bs-border); }
.label { font-size: 0.85rem; color: var(--bs-text-muted); }
.before { font-size: 0.95rem; color: var(--bs-text-toned); }
.arrow { color: var(--bs-text-muted); text-align: center; }
.after { font-family: 'Instrument Serif', serif; font-size: 1.45rem; line-height: 1.1; color: var(--bs-text); }
</style>
