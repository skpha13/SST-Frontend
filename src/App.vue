<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import text from "@/JSON Customization/text.json";
</script>

<template>
  <RouterView />

  <footer class="fixed left-0 bottom-0 w-full bg-neutral-700 text-white p-4 z-50">
    <div class="flex flex-col items-center">
      <p>&copy; 2024 Demolition Company. All rights reserved.</p>
    </div>
  </footer>

</template>