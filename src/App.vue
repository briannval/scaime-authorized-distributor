<script setup>
import Hero from "./components/Hero.vue";
import Navbar from "./components/Navbar.vue";
import Services from "./components/Services.vue";
import Catalogue from "./components/Catalogue.vue";
</script>

<template>
  <Navbar />
  <Hero />
  <section id="services">
    <Services />
  </section>
  <section id="catalogue">
    <Catalogue />
  </section>
  <section id="contact"></section>
</template>

<style scoped></style>
