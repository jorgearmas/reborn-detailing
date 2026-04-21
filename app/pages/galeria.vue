<template>
  <div>
    <AppNavbar />
    <main class="pt-24">
      <GallerySection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'
import GallerySection from '../components/sections/GallerySection.vue'
</script>