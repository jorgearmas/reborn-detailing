<template>
  <nav
    ref="navbar"
    class="fixed top-0 left-0 w-full z-50 transition-all duration-300"
    :class="scrolled ? 'bg-[#0d0d0d] border-b border-[#2a2a2a]' : 'bg-transparent'"
  >
    <div class="max-w-6xl mx-auto px-6 py-4 flex items-center justify-between">
      <img src="rebornlogo.png" alt="Reborn Detailing Studio" class="h-10" />
        <ul class="hidden md:flex items-center gap-8 text-sm text-[#f0f0f0]">
          <li><a href="/servicios" class="hover:text-[#cc2222] transition-colors">Servicios</a></li>
          <li><a href="/galeria" class="hover:text-[#cc2222] transition-colors">Galería</a></li>
          <li><a href="/nosotros" class="hover:text-[#cc2222] transition-colors">Nosotros</a></li>
          <li>
            <a href="/contacto" class="border border-[#cc2222] text-[#cc2222] px-4 py-2 rounded hover:bg-[#cc2222] hover:text-white transition-all">
              Contacto
            </a>
          </li>
        </ul>
    </div>
  </nav>
</template>

<script setup>
const scrolled = ref(false)

onMounted(() => {
  window.addEventListener('scroll', () => {
    scrolled.value = window.scrollY > 50
  })
})
</script>