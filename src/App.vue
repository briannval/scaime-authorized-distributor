<script setup>
import Hero from "./components/Hero.vue";
import Navbar from "./components/Navbar.vue";
import Services from "./components/Services.vue";
import Catalogue from "./components/Catalogue.vue";
import Footer from "./components/Footer.vue";
import Gallery from "./components/Gallery.vue";
</script>

<template>
  <Navbar />
  <Hero />
  <section id="services">
    <Services />
  </section>
  <Gallery />
  <section id="catalogue">
    <Catalogue />
  </section>
  <section id="contact"></section>
  <Footer />
</template>

<style scoped></style>
