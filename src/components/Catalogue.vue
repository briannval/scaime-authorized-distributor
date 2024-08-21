<template>
  <section class="py-8 lg:pt-[20px] my-12 mx-8">
    <div class="container mx-auto max-w-screen-xl">
      <!-- Heading -->
      <div class="w-full px-4">
        <div class="text-center mx-auto mb-6 lg:mb-8 max-w-[510px]">
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

      <!-- Select-->

      <form class="max-w-sm mx-auto my-8">
        <select
          id="countries"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          @change="handleChange($event)"
        >
          <option v-for="(sheet, index) in sheets" :value="sheet" :key="index">
            {{ sheet }}
          </option>
        </select>
      </form>

      <div
        role="status"
        class="flex justify-center items-center my-16"
        v-if="loading"
      >
        <svg
          aria-hidden="true"
          class="w-24 h-24 text-gray-200 animate-spin fill-gray-600"
          viewBox="0 0 100 101"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z"
            fill="currentColor"
          />
          <path
            d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z"
            fill="currentFill"
          />
        </svg>
        <span class="sr-only">Loading...</span>
      </div>

      <!-- Table -->
      <div class="relative overflow-x-auto shadow-md sm:rounded-lg" v-else>
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
                {{ item.cells[0] }}
              </th>
              <td
                v-for="(cell, index) in item.cells.slice(1)"
                class="px-6 py-4"
                :key="index"
              >
                {{ cell }}
              </td>
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
          <img :src="selectedProduct.image" :alt="selectedProduct.cells[0]" />
          <p class="font-bold text-xl text-gray-900 dark:text-white">
            {{ selectedProduct.cells[0] }}
          </p>
          <p
            v-for="(cell, index) in selectedProduct.cells.slice(1)"
            class="text-lg text-gray-900 dark:text-white"
          >
            {{ columns.slice(1)[index] }}: {{ cell }}
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
import axios from "axios";

const apiKey = import.meta.env.VITE_GSHEET_API_KEY;
const googleSheetId = import.meta.env.VITE_GSHEET_ID;

const sheets = ref(["Load Cells", "Mounting Kits", "Electronics"]);

const activeSheet = ref("Load Cells");

const columns = ref([]);

const data = ref([]);
const loading = ref(true);

const MAX_CELL_VALUE = 99;

const fetchData = async (sheetName) => {
  try {
    loading.value = true;
    let cellRange;
    switch (sheetName) {
      case "Load Cells":
        cellRange = `A1:F${MAX_CELL_VALUE}`;
        break;
      case "Mounting Kits":
        cellRange = `A1:D${MAX_CELL_VALUE}`;
        break;
      case "Electronics":
        cellRange = `A1:G${MAX_CELL_VALUE}`;
        break;
    }
    const range = `'${sheetName}'!${cellRange}`; // Adjust range as needed
    const url = `https://sheets.googleapis.com/v4/spreadsheets/${googleSheetId}/values/${range}?key=${apiKey}`;
    const response = await axios.get(url);
    const rows = response.data.values;
    (columns.value = rows[0].slice(0, -1)),
      (data.value = rows.slice(1).map((r) => ({
        cells: r.slice(0, -1),
        image: r.slice(-1)[0],
      })));

    console.log(data.value);
  } catch (error) {
    console.error("Error fetching data from Google Sheets:", error);
  } finally {
    loading.value = false;
  }
};

const handleChange = (e) => {
  activeSheet.value = e.target.value;
  fetchData(activeSheet.value);
};

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

fetchData("Load Cells");
</script>
