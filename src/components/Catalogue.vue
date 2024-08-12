<template>
  <section class="py-8 lg:pt-[20px]">
    <div class="container mx-auto max-w-screen-xl">
      <!-- Heading -->
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
          <span class="font-light italic text-md text-primary mb-2 block">
            Note: Click on each product to view more
          </span>
        </div>
      </div>

      <!-- Table -->
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
            <tr
              class="bg-white border-b hover:bg-gray-50"
              v-for="(item, index) in data"
              :key="index"
              @click="openModal(item)"
            >
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

    <!-- Modal -->
    <div
      v-if="showModal"
      @click.self="showModal = false"
      class="fixed inset-0 z-50 flex justify-center items-center w-full h-full bg-black bg-opacity-50"
    >
      <div
        class="relative p-4 w-full max-w-lg bg-white rounded-lg shadow-lg dark:bg-gray-700"
      >
        <div
          class="flex justify-between items-center p-4 border-b dark:border-gray-600"
        >
          <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
            Product Details
          </h3>
          <button
            @click="closeModal"
            class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ms-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
          >
            <svg
              class="w-3 h-3"
              aria-hidden="true"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 14 14"
            >
              <path
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"
              />
            </svg>
            <span class="sr-only">Close modal</span>
          </button>
        </div>
        <div class="p-4">
          <img src="/main-product.jpg" />
          <!-- Change later -->
          <p class="text-lg font-bold text-gray-900 dark:text-white">
            {{ selectedProduct.product }}
          </p>
          <p class="text-md text-gray-500 dark:text-gray-400">
            Color: {{ selectedProduct.color }}
          </p>
          <p class="text-md text-gray-500 dark:text-gray-400">
            Weight: {{ selectedProduct.weight }}
          </p>
          <p class="text-md text-gray-500 dark:text-gray-400">
            Price: {{ selectedProduct.price }}
          </p>
        </div>
        <div class="flex justify-end p-4 border-t dark:border-gray-600">
          <button
            @click="closeModal"
            class="bg-gray-600 text-white px-4 py-2 rounded-lg hover:bg-gray-500"
          >
            Close
          </button>
        </div>
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
// Modal visibility state
const showModal = ref(false);

// Selected product details
const selectedProduct = ref({});

// Function to open the modal and set the selected product
const openModal = (product) => {
  selectedProduct.value = product;
  showModal.value = true;
};

// Function to close the modal
const closeModal = () => {
  showModal.value = false;
};
</script>
