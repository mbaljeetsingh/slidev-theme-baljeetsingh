<script setup lang="ts">
defineProps<{ tone?: 'primary' | 'good' | 'warn'; title?: string }>();
</script>

<template>
  <div class="callout" :class="tone ?? 'primary'">
    <div v-if="title" class="title">{{ title }}</div>
    <div class="body"><slot /></div>
  </div>
</template>

<style scoped>
.callout {
  --tone: var(--bs-primary);
  border-radius: var(--bs-radius-lg);
  padding: 0.75rem 1rem;
  background: color-mix(in oklch, var(--tone) 9%, transparent);
  box-shadow: inset 2px 0 0 var(--tone);
  font-size: 0.9rem;
}
.good { --tone: var(--bs-good); }
.warn { --tone: var(--bs-warn); }
.title { font-weight: 600; color: var(--bs-text); margin-bottom: 0.15rem; }
.body { color: var(--bs-text-toned); }
</style>
