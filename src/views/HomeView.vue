<script setup lang="ts">
import text from "../JSON Customization/text.json"
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
import carouselImages from "@/JSON Customization/carousel-images.json"
import CarouselImage from "@/components/CarouselImage.vue";

const imgArray = carouselImages
console.log(imgArray)
</script>

<template>
  <header class="fixed top-0 left-0 w-full bg-neutral-700 text-white p-4 z-50">
    <div class="container mx-auto flex items-center justify-between">
      <h1 class="text-xl font-bold">
        <a href="#"> {{ text["company-name"] }} </a>
      </h1>

      <nav id="desktop-menu" class="space-x-4">
        <a href="#default-carousel" class="hover:bg-neutral-600 hover:rounded-lg p-2">Carousel</a>
        <a href="#about" class="hover:bg-neutral-600 hover:rounded-lg p-2">About</a>
        <a href="#" class="hover:bg-neutral-600 hover:rounded-lg p-2">Gallery</a>
        <a href="#" class="hover:bg-neutral-600 hover:rounded-lg p-2">Google Reviews</a>
        <a href="#" class="hover:bg-neutral-600 hover:rounded-lg p-2">Custom</a>
      </nav>

      <Menu id="mobile-menu" as="div" class="relative inline-block text-left">
        <div>
          <MenuButton class="inline-flex w-full justify-center gap-x-1.5 rounded-md bg-neutral-500 px-3 py-2 text-sm font-semibold text-white shadow-sm ring-1 ring-inset ring-neutral-500 hover:bg-neutral-600">
            Menu
            <ChevronDownIcon class="-mr-1 h-5 w-5 text-gray-400" aria-hidden="true" />
          </MenuButton>
        </div>

        <transition enter-active-class="transition ease-out duration-100" enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
          <MenuItems class="absolute right-0 z-10 mt-2 w-56 origin-top-right rounded-md bg-neutral-500 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none">
            <div class="py-1">
              <MenuItem v-slot="{ active }">
                <a href="#" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Carousel</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">About</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Gallery</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Google reviews</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Custom</a>
              </MenuItem>
            </div>
          </MenuItems>
        </transition>
      </Menu>
    </div>
  </header>

<!--  Empty div to allocate space for the header section, otherwise the elements
      below would be hidden -->
  <div class="mt-8"></div>

  <div id="default-carousel" class="relative w-full mt-20" data-carousel="slide">
    <!-- Carousel wrapper -->
    <div class="relative h-56 overflow-hidden rounded-lg md:h-96">
      <CarouselImage v-for="item in imgArray" :key="item.id" :path="item.path" />
    </div>
    <!-- Slider indicators -->
    <div class="absolute z-30 flex -translate-x-1/2 bottom-5 left-1/2 space-x-3 rtl:space-x-reverse">
      <button v-for="index in imgArray" type="button" class="w-3 h-3 rounded-full" aria-current="true" :aria-label="'Slide' + index" :data-carousel-slide-to="index"></button>
    </div>
    <!-- Slider controls -->
    <button type="button" class="absolute top-0 start-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none" data-carousel-prev>
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
            <svg class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 1 1 5l4 4"/>
            </svg>
            <span class="sr-only">Previous</span>
        </span>
    </button>
    <button type="button" class="absolute top-0 end-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none" data-carousel-next>
        <span class="inline-flex items-center justify-center w-10 h-10 rounded-full bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
            <svg class="w-4 h-4 text-white dark:text-gray-800 rtl:rotate-180" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 6 10">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 9 4-4-4-4"/>
            </svg>
            <span class="sr-only">Next</span>
        </span>
    </button>
  </div>

  <div id="about" class="mt-10">
    <h1 class="text-2xl text-white text-center font-extrabold">About Us</h1>

    <h1 class="text-xl font-bold text-white mb-2">Our Story</h1>
    <p>{{ text["about-mission"] }}</p>

    <h1 class="text-xl font-bold text-white mb-2 mt-4">Our Mission</h1>
    <p>{{ text["about-story"] }}</p>
  </div>

</template>

<style scoped>
@media only screen and (min-width: 400px) {
  #desktop-menu {
    display: none;
  }
  #mobile-menu {
    display: block;
  }
}

@media only screen and (min-width: 800px) {
  #desktop-menu {
    display: block;
  }
  #mobile-menu {
    display: none;
  }
}
</style>
