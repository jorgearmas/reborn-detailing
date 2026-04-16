<template>
  <section id="servicios" class="py-24 px-6">
    <div class="max-w-6xl mx-auto">
      <div ref="header" class="text-center mb-16 opacity-0">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Lo que hacemos</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white">Nuestros servicios</h2>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
        <div ref="card1" class="opacity-0 translate-y-8">
          <ServiceCard
            title="Limpieza de neumáticos"
            description="Restauramos el aspecto de tus neumáticos con productos profesionales que eliminan suciedad y oxidación."
          >
            <template #icon>
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="3"/></svg>
            </template>
          </ServiceCard>
        </div>

        <div ref="card2" class="opacity-0 translate-y-8">
          <ServiceCard
            title="Detailing y wrap"
            description="Protección y transformación total de la carrocería. Desde pulido profesional hasta wrap completo."
          >
            <template #icon>
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M3 17l2-8h14l2 8H3z"/><path d="M5 17v2h2v-2M17 17v2h2v-2"/></svg>
            </template>
          </ServiceCard>
        </div>

        <div ref="card3" class="opacity-0 translate-y-8">
          <ServiceCard
            title="Rejuvenecimiento de faros"
            description="Devolvemos la claridad original a tus faros eliminando el amarillamiento y la opacidad."
          >
            <template #icon>
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="12" cy="12" r="5"/><path d="M12 2v2M12 20v2M2 12h2M20 12h2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41"/></svg>
            </template>
          </ServiceCard>
        </div>

        <div ref="card4" class="opacity-0 translate-y-8">
          <ServiceCard
            title="Rejuvenecimiento de stops"
            description="Restauramos tus luces traseras para mejorar la estética y la seguridad de tu vehículo."
          >
            <template #icon>
              <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="8" width="20" height="8" rx="2"/><circle cx="7" cy="12" r="2"/><circle cx="17" cy="12" r="2"/></svg>
            </template>
          </ServiceCard>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import ServiceCard from '../ui/ServiceCard.vue'

gsap.registerPlugin(ScrollTrigger)

const header = ref(null)
const card1 = ref(null)
const card2 = ref(null)
const card3 = ref(null)
const card4 = ref(null)

onMounted(() => {
  gsap.set(header.value, { y: 30 })
  gsap.set([card1.value, card2.value, card3.value, card4.value], { y: 30 })

  gsap.to(header.value, {
    opacity: 1, y: 0, duration: 0.8,
    scrollTrigger: { trigger: header.value, start: 'top 80%' }
  })

  ;[card1, card2, card3, card4].forEach((card, i) => {
    gsap.to(card.value, {
      opacity: 1, y: 0, duration: 0.6,
      delay: i * 0.15,
      scrollTrigger: { trigger: card.value, start: 'top 85%' }
    })
  })
})
</script>