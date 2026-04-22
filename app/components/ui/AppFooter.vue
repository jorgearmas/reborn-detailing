<template>
  <footer class="bg-[#1a1a1a] border-t border-[#2a2a2a] py-10">
    <div class="max-w-6xl mx-auto px-6 flex flex-col md:flex-row items-center justify-between gap-6">
      <img src="rebornlogo.png" alt="Reborn Detailing Studio" class="h-10" />

      <p class="text-[#888888] text-sm">
        © {{ new Date().getFullYear() }} Reborn Detailing Studio. Todos los derechos reservados.
      </p>

      <div class="flex items-center gap-6 text-sm text-[#888888]">
        <a href="#servicios" class="hover:text-[#cc2222] transition-colors">Servicios</a>
        <a href="#galeria" class="hover:text-[#cc2222] transition-colors">Galería</a>
        <a href="#contacto" class="hover:text-[#cc2222] transition-colors">Contacto</a>
      </div>
    </div>
  </footer>
</template>