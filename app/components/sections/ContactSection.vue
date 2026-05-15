<template>
  <section id="contacto" class="py-24 px-6 bg-[#0d0d0d]">
    <div class="max-w-2xl mx-auto">
      <div class="text-center mb-16">
        <p class="text-[#cc2222] text-sm font-semibold tracking-[4px] uppercase mb-4">Escribinos</p>
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-8">Contacto</h2>
        <a
          href="https://wa.me/50259487589"
          target="_blank"
          rel="noopener"
          class="inline-flex items-center gap-3 bg-[#25d366] text-white text-sm font-semibold px-6 py-3 rounded-full hover:bg-[#1ebe5d] transition-colors duration-300"
        >
          <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
            <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
          </svg>
          Escríbenos por WhatsApp
        </a>
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