<template>
  <div class="flip-card h-64 cursor-pointer">
    <div class="flip-card-inner">
      <!-- Frente -->
      <div class="flip-card-front rounded-lg border border-black overflow-hidden relative">
        <video
          autoplay muted loop playsinline
          class="absolute inset-0 w-full h-full object-cover"
          :src="video"
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
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  video: String,
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