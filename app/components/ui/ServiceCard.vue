<template>
  <div ref="cardEl" class="flip-card h-64 cursor-pointer">
    <div class="flip-card-inner">
      <!-- Frente -->
      <div class="flip-card-front rounded-lg border border-black overflow-hidden relative">
        <video
          ref="videoEl"
          muted loop playsinline
          class="absolute inset-0 w-full h-full object-cover"
        ></video>
        <div class="absolute inset-0 bg-black bg-opacity-50"></div>
        <div class="relative z-10 h-full flex flex-col items-center justify-center gap-4 p-8">
          <slot name="icon" />
          <h3 class="text-white font-bold text-xl text-center">{{ title }}</h3>
        </div>
      </div>

      <!-- Reverso -->
      <div class="flip-card-back bg-[#0d0d0d] rounded-lg p-8 flex flex-col items-center justify-center gap-4 border border-[#cc2222]">
        <h3 class="text-[#cc2222] font-bold text-xl text-center mb-2">{{ title }}</h3>
        <p class="text-white text-sm text-center leading-relaxed whitespace-pre-line">{{ description }}</p>
        <a href="#contacto" class="mt-2 text-xs font-semibold tracking-widest uppercase text-[#cc2222] border-b border-[#cc2222] pb-0.5 hover:text-white hover:border-white transition-all duration-300">
          Cotiza Ahora →
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  description: String,
  video: String,
})

const cardEl = ref(null)
const videoEl = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      videoEl.value.src = props.video
      videoEl.value.play().catch(() => {})
      observer.disconnect()
    }
  }, { threshold: 0.1 })

  observer.observe(cardEl.value)
})
</script>

<style scoped>
.flip-card {
  perspective: 1000px;
  width: 100%;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.7s ease;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
}

.flip-card-back {
  transform: rotateY(180deg);
}
</style>
