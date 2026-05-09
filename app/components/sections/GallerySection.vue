<template>
  <section id="galeria" class="py-24 px-6 bg-[#cc2222]">
    <div class="max-w-6xl mx-auto">
      <div ref="header" class="text-center mb-16">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Nuestro trabajo</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white">Portafolio</h2>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div
          v-for="(image, index) in images"
          :key="index"
          ref="cards"
          class="relative overflow-hidden rounded-lg cursor-pointer group"
          @click="openLightbox(index)"
        >
          <img
            :src="image.src"
            :alt="image.alt"
            class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-105"
          />
          <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-40 transition-all duration-300 flex items-center justify-center">
            <span class="text-white opacity-0 group-hover:opacity-100 transition-opacity duration-300 text-sm font-semibold tracking-widest uppercase">Ver</span>
          </div>
        </div>
      </div>
    </div>

    <div
      v-if="lightboxOpen"
      class="fixed inset-0 bg-black bg-opacity-90 z-50 flex items-center justify-center"
      @click="closeLightbox"
    >
      <button class="absolute top-6 right-6 text-white text-3xl" @click="closeLightbox">✕</button>
      <img :src="images[activeIndex].src" class="max-h-[85vh] max-w-[90vw] object-contain rounded" />
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const images = [
  { src: '/gallery/1.jpg', alt: 'Trabajo 1' },
  { src: '/gallery/2.jpg', alt: 'Trabajo 2' },
  { src: '/gallery/3.jpg', alt: 'Trabajo 3' },
  { src: '/gallery/4.jpg', alt: 'Trabajo 4' },
]

const lightboxOpen = ref(false)
const activeIndex = ref(0)
const header = ref(null)
const cards = ref([])

const openLightbox = (index) => {
  activeIndex.value = index
  lightboxOpen.value = true
}

const closeLightbox = () => {
  lightboxOpen.value = false
}

onMounted(() => {
  gsap.from(header.value, {
    opacity: 0, y: 30, duration: 0.8,
    scrollTrigger: { trigger: header.value, start: 'top 80%' }
  })

  cards.value.forEach((card, i) => {
    gsap.from(card, {
      opacity: 0, y: 30, duration: 0.6,
      delay: i * 0.1,
      scrollTrigger: { trigger: card, start: 'top 85%' }
    })
  })
})
</script>