# Reborn Detailing Studio — Plan de proyecto

Landing page para estudio de detailing de autos. Stack: Nuxt 3 + Vue 3 + Tailwind CSS.

---

## Stack completo

| Capa | Herramienta |
|---|---|
| Framework | Nuxt 3 |
| UI | Vue 3 + Tailwind CSS 4 |
| Animaciones | GSAP + ScrollTrigger |
| 3D (Car Lab) | Three.js |
| Galería | Swiper.js |
| Formulario | VeeValidate + EmailJS |
| Deploy | Vercel o Netlevel (gratis) |

---

## Estructura de archivos

```
reborn-detailing/
├── assets/
│   ├── css/
│   │   └── main.css          # variables de color rojo/negro, tipografía
│   ├── fonts/
│   └── images/
│       └── logo.png
├── components/
│   ├── sections/
│   │   ├── HeroSection.vue
│   │   ├── ServicesSection.vue
│   │   ├── GallerySection.vue
│   │   ├── AboutSection.vue
│   │   ├── ContactSection.vue
│   │   └── CarLabSection.vue   # se desarrolla al final
│   ├── ui/
│   │   ├── AppNavbar.vue
│   │   ├── AppFooter.vue
│   │   ├── ServiceCard.vue
│   │   └── LightBox.vue
│   └── CarLab.vue              # componente Three.js con raycasting
├── composables/
│   ├── useAnimations.js        # lógica GSAP reutilizable
│   ├── useContactForm.js       # validación y envío EmailJS
│   └── useCarLab.js            # lógica Three.js del lab (se hace al final)
├── pages/
│   └── index.vue               # página principal, ensambla todas las secciones
├── public/
│   └── models/
│       └── car.glb             # modelo 3D del auto
├── nuxt.config.ts
├── tailwind.config.ts
└── package.json
```

---

## Secciones — orden de desarrollo

### 01 · Hero / Portada
- Video o imagen de fondo oscura con overlay rojo/negro
- Tagline animado con GSAP (entrada de texto)
- Botón CTA principal → scroll hacia servicios
- Navbar fija con logo Reborn

### 02 · Servicios
- 4 cards: Limpieza de neumáticos · Detailing/Wrap de carrocería · Rejuvenecimiento de faros · Rejuvenecimiento de stops
- Hover con borde rojo y descripción desplegable
- Animación de entrada con ScrollTrigger al hacer scroll

### 03 · Galería / Portafolio
- Grid de imágenes con Swiper.js
- Lightbox al hacer clic en cada imagen
- Opción de slider antes/después

### 04 · Sobre nosotros
- Historia del estudio, equipo, valores
- Animaciones de entrada con GSAP ScrollTrigger
- Foto del equipo o del local

### 05 · Contacto
- Formulario con campos: nombre, correo, teléfono, mensaje
- Validación en tiempo real con VeeValidate
- Envío sin backend usando EmailJS
- Estado de éxito/error visible para el usuario

### 06 · Car Lab interactivo ⚠️ se desarrolla al final
- Canvas 3D con Three.js cargando el modelo `car.glb`
- El auto gira suavemente de forma automática
- Al hacer hover sobre una zona del auto aparece un tooltip con el servicio correspondiente:
  - Neumáticos → Limpieza de neumáticos
  - Carrocería → Detailing / Wrap
  - Faros → Rejuvenecimiento de faros
  - Stops (traseros) → Rejuvenecimiento de stops
- Raycasting sobre los mesh names del modelo (definir nombres exactos cuando se tenga el .glb)
- **Motivo para dejarlo al final:** es la sección más compleja técnicamente. Desarrollar primero las demás secciones garantiza que el sitio esté funcional antes de entrar a la parte 3D.

---

## Paleta de colores

```css
/* main.css */
:root {
  --color-bg:        #0d0d0d;
  --color-surface:   #1a1a1a;
  --color-red:       #cc2222;
  --color-red-hover: #e03030;
  --color-text:      #f0f0f0;
  --color-muted:     #888888;
  --color-border:    #2a2a2a;
}
```

---

## Setup inicial — comandos CLI

```bash
# 1. Crear proyecto Nuxt 3
npx nuxi@latest init reborn-detailing
cd reborn-detailing

# 2. Instalar dependencias de UI
npm install -D tailwindcss @tailwindcss/vite

# 3. Instalar librerías del proyecto
npm install gsap swiper vee-validate @vuelidate/core emailjs-com

# 4. Three.js (instalar cuando llegues al Car Lab)
npm install three
```

---

## Notas importantes

- Nuxt corre en el **puerto 3000** — sin conflicto con tu Apache en el puerto 80.
- El archivo `car.glb` va en `public/models/` para que Nuxt lo sirva estático.
- Cuando llegues al Car Lab, tener a mano los **nombres exactos de los meshes** del modelo (están en la metadata del archivo descargado).
- EmailJS requiere crear una cuenta gratuita en [emailjs.com](https://www.emailjs.com) y obtener: `service_id`, `template_id` y `public_key`.
