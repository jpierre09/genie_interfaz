<script setup>
import { defineEmits, defineProps } from 'vue'

const props = defineProps({
  sessions: {
    type: Array,
    default: () => []
  },
  active: {
    type: Number,
    default: 0
  }
})

const emit = defineEmits(['new-chat', 'select', 'clear'])
</script>

<template>
  <aside class="w-64 bg-gray-800 text-white flex flex-col h-full">
    <div class="p-4 flex justify-between items-center border-b border-gray-700">
      <span class="text-lg font-semibold">Historial</span>
      <button @click="emit('clear')" class="text-red-400 hover:text-red-500" title="Borrar historial">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>
    <button @click="emit('new-chat')" class="m-4 px-4 py-2 bg-blue-600 hover:bg-blue-700 rounded text-sm">Nuevo chat</button>
    <div class="flex-1 overflow-y-auto px-4 space-y-2 pb-4">
      <div v-for="(session, index) in props.sessions" :key="index"
           @click="emit('select', index)"
           :class="['p-2 rounded cursor-pointer', index === props.active ? 'bg-gray-700' : 'hover:bg-gray-700']">
        {{ session }}
      </div>
    </div>
  </aside>
</template>

<style scoped>
/****** No custom styles, relying on Tailwind *****/
</style>
