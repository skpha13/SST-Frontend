<script setup lang="ts">
const props = defineProps<{
  username: string
  comment: string
  rating: number
  profilePhoto: string
}>();
</script>

<template>
  <div class="review">
    <div class="flex items-center mb-4">
      <img :src="props.profilePhoto" alt="Profile Photo" class="w-10 h-10 rounded-full mr-4">
      <div>
        <h4 class="text-lg font-semibold">{{ props.username }}</h4>
        <span class="text-gray-500">Rated {{ props.rating }}/5</span>
      </div>
    </div>
    <p class="mb-6">{{ props.comment }}</p>
  </div>
</template>

<style scoped>
.review {
  border: 1px solid #ddd;
  padding: 16px;
  border-radius: 8px;
}

.review img {
  object-fit: cover;
}

.review h4 {
  margin-bottom: 4px;
}
</style>