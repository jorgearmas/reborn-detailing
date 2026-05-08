<template>
  <div class="bg-[#cc2222] rounded-lg p-8 flex flex-col items-start gap-4 h-full">
    <div class="text-black">
      <slot name="icon" />
    </div>
    <h3 class="text-white font-bold text-xl">{{ title }}</h3>
    <p class="text-white/80 text-sm leading-relaxed">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
})
</script>