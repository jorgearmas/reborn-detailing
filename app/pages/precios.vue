<template>
  <div class="min-h-screen bg-[#0d0d0d]">
    <AppNavbar :minimal="true" />

    <main class="pt-32 pb-24 px-6">
      <div class="max-w-4xl mx-auto">

        <div class="text-center mb-16">
          <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Nuestros precios</p>
          <h1 class="text-4xl md:text-5xl font-bold text-white mb-4">Precios</h1>
          <p class="text-[#555] text-sm tracking-widest uppercase">Pasa el cursor sobre cada área del vehículo</p>
        </div>

        <!-- Contenedor imagen + hotspots -->
        <div class="relative w-full" @mouseleave="hovered = null">
          <img
            src="/gallery/sports-car.png"
            alt="Auto deportivo"
            class="w-full h-auto select-none"
            draggable="false"
          />

          <!-- SVG overlay con hotspots y tooltips -->
          <svg
            viewBox="0 0 600 338"
            class="absolute inset-0 w-full h-full"
            xmlns="http://www.w3.org/2000/svg"
          >
            <!-- ══ LÍNEAS CONECTOR ══ -->
            <line v-if="hovered === 'aro-front'"
              x1="132" y1="236" x2="30" y2="310"
              stroke="#cc2222" stroke-width="1.2" stroke-dasharray="5,3"/>

            <line v-if="hovered === 'aro-rear'"
              x1="468" y1="236" x2="530" y2="310"
              stroke="#cc2222" stroke-width="1.2" stroke-dasharray="5,3"/>

            <line v-if="hovered === 'faros'"
              x1="62" y1="168" x2="35" y2="108"
              stroke="#cc2222" stroke-width="1.2" stroke-dasharray="5,3"/>

            <line v-if="hovered === 'vidrio'"
              x1="300" y1="92" x2="300" y2="30"
              stroke="#cc2222" stroke-width="1.2" stroke-dasharray="5,3"/>

            <line v-if="hovered === 'carroceria'"
              x1="390" y1="168" x2="430" y2="108"
              stroke="#cc2222" stroke-width="1.2" stroke-dasharray="5,3"/>

            <!-- ══ TOOLTIP BOXES ══ -->

            <g v-if="hovered === 'aro-front'">
              <rect x="2" y="306" width="242" height="28" rx="4" fill="#1a1a1a" stroke="#cc2222" stroke-width="1"/>
              <text x="12" y="324" fill="#f0f0f0" font-size="10" font-family="Inter,sans-serif" font-weight="600">Rejuvenecimiento de Aros — <tspan fill="#cc2222" font-weight="700">Q. 1,000.00</tspan></text>
            </g>

            <g v-if="hovered === 'aro-rear'">
              <rect x="356" y="306" width="242" height="28" rx="4" fill="#1a1a1a" stroke="#cc2222" stroke-width="1"/>
              <text x="366" y="324" fill="#f0f0f0" font-size="10" font-family="Inter,sans-serif" font-weight="600">Rejuvenecimiento de Aros — <tspan fill="#cc2222" font-weight="700">Q. 1,000.00</tspan></text>
            </g>

            <g v-if="hovered === 'faros'">
              <rect x="2" y="74" width="158" height="28" rx="4" fill="#1a1a1a" stroke="#cc2222" stroke-width="1"/>
              <text x="12" y="92" fill="#f0f0f0" font-size="10" font-family="Inter,sans-serif" font-weight="600">Pulido de Faros — </text>
              <text x="100" y="92" fill="#cc2222" font-size="10" font-family="Inter,sans-serif" font-weight="700">Q. 1,000.00</text>
            </g>

            <g v-if="hovered === 'vidrio'">
              <rect x="208" y="4" width="184" height="28" rx="4" fill="#1a1a1a" stroke="#cc2222" stroke-width="1"/>
              <text x="218" y="22" fill="#f0f0f0" font-size="10" font-family="Inter,sans-serif" font-weight="600">Polarizado — </text>
              <text x="289" y="22" fill="#cc2222" font-size="10" font-family="Inter,sans-serif" font-weight="700">Q. 1,000.00</text>
            </g>

            <g v-if="hovered === 'carroceria'">
              <rect x="338" y="4" width="258" height="60" rx="4" fill="#1a1a1a" stroke="#cc2222" stroke-width="1"/>
              <text x="350" y="22"  fill="#f0f0f0" font-size="9.5" font-family="Inter,sans-serif">Detailing Diamante — <tspan fill="#cc2222" font-weight="700">Q. 1,500.00</tspan></text>
              <text x="350" y="40"  fill="#f0f0f0" font-size="9.5" font-family="Inter,sans-serif">Detailing Oro — <tspan fill="#cc2222" font-weight="700">Q. 1,000.00</tspan></text>
              <text x="350" y="58"  fill="#f0f0f0" font-size="9.5" font-family="Inter,sans-serif">Detailing Plata — <tspan fill="#cc2222" font-weight="700">Q. 500.00</tspan></text>
            </g>

            <!-- ══ HOTSPOT ZONES ══ -->

            <!-- Carrocería (base) -->
            <path
              d="M 30,200 L 30,140 C 60,100 130,80 200,78 L 370,72 C 420,72 470,90 520,130 L 560,180 L 560,220 L 30,220 Z"
              fill="transparent" class="cursor-pointer"
              @mouseenter="hovered = 'carroceria'"
            />

            <!-- Vidrios (encima de carrocería) -->
            <path
              d="M 222,118 L 248,80 L 378,72 L 400,118 L 222,118 Z"
              fill="transparent" class="cursor-pointer"
              @mouseenter="hovered = 'vidrio'"
            />

            <!-- Faro delantero -->
            <path
              d="M 38,188 L 44,152 L 88,150 L 90,174 L 62,186 Z"
              fill="transparent" class="cursor-pointer"
              @mouseenter="hovered = 'faros'"
            />

            <!-- Aro delantero -->
            <circle cx="158" cy="266" r="64" fill="transparent" class="cursor-pointer"
              @mouseenter="hovered = 'aro-front'"/>

            <!-- Aro trasero -->
            <circle cx="448" cy="266" r="64" fill="transparent" class="cursor-pointer"
              @mouseenter="hovered = 'aro-rear'"/>

          </svg>
        </div>

      </div>
    </main>

    <AppFooter />
  </div>
</template>

<script setup>
import AppNavbar from '../components/ui/AppNavbar.vue'
import AppFooter from '../components/ui/AppFooter.vue'

const hovered = ref(null)
</script>
