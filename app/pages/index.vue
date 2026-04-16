<template>
  <div>
    <AppNavbar />
    <main>
      <HeroSection />
      <ServicesSection />
      <GallerySection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'
import HeroSection from '../components/sections/HeroSection.vue'
import ServicesSection from '../components/sections/ServicesSection.vue'
import GallerySection from '../components/sections/GallerySection.vue'
</script>