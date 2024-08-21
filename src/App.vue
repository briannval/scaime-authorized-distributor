<script setup>
import Hero from "./components/Hero.vue";
import Navbar from "./components/Navbar.vue";
import Services from "./components/Services.vue";
import Catalogue from "./components/Catalogue.vue";
import Footer from "./components/Footer.vue";
import Certifications from "./components/Certifications.vue";
import Video from "./components/Video.vue";
import Contact from "./components/Contact.vue";
</script>

<template>
  <Navbar />
  <Hero />
  <section id="services">
    <Services />
  </section>
  <Video />
  <section id="catalogue">
    <Catalogue />
  </section>
  <Certifications />
  <section id="contact">
    <Contact />
  </section>
  <Footer />
</template>

<style scoped></style>
