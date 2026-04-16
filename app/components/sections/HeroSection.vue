<template>
  <section class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <div class="absolute inset-0 bg-[#0d0d0d]">
      <div class="absolute inset-0 bg-gradient-to-br from-[#1a0505] via-[#0d0d0d] to-[#0d0d0d]"></div>
    </div>

    <div class="relative z-10 text-center px-6">
      <p ref="tagline" class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-6 opacity-0">
        Detailing Studio
      </p>
      <h1 ref="heading" class="text-5xl md:text-7xl font-bold text-white mb-6 opacity-0">
        Tu auto merece<br />
        <span class="text-[#cc2222]">lo mejor</span>
      </h1>
      <p ref="subtitle" class="text-[#888888] text-lg md:text-xl max-w-xl mx-auto mb-10 opacity-0">
        Detailing profesional, wrap y rejuvenecimiento para llevar tu vehículo al siguiente nivel.
      </p>
        <a
        ref="cta"
        href="#servicios"
        class="opacity-0 inline-block bg-[#cc2222] text-white px-8 py-4 rounded font-semibold hover:bg-[#e03030] transition-all"
        >
        Ver servicios
        </a>
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'

const tagline = ref(null)
const heading = ref(null)
const subtitle = ref(null)
const cta = ref(null)

onMounted(() => {
  const tl = gsap.timeline({ delay: 0.3 })

    tl.to(tagline.value, { opacity: 1, y: 0, duration: 1, ease: 'power2.out' })
    .to(heading.value, { opacity: 1, y: 0, duration: 1.5, ease: 'power2.out' }, '-=0.3')
    .to(subtitle.value, { opacity: 1, y: 0, duration: 1.2, ease: 'power2.out' }, '-=0.3')
    .to(cta.value, { opacity: 1, y: 0, duration: 1, ease: 'power2.out' }, '-=0.3')
})
</script>