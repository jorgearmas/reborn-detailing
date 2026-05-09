<template>
  <section id="galeria" class="py-24 px-6 bg-[#0d0d0d]">
    <div class="max-w-6xl mx-auto">
      <div ref="header" class="text-center mb-16">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Nuestro trabajo</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white">Portafolio</h2>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
        <div>
          <p class="text-[#cc2222] text-xs font-semibold tracking-[4px] uppercase mb-2">Antes</p>
          <img
            :src="portfolio[activeIndex].thumbnail"
            :alt="portfolio[activeIndex].label + ' antes'"
            class="w-full rounded-lg object-cover"
          />
        </div>
        <div>
          <p class="text-[#cc2222] text-xs font-semibold tracking-[4px] uppercase mb-2">Después</p>
          <img
            :src="portfolio[activeIndex].thumbnailAfter"
            :alt="portfolio[activeIndex].label + ' después'"
            class="w-full rounded-lg object-cover"
          />
        </div>
      </div>
    </div>

    <!-- Modal Before/After -->
    <div
      v-if="modalOpen"
      class="fixed inset-0 bg-black bg-opacity-95 z-50 flex items-center justify-center px-4"
      @click.self="closeModal"
    >
      <div class="w-full max-w-5xl">
        <div class="flex items-center justify-between mb-6">
          <h3 class="text-white font-bold text-2xl tracking-widest uppercase">{{ portfolio[activeIndex].label }}</h3>
          <button @click="closeModal" class="text-white text-3xl hover:text-[#cc2222] transition-colors">✕</button>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <p class="text-[#cc2222] text-xs font-semibold tracking-[4px] uppercase mb-2">Antes</p>
            <video
              autoplay muted loop playsinline controls
              class="w-full rounded-lg"
              :src="portfolio[activeIndex].before"
            ></video>
          </div>
          <div>
            <p class="text-[#cc2222] text-xs font-semibold tracking-[4px] uppercase mb-2">Después</p>
            <video
              autoplay muted loop playsinline controls
              class="w-full rounded-lg"
              :src="portfolio[activeIndex].after"
            ></video>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const portfolio = [
  {
    label: 'Mercedes',
    thumbnail: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778309182/Mercedes_Before_pff3tp.jpg',
    thumbnailAfter: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778309901/Mercedes_After_ovz8pf.jpg',
  },
  {
    label: 'Ford',
    thumbnail: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778309177/Ford_Before_k1hz4n.jpg',
    thumbnailAfter: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778309113/Ford_After_jw0z5u.jpg',
  },
  {
    label: 'Toyota',
    thumbnail: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778310192/LC_Before_mvu1ef.jpg',
    thumbnailAfter: 'https://res.cloudinary.com/dpi6oudmk/video/upload/v1778309150/LC_After_cuvqq3.jpg',
  },
]

const modalOpen = ref(false)
const activeIndex = ref(0)
const header = ref(null)

const openModal = (index) => {
  activeIndex.value = index
  modalOpen.value = true
}

const closeModal = () => {
  modalOpen.value = false
}

onMounted(() => {
  gsap.from(header.value, {
    opacity: 0, y: 30, duration: 0.8,
    scrollTrigger: { trigger: header.value, start: 'top 80%' }
  })
})
</script>