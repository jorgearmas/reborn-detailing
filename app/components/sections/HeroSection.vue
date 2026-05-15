<template>
  <section class="relative w-full h-screen flex items-end pb-20 px-10 overflow-hidden">
    <video
      autoplay
      muted
      loop
      playsinline
      class="absolute inset-0 w-full h-full object-cover"
    >
      <source src="https://res.cloudinary.com/dpi6oudmk/video/upload/q_auto/f_auto/v1778252977/hero-new_fc46bm.mp4" type="video/mp4" />
</video>
    <div class="absolute inset-0 bg-gradient-to-t from-[#0d0d0d] via-transparent to-transparent"></div>
    

    <div ref="content" class="relative z-10 max-w-4xl">
      <h1 class="text-6xl md:text-8xl font-bold text-white leading-none mb-6">
        Tu auto.<br />Renacido.
      </h1>
      <a href="#servicios" class="inline-flex items-center gap-3 text-white text-sm font-semibold tracking-widest uppercase border-b border-white pb-1 hover:border-[#cc2222] hover:text-[#cc2222] transition-all duration-300">
        Ver servicios <span>→</span>
      </a>
      <a href="#contacto" class="block mt-4 text-[#888888] text-xs tracking-widest uppercase hover:text-white transition-colors duration-300">
        Cotiza ahora →
      </a>
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'

const content = ref(null)

onMounted(() => {
  gsap.from(content.value, {
    opacity: 0,
    y: 20,
    duration: 1.2,
    ease: 'power2.out',
    delay: 0.3
  })
})
</script>