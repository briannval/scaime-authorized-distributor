<template>
  <section class="py-8 lg:pt-[20px] my-20">
    <div class="container mx-auto max-w-screen-lg">
      <div class="flex flex-wrap justify-center mx-8">
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
import { onMounted, ref } from "vue";

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

onMounted(() => {
  setInterval(() => {
    highlightImage.value = (highlightImage.value + 1) % images.length;
  }, 8000);
});
</script>
