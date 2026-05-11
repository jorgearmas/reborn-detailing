<template>
  <section id="galeria" class="py-24 px-6 bg-[#0d0d0d]">
    <div class="max-w-6xl mx-auto">
      <div ref="header" class="text-center mb-16">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Nuestro trabajo</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white">Portafolio</h2>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div v-for="(item, index) in portfolio" :key="index" class="rounded-lg overflow-hidden">
          <p class="text-white font-bold text-lg tracking-widest uppercase mb-3">{{ item.label }}</p>
          <div
            class="relative h-64 select-none overflow-hidden rounded-lg cursor-col-resize"
            @mousedown="startDrag($event, index)"
            @mousemove="onDrag($event, index)"
            @mouseup="stopDrag"
            @mouseleave="stopDrag"
            @touchstart="startDragTouch($event, index)"
            @touchmove="onDragTouch($event, index)"
            @touchend="stopDrag"
          >
            <!-- After (fondo) -->
            <img :src="item.after" class="absolute inset-0 w-full h-full object-cover" />

            <!-- Before (recortado) -->
            <div class="absolute inset-0 overflow-hidden" :style="{ width: sliders[index] + '%' }">
              <img :src="item.before" class="absolute inset-0 w-full h-full object-cover" :style="{ width: (100 / sliders[index]) * 100 + '%', maxWidth: 'none' }" />
            </div>

            <!-- Línea divisora -->
            <div class="absolute top-0 bottom-0 w-0.5 bg-white shadow-lg" :style="{ left: sliders[index] + '%' }">
              <div class="absolute top-1/2 -translate-y-1/2 -translate-x-1/2 w-8 h-8 bg-white rounded-full flex items-center justify-center shadow-lg">
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#0d0d0d" stroke-width="2.5">
                  <path d="M9 18l-6-6 6-6M15 6l6 6-6 6"/>
                </svg>
              </div>
            </div>

            <!-- Labels -->
            <span class="absolute top-3 left-3 text-xs font-bold tracking-widest uppercase bg-black bg-opacity-60 text-white px-2 py-1 rounded">Antes</span>
            <span class="absolute top-3 right-3 text-xs font-bold tracking-widest uppercase bg-[#cc2222] text-white px-2 py-1 rounded">Después</span>
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
  { label: 'Corsa', before: '/gallery/Corsa-Dirty.png', after: '/gallery/Corsa-Clean.png' },
  { label: 'RAV4', before: '/gallery/RAV-Dirty.png', after: '/gallery/RAV-Clean.png' },
  { label: 'Corolla', before: '/gallery/Corolla-Dirty.png', after: '/gallery/Corolla-Clean.png' },
]

const sliders = ref([50, 50, 50])
const dragging = ref(null)
const header = ref(null)

const startDrag = (e, index) => {
  dragging.value = index
}

const onDrag = (e, index) => {
  if (dragging.value !== index) return
  const rect = e.currentTarget.getBoundingClientRect()
  const x = Math.max(0, Math.min(e.clientX - rect.left, rect.width))
  sliders.value[index] = (x / rect.width) * 100
}

const stopDrag = () => {
  dragging.value = null
}

const startDragTouch = (e, index) => {
  dragging.value = index
}

const onDragTouch = (e, index) => {
  if (dragging.value !== index) return
  const rect = e.currentTarget.getBoundingClientRect()
  const x = Math.max(0, Math.min(e.touches[0].clientX - rect.left, rect.width))
  sliders.value[index] = (x / rect.width) * 100
}

onMounted(() => {
  gsap.from(header.value, {
    opacity: 0, y: 30, duration: 0.8,
    scrollTrigger: { trigger: header.value, start: 'top 80%' }
  })
})
</script>