<template>
  <div>
    <AppNavbar />
    <main>
      <HeroSection />
      <ServicesSection />
      <GallerySection />
      <AboutSection />
      <ContactSection />
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
import AboutSection from '../components/sections/AboutSection.vue'
import ContactSection from '../components/sections/ContactSection.vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  const createOverlay = (selector, color) => {
    const el = document.querySelector(selector)
    el.style.position = 'relative'
    const overlay = document.createElement('div')
    overlay.style.cssText = `position:absolute;inset:0;background:${color};z-index:10;pointer-events:none`
    el.appendChild(overlay)
    return overlay
  }

  const pairs = [
    { id: '#servicios', color: '#0d0d0d' },
    { id: '#galeria',   color: '#f5f5f5' },
    { id: '#nosotros',  color: '#0d0d0d' },
    { id: '#contacto',  color: '#f5f5f5' },
  ]

  pairs.forEach(({ id, color }) => {
    const overlay = createOverlay(id, color)
    gsap.to(overlay, {
      opacity: 0,
      ease: 'none',
      scrollTrigger: { trigger: id, start: 'top 80%', end: 'top 20%', scrub: 1.5 }
    })
  })
})
</script>