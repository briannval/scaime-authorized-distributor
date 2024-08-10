<template>
    <section class="bg-white dark:bg-gray-900">
        <div class="grid max-w-screen-xl py-8 mx-auto lg:py-16 lg:grid-cols-12 min-h-[100vh]">
            <div class="mr-auto place-self-center lg:col-span-7">
                <h1 class="max-w-2xl mb-4 text-4xl font-extrabold tracking-tight leading-none md:text-5xl xl:text-7xl dark:text-white">The Authorized <br/>Scaime Reseller.</h1>
                <p class="max-w-2xl mb-6 font-light text-gray-500 lg:mb-8 md:text-lg lg:text-2xl dark:text-gray-400">{{ currPhrase }} &nbsp;</p>
                <a href="#" class="inline-flex items-center justify-center px-5 py-3 mr-3 text-base font-medium text-center text-white rounded-lg bg-gray-700 hover:bg-gray-800">
                    Learn More
                    <svg class="w-5 h-5 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                </a>
                <a href="#" class="inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-gray-900 border border-gray-300 rounded-lg hover:bg-gray-100 focus:ring-4 focus:ring-gray-100 dark:text-white dark:border-gray-700 dark:hover:bg-gray-700 dark:focus:ring-gray-800">
                    Contact Sales
                </a> 
            </div>
            <div class="hidden lg:mt-0 lg:col-span-5 lg:flex place-self-center">
                <img src="/main-product.jpg" alt="mockup" class="w-full h-full object-cover">
            </div>                
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';

const phrases = ["Weighing and automated systems", "Measurement and industrial control", "Load cells, force, and compression"]

const phraseIndex = ref(0);
const charIndex = ref(0);
const currPhrase = ref("")
const isDeleting = ref(false);

function loop() {
    const text = phrases[phraseIndex.value];

    if (isDeleting.value) {
        currPhrase.value = currPhrase.value.slice(0, -1);
        charIndex.value--;
    } else {
        currPhrase.value += text[charIndex.value];
        charIndex.value++;
    }

    if (charIndex.value === text.length && !isDeleting.value) {
        setTimeout(() => {
            isDeleting.value = true;
            loop(); 
        }, 2000);
        return; 
    }

    if (charIndex.value === 0) {
        currPhrase.value = "";
        isDeleting.value = false;
        phraseIndex.value++;
        if (phraseIndex.value === phrases.length) {
            phraseIndex.value = 0;
        }
    }

    const time = isDeleting.value ? 40 : 100;
    setTimeout(loop, time);
}
loop();

</script>
