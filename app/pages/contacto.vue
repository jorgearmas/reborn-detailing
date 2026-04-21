<template>
  <div>
    <AppNavbar />
    <main class="pt-24">
      <ContactSection />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'
import ContactSection from '../components/sections/ContactSection.vue'
</script>