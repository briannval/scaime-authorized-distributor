<template>
  <footer class="bg-white rounded-lg dark:bg-gray-900 mx-4 my-2">
    <div class="w-full max-w-screen-xl mx-auto px-4 mx-8">
      <div class="sm:flex sm:items-center sm:justify-between">
        <a
          href="#"
          class="flex items-center mb-4 sm:mb-0 space-x-3 rtl:space-x-reverse"
        >
          <span
            class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
            >EASY SUPPLY.</span
          >
        </a>
        <ul
          class="flex flex-wrap items-center mb-6 text-sm font-medium text-gray-500 sm:mb-0 dark:text-gray-400"
        >
          <li v-for="(link, index) in bottomLinks" :key="index">
            <a :href="link.href" class="hover:underline me-4 md:me-6">{{
              link.label
            }}</a>
          </li>
        </ul>
      </div>
      <hr
        class="my-6 border-gray-200 sm:mx-auto dark:border-gray-700 lg:my-8"
      />
      <span
        class="block text-sm text-gray-500 sm:text-center dark:text-gray-400"
        >© 2024
        <a href="https://flowbite.com/" class="hover:underline">EASY SUPPLY™</a
        >. All Rights Reserved.</span
      >
    </div>
  </footer>
</template>

<script setup>
import { ref } from "vue";

const bottomLinks = ref([
  {
    label: "About",
    href: "#",
  },
  {
    label: "Privacy Policy",
    href: "#",
  },
  {
    label: "Licensing",
    href: "#",
  },
  {
    label: "Contact",
    href: "#",
  },
]);
</script>
