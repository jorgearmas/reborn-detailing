<template>
  <div class="min-h-screen bg-[#0d0d0d]">
    <AppNavbar :minimal="true" />

    <main class="pt-32 pb-24 px-6">
      <div class="max-w-6xl mx-auto">

        <!-- Header -->
        <div class="text-center mb-16">
          <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Lo que ofrecemos</p>
          <h1 class="text-4xl md:text-5xl font-bold text-white">Paquetes</h1>
        </div>

        <!-- Grid 3x2 -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div
            v-for="(pkg, index) in packages"
            :key="index"
            class="border border-[#2a2a2a] rounded-lg overflow-hidden flex flex-col"
          >
            <!-- Preview PDF -->
            <div class="relative w-full bg-[#1a1a1a]" style="height: 320px">
              <iframe
                :src="pkg.pdf + '#toolbar=0&navpanes=0&scrollbar=0'"
                class="absolute inset-0 w-full h-full border-0 pointer-events-none"
                loading="lazy"
              ></iframe>
            </div>

            <!-- Footer de la card -->
            <div class="flex items-center justify-between px-5 py-4 bg-[#1a1a1a] border-t border-[#2a2a2a]">
              <span class="text-white font-semibold text-sm tracking-wide">{{ pkg.name }}</span>
              <a
                :href="pkg.pdf"
                target="_blank"
                class="text-[#cc2222] text-xs font-semibold tracking-widest uppercase border-b border-[#cc2222] pb-0.5 hover:text-white hover:border-white transition-all duration-300"
              >
                Ver PDF →
              </a>
            </div>
          </div>
        </div>

      </div>
    </main>

    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'

const activeIndex = ref(null)

const packages = ref([
  { name: 'Full Interior',          pdf: '/paquetes/Full_Interior.pdf' },
  { name: 'Full Power',             pdf: '/paquetes/Full_Power.pdf' },
  { name: 'Premier Style',          pdf: '/paquetes/Premier_Style.pdf' },
  { name: 'Reborn Detail Plata',    pdf: '/paquetes/Reborn_Detail_Plata.pdf' },
  { name: 'Reborn Detail Oro',      pdf: '/paquetes/Reborn_Detail_Oro.pdf' },
  { name: 'Reborn Detail Diamante', pdf: '/paquetes/Reborn_Detail_Diamante.pdf' },
])

const toggle = (index) => {
  activeIndex.value = activeIndex.value === index ? null : index
}
</script>
