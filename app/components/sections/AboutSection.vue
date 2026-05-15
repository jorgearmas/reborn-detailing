<template>
  <section id="nosotros" class="py-24 px-6 bg-white">
    <div class="max-w-6xl mx-auto">

      <div ref="text" class="text-center mb-16">
        <!-- <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Quiénes somos</p> -->
        <h2 class="text-4xl md:text-5xl font-bold text-[#0d0d0d] mb-6">Pasión por <span class="text-[#cc2222]">los detalles</span></h2>
        <p class="text-[#888888] leading-relaxed max-w-2xl mx-auto">
          Nuestro equipo está formado por profesionales con años de experiencia en detailing, corrección de pintura y protección vehicular. Cada trabajo es tratado con la misma exigencia y dedicación, sin importar el vehículo. Nos apasiona lo que hacemos — y se nota en cada resultado.
        </p>
      </div>

      <div ref="team" class="grid grid-cols-3 gap-6">
        <div v-for="member in members" :key="member.src" class="overflow-hidden rounded-lg">
          <img :src="member.src" :alt="member.name" loading="lazy" class="w-full h-80 object-cover object-top" />
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const text = ref(null)
const team = ref(null)

const members = [
  { src: '/gallery/daniel.png', name: 'Daniel' },
  { src: '/gallery/rafael.png', name: 'Rafael' },
  { src: '/gallery/ivan.png',   name: 'Ivan' },
]

onMounted(() => {
  gsap.from(text.value, {
    opacity: 0, y: 30, duration: 0.9,
    scrollTrigger: { trigger: text.value, start: 'top 80%' }
  })

  gsap.from(team.value.children, {
    opacity: 0, y: 40, duration: 0.7, stagger: 0.15,
    scrollTrigger: { trigger: team.value, start: 'top 80%' }
  })
})
</script>
