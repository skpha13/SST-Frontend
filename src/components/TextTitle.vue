<script setup lang="ts">
const props = defineProps<{
  title: string
}>()
</script>

<template>
  <h1 class="text-2xl text-white text-center font-extrabold mb-4 mt-4">{{ props.title }}</h1>
</template>