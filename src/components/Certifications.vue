<template>
  <section class="py-8 lg:pt-[20px] my-20">
    <div class="container mx-auto max-w-screen-lg">
      <!-- Heading-->
      <div class="w-full px-4">
        <div class="text-center mx-auto mb-6 lg:mb-8 max-w-[510px]">
          <span class="font-semibold text-lg text-primary mb-2 block">
            Trust On Excellence
          </span>
          <h2
            class="font-extrabold text-3xl sm:text-4xl md:text-[40px] text-dark"
          >
            Our Certifications
          </h2>
        </div>
      </div>

      <!-- Certfications -->
      <div class="flex flex-wrap justify-center m-8">
        <div class="flex flex-col items-center justify-center">
          <img
            class="h-72 w-72 md:h-96 md:w-96 rounded-lg object-contain mb-8"
            :src="`/certifications/${images[highlightImage]}`"
            alt=""
          />
          <div class="grid grid-cols-4 gap-2">
            <div
              v-for="(image, index) in images"
              @click="chooseHighlight(index)"
              :class="{
                'cursor-pointer border-2 border-gray-600 rounded-xl p-2':
                  index === highlightImage,
                'cursor-pointer border border-gray-300 rounded-xl p-2 hover:shadow-lg':
                  index !== highlightImage,
              }"
            >
              <img
                class="h-16 w-16 md:h-28 md:w-28 rounded-lg object-contain"
                :src="`/certifications/${image}`"
                alt=""
              />
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

const images = ["atex.png", "iecex.jpeg", "ntep.png", "oiml.png"];

const chooseHighlight = (i) => {
  highlightImage.value = i;
};

onMounted(() => {
  setInterval(() => {
    highlightImage.value = (highlightImage.value + 1) % images.length;
  }, 8000);
});
</script>
