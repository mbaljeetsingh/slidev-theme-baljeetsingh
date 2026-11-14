<script setup lang="ts">
// A numbered step card: n, title, tag (e.g. "Redis"), tone of the tag.
defineProps<{ n?: string | number; title: string; tag?: string; tone?: 'default' | 'primary' | 'good' | 'warn' }>();
</script>

<template>
  <div class="step">
    <span v-if="n !== undefined" class="n">{{ n }}</span>
    <div class="text">
      <div class="title">
        {{ title }}
        <Chip v-if="tag" :tone="tone">{{ tag }}</Chip>
      </div>
      <div class="body"><slot /></div>
    </div>
  </div>
</template>

<style scoped>
.step {
  display: flex;
  gap: 0.7rem;
  align-items: flex-start;
  border: 1px solid var(--bs-border);
  border-radius: var(--bs-radius-lg);
  background: var(--bs-bg-muted);
  padding: 0.55rem 0.85rem;
}
.n {
  flex: none;
  display: grid;
  place-items: center;
  width: 1.45rem;
  height: 1.45rem;
  margin-top: 0.05rem;
  border-radius: 999px;
  background: var(--bs-bg-elevated);
  color: var(--bs-text);
  font-size: 0.72rem;
  font-weight: 600;
}
.title { display: flex; align-items: center; gap: 0.5rem; font-weight: 600; font-size: 0.9rem; color: var(--bs-text); line-height: 1.5rem; }
.body { color: var(--bs-text-muted); font-size: 0.8rem; line-height: 1.4; }
</style>
