<template>
  <nav class="fixed top-0 left-0 w-full z-50 py-5 px-4">
    <div class="mx-auto flex items-center justify-between relative">

      <!-- Menú rueda esquina izquierda -->
      <div class="relative">
        <button @click="menuOpen = !menuOpen" class="flex items-center justify-center w-10 h-10 rounded-full bg-[#1a1a1a] border border-[#2a2a2a] hover:border-[#cc2222] transition-all duration-300">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#f0f0f0" stroke-width="1.5">
            <circle cx="12" cy="12" r="10"/>
            <circle cx="12" cy="12" r="3"/>
            <line x1="12" y1="2" x2="12" y2="6"/>
            <line x1="12" y1="18" x2="12" y2="22"/>
            <line x1="2" y1="12" x2="6" y2="12"/>
            <line x1="18" y1="12" x2="22" y2="12"/>
            <line x1="4.93" y1="4.93" x2="7.76" y2="7.76"/>
            <line x1="16.24" y1="16.24" x2="19.07" y2="19.07"/>
            <line x1="4.93" y1="19.07" x2="7.76" y2="16.24"/>
            <line x1="16.24" y1="7.76" x2="19.07" y2="4.93"/>
          </svg>
        </button>

        <transition name="fade">
          <ul v-if="menuOpen" class="absolute top-14 left-0 bg-[#1a1a1a] border border-[#2a2a2a] rounded-2xl py-3 w-48 text-xs font-semibold tracking-[2px] uppercase text-[#f0f0f0] shadow-xl">
            <li><a href="#servicios" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Servicios</a></li>
            <li><a href="#galeria" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Galería</a></li>
            <li><a href="#nosotros" @click="menuOpen = false" class="block px-6 py-3 hover:text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Nosotros</a></li>
            <li><a href="#contacto" @click="menuOpen = false" class="block px-6 py-3 text-[#cc2222] hover:bg-[#0d0d0d] transition-all duration-200">Contacto</a></li>
          </ul>
        </transition>
      </div>

      <!-- Logo centrado -->
      <a href="/" class="absolute left-1/2 -translate-x-1/2">
        <img src="/rebornlogo.png" alt="Reborn Detailing Studio" class="w-64 object-contain" />
      </a>

      <!-- Spacer derecho para balancear -->
      <div class="w-10"></div>

    </div>
  </nav>
</template>

<script setup>
const menuOpen = ref(false)
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}
</style>