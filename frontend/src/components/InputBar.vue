<script setup>
import { ref, defineEmits } from 'vue'

const emit = defineEmits(['send'])
const text = ref('')

function onSend() {
  if (text.value.trim() === '') return
  emit('send', text.value)
  text.value = ''
}
</script>

<template>
  <div class="p-4 border-t border-gray-300 flex items-end gap-2">
    <textarea v-model="text" rows="1" class="flex-1 p-2 border rounded resize-none" placeholder="Escribe un mensaje..."></textarea>
    <button @click="onSend" class="p-2 bg-blue-600 text-white rounded hover:bg-blue-700">
      Enviar
    </button>
    <button class="p-2 text-gray-500" title="Adjuntar archivo">
      <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
        <path stroke-linecap="round" stroke-linejoin="round" d="M18.375 12.75v6.375a2.625 2.625 0 01-2.625 2.625v0a2.625 2.625 0 01-2.625-2.625V7.875a1.875 1.875 0 013.75 0v10.125a1.125 1.125 0 01-2.25 0V9" />
      </svg>
    </button>
  </div>
</template>

<style scoped></style>
