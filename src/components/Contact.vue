<template>
  <section class="py-8 lg:pt-[20px] mb-20">
    <div class="container mx-auto max-w-screen-xl">
      <div class="flex flex-wrap justify-center">
        <div class="w-full px-4">
          <div class="text-center mx-auto mb-4 max-w-[510px]">
            <span class="font-semibold text-lg text-primary mb-2 block">
              Want to know more?
            </span>
            <h2
              class="font-extrabold text-3xl sm:text-4xl md:text-[40px] text-dark"
            >
              Contact Us
            </h2>
          </div>
        </div>
      </div>
      <form class="max-w-xl mx-auto">
        <div class="mb-6">
          <label
            for="small-input"
            class="block mb-2 text-md font-bold text-gray-900"
            >Your Name</label
          >
          <input
            type="text"
            id="small-input"
            class="block w-full p-2 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-md focus:ring-gray-500 focus:border-gray-500 focus:border-2 focus:outline-none"
          />
        </div>
        <div class="mb-6">
          <label
            for="small-input"
            class="block mb-2 text-md font-bold text-gray-900"
            >Small input</label
          >
          <input
            type="text"
            id="small-input"
            class="block w-full p-2 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-md focus:ring-gray-500 focus:border-gray-500 focus:border-2 focus:outline-none"
          />
        </div>
        <div>
          <label
            for="message"
            class="block mb-2 text-md font-bold text-gray-900"
            >Your message</label
          >
          <textarea
            id="message"
            rows="8"
            class="block w-full p-2 text-gray-900 border border-gray-300 rounded-lg bg-gray-50 text-md focus:ring-gray-500 focus:border-gray-500 focus:border-2 focus:outline-none"
          ></textarea>
        </div>
        <button
          type="submit"
          class="mt-6 w-full inline-flex items-center justify-center px-5 py-3 mr-3 text-base font-medium text-center text-white rounded-lg bg-gray-700 hover:bg-gray-800"
        >
          Submit
          <svg
            class="w-5 h-5 ml-2 -mr-1"
            fill="currentColor"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
              clip-rule="evenodd"
            ></path>
          </svg>
        </button>
      </form>
    </div>
  </section>
</template>
