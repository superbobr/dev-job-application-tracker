<script setup>
</script>
<template>
  <span class="badge">
    <slot />
  </span>
</template>

<style scoped>
.badge {
  padding: 4px 8px;
  border-radius: 4px;
  background-color: red;
  font-weight: bold;
  font-size: 0.9rem;
}
</style>