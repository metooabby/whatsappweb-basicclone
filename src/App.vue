<template>
  <div class="d-flex vh-100">
    <Sidebar :contacts="contacts" @select="selectContact" />
    <ChatWindow :contact="selectedContact" :messages="messages[selectedContact]" @send="sendMessage" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Sidebar from './components/sidebarUsersList.vue'
import ChatWindow from './components/chatWindow.vue'

const contacts = ['Alice', 'Bob', 'Charlie']
const selectedContact = ref('Alice')

const messages = ref({
  Alice: [],
  Bob: [],
  Charlie: []
})

function selectContact(name) {
  selectedContact.value = name
}

function sendMessage(text) {
  messages.value[selectedContact.value].push(text)
}
</script>
