<script setup lang="ts">
defineProps<{ tone?: 'default' | 'primary' | 'good' | 'warn' }>();
</script>

<template>
  <span class="chip" :class="tone ?? 'default'"><slot /></span>
</template>

<style scoped>
.chip {
  display: inline-flex;
  align-items: center;
  font-size: 0.7rem;
  font-weight: 500;
  line-height: 1.4;
  border-radius: 999px;
  padding: 0.05rem 0.5rem;
  border: 1px solid var(--bs-border);
  color: var(--bs-text-muted);
  white-space: nowrap;
}
.primary { color: var(--bs-primary); border-color: color-mix(in oklch, var(--bs-primary) 35%, transparent); }
.good { color: var(--bs-good); border-color: color-mix(in oklch, var(--bs-good) 35%, transparent); }
.warn { color: var(--bs-warn); border-color: color-mix(in oklch, var(--bs-warn) 35%, transparent); }
</style>
