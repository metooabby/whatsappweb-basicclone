<template>
    <div class="w-25 border-end bg-light p-4">
        <h2 class="h5 fw-bold mb-4">Chats</h2>
        <ul class="list-unstyled">
            <li v-for="name in contacts" :key="name" @click="$emit('select', name)" class="p-2 rounded cursor-pointer"
                style="cursor: pointer;" @mouseenter="hover = name" @mouseleave="hover = null"
                :class="hover === name ? 'bg-secondary bg-opacity-25' : ''">
                {{ name }}
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from 'vue'
defineProps(['contacts'])

const hover = ref(null)
</script>
