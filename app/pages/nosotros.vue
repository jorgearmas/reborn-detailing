<template>
  <div>
    <AppNavbar />
    <main class="pt-24">
      <AboutSection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'
import AboutSection from '../components/sections/AboutSection.vue'
</script>