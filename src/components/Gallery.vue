<template>
  <section class="py-8 lg:pt-[20px]">
    <div class="container mx-auto max-w-screen-lg">
      <div class="flex flex-wrap justify-center">
        <div class="grid gap-4">
          <div class="grid-cols-5">
            <img
              class="h-auto w-full rounded-lg"
              :src="images[highlightImage]"
              alt=""
            />
          </div>
          <div class="grid grid-cols-5 gap-4">
            <div
              v-for="(image, index) in images"
              @click="chooseHighlight(index)"
            >
              <img class="h-auto max-w-full rounded-lg" :src="image" alt="" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const highlightImage = ref(0);

const images = [
  "https://flowbite.s3.amazonaws.com/docs/gallery/square/image-1.jpg",
  "https://flowbite.s3.amazonaws.com/docs/gallery/square/image-2.jpg",
  "https://flowbite.s3.amazonaws.com/docs/gallery/square/image-3.jpg",
  "https://flowbite.s3.amazonaws.com/docs/gallery/square/image-4.jpg",
  "https://flowbite.s3.amazonaws.com/docs/gallery/square/image-5.jpg",
];

const chooseHighlight = (i) => {
  highlightImage.value = i;
};
</script>
