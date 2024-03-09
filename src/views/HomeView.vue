<script setup lang="ts">
import text from "../JSON Customization/text.json"
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
import {ref} from "vue";

const mobileView = ref<boolean>(false);
</script>

<template>
  <header class="fixed top-0 left-0 w-full bg-neutral-700 text-white p-4 z-50">
    <div class="container mx-auto flex items-center justify-between">
      <h1 class="text-xl font-bold">
        <a href="#"> {{ text["company-name"] }} </a>
      </h1>

      <nav id="desktop-menu" class="space-x-4">
        <a href="#" class="hover:bg-neutral-600 hover:rounded-lg p-2">Carousel</a>
        <a href="#" class="hover:bg-neutral-600 hover:rounded-lg p-2">About</a>
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
  <div class="mt-16"></div>

  <h1 class="">test</h1>
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
