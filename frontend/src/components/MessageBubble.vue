<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  role: {
    type: String,
    default: 'user'
  },
  message: {
    type: String,
    default: ''
  }
})
</script>

<template>
  <div :class="['mb-2 flex', props.role === 'user' ? 'justify-end' : 'justify-start']">
    <div :class="[
      'max-w-xs px-4 py-2 rounded-lg',
      props.role === 'user' ? 'bg-blue-600 text-white rounded-br-none' : 'bg-gray-200 text-gray-800 rounded-bl-none'
    ]">
      {{ message }}
    </div>
  </div>
</template>

<style scoped></style>
