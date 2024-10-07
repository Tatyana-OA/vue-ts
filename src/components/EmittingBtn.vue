<template lang="">
  <div><button @click="emit('add-count', 1)">ADD</button></div>
  <div><button @click="emit('reset-count')">RESET</button></div>
</template>

<script setup lang="ts">
const emit = defineEmits<{
  // Event of name 'add-count' with param of type num, returns void
  (event: 'add-count', num: number): void
  (event: 'reset-count'): void
}>()
</script>
