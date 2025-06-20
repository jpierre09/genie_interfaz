<script setup>
import { defineProps, defineEmits } from 'vue'
import MessageBubble from './MessageBubble.vue'
import InputBar from './InputBar.vue'

const props = defineProps({
  messages: {
    type: Array,
    default: () => []
  }
})

const emit = defineEmits(['send'])
</script>

<template>
  <div class="flex flex-col h-full">
    <header class="p-4 border-b border-gray-300 text-lg font-semibold">Mi Asistente</header>
    <div class="flex-1 overflow-y-auto p-4 space-y-2" id="messages">
      <MessageBubble v-for="(m, idx) in props.messages" :key="idx" :role="m.role" :message="m.content" />
    </div>
    <InputBar @send="msg => emit('send', msg)" />
  </div>
</template>

<style scoped></style>
