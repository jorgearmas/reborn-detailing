<template>
  <div>
    <AppNavbar />
    <main class="pt-24">
      <ServicesSection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'
import ServicesSection from '../components/sections/ServicesSection.vue'
</script>