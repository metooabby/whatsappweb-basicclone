<template>
  <div class="d-flex flex-column w-75">
    <div class="p-3 bg-light border-bottom fw-bold">
      {{ contact }}
    </div>
    <div class="flex-grow-1 p-3 overflow-auto bg-white" style="max-height: 400px;">
      <div v-for="msg in messages" :key="msg" class="mb-2">
        <div class="bg-success bg-opacity-25 d-inline-block p-2 rounded">
          {{ msg }}
        </div>
      </div>
    </div>
    <form @submit.prevent="handleSend" class="d-flex p-3 border-top bg-white">
      <input v-model="newMessage" class="form-control me-2" type="text" placeholder="Type a message" />
      <button class="btn btn-success px-4" type="submit">Send</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const props = defineProps(['contact', 'messages'])
const emit = defineEmits(['send'])
const newMessage = ref('')

function handleSend() {
  if (newMessage.value.trim()) {
    emit('send', newMessage.value)
    newMessage.value = ''
  }
}
</script>
