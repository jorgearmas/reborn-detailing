<template>
  <nav class="fixed top-0 left-0 w-full z-50 py-5 px-4">
    <div class="mx-auto flex items-center justify-between relative">

      <!-- Menú hamburguesa esquina izquierda -->
      <div class="relative">
        <button @click="menuOpen = !menuOpen" class="flex items-center justify-center w-10 h-10 rounded-full bg-[#1a1a1a] border border-[#2a2a2a] hover:border-[#cc2222] transition-all duration-300">
          <svg width="18" height="14" viewBox="0 0 18 14" fill="none">
            <line x1="0" y1="1" x2="18" y2="1" stroke="#f0f0f0" stroke-width="1.5" stroke-linecap="round"/>
            <line x1="0" y1="7" x2="18" y2="7" stroke="#f0f0f0" stroke-width="1.5" stroke-linecap="round"/>
            <line x1="0" y1="13" x2="18" y2="13" stroke="#f0f0f0" stroke-width="1.5" stroke-linecap="round"/>
          </svg>
        </button>

        <transition name="fade">
          <ul v-if="menuOpen" class="absolute top-14 left-0 bg-[#1a1a1a] border border-[#2a2a2a] rounded-2xl py-3 w-48 text-xs font-semibold tracking-[2px] uppercase text-[#f0f0f0] shadow-xl">
            <li><a href="/" @click="menuOpen = false" class="block px-6 py-3 text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Inicio</a></li>
            <template v-if="!minimal">
              <li><a href="#servicios" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Servicios</a></li>
              <li><a href="#galeria" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Galería</a></li>
              <li><a href="#nosotros" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Nosotros</a></li>
              <li><a href="/paquetes" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Paquetes</a></li>
              <li><a href="/precios" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Precios</a></li>
              <li><a href="#contacto" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Contacto</a></li>
            </template>
          </ul>
        </transition>
      </div>

      <!-- Logo centrado — desaparece al hacer scroll -->
      <transition name="fade">
        <a v-if="!scrolled" href="/" class="absolute left-1/2 -translate-x-1/2">
          <img src="/rebornlogo.png" alt="Reborn Detailing Studio" class="w-64 object-contain" />
        </a>
      </transition>

    </div>
  </nav>
</template>

<script setup>
const props = defineProps({ minimal: { type: Boolean, default: false } })
const menuOpen = ref(false)
const scrolled = ref(false)

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 80
  })
})
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
