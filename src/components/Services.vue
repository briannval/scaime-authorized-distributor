<template>
  <section class="py-8 lg:pt-[20px] mb-20 mx-8">
    <div class="container mx-auto max-w-screen-xl">
      <div class="flex flex-wrap justify-center mx-4">
        <div class="w-full px-4">
          <div class="text-center mx-auto mb-12 lg:mb-20 max-w-[510px]">
            <span class="font-semibold text-lg text-primary mb-2 block">
              Why Choose Us?
            </span>
            <h2
              class="font-extrabold text-3xl sm:text-4xl md:text-[40px] text-dark mb-4"
            >
              Our Services
            </h2>
          </div>
        </div>
      </div>
      <div class="flex flex-wrap justify-center -mx-4">
        <div
          v-for="(service, index) in services"
          :key="index"
          class="w-full md:w-1/2 lg:w-1/3 px-4 h-full"
        >
          <div
            class="p-10 md:px-7 xl:px-10 rounded-[20px] bg-white shadow-md hover:shadow-lg mb-8 text-center"
          >
            <img
              :src="`/services/${service.image}`"
              alt="Service Image"
              class="w-64 h-64 mx-auto mb-4 object-cover"
            />
            <h4 class="font-semibold text-xl text-dark mb-3">
              {{ service.title }}
            </h4>
            <p class="text-body-color">
              {{ service.description }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const services = ref([
  {
    title: "Capacity-based solutions",
    description:
      "We offer recommendations for optimum capacity without sacrificing precision and quality.",
    image: "/capacity.jpg",
  },
  {
    title: "Flexible mounting methods",
    description:
      "Our various mounting kits allow different load cells to be used in diverse scenarios flexibly.",
    image: "/mounting.jpg",
  },
  {
    title: "Digital and Analogue",
    description:
      "We offer load cells with either digital to analogue output, integrable with our or your own electronics.",
    image: "/digital.jpg",
  },
  {
    title: "Cost saving alternatives",
    description:
      "Utilize our fixed bearings to for horizontal tank weighing to cut costs and increase efficiency.",
    image: "/cost.png",
  },
  {
    title: "Numerous use cases",
    description:
      "From storage, material supply, manufacturing, packaging, and control, we've got you covered.",
    image: "/measurement.jpg",
  },
]);
</script>
