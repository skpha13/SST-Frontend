<script setup lang="ts">
import text from "../JSON Customization/text.json"
import galleryImages from "../JSON Customization/gallery.json"
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
import carouselImages from "@/JSON Customization/carousel-images.json"
import CarouselImage from "@/components/CarouselImage.vue";
import TextTitle from "@/components/TextTitle.vue";
import GalleryImage from "@/components/GalleryImage.vue";
import reviewsJSON from "@/JSON Customization/reviews.json"
import Review from "@/components/Review.vue";

const imgArray = carouselImages
const imgGallery = galleryImages
const reviews = reviewsJSON

const getTotalRating = () => {
  let sum = 0
  let count = 0;
  for (let item in reviews) {
    sum += parseFloat(reviews[item]['rating'])
    count += 1
  }

  return (sum / count).toFixed(2)
}
const rating = getTotalRating()

const submitForm = async() => {

}
</script>

<template>
<!--  NAVBAR SECTION  -->
  <header class="fixed top-0 left-0 w-full bg-neutral-700 text-white p-4 z-50">
    <div class="container mx-auto flex items-center justify-between">
      <h1 class="text-xl font-bold">
        <a href="#"> {{ text["company-name"] }} </a>
      </h1>

      <nav id="desktop-menu" class="space-x-4">
        <a href="#default-carousel" class="hover:bg-neutral-600 hover:rounded-lg p-2">Carousel</a>
        <a href="#about" class="hover:bg-neutral-600 hover:rounded-lg p-2">About</a>
        <a href="#gallery" class="hover:bg-neutral-600 hover:rounded-lg p-2">Gallery</a>
        <a href="#google-review" class="hover:bg-neutral-600 hover:rounded-lg p-2">Google Reviews</a>
        <a href="#contact" class="hover:bg-neutral-600 hover:rounded-lg p-2">Contact</a>
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
                <a href="#default-carousel" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Carousel</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#about" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">About</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#gallery" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Gallery</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#google-review" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Google reviews</a>
              </MenuItem>
              <MenuItem v-slot="{ active }">
                <a href="#contact" :class="[active ? 'bg-neutral-600' : 'text-white', 'block px-4 py-2 text-sm']">Contact</a>
              </MenuItem>
            </div>
          </MenuItems>
        </transition>
      </Menu>
    </div>
  </header>
<!--  NAVBAR SECTION  -->

<!--  EMPTY DIV TO COMPLETE SPACE -->
      <!--  Empty div to allocate space for the header section, otherwise the elements
            below would be hidden -->
  <div id="space" class="mt-8"></div>
<!--  EMPTY DIV TO COMPLETE SPACE -->

<!--  CAROUSEL SECTION -->
  <div id="default-carousel" class="relative w-full mt-28 " data-carousel="slide">
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
<!--  CAROUSEL SECTION -->

<!--  ABOUT SECTION -->
  <div id="about" class="mt-10">
    <TextTitle title="About Us" />

    <div class="flex flex-col md:flex-row justify-between">
      <div class="bg-neutral-800 p-8 rounded-lg mb-4 md:mr-4">
        <h1 class="text-xl font-bold text-white mb-2">Our Story</h1>
        <p>{{ text["about-mission"] }}</p>
      </div>

      <div class="bg-neutral-800 p-8 rounded-lg mb-4">
        <h1 class="text-xl font-bold text-white mb-2">Our Mission</h1>
        <p>{{ text["about-story"] }}</p>
      </div>
    </div>
  </div>
<!--  ABOUT SECTION -->

<!--  GALLERY SECTION -->
  <div id="gallery">
    <TextTitle title="Gallery" />

    <div class="grid gap-4">
      <GalleryImage :path="imgGallery.img01.path"
                    class="h-auto max-w-full rounded-lg" />
      <div class="grid grid-cols-5 gap-4">
        <GalleryImage v-for="item in imgGallery" :key="item.id" :path="item.path"
                      class="h-auto max-w-full rounded-lg"/>
      </div>
    </div>


  </div>
<!--  GALLERY SECTION -->

<!--  GOOGLE REVIEW SECTION -->
<!--  DIDN'T USE THE GOOGLE API BECAUSE IT REQUESTED CREDIT CARD INFORMATION -->
  <div id="google-review">
    <TextTitle title="Google Reviews"/>
    <h1 class="text-center mb-6 text-xl"> Average rating: {{ rating }}</h1>
    <div class="flex flex-row justify-start flex-wrap">
      <Review v-for="(item, index) in reviews"
              :key="index" :profile-photo="item['profile-photo']"
              :rating="item['rating']"
              :comment="item['comment']"
              :username="item['username']"
              class="mb-8 mx-2 max-w-96"/>
    </div>
  </div>
<!--  GOOGLE REVIEW SECTION -->

<!--  CONTACT SECTION -->
  <div id="contact" >
    <TextTitle title="Contact" />

    <form @submit.prevent="submitForm" class="max-w-md mx-auto">
      <div class="mb-4">
        <label for="name" class="block text-sm font-medium">Name</label>
        <input type="text" id="name" name="name" required
               class="mt-1 p-2 border rounded-md w-full">
      </div>

      <div class="mb-4">
        <label for="email" class="block text-sm font-medium">Email</label>
        <input type="email" id="email" name="email" required
               class="mt-1 p-2 border rounded-md w-full">
      </div>

      <div class="mb-4">
        <label for="subject" class="block text-sm font-medium">Subject</label>
        <input type="text" id="subject" name="subject" required
               class="mt-1 p-2 border rounded-md w-full">
      </div>

      <div class="mb-4">
        <label for="message" class="block text-sm font-medium">Message</label>
        <textarea id="message" name="message" rows="4" required
                  class="mt-1 p-2 border rounded-md w-full"></textarea>
      </div>

      <button type="submit" class="bg-neutral-700 text-white p-2 rounded-md hover:bg-neutral-600">Send Message</button>
    </form>
  </div>
<!--  CONTACT SECTION -->

<!--  EMPTY DIV TO COMPLETE SPACE -->
<!--  Empty div to allocate space for the footer section, otherwise the elements
        above would be hidden -->
  <div class="h-[96px]"></div>
<!--  EMPTY DIV TO COMPLETE SPACE -->
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

input,
textarea {
  background-color: var(--tw-bg-opacity);
}

input:focus,
textarea:focus {
  border-color: white;
  box-shadow: none;
  -moz-box-shadow: none;
  -webkit-box-shadow: none;
}

</style>
