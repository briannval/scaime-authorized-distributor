<template>
  <section class="py-8 lg:pt-[20px]">
    <div class="container mx-auto max-w-screen-xl">
      <div class="w-full px-4">
        <div class="text-center mx-auto mb-12 lg:mb-20 max-w-[510px]">
          <span class="font-semibold text-lg text-primary mb-2 block">
            High Quality Products
          </span>
          <h2
            class="font-extrabold text-3xl sm:text-4xl md:text-[40px] text-dark mb-4"
          >
            Our Catalogue
          </h2>
        </div>
      </div>
      <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
        <table
          class="w-full text-md text-left rtl:text-right text-gray-500 dark:text-gray-400"
        >
          <thead
            class="text-lg text-gray-700 uppercase bg-gray-100 dark:bg-gray-700 dark:text-gray-400"
          >
            <tr>
              <th scope="col" class="px-6 py-3" v-for="column in columns">
                <div class="flex items-center">{{ column }}</div>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr class="bg-white border-b hover:bg-gray-50" v-for="item in data">
              <th
                scope="row"
                class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap"
              >
                {{ item.product }}
              </th>
              <td class="px-6 py-4">{{ item.color }}</td>
              <td class="px-6 py-4">{{ item.weight }}</td>
              <td class="px-6 py-4">{{ item.price }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const columns = ref(["Product", "Color", "Weight", "Price"]);

const data = ref([
  {
    product: "Product 1",
    color: "Gray",
    weight: "100",
    price: "$2999",
  },
  {
    product: "Product 2",
    color: "Silver",
    weight: "80",
    price: "$1399",
  },
  {
    product: "Product 3",
    color: "Black",
    weight: "70",
    price: "$1199",
  },
  {
    product: "Product 4",
    color: "Blue",
    weight: "85",
    price: "$1499",
  },
  {
    product: "Product 5",
    color: "Rose Gold",
    weight: "75",
    price: "$1099",
  },
]);
</script>
