<script setup>
import Hero from './components/Hero.vue';
import Navbar from './components/Navbar.vue';
import Services from './components/Services.vue';
</script>

<template>
  <Navbar />
  <Hero />
  <section id="about">
    <Services />
  </section>
  <section id="products"></section>
  <section id="contact"></section>
</template>

<style scoped>
</style>
