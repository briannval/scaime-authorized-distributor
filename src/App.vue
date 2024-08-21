<script setup>
import {
  Hero,
  Navbar,
  Services,
  Catalogue,
  Footer,
  Certifications,
  Video,
  Contact,
} from "./components";

const sections = [
  { id: null, component: Navbar },
  { id: null, component: Hero },
  { id: "services", component: Services },
  { id: null, component: Video },
  { id: "catalogue", component: Catalogue },
  { id: "certifications", component: Certifications },
  { id: "contact", component: Contact },
  { id: null, component: Footer },
];
</script>

<template>
  <div>
    <component
      v-for="(section, index) in sections"
      :is="section.component"
      :key="index"
      :id="section.id"
    />
  </div>
</template>

<style scoped></style>
