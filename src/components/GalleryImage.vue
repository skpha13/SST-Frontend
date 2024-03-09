<script setup lang="ts">
const props = defineProps<{
  path: string
}>()
console.log(props.path)
</script>

<template>
  <div>
    <img class="h-full max-w-full rounded-lg object-cover w-full" :src="props.path" alt="Failed to load Image">
  </div>
</template>