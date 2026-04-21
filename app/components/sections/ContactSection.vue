<template>
  <section id="contacto" class="py-24 px-6">
    <div class="max-w-2xl mx-auto">
      <div class="text-center mb-16">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Escribinos</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white">Contacto</h2>
      </div>

      <form @submit.prevent="handleSubmit" class="flex flex-col gap-6">
        <div>
          <label class="text-[#888888] text-sm mb-2 block">Nombre</label>
          <input
            v-model="form.name"
            type="text"
            placeholder="Tu nombre"
            class="w-full bg-[#1a1a1a] border border-[#2a2a2a] rounded px-4 py-3 text-white placeholder-[#555] focus:outline-none focus:border-[#cc2222] transition-colors"
          />
          <span v-if="errors.name" class="text-[#cc2222] text-xs mt-1 block">{{ errors.name }}</span>
        </div>

        <div>
          <label class="text-[#888888] text-sm mb-2 block">Correo</label>
          <input
            v-model="form.email"
            type="email"
            placeholder="tu@correo.com"
            class="w-full bg-[#1a1a1a] border border-[#2a2a2a] rounded px-4 py-3 text-white placeholder-[#555] focus:outline-none focus:border-[#cc2222] transition-colors"
          />
          <span v-if="errors.email" class="text-[#cc2222] text-xs mt-1 block">{{ errors.email }}</span>
        </div>

        <div>
          <label class="text-[#888888] text-sm mb-2 block">Teléfono</label>
          <input
            v-model="form.phone"
            type="tel"
            placeholder="Tu número"
            class="w-full bg-[#1a1a1a] border border-[#2a2a2a] rounded px-4 py-3 text-white placeholder-[#555] focus:outline-none focus:border-[#cc2222] transition-colors"
          />
        </div>

        <div>
          <label class="text-[#888888] text-sm mb-2 block">Mensaje</label>
          <textarea
            v-model="form.message"
            rows="5"
            placeholder="¿En qué podemos ayudarte?"
            class="w-full bg-[#1a1a1a] border border-[#2a2a2a] rounded px-4 py-3 text-white placeholder-[#555] focus:outline-none focus:border-[#cc2222] transition-colors resize-none"
          ></textarea>
          <span v-if="errors.message" class="text-[#cc2222] text-xs mt-1 block">{{ errors.message }}</span>
        </div>

        <button
          type="submit"
          :disabled="sending"
          class="bg-[#cc2222] text-white py-4 rounded font-semibold hover:bg-[#e03030] transition-all disabled:opacity-50"
        >
          {{ sending ? 'Enviando...' : 'Enviar mensaje' }}
        </button>

        <p v-if="success" class="text-green-400 text-center text-sm">¡Mensaje enviado correctamente!</p>
        <p v-if="error" class="text-[#cc2222] text-center text-sm">Hubo un error al enviar. Intentá de nuevo.</p>
      </form>
    </div>
  </section>
</template>

<script setup>
const form = ref({ name: '', email: '', phone: '', message: '' })
const errors = ref({})
const sending = ref(false)
const success = ref(false)
const error = ref(false)

const validate = () => {
  errors.value = {}
  if (!form.value.name) errors.value.name = 'El nombre es requerido'
  if (!form.value.email) errors.value.email = 'El correo es requerido'
  if (!form.value.message) errors.value.message = 'El mensaje es requerido'
  return Object.keys(errors.value).length === 0
}

const handleSubmit = async () => {
  if (!validate()) return
  sending.value = true
  error.value = false
  success.value = false

  try {
    // EmailJS se configura aquí cuando tengas las credenciales
    // await emailjs.send('SERVICE_ID', 'TEMPLATE_ID', form.value, 'PUBLIC_KEY')
    await new Promise(resolve => setTimeout(resolve, 1000))
    success.value = true
    form.value = { name: '', email: '', phone: '', message: '' }
  } catch (e) {
    error.value = true
  } finally {
    sending.value = false
  }
}
</script>