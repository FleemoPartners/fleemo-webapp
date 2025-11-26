<template>
  <div class="base-card">
    <slot></slot>
  </div>
</template>

<style scoped>
.base-card {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  transition: transform var(--transition-fast), border-color var(--transition-fast);
}

.base-card:hover {
  transform: translateY(-4px);
  border-color: var(--color-primary);
}
</style>
