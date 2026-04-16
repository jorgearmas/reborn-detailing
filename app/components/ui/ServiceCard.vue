<template>
  <div class="border border-[#2a2a2a] rounded-lg p-8 bg-[#1a1a1a] hover:border-[#cc2222] transition-all duration-300 group">
    <div class="text-[#cc2222] mb-4">
      <slot name="icon" />
    </div>
    <h3 class="text-white font-semibold text-xl mb-3">{{ title }}</h3>
    <p class="text-[#888888] text-sm leading-relaxed">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
})
</script>