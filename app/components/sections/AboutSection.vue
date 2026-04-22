<template>
  <section id="nosotros" class="py-24 px-6">
    <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
      <div ref="text">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Quiénes somos</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">Pasión por<br /><span class="text-[#cc2222]">los detalles</span></h2>
        <p class="text-[#888888] leading-relaxed mb-4">
          Reborn Detailing Studio nació de la pasión por los autos y la obsesión por el detalle. Cada vehículo que entra a nuestro taller recibe un tratamiento personalizado con los mejores productos del mercado.
        </p>
        <p class="text-[#888888] leading-relaxed">
          Nuestro equipo cuenta con años de experiencia en detailing profesional, wrap y restauración de iluminación. No solo limpiamos autos — los transformamos.
        </p>
      </div>

      <div ref="image" class="relative">
        <div class="border border-[#2a2a2a] rounded-lg overflow-hidden">
          <img src="/rebornlogo.png" alt="Reborn Detailing Studio" class="w-full object-cover" />
        </div>
        <div class="absolute -bottom-4 -left-4 border border-[#cc2222] rounded-lg w-full h-full -z-10"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const text = ref(null)
const image = ref(null)

onMounted(() => {
  gsap.from(text.value, {
    opacity: 0, x: -40, duration: 0.9,
    scrollTrigger: { trigger: text.value, start: 'top 80%' }
  })

  gsap.from(image.value, {
    opacity: 0, x: 40, duration: 0.9,
    scrollTrigger: { trigger: image.value, start: 'top 80%' }
  })
})
</script>