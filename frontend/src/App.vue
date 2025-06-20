<script setup>
import { ref } from 'vue'
import Sidebar from './components/Sidebar.vue'
import ChatWindow from './components/ChatWindow.vue'

const sessions = ref(['Chat de ejemplo'])
const messages = ref([
  { role: 'assistant', content: 'Hola, ¿en qué puedo ayudarte?' },
  { role: 'user', content: 'Necesito información sobre tu proyecto.' },
  { role: 'assistant', content: 'Claro, este es un demo con Vue y Tailwind.' }
])

function handleSend(msg) {
  messages.value.push({ role: 'user', content: msg })
  // Aquí se agregaría la llamada al backend en un futuro
  messages.value.push({ role: 'assistant', content: 'Respuesta simulada.' })
}
</script>

<template>
  <div class="h-screen flex">
    <Sidebar :sessions="sessions" @new-chat="() => {}" @select="() => {}" @clear="() => {}" />
    <main class="flex-1">
      <ChatWindow :messages="messages" @send="handleSend" />
    </main>
  </div>
</template>

<style scoped></style>
